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
source-git-commit: f66bb283e5c2a746821839269e112be8c2714ba7
workflow-type: tm+mt
source-wordcount: '317'
ht-degree: 29%

---

# Mise à niveau vers Adobe Experience Manager (AEM) 6.5 LTS {#upgrading-to-aem}

>[!NOTE]
>La mise à niveau vers AEM 6.5 LTS est prise en charge à partir des 6 derniers Service Packs.

Cette section décrit la mise à niveau d’une installation AEM vers AEM 6.5 :

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

Voici les principales modifications à souligner au cours des dernières versions d’AEM :

1. La couche Foundation a été mise à niveau pour prendre en charge Java 17 (qui comprend des couches open source de lots d’Apache Sling, Apache Felix et Apache Jackrabbit Oak)

1. Le package jar AEM 6.5 LTS prend désormais en charge les spécifications 5 des API de servlet Jarkarta et le package war peut être déployé sur les conteneurs de servlet mettant en œuvre les spécifications 5/6 des API de servlet Jakarta

1. Le package de l’uber-jar LTS AEM 6.5 a été modifié. Pour plus d’informations, consultez [Mise à niveau du code et des personnalisations](/help/sites-deploying/upgrading-code-and-customizations.md).

### Fonctionnalités/artefacts hérités supprimés {#removed-legacy-features-artifacts}

Les solutions héritées suivantes ont été supprimées d’AEM 6.5 LTS. Pour plus d’informations, reportez-vous à à déterminer : lien vers les notes de mise à jour et [ Liste des lots obsolètes désinstallés après la mise à niveau](/help/sites-deploying/obsolete-bundles.md)

1. Social
1. Commerce
1. Screens
1. We-retail
1. Intégration de la recherche et de la promotion

**Artefacts supprimés**

1. CRX-explorer
1. Crx2oak
1. Google guava (supprimé en raison de vulnérabilités de sécurité)
1. Analyseur Android (supprimé en raison de failles de sécurité)
1. jdom (`org.apache.servicemix.bundles.jdom`) (supprimé en raison de failles de sécurité)
1. `com.github.jknack.handlebars` (supprimé en raison de vulnérabilités de sécurité)

Le LTS AEM 6.5 met l’accent sur la rétrocompatibilité des fonctionnalités et est fourni avec un outil d’analyse. Consultez [Évaluation de la complexité de la mise à niveau à l’aide d’AEM Analyzer](/help/sites-deploying/pattern-detector.md) pour évaluer la complexité lorsque vous commencez à planifier la mise à niveau. Pour plus d’informations sur les autres modifications apportées, consultez les notes de mise à jour complètes ici. À déterminer : lien vers les notes de mise à jour d’AEM 6.5 LTS.