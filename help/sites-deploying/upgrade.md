---
title: Mise à niveau vers Adobe Experience Manager 6.5
description: Découvrez les principes de base de la mise à niveau d’une installation Adobe Experience Manager (AEM) plus ancienne vers AEM 6.5.
contentOwner: sarchiz
topic-tags: upgrading
content-type: reference
docset: aem65
targetaudience: target-audience upgrader
feature: Upgrading
solution: Experience Manager, Experience Manager Sites
role: Admin
source-git-commit: 598d6eecbdd3887c41a36a14daa215e2e8e6e09a
workflow-type: tm+mt
source-wordcount: '195'
ht-degree: 34%

---

# Mise à niveau vers Adobe Experience Manager (AEM) 6.5 LTS {#upgrading-to-aem}

>[!NOTE]
>La mise à niveau vers AEM 6.5 LTS est prise en charge à partir des 6 derniers Service Packs.

Cette section couvre la mise à niveau d’une installation AEM vers AEM 6.5 LTS :

<!-- Alexandru: drafting for now 

* [Planning Your Upgrade](/help/sites-deploying/upgrade-planning.md)
* [Assessing the Upgrade Complexity with Pattern Detector](/help/sites-deploying/pattern-detector.md)
* [Backward Compatibility in AEM 6.5](/help/sites-deploying/backward-compatibility.md)
  This was drafted before: * [Using Offline Reindexing To Reduce Downtime During an Upgrade](/help/sites-deploying/upgrade-offline-reindexing.md)-->

<!--
* [Upgrade Procedure](/help/sites-deploying/upgrade-procedure.md)
* [Upgrading Code and Customizations](/help/sites-deploying/upgrading-code-and-customizations.md)
* [Pre-Upgrade Maintenance Tasks](/help/sites-deploying/pre-upgrade-maintenance-tasks.md)
* [Performing an In-Place Upgrade](/help/sites-deploying/in-place-upgrade.md)
* [Post Upgrade Checks and Troubleshooting](/help/sites-deploying/post-upgrade-checks-and-troubleshooting.md)
* [Sustainable Upgrades](/help/sites-deploying/sustainable-upgrades.md)
* [Lazy Content Migration](/help/sites-deploying/lazy-content-migration.md)

-->

Pour une référence conviviale aux instances d’AEM incluses dans ces procédures, les termes suivants sont utilisés tout au long de ces articles :

* L’instance *source* est l’instance AEM à partir de laquelle vous effectuez une mise à niveau.
* L’instance *cible* est celle vers laquelle vous effectuez une mise à niveau.

## Qu’est-ce qui a changé ? {#what-has-changed}

### Mises à jour {#updates}

La couche Foundation prend désormais en charge Java 17, en incorporant les derniers lots open source d’Apache Sling, Felix et Jackrabbit Oak. En outre, le packaging de l’uber-jar AEM 6.5 LTS a changé. En outre, quelques fonctionnalités héritées ont été supprimées d’AEM 6.5 LTS. Pour plus d’informations, consultez les sections [Notes de mise à jour](/help/release-notes/release-notes.md#whats-new-what-s-new) et [Liste des lots obsolètes désinstallés après la mise à niveau](/help/sites-deploying/obsolete-bundles.md)

Le LTS AEM 6.5 met l’accent sur la rétrocompatibilité des fonctionnalités et est fourni avec un outil d’analyse. Consultez [Évaluation de la complexité de la mise à niveau à l’aide d’AEM Analyzer](/help/sites-deploying/pattern-detector.md) pour évaluer la complexité lorsque vous commencez à [planifier la mise à niveau](/help/sites-deploying/upgrade-planning.md).
