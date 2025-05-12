---
title: Procédure de mise à niveau pour les installations de serveur d’applications (WLP)
description: Découvrez comment mettre à niveau les instances d’AEM déployées via Websphere Liberty.
feature: Upgrading
solution: Experience Manager, Experience Manager Sites
role: Admin
exl-id: 2a5d9026-49bc-4766-bcbe-38d834c14f72
source-git-commit: e5acea11254a6c4dbd24ff2a6d8ae3578b6690da
workflow-type: tm+mt
source-wordcount: '499'
ht-degree: 17%

---

# Procédure de mise à niveau pour les installations de serveur d’applications (WLP) {#upgrade-steps-for-application-server-installations-wlp}

>[!NOTE]
>
>Cette page décrit la procédure de mise à niveau pour AEM 6.5 LTS on WLP (WebSphere® Liberty).

## Étapes préalables à la mise à niveau {#pre-upgrade-steps}

Avant d’exécuter votre mise à niveau, plusieurs étapes doivent être réalisées. Voir [Mise à niveau du code et des personnalisations](/help/sites-deploying/upgrading-code-and-customizations.md) et [Tâches de maintenance avant la mise à niveau](/help/sites-deploying/pre-upgrade-maintenance-tasks.md) pour plus d’informations. Assurez-vous également que votre système répond à la [configuration requise pour AEM 6.5 LTS](/help/sites-deploying/technical-requirements.md).

Cochez [ Planification de la mise à niveau ](/help/sites-deploying/upgrade-planning.md) et comment l’[AEM Analyzer](/help/sites-deploying/aem-analyzer.md) peut vous aider à estimer la complexité de la mise à niveau d’AEM.

### Conditions préalables à la migration {#migration-prerequisites}

* **Version Java minimale requise** : assurez-vous d’avoir installé IBM® Sumeru JRE 17/21 sur votre serveur WLP.

### Exécuter la mise à niveau {#performing-the-upgrade}

1. Assurez-vous d’avoir effectué les étapes [avant la mise à niveau](#pre-upgrade-steps) telles que la sauvegarde du serveur AEM 6.5 avant d’effectuer toute activité de mise à niveau
1. Selon vos besoins, choisissez l’un des chemins de mise à niveau suivants :
   1. **Mise à niveau statique** : si votre serveur WLP actuel prend en charge le servlet 6, vous pouvez effectuer une mise à niveau statique et passer à l’étape 3.
   1. **Sidegrade** : si vous préférez une nouvelle configuration ou si votre serveur WLP ne prend pas en charge le servlet 6, configurez une nouvelle instance WLP avec AEM 6.5 LTS et migrez le contenu en suivant la [Migration de contenu AEM 6.5 vers AEM 6.5 LTS à l’aide d’Oak-upgrade](/help/sites-deploying/aem-65-to-aem-65lts-content-migration-using-oak-upgrade.md) et passez à la section [Déployer la base de code mise à niveau](#deploy-upgraded-codebase)

1. Désactivez l’instance AEM. Cette opération peut généralement être effectuée à l’aide de la commande suivante :

   ```shell
   <path-to-wlp-directory>/bin/server stop server_name
   ```

1. Supprimez les fichiers et les dossiers qui ne sont plus nécessaires. Les éléments à supprimer sont les suivants :

   * Le fichier **cq-quickstart-65.war** du dossier `dropins` et du dossier `expanded` se trouvant généralement respectivement à l’emplacement `<path-to-aem-server>/dropins/cq-quickstart-65.war` et `<path-to-aem-server>/apps/expanded/cq-quickstart-65.war`
   * Le dossier `launchpad/startup`. Vous pouvez le supprimer en exécutant la commande suivante dans le terminal , à condition que vous soyez dans le dossier du serveur :

     ```shell
     rm -rf crx-quickstart/launchpad/startup
     ```

   * Le fichier `base.jar`. Pour ce faire, exécutez les commandes suivantes :

     ```shell
     find crx-quickstart/launchpad -type f -name "org.apache.sling.launchpad.base.jar*" -exec rm -f {} \;
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
1. Installez Java 17/Java 21 et assurez-vous qu’il est correctement installé en exécutant :

   ```shell
   java -version
   ```

1. Vérifiez les paramètres de démarrage du serveur AEM et assurez-vous de mettre à jour les paramètres en fonction de vos besoins. Pour plus d’informations, consultez les Considérations relatives à [Java 17/Java 21](/help/sites-deploying/custom-standalone-install.md#java-considerations).
1. Téléchargez le nouveau fichier war LTS 6.5 et copiez-le dans le dossier dropins situé à l’adresse : `/<path-to-aem-server>/dropins/`
1. Démarrez l’instance AEM : vous pouvez généralement le faire à l’aide de la commande suivante :

   ```shell
   <path-to-wlp-directory>/bin/server start server_name
   ```

1. Si vous disposez de modifications personnalisées dans `sling.properties`, suivez les instructions ci-dessous :

   1. Arrêtez l’instance AEM en exécutant `<path-to-wlp-directory>/bin/server stop server_name`
   1. Appliquez vos modifications de `sling.properties` personnalisées au fichier `sling.properties` nouvellement généré (en vous référant au fichier de sauvegarde créé à l’étape 5)
   1. Démarrez l’instance AEM. Vous pouvez le faire généralement en exécutant : `<path-to-wlp-directory>/bin/server start server_name`

## Déployer le base de code mise à niveau {#deploy-upgraded-codebase}

Une fois le processus de mise à niveau terminé, la base de code mise à jour doit être déployée. La procédure de mise à jour de la base de code pour qu’elle fonctionne dans la version cible d’AEM est disponible dans la page [Mise à niveau du code et personnalisations](/help/sites-deploying/upgrading-code-and-customizations.md).

## Effectuer Des Vérifications Et Un Dépannage Après La Mise À Niveau {#perform-post-upgrade-checks-and-troubleshooting}

Voir [Vérifications et dépannage après une mise à niveau](/help/sites-deploying/post-upgrade-checks-and-troubleshooting.md).
