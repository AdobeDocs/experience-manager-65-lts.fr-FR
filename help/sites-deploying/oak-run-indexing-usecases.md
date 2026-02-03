---
title: Indexation du fichier Oak-run.jar – Scénarios d’utilisation
description: Découvrez les différents cas d’utilisation pour effectuer une indexation avec l’outil Oak-run.
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: deploying
noindex: true
solution: Experience Manager, Experience Manager Sites
feature: Deploying
role: Admin
exl-id: a7a8a20a-e513-43df-80b7-1e6daf957f20
source-git-commit: c714e51f0c0368988ce552969747ab5fce5c186f
workflow-type: tm+mt
source-wordcount: '1348'
ht-degree: 47%

---

# Indexation du fichier Oak-run.jar – Scénarios d’utilisation{#oak-run-jar-indexing-use-cases}

Oak-run prend en charge tous les scénarios d’indexation sur la ligne de commande, sans qu’il faille orchestrer l’exécution de ces scénarios par le biais de la console JMX d’AEM.

Les principaux avantages de l’utilisation de la commande d’index `oak-run.jar` pour gérer les index Oak sont les suivants :

* La commande d’index Oak-run fournit un nouveau jeu d’outils d’indexation depuis la version AEM 6.4.
* Oak-run diminue le temps de réindexation, ce qui réduit le délai de réindexation sur des référentiels plus volumineux.
* Oak-run réduit la consommation de ressources lors de la réindexation dans AEM, ce qui entraîne de meilleures performances globales du système.
* Oak-run fournit une réindexation hors bande, prenant en charge les situations dans lesquelles la production doit être disponible et ne peut pas tolérer la maintenance ou les temps d&#39;arrêt autrement nécessaires à la réindexation.

Les sections ci-dessous fournissent des exemples de commandes. La commande d’index Oak-run prend en charge toutes les configurations NodeStore et BlobStore. Les exemples fournis ci-dessous concernent les configurations comportant FileDataStore et SegmentNodeStore.

## Cas d’utilisation 1 - Vérification de la cohérence de l’index {#usercase1indexconsistencycheck}

Ce cas d’utilisation est lié à la corruption d’index. Parfois, il n’était pas possible de déterminer lesquels des index étaient corrompus. Par conséquent, Adobe a fourni des outils offrant les fonctionnalités suivantes :

* Effectue des contrôles de cohérence sur tous les index et génère un rapport sur les index valides et non valides.
* Les fonctionnalités peuvent être utilisées même si AEM n’est pas accessible.
* Cette méthode est facile à utiliser.

Utilisez `--index-consistency-check` pour rechercher des index corrompus :

```shell
java -jar oak-run*.jar index --fds-path=/path/to/datastore  /path/to/segmentstore/ --index-consistency-check
```

Cette opération génère un rapport dans `indexing-result/index-consistency-check-report.txt`. Voir ci-dessous pour un exemple de rapport :

```
Valid indexes :
        - /content/oak:index/enablementResourceName
        - /oak:index/cqProjectLucene
        - /oak:index/cqTagLucene
        - /oak:index/lucene
        - /oak:index/ntBaseLucene
        - /oak:index/socialLucene
    Invalid indexes :
        - /oak:index/atDamIndex
        - /oak:index/atIndex
        - /oak:index/cqPageLucene
        - /oak:index/damAssetLucene
        - /oak:index/groups
        - /oak:index/slingeventJob
        - /oak:index/users
        - /oak:index/workflowDataLucene
    Ignored indexes as these are not of type lucene:
        - /oak:index/acPrincipalName
        - /oak:index/active
```

### Avantages {#uc1benefits}

L’assistance et les administrateurs système peuvent utiliser les outils pour identifier rapidement les index corrompus et les réindexer.

## Cas d’utilisation 2 - Statistiques d’index {#usecase2indexstatistics}

Pour diagnostiquer certains cas concernant les performances des requêtes, Adobe a souvent eu besoin d’une définition d’index existante, de statistiques liées à l’index provenant de la configuration du client. Pour faciliter la résolution des problèmes, Adobe a créé des outils qui effectuent les opérations suivantes :

1. vident toute la définition d’index présente sur le système dans un seul fichier JSON ;

1. vident les statistiques importantes des index existants ;

1. vident le contenu de l’index en vue d’une analyse hors ligne ;

1. Il est utilisable même si AEM n’est pas accessible

Vous pouvez effectuer les opérations ci-dessus à l’aide des commandes d’index suivantes :

* `--index-info` : collecte et vide diverses statistiques liées aux index.

* `--index-definitions` : collecte et vide des définitions d’index.

* `--index-dump` : vide le contenu de l’index.

Vous trouverez, ci-dessous, un exemple d’utilisation pratique des commandes :

```shell
java -jar oak-run*.jar index --fds-path=/path/to/datastore  /path/to/segmentstore/ --index-info --index-definitions --index-dump
```

