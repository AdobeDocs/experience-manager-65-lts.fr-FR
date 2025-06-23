---
title: Notes de mise à jour actuelles de Adobe Experience Manager 6.5 LTS
description: Recherchez les informations de mise à jour actuelles pour Adobe Experience Manager 6.5 LTS.
solution: Experience Manager
feature: Release Information
role: User,Admin,Architect,Developer
exl-id: b5a8f555-c061-4fe2-a100-cc01335959cb
source-git-commit: d353cde4e9cc2af738e600d5a9b74928d98496cb
workflow-type: tm+mt
source-wordcount: '1019'
ht-degree: 34%

---

# Notes de mise à jour actuelles de Adobe Experience Manager 6.5 LTS {#release-notes}

## Informations sur la version {#release-information}

| Produit | [!DNL Adobe Experience Manager] |
|---|---|
| Version | 6,5 LTS |
| Type | Version majeure |
| Date de disponibilité générale | samedi 7 mars 2025 |

## Nouveautés {#what-s-new}

[!DNL Adobe Experience Manager] 6.5 LTS est une mise à niveau de la base de code d’[!DNL Adobe Experience Manager] 6.5. Il fournit des correctifs clés pour les clients, des améliorations prioritaires pour les clients et des correctifs généraux orientés vers la stabilisation du produit. Elle comprend également les versions du pack de services [!DNL Adobe Experience Manager] 6.5 jusqu’au SP22.

Vous en trouverez un aperçu dans la liste ci-dessous, puis des détails complets dans les pages suivantes.

### [!DNL Experience Manager Foundation] {#experience-manager-foundation}

La plateforme du LTS [!DNL Adobe Experience Manager] 6.5 s’appuie sur les versions mises à jour du framework OSGi (Apache Sling et Apache Felix) et du référentiel de contenu Java™ : Apache Jackrabbit Oak 1.68.x.

Eclipse Jetty 11.0.x est utilisé comme moteur de servlet pour Quickstart.

#### Prise en charge de Java™  {#java-support}

* Prise en charge de Java™ 17 et Java™ 21.
* Pour des performances optimales, remplacez les valeurs par défaut du CPG par d’autres valeurs. Pour plus d’informations, consultez la section [Installation et mise à jour](/help/sites-deploying/custom-standalone-install.md).
* Adobe distribue des mises à jour de maintenance Java™ 17 et Java™ 21 pour l’utilisation par les clients dans les projets liés à AEM, lorsqu’elles ne sont pas disponibles publiquement depuis Oracle.

#### Package Uberjar {#uber-jar-packaging}

