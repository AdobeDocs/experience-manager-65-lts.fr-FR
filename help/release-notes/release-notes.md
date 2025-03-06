---
title: Notes de mise à jour actuelles de Adobe Experience Manager 6.5 LTS
description: Voici les notes de mise à jour actuelles de Adobe Experience Manager 6.5 LTS.
exl-id: b5a8f555-c061-4fe2-a100-cc01335959cb
source-git-commit: 9bbd7acd498a1a0614db246f9d1326a62c199806
workflow-type: tm+mt
source-wordcount: '796'
ht-degree: 40%

---

# Notes de mise à jour actuelles de Adobe Experience Manager 6.5 LTS {#release-notes}

## Informations sur la version {#release-information}

| Produit | [!DNL Adobe Experience Manager] |
|---|---|
| Version | 6,5 LTS |
| Type | Version majeure |
| Date de disponibilité générale | samedi 7 mars 2025 |

## Nouveautés {#what-s-new}

[!DNL Adobe Experience Manager] 6.5 LTS est une mise à niveau de la base de code d’[!DNL Adobe Experience Manager] 6.5. Cette version comporte de nouvelles fonctionnalités améliorées, des correctifs clés de bugs signalés par des clients ou des clientes, des améliorations prioritaires demandées par les clients et les clientes et des correctifs de bugs généraux destinés à améliorer la stabilité du produit. Elle comprend également les versions du pack de services [!DNL Adobe Experience Manager] 6.5 jusqu’au SP22.

Vous en trouverez un aperçu dans la liste ci-dessous, puis des détails complets dans les pages suivantes.

### [!DNL Experience Manager Foundation] {#experience-manager-foundation}

La plateforme du LTS [!DNL Adobe Experience Manager] 6.5 repose sur les versions mises à jour du framework OSGi (Apache Sling et Apache Felix) et du référentiel de contenu Java™ : Apache Jackrabbit Oak 1.68.0.

Le démarrage rapide utilise Eclipse Jetty 11.0.x comme moteur de servlet.

#### Prise en charge de Java™  {#java-support}

* Prise en charge de Java™ 17.
* Pour des performances optimales, remplacez les valeurs par défaut du CPG par d’autres valeurs. Pour plus d’informations, consultez la section [Installation et mise à jour](/help/sites-deploying/custom-standalone-install.md).
* Les mises à jour de maintenance Java™ 17 sont distribuées par Adobe pour que les clients puissent les utiliser dans les projets liés à AEM, lorsqu’elles ne sont pas disponibles publiquement depuis Oracle.

#### Package Uberjar {#uber-jar-packaging}

