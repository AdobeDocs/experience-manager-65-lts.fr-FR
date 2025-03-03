---
title: Procédure de mise à niveau pour les installations de serveur d’applications (WLP)
description: Découvrez comment mettre à niveau les instances d’AEM déployées via Websphere Liberty.
feature: Upgrading
solution: Experience Manager, Experience Manager Sites
role: Admin
source-git-commit: 6a62741ee0ce22a6fb80cf8c68c6eeafacd2e873
workflow-type: tm+mt
source-wordcount: '479'
ht-degree: 15%

---

# Procédure de mise à niveau pour les installations de serveur d’applications (WLP) {#upgrade-steps-for-application-server-installations-wlp}

>[!NOTE]
>
>Cette page décrit la procédure de mise à niveau pour le war LTS d’AEM 6.5 sur WLP (WebSphere Liberty).

## Étapes préalables à la mise à niveau {#pre-upgrade-steps}

Avant d’exécuter votre mise à niveau, plusieurs étapes doivent être réalisées. Voir [Mise à niveau du code et des personnalisations](/help/sites-deploying/upgrading-code-and-customizations.md) et [Tâches de maintenance avant la mise à niveau](/help/sites-deploying/pre-upgrade-maintenance-tasks.md) pour plus d’informations. Assurez-vous également que votre système répond à la configuration requise pour AEM 6.5 LTS. Découvrez comment Analyzer peut vous aider à estimer la complexité de votre mise à niveau et planifiez une mise à niveau (voir [ Planification de la mise à niveau ](/help/sites-deploying/upgrade-planning.md) pour plus d’informations).

### Conditions préalables à la migration {#migration-prerequisites}

* **Version Java minimale requise** : assurez-vous d’avoir installé IBM Sumeru JRE 17 sur votre serveur WLP.

### Exécuter la mise à niveau {#performing-the-upgrade}

1. Effectuez une sauvegarde de votre instance avant de démarrer toute activité de mise à niveau.
1. Déterminez si vous avez besoin d&#39;une mise à niveau ou d&#39;une mise à niveau sur place en fonction de la version du serveur WLP que vous utilisez. Si votre serveur WLP actuel prend en charge Servlet 6, vous pouvez effectuer une mise à niveau sur place et poursuivre avec cette documentation. Sinon, vous devez effectuer un dégradé. Pour la mise à niveau latérale, suivez le lien Migration de contenu avec Oak-Upgrade Documentation - [ à déterminer à ajouter]
1. Désactivez l’instance AEM. Cette opération peut généralement être effectuée à l’aide de la commande suivante :

   ```shell
   <path-to-wlp-directory>/bin/server stop server_name
   ```

1. Supprimez les fichiers et les dossiers qui ne sont plus nécessaires. Les éléments à supprimer sont les suivants :

   * Les `cq-quickstart-65.war` du dossier `dropins` et du dossier développé se trouvent généralement aux emplacements `<path-to-aem-server>/dropins/cq-quickstart-65.war` et `<path-to-aem-server>/apps/expanded/cq-quickstart-65.war`, respectivement
   * Le dossier `launchpad/startup`. Vous pouvez le supprimer en exécutant la commande suivante dans le terminal , à condition que vous soyez dans le dossier du serveur :

     ```shell
     rm -rf crx-quickstart/launchpad/startup
     ```

   * Le fichier `base.jar`. Pour ce faire, exécutez les commandes suivantes :

     ```shell
     find crx-quickstart/launchpad -type f -name 
     "org.apache.sling.launchpad.base.jar*" -exec rm -f {} \;
     ```

   * Fichier `BootstrapCommandFile_timestamp.txt` :

     ```shell
     rm -f crx-quickstart/launchpad/felix/bundle0/BootstrapCommandFile_timestamp.txt
     ```

   * Supprimez le fichier `sling.options` en exécutant :

     ```shell
     find crx-quickstart/launchpad -type f -name "sling.options.file" -exec rm -rf {} \; 
     ```

   * Supprimez le fichier `sling.bootstrap.txt` :

     ```shell
     rm -rf crx-quickstart/launchpad/sling_bootstrap.txt
     ```

1. Effectuez une sauvegarde du fichier `sling.properties` (généralement présent dans `crx-quickstart/conf/`) et supprimez-le
1. Remplacez la version du servlet par **6.0** dans le fichier `server.xml`
1. Vérifiez les paramètres de démarrage du serveur AEM et assurez-vous de les mettre à jour en fonction de la configuration requise. Voir [Installation autonome personnalisée](/help/sites-deploying/custom-standalone-install.md) pour plus d’informations
1. Installez Java 17 et assurez-vous qu’il est correctement installé en exécutant :

   ```shell
   java -version
   ```

1. Téléchargez le nouveau war 6.5 LTS à partir de la distribution logicielle et copiez-le dans le dossier dropins situé à l’adresse : `/<path-to-aem-server>/dropins/`
1. Démarrez l’instance AEM : vous pouvez généralement le faire à l’aide de la commande suivante :

   ```shell
   <path-to-wlp-directory>/bin/server start server_name
   ```

1. Si vous disposez de modifications personnalisées dans `sling.properties`, suivez les instructions ci-dessous :

   1. Arrêtez l’instance AEM en exécutant `<path-to-wlp-directory>/bin/server stop server_name`
   1. Appliquez vos modifications de `sling.properties` personnalisées au fichier `sling.properties` nouvellement généré (en se référant au fichier de sauvegarde créé à l’étape 6)
   1. Démarrez l’instance AEM. Vous pouvez le faire généralement en exécutant : `<path-to-wlp-directory>/bin/server start server_name`

## Déployer le base de code mise à niveau {#deploy-upgraded-codebase}

Une fois la mise à niveau statique terminée, la base de code mise à niveau doit être déployée. La procédure de mise à jour de la base de code pour qu’elle fonctionne dans la version cible d’AEM est disponible à la page [Mise à niveau du code et personnalisations](/help/sites-deploying/upgrading-code-and-customizations.md).

## Effectuer Des Vérifications Et Un Dépannage Après La Mise À Niveau {#perform-post-upgrade-checks-and-troubleshooting}

Voir [Vérifications et dépannage après la mise à niveau](/help/sites-deploying/post-upgrade-checks-and-troubleshooting.md) pour plus d’informations.