* Il existe une légère différence dans le conditionnement Uberjar d’AEM 6.5 LTS. Pour plus d’informations, voir [Mise à jour de la version AEM Uber Jar](/help/sites-deploying/upgrading-code-and-customizations.md#update-the-aem-uber-jar-version).

#### Mise à niveau {#upgrade}

* Pour plus d’informations sur la procédure de mise à niveau, consultez la [documentation de mise à niveau](/help/sites-deploying/upgrade.md).

## Installation et mise à jour {#install-update}

Pour connaître les exigences de configuration, consultez les [instructions d’installation](/help/sites-deploying/custom-standalone-install.md).

Pour obtenir des instructions détaillées, consultez la [documentation de mise à niveau](/help/sites-deploying/upgrade.md).

>[!NOTE]
>
> Pour les nouvelles installations d’AEM 6.5 LTS, les définitions d’index doivent être installées séparément. Pour plus d’informations, reportez-vous [ci](/help/sites-deploying/pre-upgrade-maintenance-tasks.md#index-definitions).

## Plateformes prises en charge {#supported-platforms}

Recherchez la matrice complète des plateformes prises en charge, y compris le niveau de prise en charge dans les [exigences techniques LTS d’AEM 6.5](/help/sites-deploying/technical-requirements.md).

>[!NOTE]
>
>Il est recommandé d’utiliser Java™ 17/Java™ 21 avec AEM 6.5 LTS.

## Fonctionnalités obsolètes et supprimées {#deprecated-and-removed-features}

Adobe examine continuellement les fonctionnalités du produit afin d’améliorer la valeur client en modernisant ou en remplaçant les anciennes fonctionnalités. Ces modifications sont effectuées avec une attention particulière portée à la rétrocompatibilité.

Pour communiquer la suppression ou le remplacement imminent(e) de fonctionnalités d’Adobe Experience Manager (AEM), les règles suivantes s’appliquent :

1. L’annonce de la suppression arrive en premier. Bien qu’elles soient obsolètes, les fonctionnalités sont toujours disponibles, mais ne sont pas améliorées.
1. La suppression des fonctionnalités obsolètes se produit au plus tôt dans la version majeure suivante. La date cible réelle de suppression est prévue pour une annonce ultérieure.

Ce processus donne aux clients au moins un cycle de version pour adapter leur implémentation à une nouvelle version ou à un produit de remplacement pour une fonctionnalité obsolète, avant que la suppression ne soit effective.

### Fonctionnalités obsolètes {#deprecated-features}

Cette section répertorie les fonctionnalités qu’Adobe a abandonnées dans AEM 6.5 LTS. En règle générale, Adobe rend les fonctionnalités obsolètes avant de les supprimer dans une version ultérieure et fournit une alternative.


Il est conseillé aux clients de réfléchir à leur utilisation de la fonctionnalité dans leur déploiement actuel et de prévoir la modification de leur mise en œuvre de façon à utiliser l’alternative proposée.

| Domaine | Fonctionnalité | Remplacement | Version (SP) |
|---|---|---|---|
| Sites | [Éditeur SPA](/help/sites-developing/spa-overview.md) | Les éditeurs recommandés pour la gestion du contenu découplé dans AEM sont les suivants : <br>- [Éditeur universel](/help/sites-developing/universal-editor/introduction.md) pour la modification visuelle.<br>- [Éditeur de fragment de contenu](/help/assets/content-fragments/content-fragments-managing.md) pour la modification basée sur les formulaires. | 6.5 LTS (disponibilité générale) |

### Fonctionnalités supprimées {#removed-features}

Cette section répertorie les fonctionnalités qui ont été supprimées d’AEM 6.5 LTS. Ces fonctionnalités étaient signalées comme obsolètes dans les versions antérieures.

| Domaine | Fonctionnalité | Remplacement | Version (SP) |
|--- |--- |--- |--- |
| Commerce | AEM CIF Classic n’est pas pris en charge. | Migration vers [AEM CIF](/help/commerce/cif/migration.md). | 6.5 LTS (disponibilité générale) |
| Solutions | Social/Communities n’est pas pris en charge. | Aucun remplacement disponible. | 6.5 LTS (disponibilité générale) |
| Screens | Screens ne sont pas pris en charge. | Aucun remplacement disponible. | 6.5 LTS (disponibilité générale) |
| Ressources | `dam-pim` et `dam-rating` ne sont pas pris en charge, car les lots dépendent des réseaux sociaux. | Aucun remplacement disponible. | 6.5 LTS (disponibilité générale) |
| Ressources | `com.day.cq.dam.scene7.api.model.Scene7ViewerConfig#getSettings()` a été supprimé. | Utilisez l’autre `com.day.cq.dam.scene7.api.model.Scene7ViewerConfig#getSettingsList()` d’api qui a été ajouté. | 6.5 LTS (disponibilité générale) |
| Portail | AEM Portal Director n’est pas pris en charge. | Aucun remplacement disponible. | 6.5 LTS (disponibilité générale) |
| Granite | Le lot `com.adobe.granite.socketio` est supprimé. | Aucun remplacement disponible. | 6.5 LTS (disponibilité générale) |
| Granite | `com.adobe.granite.crx-explorer` n’est pas pris en charge. | Aucun remplacement disponible. | 6.5 LTS (disponibilité générale) |
| Granite | `crx2oak` n’est pas pris en charge. | Sélectionnez la version appropriée de [oak-upgrade](https://mvnrepository.com/artifact/org.apache.jackrabbit/oak-upgrade) | 6.5 LTS (disponibilité générale) |
| Adobe | `com.adobe.cq.cq-searchpromote-integration` n’est pas pris en charge. | Aucun remplacement disponible. | 6.5 LTS (disponibilité générale) |
| Goyave | Toutes les dépendances guava sont désormais supprimées dans AEM. Par conséquent, le lot `com.adobe.granite.osgi.wrapper.guava-15.0.0-0002` ne fait pas partie d’AEM. | Les clients peuvent ajouter de la goyave eux-mêmes s’ils en dépendent ou remplacer le code goyave par des collections java ou d’autres alternatives si possible. | 6.5 LTS (disponibilité générale) |
| We.Retail | L’exemple de site We-retail n’est pas pris en charge. | Aucun remplacement disponible. | 6.5 LTS (disponibilité générale) |
| Open Source | `oak-solr-osgi` lot n’est pas pris en charge. | Aucun remplacement disponible. | 6.5 LTS (disponibilité générale) |
| Open Source | `org.apache.servicemix.bundles.abdera-parser`, `org.apache.servicemix.bundles.jdom` et `org.apache.sling.atom.taglib` ne sont pas pris en charge. | Aucun remplacement disponible. | 6.5 LTS (disponibilité générale) |
| Open Source | Les packages `org.apache.commons.io` sont désormais exportés depuis `org.apache.commons.commons-io`. | Aucune modification n’est requise. | 6.5 LTS (disponibilité générale) |
| Open Source | `javax.mail` packages sont exportés à partir du lot `com.sun.javax.mail`. | Aucune modification n’est requise. | 6.5 LTS (disponibilité générale) |
| Open Source | Les packages `org.apache.jackrabbit.api` sont désormais exportés à partir du lot `org.apache.jackrabbit.oak-jackrabbit-api` . | Aucune modification n’est requise. | 6.5 LTS (disponibilité générale) |
| Open Source | `com.github.jknack.handlebars` n’est pas pris en charge | Sélectionnez la [version](https://mvnrepository.com/artifact/com.github.jknack/handlebars) appropriée. | 6.5 LTS (disponibilité générale) |

## Problèmes connus {#known-issues}

### Problème avec le lot de scripts JSP dans AEM 6.5.21-6.5.23 et AEM 6.5 LTS GA

AEM 6.5.21, 6.5.22, 6.5.23 et AEM 6.5 LTS GA sont fournis avec le lot `org.apache.sling.scripting.jsp:2.6.0`, qui contient un problème connu. Le problème se produit généralement sous une charge élevée lorsque l’instance AEM gère de nombreuses requêtes simultanées.

Lorsque ce problème se produit, l’une des exceptions suivantes peut apparaître dans les journaux d’erreurs avec des références à `org.apache.sling.scripting.jsp:2.6.0` :

* `java.io.IOException: classFile.delete() failed`
* `java.io.IOException: tmpFile.renameTo(classFile) failed`
* `java.lang.ArrayIndexOutOfBoundsException: Index 0 out of bounds for length 0`
* `java.io.FileNotFoundException`

Un correctif [cq-6.5.lts.0-hotfix-NPR-42640](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq660/hotfixes/cq-6.5.lts.0-hotfix-NPR-42640-1.2.zip) est disponible pour résoudre ce problème.

### Échec de connexion à Dispatcher avec la fonction SSL uniquement {#ssl-only-feature}

Lors de l’activation de la fonction SSL uniquement dans les déploiements AEM, un problème connu affecte la connectivité entre les instances Dispatcher et AEM. Une fois cette fonctionnalité activée, les contrôles d’intégrité peuvent échouer et la communication entre les instances Dispatcher et AEM peut être interrompue.

**Impact:**

* Échec des contrôles d’intégrité avec les codes de réponse HTTP 500
* Trafic rompu entre les instances Dispatcher et AEM
* Le contenu ne peut pas être correctement diffusé via Dispatcher

**Environnements affectés :**

* Déploiements d’AEM avec les configurations Dispatcher
* Systèmes sur lesquels la fonction SSL uniquement a été activée

**Solution :**
Si vous rencontrez ce problème, contactez le service clientèle d’Adobe. Un correctif [cq-6.5.lts.0-hotfix-CQ-4359803](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq660/hotfixes/cq-6.5.lts.0-hotfix-CQ-4359803-1.0.2.zip) est disponible pour résoudre ce problème. N’essayez pas d’activer les fonctionnalités SSL uniquement avant d’avoir appliqué le correctif nécessaire.

## Sites web restreints{#restricted-sites}

Ces sites Web sont disponibles uniquement pour les clients. Si vous êtes client et avez besoin d’un accès, contactez votre responsable de compte Adobe.

* [Téléchargement du produit à l’adresse licensing.adobe.com](https://licensing.adobe.com/)
* [Contacter l’assistance clientèle Adobe](https://experienceleague.adobe.com/fr/docs/customer-one/using/home).