* Il existe une légère différence dans le conditionnement Uberjar d’AEM 6.5 LTS. Pour plus d’informations [voir ](/help/sites-deploying/upgrading-code-and-customizations.md#update-the-aem-uber-jar-version-update-the-aem-uber-jar-version).

#### Mise à niveau {#upgrade}

* Pour plus d’informations sur la procédure de mise à niveau, consultez la [documentation de mise à niveau](/help/sites-deploying/upgrade.md).

## Installation et mise à jour {#install-update}

Pour connaître les exigences de configuration, consultez les [instructions d’installation](/help/sites-deploying/custom-standalone-install.md).

Pour obtenir des instructions détaillées, consultez la [documentation de mise à niveau](/help/sites-deploying/upgrade.md).

## Plateformes prises en charge {#supported-platforms}

Recherchez la matrice complète des plateformes prises en charge, y compris le niveau de prise en charge dans les [exigences techniques LTS d’AEM 6.5](/help/sites-deploying/technical-requirements.md).

>[!NOTE]
>
>Il est recommandé d’utiliser Java™ 17 avec AEM 6.5 LTS.

## Fonctionnalités obsolètes et supprimées {#deprecated-and-removed-features}

Adobe étudie constamment les fonctionnalités du produit de façon à les réinventer au fil du temps ou à remplacer les fonctions plus anciennes par des variantes plus modernes, pour améliorer la valeur client globale, le tout en faisant toujours attention à la compatibilité ascendante.

Pour communiquer la suppression ou le remplacement imminent(e) de fonctionnalités d’Adobe Experience Manager (AEM), les règles suivantes s’appliquent :

1. L’annonce de la suppression arrive en premier. Bien qu’elles soient obsolètes, les fonctionnalités sont toujours disponibles, mais ne sont pas améliorées.
1. La suppression des fonctionnalités obsolètes se produit au plus tôt dans la version majeure suivante. La date précise de suppression sera annoncée plus tard.

Ce processus donne aux clients au moins un cycle de version pour adapter leur implémentation à une nouvelle version ou à un produit de remplacement pour une fonctionnalité obsolète, avant que la suppression ne soit effective.

### Fonctionnalités obsolètes {#deprecated-features}

Cette section répertorie les fonctionnalités qui ont été marquées comme obsolètes par AEM 6.5 LTS. En règle générale, les fonctionnalités dont la suppression est prévue dans une version ultérieure sont d’abord définies comme obsolètes, et une alternative est fournie.

Il est conseillé aux clients de réfléchir à leur utilisation de la fonctionnalité dans leur déploiement actuel et de prévoir la modification de leur mise en œuvre de façon à utiliser l’alternative proposée.

| Domaine | Fonctionnalité | Remplacement | Version (SP) |
|---|---|---|---|
| Sites | [Éditeur SPA](/help/sites-developing/spa-overview.md) | Les éditeurs recommandés pour la gestion du contenu découplé dans AEM sont les suivants : <br>- [Éditeur universel](/help/sites-developing/universal-editor/introduction.md) pour la modification visuelle.<br>- [Éditeur de fragment de contenu](/help/assets/content-fragments/content-fragments-managing.md) pour la modification basée sur les formulaires. | 6,5 LTS GA |

### Fonctionnalités supprimées {#removed-features}

Cette section répertorie les fonctionnalités qui ont été supprimées d’AEM 6.5 LTS. Ces fonctionnalités étaient signalées comme obsolètes dans les versions antérieures.

| Domaine | Fonctionnalité | Remplacement | Version (SP) |
|--- |--- |--- |--- |
| Commerce | AEM CIF Classic n’est pas pris en charge. | Vous devez migrer vers [AEM CIF](/help/commerce/cif/migration.md). | 6,5 LTS GA |
| Solutions | Social/Communities n’est pas pris en charge. | Aucun remplacement disponible. | 6,5 LTS GA |
| Screens | Screens n’est pas pris en charge. | Aucun remplacement disponible. | 6,5 LTS GA |
| Ressources | `dam-pim` et `dam-rating` ne sont pas pris en charge, car les lots dépendent des réseaux sociaux. | Aucun remplacement disponible. | 6,5 LTS GA |
| Ressources | `com.day.cq.dam.scene7.api.model.Scene7ViewerConfig#getSettings()` a été supprimé. | Utilisez l’autre `com.day.cq.dam.scene7.api.model.Scene7ViewerConfig#getSettingsList()` d’api qui a été ajouté. | 6,5 LTS GA |
| Portail | AEM Portal Director n’est pas pris en charge. | Aucun remplacement disponible. | 6,5 LTS GA |
| Granite | Le lot `com.adobe.granite.socketio` est supprimé. | Aucun remplacement disponible. | 6,5 LTS GA |
| Granite | `com.adobe.granite.crx-explorer` n’est pas pris en charge. | Aucun remplacement disponible. | 6,5 LTS GA |
| Granite | `crx2oak` n’est pas pris en charge. | Sélectionnez la version appropriée de [oak-upgrade](https://mvnrepository.com/artifact/org.apache.jackrabbit/oak-upgrade) | 6,5 LTS GA |
| Adobe | `com.adobe.cq.cq-searchpromote-integration` n’est pas pris en charge. | Aucun remplacement disponible. | 6,5 LTS GA |
| Goyave | Toutes les dépendances guava sont désormais supprimées dans AEM. Par conséquent, le lot `com.adobe.granite.osgi.wrapper.guava-15.0.0-0002` ne fait pas partie d’AEM. | Les clients peuvent ajouter de la goyave eux-mêmes s’ils en dépendent ou remplacer le code goyave par des collections java ou d’autres alternatives si possible. | 6,5 LTS GA |
| We.Retail | L’exemple de site We-retail n’est pas pris en charge. | Aucun remplacement disponible. | 6,5 LTS GA |
| Open Source | `oak-solr-osgi` lot n’est pas pris en charge. | Aucun remplacement disponible. | 6,5 LTS GA |
| Open Source | `org.apache.servicemix.bundles.abdera-parser`, `org.apache.servicemix.bundles.jdom` et `org.apache.sling.atom.taglib` ne sont pas pris en charge. | Aucun remplacement disponible. | 6,5 LTS GA |
| Open Source | Les packages `org.apache.commons.io` sont désormais exportés depuis `org.apache.commons.commons-io`. | Aucune modification n’est requise. | 6,5 LTS GA |
| Open Source | `javax.mail` packages sont exportés à partir du lot `com.sun.javax.mail`. | Aucune modification n’est requise. | 6,5 LTS GA |
| Open Source | Les packages `org.apache.jackrabbit.api` sont désormais exportés à partir du lot `org.apache.jackrabbit.oak-jackrabbit-api` . | Aucune modification n’est requise. | 6,5 LTS GA |
| Open Source | `com.github.jknack.handlebars` n’est pas pris en charge | Choisir la [version](https://mvnrepository.com/artifact/com.github.jknack/handlebars) appropriée | 6,5 LTS GA |

## Sites web restreints{#restricted-sites}

Ces sites Web sont disponibles uniquement pour les clients. Si vous êtes client et avez besoin d’un accès, contactez votre responsable de compte Adobe.

* [Téléchargement du produit à l’adresse licensing.adobe.com](https://licensing.adobe.com/)
* [Contacter l’assistance clientèle Adobe](https://experienceleague.adobe.com/fr/docs/customer-one/using/home).

