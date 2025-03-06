---
title: Vérifications et dépannage après une mise à niveau
description: Découvrez comment résoudre les problèmes qui peuvent apparaître après une mise à niveau.
contentOwner: sarchiz
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: upgrading
content-type: reference
docset: aem65
feature: Upgrading
solution: Experience Manager, Experience Manager Sites
role: Admin
exl-id: 8b3d8d0f-10f7-4736-881d-8f1f21c69182
source-git-commit: a037dc7cbb13abfeb8a7289baded50d3d788cbf6
workflow-type: tm+mt
source-wordcount: '1200'
ht-degree: 80%

---

# Vérifications et dépannage après une mise à niveau{#post-upgrade-checks-and-troubleshooting}

## Vérifications après mise à niveau {#post-upgrade-checks}

Après la [mise à niveau statique](/help/sites-deploying/in-place-upgrade.md), les activités suivantes doivent être exécutées pour finaliser la mise à niveau. On suppose qu’AEM a été démarré avec le jar LTS AEM 6.5 et que la base de code mise à niveau a été déployée.

* [Vérification des journaux pour la réussite de la mise à niveau](#verify-logs-for-upgrade-success)

* [Vérification des lots OSGi](#verify-osgi-bundles)

* [Vérifier la version d’Oak](#verify-oak-version)

* [Validation initiale des pages](#initial-validation-of-pages)

* [Vérification des configurations de maintenance planifiées](#verify-scheduled-maintenance-configurations)

* [Activation des agents de réplication](#enable-replication-agents)

* [Activation des tâches planifiées personnalisées](#enable-custom-scheduled-jobs)

* [Exécution du plan de test](#execute-test-plan)


### Vérification des journaux pour la réussite de la mise à niveau {#verify-logs-for-upgrade-success}

**upgrade.log**

Auparavant, la vérification de l’état de votre instance après la mise à niveau nécessitait une inspection minutieuse de divers fichiers journaux, de parties du référentiel et du lanchpad. La génération d’un rapport après la mise à niveau permet de détecter les mises à niveau défectueuses avant la mise en service.

L’objectif principal de cette fonctionnalité est de réduire la nécessité d’une interprétation manuelle ou d’une logique d’analyse complexe sur plusieurs points d’entrée requis pour que la mise à niveau soit réussie. La solution vise à fournir des informations non ambiguës pour que les systèmes d’automatisation externes réagissent au succès ou à l’échec identifié d’une mise à jour.

Plus précisément, il garantit ce qui suit :

* Les échecs de mise à niveau détectés par la structure de mise à niveau sont centralisés dans un rapport de mise à niveau unique.
* le rapport de mise à niveau comprend des indicateurs sur l’intervention manuelle nécessaire.

Pour cela, les modifications ont été apportées à la façon dont les journaux sont générés dans le fichier `upgrade.log`.

**error.log**

Le fichier error.log doit être soigneusement examiné pendant et après le démarrage d’AEM à l’aide du fichier jar de la version cible. Les avertissements et erreurs doivent être examinés. En général, il est préférable de rechercher les problèmes au début du journal. Les erreurs qui se produisent plus tard dans le journal peuvent en fait être des effets secondaires d’une cause racine repérée plus tôt dans le fichier. En cas d’erreurs et d’avertissements répétés, reportez-vous à la section ci-dessous pour [Analyser les problèmes liés à la mise à niveau](/help/sites-deploying/post-upgrade-checks-and-troubleshooting.md#analyzing-issues-with-the-upgrade).

### Vérification des lots OSGi {#verify-osgi-bundles}

Accédez à la console OSGi `/system/console/bundles` et vérifiez si des lots n’ont pas démarré. Si des lots sont installés, consultez le fichier `error.log` pour identifier le problème racine.

### Vérifier la version d’Oak {#verify-oak-version}

Après la mise à niveau, vous devriez voir que la version d’Oak a été mise à jour vers **1.68.x**. Pour vérifier la version d’Oak, accédez à la console OSGi et examinez la version associée aux lots Oak : Oak Core, Oak Commons, Oak Segment Tar.

### Validation initiale des pages {#initial-validation-of-pages}

Effectuez une validation initiale sur plusieurs pages dans AEM. En cas de mise à niveau d’un environnement de création, ouvrez la page de démarrage et la page d’accueil ( `/aem/start.html`, `/libs/cq/core/content/welcome.html`). Dans les environnements de création et de publication, ouvrez quelques pages d’application et testez-les pour vous assurer qu’elles fonctionnent correctement. En cas de problème, veuillez consulter le fichier `error.log` pour un dépannage.

### Vérification des configurations de maintenance planifiées {#verify-scheduled-maintenance-configurations}

#### Activer la récupération de l’espace mémoire du magasin de données {#enable-data-store-garbage-collection}

Si vous utilisez un magasin de données basé sur les fichiers, assurez-vous que la tâche de nettoyage de l’espace mémoire du magasin de données est activée et ajoutée à la liste de maintenance hebdomadaire. Les instructions sont décrites sous [Nettoyage des révisions](/help/sites-administering/data-store-garbage-collection.md).

>[!NOTE]
>
>Cela n’est pas recommandé pour les installations de magasin de données personnalisé S3 ou lors de l’utilisation d’un magasin de données partagé.

#### Activation du nettoyage des révisions en ligne {#enable-online-revision-cleanup}

Si vous utilisez MongoMK ou le nouveau format de segment TarMK, assurez-vous que la tâche de nettoyage de révision est activée et ajoutée à la liste de maintenance quotidienne. Les instructions sont décrites sous [Nettoyage des révisions](/help/sites-deploying/revision-cleanup.md).

### Activation des agents de réplication {#enable-replication-agents}

Une fois que l’environnement de publication a été entièrement mis à niveau et validé, activez les agents de réplication dans l’environnement de création. Vérifiez que les agents sont en mesure de se connecter aux instances de publication respectives. Voir [Procédure de mise à niveau](/help/sites-deploying/upgrade-procedure.md) pour plus d’informations sur l’ordre des événements.

### Activation des tâches planifiées personnalisées {#enable-custom-scheduled-jobs}

À ce stade, toutes les tâches planifiées faisant partie de la base de code peuvent être activées.

### Exécution du plan de test {#execute-test-plan}

Exécutez le plan de test détaillé comme défini dans [Mise à niveau du code et des personnalisations dans la section **Procédure de test**](/help/sites-deploying/upgrading-code-and-customizations.md#testing-procedure-testing-procedure).

## Analyser les problèmes liés à la mise à niveau {#analyzing-issues-with-the-upgrade}

Cette section présente certains scénarios de problèmes auxquels vous pourriez être confronté lors de la procédure de mise à niveau vers AEM 6.5 LTS.

### Échec de la mise à jour des packages et des lots  {#packages-and-bundles-fail-to-update}

Si l’installation des packages échoue pendant la mise à niveau, les lots qu’ils contiennent ne seront pas mis à jour non plus. Cette catégorie de problèmes est due à une mauvaise configuration du magasin de données. Ils apparaissent également sous la forme de messages **ERROR** (erreur) et **WARN** (avertissement) dans error.log. Étant donné que dans la plupart de ces cas, la connexion par défaut peut ne pas fonctionner, vous pouvez utiliser CRXDE directement pour inspecter et trouver les problèmes de configuration.

### La mise à niveau n’a pas été exécutée. {#the-upgrade-did-not-run}

Avant de commencer les étapes de préparation, veillez à exécuter d&#39;abord l&#39;instance **source** en l&#39;exécutant avec la commande `java -jar aem-quickstart.jar`. Cela est nécessaire pour s’assurer que le fichier quickstart.properties est généré correctement. S’il est manquant, la mise à niveau ne fonctionnera pas. Vous pouvez également vérifier si le fichier est présent en regardant sous `crx-quickstart/conf` dans le dossier d’installation de l’instance source. En outre, lors du démarrage d’AEM pour lancer la mise à niveau, celle-ci doit être exécutée avec la commande `java -jar <aem-quickstart-6.5-LTS.jar>`. Le démarrage à partir d’un script de démarrage ne démarre pas AEM en mode de mise à niveau.

### Certains lots AEM ne passent pas à l’état actif. {#some-aem-bundles-are-not-switching-to-the-active-state}

Si des lots ne démarrent pas, recherchez des dépendances insatisfaites.

Si ce problème est présent mais qu’il est dû à un échec de l’installation du package qui a entraîné la non-mise à niveau des lots, ils seront considérés comme incompatibles pour la nouvelle version. Pour plus d’informations sur la manière de résoudre ce problème, voir **Échec de la mise à jour des packages et des lots** ci-dessus.

Il est également recommandé de comparer la liste des lots d’une instance LTS AEM 6.5 neuve avec celle de l’instance mise à niveau afin de détecter les lots qui n’ont pas été mis à niveau. Cela permettra de réduire le champ des recherches dans le fichier `error.log`.

### Les lots personnalisés ne passent pas à l’état actif {#custom-bundles-not-switching-to-the-active-state}

Si vos lots personnalisés ne passent pas à l’état actif, il est probable qu’une partie du code ne procède pas à l’importation de l’API modifiée. Cela entraîne le plus souvent des dépendances non satisfaites.

Il est également préférable de vérifier si la modification à l’origine du problème était nécessaire et de revenir en arrière si ce n’est pas le cas. Vérifiez également si la nouvelle version du package d’exportation est plus élevée que nécessaire, à l’aide du contrôle de version sémantique strict.

### Analyse des journaux error.log et upgrade.log {#analyzing-the-error.log-and-upgrade.log}

Dans la plupart des cas, les journaux doivent être consultés afin d’y chercher des erreurs pour détecter la cause d’un problème. Toutefois, pour les mises à niveau, il est également nécessaire de surveiller les problèmes de dépendance, car les anciens lots peuvent ne pas être mis à niveau correctement.

Pour ce faire, la meilleure méthode consiste à élaguer le fichier error.log en supprimant tous les messages qui ne sont pas liés au problème auquel vous êtes confronté. Vous pouvez le faire à l’aide d’un outil comme grep, en utilisant la méthode suivante :

```shell
grep -v UnrelatedErrorString
```

Certains messages d’erreur peuvent ne pas être immédiatement descriptifs. Dans ce cas, regarder le contexte dans lequel ceux-ci se produisent peut vous aider à comprendre où l’erreur s’est créée. Vous pouvez séparer l&#39;erreur à l’aide des éléments suivants :

* `grep -B` pour l’ajout de lignes avant l’erreur

ou

* `grep -A` pour l’ajout de lignes après l’erreur.

Dans de rares cas, des erreurs peuvent également se trouver dans les messages AVERTISSEMENT, car il peut y avoir des cas valides qui mènent à cet état, et l’application n’est pas toujours capable de déterminer s’il s’agit d’une véritable erreur. Il est important que vous consultiez également ces messages.

### Contacter le support technique d’Adobe {#contacting-adobe-support}

Si vous avez suivi les conseils de cette page et que vous rencontrez toujours des problèmes, contactez l’assistance d’Adobe. Pour fournir autant d’informations que possible à l’ingénieur du support qui travaille sur votre cas, veillez à inclure les fichiers `error.log` et `upgrade.log` de votre mise à niveau.
