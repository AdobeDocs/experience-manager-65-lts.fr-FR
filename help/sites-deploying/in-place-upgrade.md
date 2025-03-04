---
title: Effectuer une mise à niveau statique
description: Découvrez comment effectuer une mise à niveau statique pour AEM 6.5 LTS.
topic-tags: upgrading
feature: Upgrading
solution: Experience Manager, Experience Manager Sites
role: Admin
source-git-commit: c3df47efd4b13dcd8061e5cdac32a75fbf36df4b
workflow-type: tm+mt
source-wordcount: '538'
ht-degree: 47%

---

# Effectuer une mise à niveau statique {#performing-an-in-place-upgrade}

>[!NOTE]
>
>Cette page décrit la procédure de mise à niveau sur place pour AEM 6.5 LTS. Si vous disposez d’une installation déployée sur un serveur d’applications, voir [Procédure de mise à niveau pour les installations de serveur d’applications](/help/sites-deploying/app-server-upgrade.md).

## Étapes préalables à la mise à niveau {#pre-upgrade-steps}

Avant d’exécuter votre mise à niveau, plusieurs étapes doivent être réalisées. Voir [Mise à niveau du code et des personnalisations](/help/sites-deploying/upgrading-code-and-customizations.md) et [Tâches de maintenance avant la mise à niveau](/help/sites-deploying/pre-upgrade-maintenance-tasks.md) pour plus d’informations. En outre, assurez-vous que votre système répond à la [configuration requise pour AEM 6.5 LTS](/help/sites-deploying/technical-requirements.md), consultez les [considérations relatives à la planification de la mise à niveau](/help/sites-deploying/upgrade-planning.md) et sur la manière dont [Analyzer](/help/sites-deploying/pattern-detector.md) peut vous aider à estimer la complexité.

<!--Finally, the downtime during the upgrade can be significally reduced by indexing the repository **before** performing the upgrade. For more information, see [Using Offline Reindexing To Reduce Downtime During an Upgrade](/help/sites-deploying/upgrade-offline-reindexing.md)-->

## Conditions préalables à la migration {#migration-prerequisites}

* **Version Java minimale requise :** Vérifiez qu’Oracle Java™ 17 est installé sur votre système.

## Préparation du fichier jar de démarrage rapide AEM {#prep-quickstart-file}

1. Téléchargez le nouveau fichier JAR LTS d’AEM 6.5

