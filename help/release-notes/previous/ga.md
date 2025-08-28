---
title: 'Notes de mise à jour pour la version 6.5 du LTS d’ [!DNL Adobe Experience Manager] '
description: Recherchez les informations de mise à jour actuelles pour Adobe Experience Manager 6.5 LTS.
solution: Experience Manager
feature: Release Information
role: User,Admin,Architect,Developer
source-git-commit: 922b2391b45ac1a08987f286cdbd736fe9a383c8
workflow-type: tm+mt
source-wordcount: '1068'
ht-degree: 93%

---

# Notes de mise à jour actuelles pour Adobe Experience Manager 6.5 LTS {#release-notes}

## Informations sur la version {#release-information}

| Produit | [!DNL Adobe Experience Manager] |
|---|---|
| Version | 6.5 LTS |
| Type | Version majeure |
| Disponibilité générale | 7 mars 2025 |

## Nouveautés {#what-s-new}

[!DNL Adobe Experience Manager] 6.5 LTS est une mise à niveau de la base de code d’[!DNL Adobe Experience Manager] 6.5. Cette version comporte des correctifs clés de bugs signalés par des clients ou des clientes, des améliorations prioritaires demandées par les clients et les clientes et des correctifs de bugs généraux destinés à améliorer la stabilité du produit. Elle comprend également les mises à jour des packs de services d’[!DNL Adobe Experience Manager] 6.5 jusqu’au SP22.

Vous en trouverez un aperçu dans la liste ci-dessous, puis des détails complets dans les pages suivantes.

### [!DNL Experience Manager Foundation] {#experience-manager-foundation}

La plateforme d’[!DNL Adobe Experience Manager] 6.5 LTS repose sur les versions mises à jour de l’architecture OSGi (Apache Sling et Apache Felix), ainsi que sur le référentiel de contenu Java™ : Apache Jackrabbit Oak 1.68.x.

Eclipse Jetty 11.0.x est utilisé comme moteur de servlet pour Quickstart.

#### Prise en charge de Java™  {#java-support}

* Prise en charge de Java™ 17 et Java™ 21.
* Pour des performances optimales, remplacez les valeurs par défaut du GC par d’autres valeurs. Pour plus d’informations, consultez la section [Installation et mise à jour](/help/sites-deploying/custom-standalone-install.md).
* Adobe distribue des mises à jour de maintenance Java™ 17 et Java™ 21 pour l’utilisation par les clientes et les clients dans les projets liés à AEM, lorsqu’elles ne sont pas disponibles publiquement depuis Oracle.

#### Conditionnement Uberjar {#uber-jar-packaging}

