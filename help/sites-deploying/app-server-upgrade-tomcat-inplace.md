---
title: Étapes de mise à niveau pour les installations de serveur d’applications (Tomcat)
description: Découvrez comment mettre à niveau les instances d’AEM déployées via Tomcat.
feature: Upgrading
solution: Experience Manager, Experience Manager Sites
role: Admin
source-git-commit: b3c4e946a3f235fa0e3a0945f1ad692ee195e3ef
workflow-type: tm+mt
source-wordcount: '408'
ht-degree: 9%

---

# Étapes de mise à niveau pour les installations de serveur d’applications (Tomcat - Mise à niveau statique) {#upgrade-steps-for-application-server-installations-tomcat-inplace}

>[!NOTE]
>
>Cette page décrit la procédure de mise à niveau (mise à niveau statique) d’AEM 6.5 LTS vers AEM 6.5 LTS Servicepack sur Tomcat. Pour effectuer la mise à niveau d’AEM 6.5 vers 6.5 LTS, [voir ici](/help/sites-deploying/app-server-upgrade-tomcat.md).

## Étapes préalables à la mise à niveau {#pre-upgrade-steps}

Avant d’exécuter votre mise à niveau, plusieurs étapes doivent être réalisées. Voir [Tâches de maintenance avant la mise à niveau](/help/sites-deploying/pre-upgrade-maintenance-tasks.md) pour plus d’informations. En outre, assurez-vous que votre système répond à la [configuration requise pour le pack de services LTS AEM 6.5](/help/sites-deploying/technical-requirements.md) et consultez les [considérations relatives à la planification de la mise à niveau](/help/sites-deploying/upgrade-planning.md).


### Conditions préalables à la migration {#migration-prerequisites}

* **Version Java minimale requise** : assurez-vous d’avoir installé Oracle® JRE 17/21 sur votre serveur Tomcat.
* **Serveur Tomcat** : les versions prises en charge du serveur Tomcat pour AEM 6.5 LTS et ses ServicePacks sont **10.0.x** et **10.1.x**.

### Exécuter la mise à niveau {#performing-the-upgrade}

Tous les exemples de cette procédure utilisent Tomcat comme serveur d’applications et impliquent que vous disposez d’une version de travail d’AEM 6.5 LTS déjà déployée. La procédure est destinée à documenter les mises à niveau d’AEM version **6.5** LTS vers **6.5 LTS** Servicepack.

1. Si AEM 6.5 LTS est déjà déployé, vérifiez que les lots fonctionnent correctement en accédant à : *`https://<serveraddress:port>/system/console/bundles`*
1. Ensuite, arrêtez AEM 6.5 LTS. Pour ce faire, utilisez Tomcat App Manager à l’adresse : *`https://<serveraddress:port>/manager/html`*
1. Assurez-vous d’avoir terminé les activités [pré-mise à niveau](#pre-upgrade-steps) telles que la sauvegarde du serveur LTS AEM 6.5 avant d’effectuer toute activité de mise à niveau
1. Arrêtez le serveur Tomcat LTS AEM 6.5 . Dans la plupart des cas, vous pouvez le faire en exécutant le script `./catalina.sh` , en exécutant cette commande à partir du terminal :

   ```
   $CATALINA_HOME/bin/catalina.sh stop
   ```

1. Supprimez les fichiers et les dossiers qui ne sont plus nécessaires. Les éléments à supprimer sont les suivants :

   * Le fichier **cq-quickstart-65.war** et le dossier `cq-quickstart-65` de `webapps` dossier se trouvent généralement à l’emplacement `<path-to-aem-server>/webapps`
   * Le dossier `launchpad/startup`. Vous pouvez le supprimer en exécutant la commande suivante dans le terminal , à condition que vous soyez dans le dossier du serveur :

     ```shell
     rm -rf <path-to-aem-server>/bin/crx-quickstart/launchpad/startup
     ```

   * Le fichier `base.jar`. Pour ce faire, exécutez les commandes suivantes :

     ```shell
     find <path-to-aem-server>/bin/crx-quickstart/launchpad -type f -name "org.apache.sling.launchpad.base.jar*" -exec rm -f {} \;
     ```

   * Fichier `BootstrapCommandFile_timestamp.txt` :

     ```shell
     rm -f <path-to-aem-server>/bin/crx-quickstart/launchpad/felix/bundle0/BootstrapCommandFile_timestamp.txt
     ```

   * Supprimez le fichier `sling.options` en exécutant :

     ```shell
     find <path-to-aem-server>/bin/crx-quickstart/launchpad -type f -name "sling.options.file" -exec rm -rf {} \; 
     ```

   * Supprimez le fichier `sling.bootstrap.txt` :

     ```shell
     rm -rf <path-to-aem-server>/bin/crx-quickstart/launchpad/sling_bootstrap.txt
     ```

1. Effectuez une sauvegarde du fichier `sling.properties` (généralement présent dans `<path-to-aem-server>/bin/crx-quickstart/launchpad/`) et supprimez-le
1. Copiez le fichier war du pack de services LTS d’AEM 6.5 dans `<path-to-aem-server>/webapps` dossier
1. Démarrez le serveur Tomcat LTS AEM 6.5 en exécutant :

   ```
   $CATALINA_HOME/bin/catalina.sh start
   ```

1. Surveillez les journaux d’erreurs pendant le démarrage d’AEM pour vérifier qu’il n’y a aucune erreur et qu’AEM s’exécute correctement
1. Une fois AEM 6.5 LTS démarré, vérifiez que les lots fonctionnent correctement en accédant à : *`https://<serveraddress:port>/cq/system/console/bundles`*

## Effectuer Des Vérifications Et Un Dépannage Après La Mise À Niveau {#perform-post-upgrade-checks-and-troubleshooting}

Voir [Vérifications et dépannage après la mise à niveau](/help/sites-deploying/post-upgrade-checks-and-troubleshooting.md) pour plus d’informations.