Les rapports sont générés dans `indexing-result/index-info.txt` et dans `indexing-result/index-definitions.json`

En outre, les mêmes détails sont fournis par le biais de la console web et font partie du fichier zip de vidage de la configuration. Ils se trouvent à l’emplacement suivant :

`https://serverhost:serverport/system/console/status-oak-index-defn`

### Avantages {#uc2benefits}

Cet outil permet de collecter rapidement tous les détails requis liés aux problèmes d’indexation ou de requête et de réduire le temps passé à extraire ces informations.

## Cas d’utilisation 3 - Réindexation {#usecase3reindexing}

En fonction des [scénarios](https://jackrabbit.apache.org/oak/docs/query/indexing.html#reindexing), une réindexation doit être parfois effectuée. Actuellement, vous effectuez une réindexation en définissant l’indicateur `reindex` sur `true` dans le nœud de définition d’index à l’aide de CRXDE ou de l’interface utilisateur du Gestionnaire d’index. Une fois l’indicateur défini, la réindexation s’exécute de manière asynchrone. Une fois l’indicateur défini, la réindexation est effectuée de manière asynchrone.

Voici quelques points à noter autour de la réindexation :

* La réindexation s’avère beaucoup plus lente sur les configurations `DocumentNodeStore` que sur les configurations `SegmentNodeStore` dans lesquelles tout le contenu est local.

* Avec la conception actuelle, la situation est la suivante : pendant la réindexation, le moteur d’indexation asynchrone est bloqué, et tous les autres index deviennent obsolètes et ne sont plus mis à jour pendant la durée de l’indexation. Par conséquent, si le système est en cours d’utilisation, il se peut que les utilisateurs n’aient pas accès à des résultats à jour.
* La réindexation implique la traversée de l’ensemble du référentiel, ce qui peut placer une charge élevée sur la configuration d’AEM et avoir ainsi un impact sur l’expérience de l’utilisateur final.
* Dans le cas d’une installation `DocumentNodeStore` dans laquelle la réindexation peut prendre un temps considérable, une défaillance de connexion à la base de données Mongo pendant l’opération peut interrompre l’indexation. Dans ce cas, vous devez redémarrer l’indexation à partir de zéro.


* La réindexation peut parfois prendre beaucoup de temps en raison de l’extraction de texte. Un tel problème peut se produire lorsqu’il est spécifique à des configurations comportant de nombreux fichiers PDF, où le temps passé sur l’extraction de texte peut avoir une incidence sur le temps d’indexation.

Pour atteindre ces objectifs, l’outil d’indexation exécuté par Oak prend en charge différents modes de réindexation qui peuvent être utilisés selon les besoins. La commande d’index exécutée par Oak offre les avantages suivants :

* **réindexation hors-bande** : la réindexation exécutée par Oak peut être effectuée séparément d’une configuration AEM en cours d’exécution, ce qui réduit l’impact sur l’instance AEM en cours d’utilisation.

* **Réindexation hors-piste** : la réindexation s’effectue sans que cela n’ait d’incidence sur les opérations d’indexation. L’indexeur asynchrone peut continuer à indexer d’autres index ;

* **Réindexation simplifiée pour les installations** : pour les installations `DocumentNodeStore`, la réindexation peut être réalisée avec une seule commande, ce qui garantit une exécution optimale.

* **Prise en charge de la mise à jour des définitions d’index et de l’ajout de nouvelles définitions d’index**

### Réindexation – DocumentNodeStore {#reindexdocumentnodestore}

Pour les installations `DocumentNodeStore`, vous pouvez effectuer une réindexation à l’aide d’une seule commande Oak-run :

```shell
java -jar oak-run*.jar index --reindex --index-paths=/oak:index/lucene --read-write --fds-path=/path/to/datastore mongodb://server:port/aem
```

Cette opération offre les avantages suivants :

* Impact minimal sur l’exécution des instances AEM. La plupart des lectures peuvent être effectuées à partir de serveurs secondaires et les activités de traversée requises pour la réindexation n’ont pas de répercussions négatives sur les caches AEM en cours d’exécution.
* Les utilisateurs et utilisatrices peuvent également fournir un fichier JSON d’un index nouveau ou mis à jour par le biais de l’option `--index-definitions-file`.

### Réindexation – SegmentNodeStore {#reindexsegmentnodestore}

Pour les installations `SegmentNodeStore`, la réindexation peut être effectuée de l’une des façons suivantes :

#### Réindexation en ligne - SegmentNodeStore {#onlinereindexsegmentnodestore}

Suivez la méthode habituelle où la réindexation est effectuée en définissant l’indicateur `reindex`.

#### Réindexation en ligne - SegmentNodeStore - L’instance AEM est en cours d’exécution {#onlinereindexsegmentnodestoretheaeminstanceisrunning}

Dans le cas des installations `SegmentNodeStore`, un seul processus peut accéder à des fichiers de segment en mode lecture/écriture. Par conséquent, certaines opérations de l’indexation exécutée par Oak nécessitent la réalisation d’étapes manuelles supplémentaires, notamment :

1. Texte des étapes.
1. Connectez le `oak-run` au même référentiel que celui utilisé par AEM en mode lecture seule.
1. Procédez à l’indexation en prenant comme exemple ce qui suit :

   ```shell
   java -jar oak-run-1.7.6.jar index --fds-path=/Users/dhasler/dev/cq/quickstart/target/crx-quickstart/repository/datastore/ --checkpoint 26b7da38-a699-45b2-82fb-73aa2f9af0e2 --reindex --index-paths=/oak:index/lucene /Users/dhasler/dev/cq/quickstart/target/crx-quickstart/repository/segmentstore/
   ```

1. Enfin, importez les fichiers d’index créés au moyen de l’opération `IndexerMBean#importIndex` à partir de l’emplacement où Oak-run a enregistré les fichiers d’indexation après avoir exécuté la commande ci-dessus.

Dans ce scénario, vous n’avez pas besoin d’arrêter le serveur AEM ni de configurer une nouvelle instance. Cependant, comme l’indexation implique la traversée de l’ensemble du référentiel, cela augmenterait la charge d’E/S sur l’installation, ce qui aurait un impact négatif sur les performances d’exécution.

#### Réindexation en ligne - SegmentNodeStore - L’instance AEM est arrêtée {#onlinereindexsegmentnodestoreaeminstanceisdown}

Pour les installations `SegmentNodeStore`, vous pouvez effectuer une réindexation à l’aide d’une seule commande Oak-run. Toutefois, l’instance AEM doit être arrêtée.

Vous pouvez déclencher la réindexation avec la commande suivante :

```shell
java -jar oak-run*.jar index --reindex --index-paths=/oak:index/lucene --read-write --fds-path=/path/to/datastore  /path/to/segmentstore/
```

La différence entre cette approche et celle expliquée ci-dessus est que la création de points de contrôle et l&#39;importation d’index s’effectuent automatiquement. L’inconvénient est qu’AEM doit être arrêté pendant le processus.

#### Réindexation hors-bande - SegmentNodeStore {#outofbandreindexsegmentnodestore}

Dans ce cas d’utilisation, vous pouvez effectuer une réindexation sur une configuration clonée pour minimiser l’impact sur l’instance AEM en cours d’exécution :

1. Créez un point de contrôle au moyen d’une opération JMX. Accédez à la [console JMX](/help/sites-administering/jmx-console.md) et recherchez `CheckpointManager`. Cliquez ensuite sur l’opération **createCheckpoint(long p1)** avec une valeur d’expiration élevée, en secondes (par exemple, **2592000**).
1. Copiez le dossier `crx-quickstart` sur un nouvel ordinateur.
1. Effectuez la réindexation au moyen de la commande d’index exécutée par Oak.

1. Copiez les fichiers d’index générés sur un serveur AEM.

1. Importez les fichiers d’index via JMX.

Dans ce cas d’utilisation, le magasin de données doit être accessible à partir d’une autre instance, ce qui peut s’avérer impossible lorsque `FileDataStore` réside sur une solution de stockage cloud telle qu’EBS. Cette situation exclut le scénario dans lequel `FileDataStore` est également cloné. Si la définition d’index n’effectue pas d’indexation du texte intégral, il n’est pas nécessaire d’accéder à `DataStore`.

## Cas d’utilisation 4 - Mise à jour des définitions d’index {#usecase4updatingindexdefinitions}

Actuellement, vous pouvez envoyer des modifications de définition d’index par le biais du package [ACS Ensure Index](https://adobe-consulting-services.github.io/acs-aem-commons/features/ensure-oak-index/index.html). Vous pouvez envoyer les définitions d’index dans un package de contenu, puis effectuer une réindexation en définissant l’indicateur de `reindex` sur `true`.


Cela fonctionne bien sur des petites installations pour lesquelles la réindexation prend peu de temps. . Cependant, pour les référentiels volumineux, la réindexation est effectuée dans un délai considérablement plus long. Dans ce cas, vous pouvez désormais utiliser l’outil d’indexation exécuté par Oak.

Oak-run prend désormais en charge la fourniture de définitions d’index au format JSON et la création d’index en mode hors bande où aucune modification n’est effectuée sur une instance active.

Le processus à prendre en compte pour ce cas d’utilisation est le suivant :

1. Un développeur met à jour les définitions d’index sur une instance locale, puis génère un fichier JSON de définition d’index au moyen de l’option `--index-definitions`.
1. Le fichier JSON mis à jour est ensuite transmis à l’administrateur ou l’administratrice système.
1. L’administrateur système suit la méthode hors-bande et prépare l’index sur une autre installation.
1. Une fois cette opération terminée, les fichiers d’index générés sont importés sur une installation AEM en cours d’exécution.