* Il existe une légère différence dans le packaging Uberjar d’AEM 6.5 LTS. Pour plus d’informations, consultez [Mettre à jour la version AEM Uber Jar](/help/sites-deploying/upgrading-code-and-customizations.md#update-the-aem-uber-jar-version).

#### Mise à niveau {#upgrade}

* Pour plus d’informations sur la procédure de mise à niveau, consultez la [documentation de mise à niveau](/help/sites-deploying/upgrade.md).

## Installation et mise à jour {#install-update}

Pour connaître les exigences de configuration, consultez les [instructions d’installation](/help/sites-deploying/custom-standalone-install.md).

Pour obtenir des instructions détaillées, consultez la [documentation de mise à niveau](/help/sites-deploying/upgrade.md).

>[!NOTE]
>
> Pour les nouvelles installations d’AEM 6.5 LTS, les définitions d’index doivent être installées séparément. Pour plus d’informations, consultez [cet article](/help/sites-deploying/pre-upgrade-maintenance-tasks.md#index-definitions).

## Plateformes prises en charge {#supported-platforms}

Recherchez la matrice complète des plateformes prises en charge, y compris le niveau de prise en charge dans les [Exigences techniques AEM 6.5 LTS](/help/sites-deploying/technical-requirements.md).

>[!NOTE]
>
>Les versions 17 et 21 de Java™ sont recommandées pour une utilisation avec AEM 6.5 LTS.

## Fonctionnalités obsolètes et supprimées {#deprecated-and-removed-features}

Adobe examine continuellement les fonctionnalités du produit afin d’améliorer la valeur client en modernisant ou en remplaçant les anciennes fonctionnalités. Ces modifications sont effectuées avec une attention particulière portée à la rétrocompatibilité.

Pour communiquer la suppression ou le remplacement imminent(e) de fonctionnalités d’Adobe Experience Manager (AEM), les règles suivantes s’appliquent :

1. L’annonce de la suppression arrive en premier. Bien qu’elles soient obsolètes, les fonctionnalités sont toujours disponibles, mais ne sont pas améliorées.
1. La suppression des fonctionnalités obsolètes se produit au plus tôt dans la version majeure suivante. La date cible réelle de suppression est prévue pour une annonce ultérieure.

Ce processus donne aux clients au moins un cycle de version pour adapter leur implémentation à une nouvelle version ou à un produit de remplacement pour une fonctionnalité obsolète, avant que la suppression ne soit effective.

### Fonctionnalités obsolètes {#deprecated-features}

Cette section répertorie les fonctionnalités qu’Adobe a abandonnées dans AEM 6.5 LTS. En règle générale, Adobe rend les fonctionnalités obsolètes avant de les supprimer dans une version ultérieure et fournit une alternative.


Il est conseillé aux clients de réfléchir à leur utilisation de la fonctionnalité dans leur déploiement actuel et de prévoir la modification de leur mise en œuvre de façon à utiliser l’alternative proposée.

| Domaine | Fonctionnalité | Remplacement | Version (SP) |
|---|---|---|---|
| Sites | [Éditeur SPA](/help/sites-developing/spa-overview.md) | Les éditeurs recommandés pour la gestion du contenu découplé dans AEM sont les suivants : <br>- [Éditeur universel](/help/sites-developing/universal-editor/introduction.md) pour la modification visuelle.<br>- [Éditeur de fragment de contenu](/help/assets/content-fragments/content-fragments-managing.md) pour la modification basée sur les formulaires. | 6.5 LTS GA |

### Fonctionnalités supprimées {#removed-features}

Cette section répertorie les fonctionnalités qui ont été supprimées dans AEM 6.5 LTS. Ces fonctionnalités étaient signalées comme obsolètes dans les versions antérieures.

| Domaine | Fonctionnalité | Remplacement | Version (SP) |
|--- |--- |--- |--- |
| Commerce | AEM CIF Classic n’est pas pris en charge. | Migrez vers [AEM CIF](/help/commerce/cif/migration.md). | 6.5 LTS GA |
| Solutions | Social/Communities n’est pas pris en charge. | Aucun remplacement n’est disponible. | 6.5 LTS GA |
| Screens | Screens n’est pas pris en charge. | Aucun remplacement n’est disponible. | 6.5 LTS GA |
| Assets | `dam-pim` et `dam-rating` ne sont pas pris en charge, car les lots dépendent de Social. | Aucun remplacement n’est disponible. | 6.5 LTS GA |
| Assets | `com.day.cq.dam.scene7.api.model.Scene7ViewerConfig#getSettings()` a été supprimé. | Utilisez l’autre API `com.day.cq.dam.scene7.api.model.Scene7ViewerConfig#getSettingsList()` qui a été ajoutée. | 6.5 LTS GA |
| Portail | AEM Portal Director n’est pas pris en charge. | Aucun remplacement n’est disponible. | 6.5 LTS GA |
| Granite | Le lot `com.adobe.granite.socketio` est supprimé. | Aucun remplacement n’est disponible. | 6.5 LTS GA |
| Granite | `com.adobe.granite.crx-explorer` n’est pas pris en charge. | Aucun remplacement n’est disponible. | 6.5 LTS GA |
| Granite | `crx2oak` n’est pas pris en charge. | Sélectionnez la version appropriée de [Oak-upgrade](https://mvnrepository.com/artifact/org.apache.jackrabbit/oak-upgrade) | 6.5 LTS GA |
| Adobe | `com.adobe.cq.cq-searchpromote-integration` n’est pas pris en charge. | Aucun remplacement n’est disponible. | 6.5 LTS GA |
| Guava | Toutes les dépendances guava sont désormais supprimées dans AEM. Par conséquent, le lot `com.adobe.granite.osgi.wrapper.guava-15.0.0-0002` ne fait pas partie d’AEM. | La clientèle peut ajouter Guava elle-même si elle en dépend ou remplacer le code Guava par des collections Java ou d’autres alternatives si possible. | 6.5 LTS GA |
| `We.Retail` | `We-retail` site d’exemple n’est pas pris en charge. | Aucun remplacement n’est disponible. | 6.5 LTS GA |
| Open Source | Le lot `oak-solr-osgi` n’est pas pris en charge. | Aucun remplacement n’est disponible. | 6.5 LTS GA |
| Open Source | `org.apache.servicemix.bundles.abdera-parser`, `org.apache.servicemix.bundles.jdom` et `org.apache.sling.atom.taglib` ne sont pas pris en charge. | Aucun remplacement n’est disponible. | 6.5 LTS GA |
| Open Source | Les packages `org.apache.commons.io` sont désormais exportés depuis `org.apache.commons.commons-io`. | Aucune modification n’est requise. | 6.5 LTS GA |
| Open Source | Les packages `javax.mail` sont exportés à partir du lot `com.sun.javax.mail`. | Aucune modification n’est requise. | 6.5 LTS GA |
| Open Source | Les packages `org.apache.jackrabbit.api` sont désormais exportés à partir du lot `org.apache.jackrabbit.oak-jackrabbit-api` . | Aucune modification n’est requise. | 6.5 LTS GA |
| Open Source | `com.github.jknack.handlebars` n’est pas pris en charge. | Sélectionnez la [version](https://mvnrepository.com/artifact/com.github.jknack/handlebars) appropriée. | 6.5 LTS GA |

## Problèmes connus {#known-issues}

### Problème avec le lot de scripts JSP dans AEM 6.5.21-6.5.23 et AEM 6.5 LTS GA

AEM 6.5.21, 6.5.22, 6.5.23 et AEM 6.5 LTS GA sont fournis avec le lot `org.apache.sling.scripting.jsp:2.6.0`, qui contient un problème connu. Le problème se produit généralement sous une charge élevée lorsque l’instance AEM gère de nombreuses requêtes simultanées.

Lorsque ce problème se produit, l’une des exceptions suivantes peut apparaître dans les journaux d’erreurs avec des références à `org.apache.sling.scripting.jsp:2.6.0` :

* `java.io.IOException: classFile.delete() failed`
* `java.io.IOException: tmpFile.renameTo(classFile) failed`
* `java.lang.ArrayIndexOutOfBoundsException: Index 0 out of bounds for length 0`
* `java.io.FileNotFoundException`

Un correctif [cq-6.5.lts.0-hotfix-NPR-42640](https://experience.adobe.com/#/downloads/content/software-distribution/fr/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq660/hotfixes/cq-6.5.lts.0-hotfix-NPR-42640-1.2.zip) est disponible pour résoudre ce problème.

### Échec de la connexion à Dispatcher avec la fonction SSL uniquement {#ssl-only-feature}

Lors de l’activation de la fonction SSL uniquement dans les déploiements AEM, un problème connu affecte la connectivité entre les instances Dispatcher et AEM. Une fois cette fonctionnalité activée, les contrôles d’intégrité peuvent échouer et la communication entre les instances Dispatcher et AEM peut être interrompue. Ce problème se produit spécifiquement lorsque les clients tentent de se connecter via `https + IP` à partir des instances Dispatcher vers AEM. Elle est liée à des problèmes de validation SNI (Server Name Indication).

**Impact :**

* Échec des contrôles d’intégrité avec les codes de réponse HTTP 400
* Trafic rompu entre les instances Dispatcher et AEM
* Contenu diffusé incorrectement via Dispatcher
* Échecs de connexion lors de l’utilisation de HTTPS avec des adresses IP dans la configuration Dispatcher
* Erreurs HTTP 400 « SNI non valide » lors de la connexion via HTTPS + IP

**Environnements affectés :**

* Déploiements d’AEM avec les configurations Dispatcher
* Systèmes sur lesquels la fonction SSL uniquement a été activée
* Configurations Dispatcher utilisant la méthode de connexion `https + IP` aux instances AEM

**Solution :**
Si vous rencontrez ce problème, contactez l’Assistance Client d’Adobe. Un correctif [cq-6.5.lts.0-hotfix-CQ-4359803](https://experience.adobe.com/#/downloads/content/software-distribution/fr/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq660/hotfixes/cq-6.5.lts.0-hotfix-CQ-4359803-1.0.2.zip) est disponible pour résoudre ce problème. N’essayez pas d’activer les fonctions SSL uniquement avant d’avoir appliqué le correctif nécessaire.

## Sites web à accès limité{#restricted-sites}

Ces sites Web sont disponibles uniquement pour les clients. Si vous êtes client et avez besoin d’un accès, contactez votre responsable de compte Adobe.

* [Téléchargement du produit à l’adresse licensing.adobe.com](https://licensing.adobe.com/)
* [Contacter l’assistance clientèle Adobe](https://experienceleague.adobe.com/fr/docs/customer-one/using/home).
