---
title: Tâches de maintenance avant la mise à niveau
description: Découvrez les tâches préalables à la mise à niveau conseillées pour AEM.
contentOwner: sarchiz
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: upgrading
docset: aem65
feature: Upgrading
solution: Experience Manager, Experience Manager Sites
role: Admin
exl-id: 1dd5d370-d1d4-4d15-9663-35b941b9076b
source-git-commit: 8f7bbc3887601e10cf29e99ee54959a10c8a3f98
workflow-type: tm+mt
source-wordcount: '1116'
ht-degree: 80%

---

# Tâches de maintenance avant la mise à niveau{#pre-upgrade-maintenance-tasks}

Avant de commencer la mise à niveau, il est important d’effectuer ces tâches de maintenance pour vous assurer que le système est prêt et peut être restauré en cas de problème :

* [Définitions d’index](#index-definitions)
* [Vérification de la disponibilité de l’espace disque nécessaire](/help/sites-deploying/pre-upgrade-maintenance-tasks.md#ensure-sufficient-disk-space)
* [Sauvegarde complète d’AEM](/help/sites-deploying/pre-upgrade-maintenance-tasks.md#fully-back-up-aem)
* [Génération du fichier quickstart.properties](/help/sites-deploying/pre-upgrade-maintenance-tasks.md#generate-quickstart-properties)
* [Configuration de la purge du workflow et du journal d’audit](/help/sites-deploying/pre-upgrade-maintenance-tasks.md#configure-wf-audit-purging)
* [Installation, configuration et exécution des tâches précédant la mise à niveau](/help/sites-deploying/pre-upgrade-maintenance-tasks.md#install-configure-run-pre-upgrade-tasks)
* [Suppression des mises à jour du répertoire /install](/help/sites-deploying/pre-upgrade-maintenance-tasks.md#remove-updates-install-directory)
* [Arrêt de toutes les instances Cold Standby](/help/sites-deploying/pre-upgrade-maintenance-tasks.md#stop-tarmk-coldstandby-instance)
* [Désactivation des tâches planifiées personnalisées](/help/sites-deploying/pre-upgrade-maintenance-tasks.md#disable-custom-scheduled-jobs)
* [Exécution d’un nettoyage des révisions hors ligne](/help/sites-deploying/pre-upgrade-maintenance-tasks.md#execute-offline-revision-cleanup)
* [Exécution de la récupération de l’espace mémoire du magasin de données](/help/sites-deploying/pre-upgrade-maintenance-tasks.md#execute-datastore-garbage-collection)
* [Mise à niveau du schéma de base de données si nécessaire](/help/sites-deploying/pre-upgrade-maintenance-tasks.md#upgradethedatabaseschemaifneeded)
* [Rotation des fichiers journaux](/help/sites-deploying/pre-upgrade-maintenance-tasks.md#rotate-log-files)

## Définitions d’index {#index-definitions}

Assurez-vous d’avoir installé les définitions d’index requises publiées avec le dernier pack de services AEM 6.5. (Pour plus d’informations[&#x200B; consultez les notes de mise à jour du pack de services AEM 6.5 &#x200B;](https://experienceleague.adobe.com/fr/docs/experience-manager-65/content/release-notes/release-notes)).

## Vérification de la disponibilité de l’espace disque nécessaire {#ensure-sufficient-disk-space}

Lors de l’exécution de la mise à niveau, assurez-vous que l’espace disque est suffisant.

## Sauvegarde complète d’AEM {#fully-back-up-aem}

AEM doit être entièrement sauvegardé avant le début de la mise à niveau. Veillez à sauvegarder votre référentiel, l’installation de l’application, le magasin de données et les instances Mongo, le cas échéant. Pour plus d’informations sur la sauvegarde et la restauration d’une instance AEM, reportez-vous à la section [Sauvegarde et restauration](/help/sites-administering/backup-and-restore.md).

## Générer le fichier quickstart.properties {#generate-quickstart-properties}

Lors du démarrage d’AEM depuis le fichier jar, un fichier `quickstart.properties` est généré sous `crx-quickstart/conf`. Si AEM a uniquement été démarré avec le script de démarrage dans le passé, ce fichier n’est pas présent et la mise à niveau échoue. Assurez-vous de vérifier l’existence de ce fichier et redémarrez AEM à partir du fichier jar s’il n’est pas présent.

## Configuration de la purge du workflow et du journal d’audit {#configure-wf-audit-purging}

Les tâches `WorkflowPurgeTask` et `com.day.cq.audit.impl.AuditLogMaintenanceTask` nécessitent des configurations OSGi distinctes et ne fonctionneront pas sans celles-ci. Si elles échouent lors de l’exécution de la tâche avant la mise à niveau, des configurations manquantes en sont la raison la plus probable. Par conséquent, veillez à ajouter des configurations OSGi pour ces tâches ou à les supprimer complètement de la liste des tâches d’optimisation avant la mise à niveau si vous ne souhaitez pas les exécuter. Vous trouverez la documentation relative à la configuration des tâches de purge des workflows dans la section [Administration des instances de workflow](/help/sites-administering/workflows-administering.md) et la configuration de la tâche de maintenance du journal d’audit dans la section [Maintenance du journal d’audit dans AEM 6](/help/sites-administering/operations-audit-log.md).


## Installation, configuration et exécution des tâches précédant la mise à niveau {#install-configure-run-pre-upgrade-tasks}

Les tâches de maintenance préalables à la mise à niveau qui devaient auparavant être effectuées manuellement sont optimisées et automatisées. L’optimisation de la maintenance avant la mise à niveau permet de déclencher ces tâches de manière unifiée et d’examiner leur résultat à la demande.

### Utilisation {#how-to-use-it}

Le composant OSGi `PreUpgradeTasksMBean` est préconfiguré avec une liste de tâches de maintenance bénéficiant déjà de la mise à niveau, pouvant toutes être exécutées simultanément. Vous pouvez configurer les tâches en suivant la procédure ci-dessous :

1. Accédez à la console web en vous rendant sur *https://serveraddress:serverport/system/console/configMgr*

1. Recherchez « **preupgradetasks** », puis cliquez sur le premier composant correspondant. Le nom complet du composant est `com.adobe.aem.upgrade.prechecks.mbean.impl.PreUpgradeTasksMBeanImpl`.

1. Modifiez la liste des tâches de maintenance devant être exécutées comme illustré ci-dessous :

   ![1487758925984](assets/1487758925984.png)

Vous trouverez ci-dessous une description du mode d’exécution pour lequel chaque tâche de maintenance est conçue.

| Tâche | Remarques |
|---|---|
| WorkflowPurgeTask | Doit configurer la configuration OSGi de purge du workflow Granite d’Adobe avant l’exécution. |
| GenerateBundlesListFileTask |   |
| TâcheNettoyageRévision |   |
| com.day.cq.audit.impl.AuditLogMaintenanceTask | Doit configurer la configuration OSGi du planificateur de purge du journal d’audit avant l’exécution. |

### Configuration par défaut des contrôles de l’intégrité avant la mise à niveau {#default-configuration-of-the-pre-upgrade-health-checks}

Le composant OSGi `PreUpgradeTasksMBeanImpl` est préconfiguré avec une liste de balises de vérification de l’intégrité précédant la mise à niveau à exécuter lorsque la méthode `runAllPreUpgradeHealthChecks` est appelée :

* **système** : balise utilisée par les contrôles de l’intégrité de la maintenance Granite

* **avant la mise à niveau** : balise personnalisée qui peut être ajoutée à toutes les vérifications d’intégrité dont vous pouvez définir l’exécution avant une mise à niveau

**Méthodes MBean**

La fonctionnalité Bean gérée est accessible à l’aide de la [console JMX](/help/sites-administering/jmx-console.md).

Vous pouvez accéder aux MBeans en procédant comme suit :

1. Accédez à la console JMX à l’adresse *https://serveraddress:serverport/system/console/jmx*
1. Recherchez **PreUpgradeTasks** et cliquez sur le résultat.

1. Sélectionnez une méthode à partir de la section **Opérations** et sélectionnez **Invoquer** dans la fenêtre suivante.

Vous trouverez ci-dessous la liste de toutes les méthodes disponibles offertes par `PreUpgradeTasksMBeanImpl` :

| Nom de méthode | Type | Description |
|---|---|---|
| runAllPreUpgradeTasks() | ACTION | Exécute toutes les tâches de maintenance avant la mise à niveau de la liste. |
| runPreUpgradeTask(preUpgradeTaskName) | ACTION | Exécute la tâche de maintenance avant la mise à niveau avec le nom donné en tant que paramètre. |
| getPreUpgradeTaskLastRunTime(preUpgradeTaskName) | ACTION | Affiche l’heure d’exécution exacte de la tâche de maintenance avant la mise à niveau avec le nom donné en tant que paramètre. |
| getPreUpgradeTaskLastRunState(preUpgradeTaskName) | ACTION | Affiche le dernier état d’exécution de la tâche de maintenance avant la mise à niveau avec le nom donné en tant que paramètre. |
| runAllPreUpgradeHealthChecks(shutdownOnSuccess) | ACTION | Exécute toutes les vérifications d’intégrité avant la mise à niveau et enregistre leur statut dans un fichier nommé preUpgradeHCStatus.properties dans le chemin d’accès Sling de l’accueil. Si shutdownOnSuccess a la valeur true, l’instance AEM est arrêtée, mais uniquement si toutes les vérifications d’intégrité avant la mise à niveau renvoient le statut « OK ». Le fichier de propriétés est utilisé comme prérequis pour toute mise à niveau ultérieure et le processus de mise à niveau est arrêté si l’exécution de la vérification de l’intégrité précédant la mise à niveau a échoué. Si vous souhaitez tout de même ignorer le résultat des vérifications d’intégrité avant la mise à niveau et lancer la mise à niveau, vous pouvez supprimer le fichier . |
| detectorUsageOfUnavailableAPI(aemVersion) | ACTION | Répertorie tous les packages importés qui ne fonctionneront plus lors de la mise à niveau vers la version d’AEM spécifiée. La version AEM cible doit être indiquée en tant que paramètre. |

>[!NOTE]
>
>Les méthodes MBean peuvent être invoquées via :
>
>* La console JMX
>* Toute application externe qui se connecte à JMX
>* cURL
>

## Suppression des mises à jour du répertoire /install {#remove-updates-install-directory}

>[!NOTE]
>
>Supprimez uniquement les packages du répertoire crx-quickstart/install APRÈS avoir arrêté l’instance AEM. Cette étape est l’une des dernières avant de commencer la procédure de mise à niveau statique.

Supprimez tous les packs de services, les packs de fonctionnalités ou les correctifs logiciels qui ont été déployés via le répertoire `crx-quickstart/install` sur le système de fichiers local. Cela évite l’installation accidentelle d’anciens correctifs et packs de services en plus de la nouvelle version d’AEM une fois la mise à jour terminée.

## Arrêt de toutes les instances Cold Standby {#stop-tarmk-coldstandby-instance}

Si vous utilisez un secours différé TarMK, arrêtez tous les secours différés. Cela garantit un moyen efficace de revenir en ligne en cas de problèmes lors de la mise à niveau. Une fois la mise à niveau terminée, les secours différés doivent être reconstruits à partir des instances principales mises à niveau.

## Désactivation des tâches planifiées personnalisées {#disable-custom-scheduled-jobs}

Désactivez toutes les tâches OSGi planifiées incluses dans le code de votre application.

## Exécution d’un nettoyage des révisions hors ligne {#execute-offline-revision-cleanup}

>[!NOTE]
>
>Cette étape n’est nécessaire que pour les installations TarMK.

Si vous utilisez TarMK, vous devez exécuter le nettoyage des révisions hors ligne avant la mise à niveau. Cela permet à l’étape de migration du référentiel et aux tâches de mise à niveau suivantes de s’exécuter beaucoup plus rapidement et de garantir que le nettoyage des révisions en ligne peut s’exécuter correctement une fois la mise à niveau terminée. Pour plus d’informations sur l’exécution du nettoyage des révisions hors ligne, reportez-vous à la section [Exécution du nettoyage des révisions hors ligne](/help/sites-deploying/revision-cleanup.md#revision-cleanuprevision-cleanup).

## Exécution de la récupération de l’espace mémoire du magasin de données {#execute-datastore-garbage-collection}

Après avoir exécuté le nettoyage des révisions sur les instances CRX3, vous devez exécuter la récupération de l’espace mémoire du magasin de données pour supprimer tous les objets blob non référencés dans le magasin de données. Pour obtenir des instructions, consultez la documentation sur la [récupération de l’espace mémoire du magasin de données](/help/sites-administering/data-store-garbage-collection.md).

## Rotation des fichiers journaux {#rotate-log-files}

Nous vous recommande d’archiver vos fichiers journaux actuels avant de commencer la mise à niveau. Cela facilite la surveillance et l’analyse de vos fichiers journaux pendant et après la mise à niveau pour identifier et résoudre les problèmes qui peuvent surgir.