1. [Détermination de la commande de démarrage de mise à niveau appropriée](/help/sites-deploying/in-place-upgrade.md#determining-the-correct-upgrade-start-command-determining-the-correct-upgrade-start-command)

1. Arrêter l’instance si elle est en cours d’exécution

1. Utilisez le nouveau fichier jar LTS AEM 6.5 pour remplacer l’ancien en dehors du dossier `crx-quickstart`

1. Effectuez une sauvegarde du fichier `sling.properties` (généralement présent dans le `crx-quickstart/conf/`), puis supprimez-le

1. Décompressez le nouveau fichier jar de démarrage rapide en exécutant :

   ```shell
   java -Xmx4096m -jar aem-quickstart.jar -unpack
   ```

1. La commande unpack génère un nouveau fichier `sling.properties` sous le dossier `crx-quickstart/conf/`. Vous pouvez maintenant appliquer vos modifications personnalisées au fichier `sling.properties` nouvellement généré.

<!-- Alexandru: drafting temporarily

## Content Repository Migration {#content-repository-migration}

This migration is not required if you are upgrading from AEM 6.3. For versions older than 6.3, Adobe provides a tool that can be used to migrate the repository to the new version of the Oak Segment Tar present in AEM 6.3. It is provided as part of the quickstart package and is mandatory for any upgrades that will be using TarMK. Upgrades for environments that are using MongoMK do not require repository migration. For more information on what the benefits of the new Segment Tar format are, see the [Migrating to Oak Segment Tar FAQ](/help/sites-deploying/revision-cleanup.md#online-revision-cleanup-frequently-asked-questions).

The actual migration is performed using the standard AEM quickstart jar file, executed with a new `-x crx2oak` option which executes the crx2oak tool to simplify the upgrade and make it more robust.

>[!NOTE]
>
>If you are performing TarMK repository content migration using the CRX2Oak Quickstart extension, you might remove the **samplecontent** runmode by adding the following to the migration command line:
>
>* `--promote-runmode nosamplecontent`
>

To determine the command that you should run, use the following command:

```shell
java -Xmx4096m -jar aem-quickstart.jar -v -x crx2oak -xargs -- --load-profile <<YOUR_PROFILE>> <<ADDITIONAL_FLAGS>>
```

Where `<<YOUR_PROFILE>>` and `<<ADDITIONAL_FLAGS>>` are replaced with the profile and flags listed in the following table:

<table>
 <tbody>
  <tr>
   <td><strong>Source Repository</strong></td>
   <td><strong>Target Repository</strong></td>
   <td><strong>Profile</strong></td>
   <td><strong>Additional Flags</strong><br /> </td>
  </tr>
  <tr>
   <td>crx2 or TarMK with <code>FileDataStore</code></td>
   <td>TarMK</td>
   <td>segment-fds</td>
   <td>See Troubleshooting section below</td>
  </tr>
  <tr>
   <td>crx2</td>
   <td>MongoMK</td>
   <td>mongo-from-crx2 </td>
   <td><code>-T mongo-uri=mongo://mongo-host:mongo-port -T mongo-db=mongo-database-name</code></td>
  </tr>
  <tr>
   <td>TarMK or crx2 with <code>S3DataStore</code></td>
   <td>TarMK</td>
   <td>segment-custom-ds</td>
   <td>See Troubleshooting section below</td>
  </tr>
  <tr>
   <td>TarMK with no datastore</td>
   <td>TarMK</td>
   <td>segment-no-ds</td>
   <td> </td>
  </tr>
  <tr>
   <td>MongoMK</td>
   <td>MongoMK</td>
   <td>No migration is needed</td>
   <td> </td>
  </tr>
 </tbody>
</table>

**Where:**

* `mongo-host` is the MongoDB server IP (for example, 127.0.0.1)

* `mongo-port` is the MongoDB server port (for example: 27017)

* `mongo-database-name` represents the name of the database (for example: aem-author)

**You may also require additional switches for the following scenarios:**

* If you are performing the upgrade on a Windows system where Java memory mapping is not handled correctly, add the `--disable-mmap` parameter to the command.

For additional instructions on using the crx2oak tool, see Using the [CRX2Oak Migration Tool](/help/sites-deploying/using-crx2oak.md). The crx2oak helper JAR can be manually upgraded if needed, by manually replacing it with newer versions after unpacking the quickstart. Its location in the AEM installation folder is: `<aem-install>/crx-quickstart/opt/extensions/crx2oak.jar`. The newest version of the CRX2Oak migration tool is available for download from the Adobe Repository at: [https://repo1.maven.org/maven2/com/adobe/granite/crx2oak/](https://repo1.maven.org/maven2/com/adobe/granite/crx2oak/)

If the migration has completed successfully, the tool will exit with an exit code of zero. Additionally, check for WARN and ERROR messages in the `upgrade.log` file, located under `crx-quickstart/logs` in the AEM installation directory, as these could indicate non-fatal errors that occurred during the migration.

Check the configuration files beneath `crx-quickstart/install` folder. If a migration was necessary these will be updated to reflect the target repository.

**A note on datastores:**

While `FileDataStore` is the new default for AEM 6.3 installations, using an external datastore is not required. While using an external datastore is recommended as a best practice for production deployments, it is not a prerequisite to upgrade. Due to the complexity already present in upgrading AEM, Adobe recommends performing the upgrade without doing a datastore migration. If desired, a datastore migration can be executed afterwards as a separate effort.

## Troubleshooting Migration Issues {#troubleshooting-migration-issues}

Skip this section if you are upgrading from 6.3. While the provided crx2oak profiles should meet the needs of most customers, there are times when additional parameters will be necessary. If you run into an error during your migration, it is possible that there are aspects of your environment that require additional configuration options to be provided. If so, you will likely encounter the following error:

**Checkpoints are not copied, because no external datastore has been specified. This will result in the full repository reindexing on the first start. Use --skip-checkpoints to force the migration or see https://jackrabbit.apache.org/oak/docs/migration.html#Checkpoints_migration for more info.**

For some reason, the migration process needs access to binaries in the datastore and is unable to find it. To specify your datastore configuration, include the following flags in the `<<ADDITIONAL_FLAGS>>` portion of your migration command:

**For S3 datastores:**

```shell
--src-s3config=/path/to/SharedS3DataStore.config --src-s3datastore=/path/to/datastore
```

Where `/path/to/SharedS3DataStore.config` represents the path to your S3 datastore config file and `/path/to/datastore` represents the path to your S3 datastore.

**For File datastores:**

```shell
--src-datastore=/path/to/datastore
```

Where `/path/to/datastore` represents the path to your File Datastore.

-->

## Exécution de la mise à niveau {#performing-the-upgrade}

**Si vous utilisez S3 :**

1. Supprimez les fichiers JAR sous `crx-quickstart/install` associés à une version antérieure du connecteur S3.

1. Téléchargez la dernière version du connecteur S3 1.60.2 à partir de [https://repo1.maven.org/maven2/com/adobe/granite/com.adobe.granite.oak.s3connector/](https://repo1.maven.org/maven2/com/adobe/granite/com.adobe.granite.oak.s3connector/) <!-- Alexandru: this is a stub link for now -->

1. Extrayez le connecteur S3 (version 1.60.2) et copiez le contenu des dossiers suivants sous `crx-quickstart/install`, comme suit :

   1. Copiez `com.adobe.granite.oak.s3connector-1.60.2/jcr_root/libs/system/install/1` sous `crx-quickstart/install/1`
   1. Copiez `com.adobe.granite.oak.s3connector-1.60.2/jcr_root/libs/system/install/15` sous `crx-quickstart/install/15`

Démarrez à présent l’instance AEM à l’aide de la nouvelle commande déterminée à l’aide des informations de la section [Détermination de la commande de démarrage de mise à niveau appropriée](#determining-the-correct-upgrade-start-command).

### Détermination de la commande de démarrage de mise à niveau appropriée {#determining-the-correct-upgrade-start-command}

>[!NOTE]
>
>](https://docs.oracle.com/en/java/javase/17/docs/specs/man/java.html) La prise en charge de certains arguments Java 8/11 a été supprimée dans Java 17, consultez les [documents Oracle Java™ 17 et les [considérations relatives aux arguments Java&amp;trade pour AEM 6.5 LTS](https://git.corp.adobe.com/AdobeDocs/experience-manager-65-lts.en/blob/main/help/sites-deploying/custom-standalone-install.md#java-17-considerations-java-considerations).

Pour exécuter la mise à niveau, il est important de démarrer AEM à l’aide du fichier jar pour afficher l’instance.

Notez que le démarrage d’AEM à partir du script de démarrage ne lance pas la mise à niveau. La plupart des clientes et clients démarre AEM à l’aide du script de démarrage et ont personnalisé ce script de démarrage pour inclure des commutateurs pour les configurations d’environnement telles que les paramètres de mémoire, les certificats de sécurité, etc. Pour cette raison, Adobe recommande de suivre cette procédure pour déterminer la commande de mise à niveau appropriée :

1. Sur une instance d’AEM en cours d’exécution, exécutez les opérations ci-dessous dans une ligne de commande :

   ```shell
   ps -ef | grep java
   ```

1. Recherchez le processus AEM. Le code se présente comme suit :

   ```shell
   /usr/bin/java -server -Xmx1024m -Djava.awt.headless=true -Dsling.run.modes=author,crx3,crx3tar -jar crx-quickstart/app/cq-quickstart-6.5.0-standalone-quickstart.jar start -c crx-quickstart -i launchpad -p 4502 -Dsling.properties=conf/sling.properties
   ```

1. Modifiez la commande en remplaçant le chemin d’accès dans le fichier jar existant ( `crx-quickstart/app/aem-quickstart*.jar` dans ce cas) par le nouveau fichier jar LTS d’AEM 6.5 qui est un frère du dossier `crx-quickstart`. Avec la commande précédente comme exemple, la commande serait la suivante :

   ```shell
   /usr/bin/java -server -Xmx4096m -Djava.awt.headless=true -Dsling.run.modes=author,crx3,crx3tar -jar <AEM-6.5-LTS.jar> -c crx-quickstart -p 4502 -Dsling.properties=conf/sling.properties
   ```

   Cela permet de s’assurer que tous les paramètres de mémoire appropriés, les modes d’exécution personnalisés et d’autres paramètres d’environnement sont appliqués pour la mise à niveau. Une fois la mise à niveau terminée, l’instance peut être lancée à partir du script de démarrage lors des prochains lancements.

## Déployer le base de code mise à niveau {#deploy-upgraded-codebase}

Une fois la mise à niveau statique terminée, la base de code mise à niveau doit être déployée. La procédure de mise à jour de la base de code pour qu’elle fonctionne dans la version cible d’AEM est disponible dans la page [Mise à niveau du code et personnalisations](/help/sites-deploying/upgrading-code-and-customizations.md).

## Effectuer les vérifications et le dépannage après la mise à niveau {#perform-post-upgrade-check-troubleshooting}

Voir [Vérifications et dépannage après une mise à niveau](/help/sites-deploying/post-upgrade-checks-and-troubleshooting.md).
