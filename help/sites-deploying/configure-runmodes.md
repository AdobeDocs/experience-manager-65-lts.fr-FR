---
title: Modes d’exécution
description: Découvrez comment ajuster votre instance d’AEM à des fins spécifiques à l’aide des modes d’exécution.
feature: Administering
solution: Experience Manager, Experience Manager Sites
role: Admin
exl-id: b21555f2-bc07-4653-a5da-966b9aa7ea1f
source-git-commit: 408f6aaedd2cc0315f6e66b83f045ca2716db61d
workflow-type: tm+mt
source-wordcount: '679'
ht-degree: 96%

---

# Modes d’exécution{#run-modes}

Les modes d’exécution vous permettent d’ajuster votre instance d’AEM à des fins spécifiques, par exemple pour la création ou la publication, le test, le développement, l’intranet et plus encore.

Vous pouvez :

* [Définition de collections de paramètres de configuration pour chaque mode d’exécution](#defining-configuration-properties-for-a-run-mode).

  Un ensemble de paramètres de configuration de base est appliqué à tous les modes d’exécution, puis vous pouvez ajuster les ensembles ajoutés en fonction de l’objectif de votre environnement spécifique. Ils sont appliqués selon les besoins.

* [Définition de lots supplémentaires à installer pour un mode spécifique](#defining-additional-bundles-to-be-installed-for-a-run-mode).

L’ensemble des paramètres et des définitions sont stockés dans le référentiel et activé en définissant le **mode d’exécution**.

## Modes d’exécution d’installation {#installation-run-modes}

Les modes d’exécution d’installation (ou fixes) sont utilisés lors de l’installation, puis restent fixes pendant toute la durée de vie de l’instance. Ils ne peuvent pas être modifiés.

Les modes d’exécution d’installation sont fournis prêts à l’emploi :

* `author`
* `publish`

Voici deux paires de modes d’exécution qui sont mutuellement exclusifs. Par exemple, vous pouvez :

* définir le mode `author` ou `publish`, mais pas les deux en même temps ;

>[!CAUTION]
>
>Lors de l’utilisation de l’un des modes d’exécution ci-dessus (création, publication), la valeur utilisée au moment de l’installation définit le mode d’exécution pour la *durée de vie complète* de cette installation.
>
>Vous *ne pouvez pas* modifier ces modes d’exécution après l’installation.

## Modes d’exécution personnalisés {#customized-run-modes}

Vous pouvez également créer vos propres modes d’exécution personnalisés. Ils peuvent être combinés pour prendre en charge des scénarios tels que :

* `author` + `development`

* `publish` + `test`

* `publish` + `test` + `golive`

* `publish` + `intranet`

* le cas échéant.

Les modes d’exécution personnalisés peuvent également être sélectionnés à chaque démarrage.

## Définir des propriétés de configuration pour un mode d’exécution {#defining-configuration-properties-for-a-run-mode}

Une collection de valeurs pour les propriétés de configuration, utilisée pour un mode d’exécution spécifique, peut être enregistrée dans le référentiel.

Le mode d’exécution est indiqué par un suffixe sur le nom du dossier. Vous pouvez ainsi stocker toutes les configurations dans un seul référentiel. Par exemple :

* `config`

  Applicable à tous les modes d’exécution

* `config.author`

  Utilisé pour le mode d’exécution auteur

* `config.publish`

  Utilisé pour le mode d’exécution de publication

* `config.<run-mode>`

  Utilisé pour le mode d’exécution applicable, par exemple « config »

Voir [Configuration d’OSGi dans le référentiel](/help/sites-deploying/configuring-osgi.md#osgi-configuration-in-the-repository) pour plus d’informations sur la définition des différents nœuds de configuration dans ces dossiers et sur la création de configurations pour des combinaisons de plusieurs modes d’exécution.

>[!NOTE]
>
>Pour les [Modes d’exécution d’installation](#installation-run-modes) (instance de création, par exemple), le mode d’exécution ne peut pas être modifié après l’installation. Toutefois, les modifications apportées aux propriétés de configuration individuelles prennent effet au redémarrage.

## Définir des lots supplémentaires à installer pour un mode d’exécution {#defining-additional-bundles-to-be-installed-for-a-run-mode}

Vous pouvez également spécifier des lots supplémentaires qui doivent être installés pour un mode d’exécution spécifique. Pour ces définitions, les dossiers d’installation sont utilisés pour contenir les lots. Là aussi, le mode d’exécution est indiqué par un préfixe :

* `install.author`
* `install.publish`

Ces dossiers sont de type `nt:folder` et doivent contenir le lot approprié.

## Démarrer CQ avec un mode d’exécution spécifique {#starting-cq-with-a-specific-run-mode}

Si vous avez défini des configurations pour plusieurs modes d’exécution, vous devez définir celui qui doit être utilisé au démarrage. Il existe plusieurs méthodes pour spécifier le mode d’exécution à utiliser. L’ordre de résolution est le suivant :

1. [Propriétés système (](#using-a-system-property-in-the-start-script)
1. [&#128279;](#using-the-sling-properties-file)
1. [&#128279;](#using-the-r-option)
1. [Détection du nom de fichier](#filename-detection-renaming-the-jar-file)

Lorsque vous utilisez un serveur d’application, vous pouvez également [définir le mode d’exécution dans web.xml](#defining-the-run-mode-in-web-xml-with-application-server).

### Utilisation du fichier sling.properties {#using-the-sling-properties-file}

Vous pouvez utiliser le fichier `sling.properties` pour définir le mode d’exécution requis :

1. Modifiez le fichier de configuration :

   `<cq-installation-dir>/crx-quickstart/conf/sling.properties`

1. Ajoutez les propriétés suivantes. L’exemple suivant concerne le mode d’exécution auteur :

   `sling.run.modes=author`

### Utilisation de l’option -r {#using-the-r-option}

Un mode d’exécution personnalisé peut être activé à l’aide de l’option `-r` lors du lancement du démarrage rapide. Par exemple, utilisez la commande ci-dessous pour lancer une instance AEM avec le mode d’exécution défini sur dev. &grave;&grave;

```shell
java -jar cq-56-p4545.jar -r dev
```

### Utilisation d’une propriété système dans le script de démarrage {#using-a-system-property-in-the-start-script}

Une propriété système dans le script de démarrage peut être utilisée pour spécifier le mode d’exécution.

* Par exemple, utilisez le code ci-dessous pour lancer une instance de publication de production localisée aux États-Unis :

  `-Dsling.run.modes=publish,prod,us`

### Détection de nom de fichier : attribution d’un nouveau nom au fichier JAR {#filename-detection-renaming-the-jar-file}

Les deux modes d’exécution d’installation ci-dessous peuvent être activés en renommant le fichier JAR d’installation avant l’installation :

* publication
* auteur

Le fichier jar doit utiliser la convention de dénomination :

`cq5-<run-mode>-p<port-number>`

Par exemple, définissez le mode d’exécution `publish` en nommant le fichier JAR :

`cq5-publish-p4503`

### Définir le mode d’exécution au format web.xml (avec le serveur d’applications) {#defining-the-run-mode-in-web-xml-with-application-server}

Lorsque vous utilisez un serveur d’applications, vous pouvez également configurer la propriété :

`sling.run.modes`

dans le fichier :

`WEB-INF/web.xml`

Il se trouve dans le fichier `war` d’AEM et doit être mis à jour avant le déploiement.

Pour plus d’informations, consultez [Installation d’AEM avec un serveur d’application](/help/sites-deploying/application-server-install.md).
