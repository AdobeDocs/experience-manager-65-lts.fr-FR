---
title: Étapes de mise à niveau pour les installations de serveur d’applications (Tomcat)
description: Découvrez comment mettre à niveau les instances d’AEM déployées via Tomcat.
feature: Upgrading
solution: Experience Manager, Experience Manager Sites
role: Admin
exl-id: 7f8de16f-9e9a-4d37-9978-d26c496b911c
source-git-commit: 2a33cb4b8aa1dcfd989cf61465492d563f9cd99a
workflow-type: tm+mt
source-wordcount: '494'
ht-degree: 16%

---

# Étapes de mise à niveau pour les installations de serveur d’applications (Tomcat - Sidegrade) {#upgrade-steps-for-application-server-installations-tomcat}

>[!NOTE]
>
>Cette page décrit la procédure de mise à niveau d’AEM 6.5 vers AEM 6.5 LTS sur Tomcat. Pour effectuer la mise à niveau d’AEM 6.5 LTS vers AEM 6.5 LTS Servicepack [consultez cette section](/help/sites-deploying/app-server-upgrade-tomcat-inplace.md)

## Étapes préalables à la mise à niveau {#pre-upgrade-steps}

Avant d’exécuter votre mise à niveau, plusieurs étapes doivent être réalisées. Voir [Mise à niveau du code et des personnalisations](/help/sites-deploying/upgrading-code-and-customizations.md) et [Tâches de maintenance avant la mise à niveau](/help/sites-deploying/pre-upgrade-maintenance-tasks.md) pour plus d’informations. En outre, assurez-vous que votre système répond à la [configuration requise pour AEM 6.5 LTS](/help/sites-deploying/technical-requirements.md), consultez les [considérations relatives à la planification de la mise à niveau](/help/sites-deploying/upgrade-planning.md) et comment [Analyzer](/help/sites-deploying/aem-analyzer.md) peut vous aider à estimer la complexité.


### Conditions préalables à la migration {#migration-prerequisites}

* **Version Java minimale requise** : assurez-vous d’avoir installé Oracle® JRE 17/21 sur votre serveur Tomcat.
* **Serveur Tomcat** : les versions prises en charge du serveur Tomcat pour AEM 6.5 LTS sont **10.0.x** et **10.1.x**.

### Exécuter la mise à niveau {#performing-the-upgrade}

Tous les exemples de cette procédure utilisent Tomcat comme serveur d’applications et présument que vous disposez d’une version de travail d’AEM déjà déployée. La procédure est destinée à documenter les mises à niveau d’AEM version **6.5** vers **6.5 LTS**.

1. Si AEM 6.5 est déjà déployé, vérifiez que les lots fonctionnent correctement en accédant à : *`https://<serveraddress:port>/system/console/bundles`*
1. Ensuite, arrêtez AEM 6.5. Pour ce faire, utilisez Tomcat App Manager à l’adresse : *`https://<serveraddress:port>/manager/html`*
1. Assurez-vous d’avoir terminé les activités [pré-mise à niveau](#pre-upgrade-steps) telles que la sauvegarde du serveur AEM 6.5 avant d’effectuer toute activité de mise à niveau
1. Installez Java 17/Java 21 et assurez-vous qu’il est correctement installé en exécutant la commande :

   ```
   java –version
   ```

1. Configuration d’un serveur Tomcat compatible avec AEM 6.5 LTS
1. Vérifiez les paramètres de démarrage du serveur AEM et assurez-vous de les mettre à jour en fonction de la configuration requise. Voir [Considérations relatives à Java 17/Java 21](/help/sites-deploying/custom-standalone-install.md#java-considerations) pour plus d’informations
1. Déployez le fichier war 6.5 LTS récemment téléchargé sur le serveur Tomcat à l’aide de Java 17/Java 21 et démarrez le serveur Tomcat 6.5 LTS AEM en exécutant :

   ```
   $CATALINA_HOME/bin/catalina.sh start
   ```

1. Une fois AEM en cours d’exécution, assurez-vous que tous les lots sont en cours d’exécution en accédant à : *`https://<serveraddress:port>/cq/system/console/bundles`*
1. Arrêtez le serveur Tomcat LTS AEM 6.5 . Dans la plupart des cas, vous pouvez le faire en exécutant le script `./catalina.sh` , en exécutant cette commande à partir du terminal :

   ```
   $CATALINA_HOME/bin/catalina.sh stop
   ```

1. À présent, migrez votre contenu d’AEM 6.5 vers AEM 6.5 LTS en suivant les étapes ci-dessous : [Migration de contenu AEM 6.5 vers AEM 6.5 LTS à l’aide de la mise à niveau d’Oak](/help/sites-deploying/aem-65-to-aem-65lts-content-migration-using-oak-upgrade.md)
1. Une fois le contenu migré, appliquez les modifications personnalisées requises dans le fichier `sling.properties`
1. Démarrez le serveur Tomcat LTS AEM 6.5 en exécutant :

   ```
   $CATALINA_HOME/bin/catalina.sh start
   ```

1. Surveillez les journaux d’erreurs pendant le démarrage d’AEM pour vérifier qu’il n’y a aucune erreur et qu’AEM s’exécute correctement
1. Une fois AEM 6.5 LTS démarré, vérifiez que les lots fonctionnent correctement en accédant à : *`https://<serveraddress:port>/cq/system/console/bundles`*

## Déployer le base de code mise à niveau {#deploy-upgraded-codebase}

Une fois le processus de mise à niveau terminé, la base de code mise à jour doit être déployée. La procédure de mise à jour de la base de code pour qu’elle fonctionne dans la version cible d’AEM est disponible dans la page [Mise à niveau du code et personnalisations](/help/sites-deploying/upgrading-code-and-customizations.md).

## Effectuer Des Vérifications Et Un Dépannage Après La Mise À Niveau {#perform-post-upgrade-checks-and-troubleshooting}

Voir [Vérifications et dépannage après la mise à niveau](/help/sites-deploying/post-upgrade-checks-and-troubleshooting.md) pour plus d’informations.
