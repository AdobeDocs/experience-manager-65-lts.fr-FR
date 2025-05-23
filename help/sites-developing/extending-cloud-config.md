---
title: Configuration de Cloud Services
description: Vous pouvez étendre les instances existantes pour créer vos propres configurations.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: extending-aem
content-type: reference
solution: Experience Manager, Experience Manager Sites
feature: Developing
role: Developer
exl-id: 6b9b8d8c-8cd5-4c21-9b75-acd74d00354a
source-git-commit: a869ffbc6015fd230285838d260434d9c0ffbcb0
workflow-type: tm+mt
source-wordcount: '552'
ht-degree: 99%

---

# Configuration de Cloud Services{#cloud-service-configurations}

Les configurations sont conçues pour fournir la logique et la structure de stockage des configurations de service.

Vous pouvez étendre les instances existantes pour créer vos propres configurations.

## Concepts {#concepts}

Les principes utilisés dans le développement des configurations ont été basés sur les concepts suivants :

* Les services/adaptateurs sont utilisés pour récupérer les configurations.
* Les configurations (par exemple, les propriétés/paragraphes) sont héritées des parents.
* Référencement à partir des nœuds d’analyse par chemin d’accès.
* Facilement extensibles.
* Permet de répondre à des configurations plus complexes, telles [Adobe Analytics](/help/sites-administering/marketing-cloud.md#integrating-with-adobe-analytics).
* Prise en charge des dépendances (par exemple, les plug-ins [Adobe Analytics](/help/sites-administering/marketing-cloud.md#integrating-with-adobe-analytics) nécessitent une configuration [Adobe Analytics](/help/sites-administering/marketing-cloud.md#integrating-with-adobe-analytics)).

## Structure {#structure}

Le chemin de base de la configuration est le suivant :

`/etc/cloudservices`.

Pour chaque type de configuration, un modèle et un composant sont fournis. Cela permet de disposer de modèles de configuration qui peuvent répondre à la plupart des besoins après avoir été personnalisés.

Pour fournir une configuration pour les nouveaux services, procédez comme suit :

* Créez une page de service dans

  `/etc/cloudservices`

* Sous :

   * Modèle de configuration
   * Composant de configuration

Le modèle et le composant doivent hériter du `sling:resourceSuperType` du modèle de base :

`cq/cloudserviceconfigs/templates/configpage`

Ou composant de base, respectivement

`cq/cloudserviceconfigs/components/configpage`

Le fournisseur de services doit également fournir la page de service :

`/etc/cloudservices/<service-name>`

### Modèle {#template}

Votre modèle étend le modèle de base :

`cq/cloudserviceconfigs/templates/configpage`

Et définissez un `resourceType` qui pointe vers le composant personnalisé.

```xml
/libs/cq/analytics/templates/sitecatalyst
sling:resourceSuperType = cq/cloudserviceconfigs/templates/configpage
allowedChildren = /libs/cq/analytics/templates/sitecatalyst
allowedPaths = /etc/cloudservices/analytics/*, /etc/cloudservices/analytics/.*
componentReference = cq/analytics/components/sitecatalyst
jcr:content/
cq:designPath = /etc/designs/cloudservices
sling:resourceType = cq/analytics/components/sitecatalystpage

/libs/cq/analytics/templates/generictracker
sling:resourceSuperType = cq/cloudservices/templates/configpage
allowedChildren = /libs/cq/analytics/templates/generictracker
allowedPaths = /etc/cloudservices/analytics/*, /etc/cloudservices/analytics/.*
jcr:content/
cq:designPath = /etc/designs/cloudservices
sling:resourceType = cq/analytics/components/generictrackerpage
```

### Composants {#components}

Votre composant doit étendre le composant de base :

`cq/cloudserviceconfigs/templates/configpage`

```xml
/libs/cq/analytics/components/sitecatalystpage

/libs/cq/analytics/components/generictrackerpage
```

Après avoir configuré votre modèle et votre composant, vous pouvez ajouter votre configuration en ajoutant des sous-pages sous :

`/etc/cloudservices/<service-name>`

### Modèle de contenu {#content-model}

Le modèle de contenu est stocké sous la forme `cq:Page` sous :

`/etc/cloudservices/<service-name>(/*)`

```xml
/etc/cloudservices
/etc/cloudservices/service-name
/etc/cloudservices/service-name/config
/etc/cloudservices/service-name/config/inherited-config
```

Les configurations sont stockées sous le sous-nœud `jcr:content`.

* Les propriétés fixes, définies dans une boîte de dialogue, doivent être stockées directement sur le `jcr:node`.
* Les éléments dynamiques (utilisant `parsys` ou `iparsys`) se servent d’un sous-nœud pour stocker les données du composant.

```xml
/etc/cloudservices/service/config/jcr:content as nt:unstructured
propertyname
*
par/component/ as cq:Component
propertyname
*
```

### API {#api}

Pour consulter la documentation de référence sur l’API, voir [com.day.cq.wcm.webservicesupport](https://developer.adobe.com/experience-manager/reference-materials/6-5-lts/javadoc/com/day/cq/wcm/webservicesupport/package-summary.html).

### Intégration d’AEM {#aem-integration}

Les services disponibles sont répertoriés dans l’onglet **Services cloud** de la boîte de dialogue **Propriétés de la page** (de toute page héritant de `foundation/components/page` ou `wcm/mobile/components/page`).

Cet onglet contient également les informations suivantes :

* Lien vers l’emplacement où vous pouvez activer le service.
* Choisissez une configuration (sous-nœud du service) à partir d’un champ de chemin d’accès.

#### Chiffrement de mot de passe {#password-encryption}

Lors du stockage des informations d’identification d’utilisateur ou d’utilisatrice pour le service, tous les mots de passe doivent être chiffrés.

Pour cela, il faut ajouter un champ de formulaire masqué. L’annotation `@Encrypted` doit être présente dans le nom de propriété de ce champ, par exemple, pour le champ `password`, le nom de la propriété serait écrit comme suit :

`password@Encrypted`

La propriété est alors automatiquement chiffrée (en utilisant le service `CryptoSupport`) par `EncryptionPostProcessor`.

>[!NOTE]
>
>Ceci est similaire aux annotations ` [SlingPostServlet](https://sling.apache.org/site/manipulating-content-the-slingpostservlet-servletspost.html)` standard.

>[!NOTE]
>
>Par défaut, `EcryptionPostProcessor` chiffre uniquement les requêtes `POST` effectuées sur `/etc/cloudservices`.

#### Propriétés supplémentaires pour les nœuds jcr:content de page de service {#additional-properties-for-service-page-jcr-content-nodes}

<table>
 <tbody>
  <tr>
   <td><strong>Propriété</strong></td>
   <td><strong>Description</strong></td>
  </tr>
  <tr>
   <td>componentReference</td>
   <td>Chemin d’accès de référence à un composant à inclure automatiquement dans la page.<br /> Ceci est utilisé pour des fonctionnalités supplémentaires et des inclusions JS.<br /> Cela inclut le composant sur la page où<br /> <code> cq/cloudserviceconfigs/components/servicecomponents</code><br /> est inclus (normalement avant la variable <code>body</code>).<br /> Dans le cas d’Adobe Analytics et d’Adobe Target, nous utilisons ceci pour insérer des fonctionnalités supplémentaires, telles que des appels JavaScript, afin de suivre le comportement des visiteurs et visiteuses.</td>
  </tr>
  <tr>
   <td>description</td>
   <td>Brève description du service.<br /> </td>
  </tr>
  <tr>
   <td>descriptionExtended</td>
   <td>Description étendue du service.</td>
  </tr>
  <tr>
   <td>ranking</td>
   <td>Classement des services à utiliser dans les listes.</td>
  </tr>
  <tr>
   <td>selectableChildren</td>
   <td>Filtre permettant d’afficher les configurations dans la boîte de dialogue des propriétés de la page.</td>
  </tr>
  <tr>
   <td>serviceUrl</td>
   <td>URL du site Web du service.</td>
  </tr>
  <tr>
   <td>serviceUrlLabel</td>
   <td>Libellé de l’URL du service.</td>
  </tr>
  <tr>
   <td>thumbnailPath</td>
   <td>Chemin d’accès à la miniature du service.</td>
  </tr>
  <tr>
   <td>visible</td>
   <td>Visibilité dans la boîte de dialogue des propriétés de page ; visible par défaut (facultatif)</td>
  </tr>
 </tbody>
</table>

### Cas d’utilisation {#use-cases}

Ces services sont fournis par défaut :

* [Fragments de code de suivi](/help/sites-administering/external-providers.md) (Google, WebTrends, etc.)
* [Adobe Analytics](/help/sites-administering/marketing-cloud.md#integrating-with-adobe-analytics)
* [Test&amp;Target](/help/sites-administering/marketing-cloud.md#integrating-with-adobe-target)
<!-- Search&Promote is end of life as of September 1, 2022 * [Search&Promote](/help/sites-administering/marketing-cloud.md#integrating-with-search-promote) -->
* [Dynamic Media](/help/sites-administering/marketing-cloud.md#integrating-with-scene)

>[!NOTE]
>
>Consultez également [Création d’un service cloud personnalisé](/help/sites-developing/extending-cloud-config-custom-cloud.md).
