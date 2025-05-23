---
title: Mettre à niveau les formulaires de recherche personnalisés
description: Cet article décrit les ajustements nécessaires après une mise à niveau pour que les formulaires de recherche personnalisés fonctionnent.
feature: Upgrading
solution: Experience Manager, Experience Manager Sites
role: Admin
hide: true
hidefromtoc: true
exl-id: 9df608f8-cdd0-4820-aab1-eab9fd70f961
source-git-commit: 547d7866346fb148cb66f546d8a2e1141f69f563
workflow-type: tm+mt
source-wordcount: '1797'
ht-degree: 100%

---

# Mettre à niveau les formulaires de recherche personnalisés{#upgrading-custom-search-forms}

Dans AEM 6.2, l’emplacement de stockage des formulaires de recherche personnalisés dans le référentiel n’est plus le même. Lors de la mise à niveau, ils sont déplacés de leur emplacement dans la version 6.1 vers :

* /apps/cq/gui/content/facets

vers un nouvel emplacement dans :

* /conf/global/settings/cq/search/facets

Des ajustements manuels sont donc nécessaires après une mise à niveau pour que les formulaires continuent à fonctionner.

Cela s’applique aux nouveaux formulaires de recherche et aux formulaires par défaut qui ont été personnalisés.

Pour plus d’informations, voir la documentation sur [Facettes de recherche](/help/assets/search-facets.md).

## Modification de la propriété resourceType {#changing-the-resourcetype-property}

Sauf indication contraire, la plupart des réglages qui doivent être effectués après la mise à niveau nécessitent de modifier la propriété `sling:resourceType` pour les formulaires de recherche personnalisée configurés. Cela est nécessaire afin que la propriété pointe vers le bon emplacement du script de rendu.

Vous pouvez changer la propriété en procédant comme suit :

1. Ouvrez CRXDE Lite en accédant à `https://server:port/crx/de/index.jsp`.
1. Accédez à l’emplacement du nœud qui doit être ajusté, comme indiqué dans la liste de [formulaires de recherche personnalisée](/help/sites-deploying/upgrading-custom-search-forms.md#list-of-custom-search-forms) ci-dessous.
1. Cliquez sur le nœud. Dans le volet des propriétés de droite, cliquez sur la propriété **sling:resourceType** et modifiez-la.
1. Enfin, enregistrez les modifications en appuyant sur le bouton **Enregistrer tout**.

## Liste des formulaires de recherche personnalisés {#list-of-custom-search-forms}

Vous trouverez ci-dessous la liste de tous les formulaires de recherche personnalisés et des modifications nécessaires après la mise à niveau. Ils font référence aux noms figurant dans la section `/conf/global/settings/cq/search/facets/sites/items`.

### Prédicat de texte intégral avec pour nom de nœud « fulltext » {#fulltext-predicate-with-node-name-fulltext}

<table>
 <tbody>
  <tr>
   <td>Nœud(s) dans le formulaire de recherche par défaut dans la version 6.1</td>
   <td>fulltext</td>
  </tr>
  <tr>
   <td><p>Type de ressource dans la version 6.1</p> </td>
   <td><p>cq/gui/components/common/admin/customsearch/searchpredicates/fulltextpredicate</p> </td>
  </tr>
  <tr>
   <td>Type de ressource dans la version 6.2</td>
   <td>n/a</td>
  </tr>
 </tbody>
</table>

Dans AEM 6.1, le prédicat de texte intégral standard faisait partie du formulaire de recherche. Dans la version 6.2, le champ de texte intégral a été remplacé par OmniSearch. Ce prédicat est ignoré par programmation et peut être supprimé.

**Action :** supprimez entièrement le nœud.

### Autres prédicats de texte intégral {#other-fulltext-predicates}

<table>
 <tbody>
  <tr>
   <td>Nœud(s) dans le formulaire de recherche par défaut dans la version 6.1</td>
   <td>n/a</td>
  </tr>
  <tr>
   <td><p>Type de ressource dans la version 6.1</p> </td>
   <td><p>cq/gui/components/common/admin/customsearch/searchpredicates/fulltextpredicate</p> </td>
  </tr>
  <tr>
   <td>Type de ressource dans la version 6.2</td>
   <td><p>cq/gui/components<strong>/coral/</strong>common/admin/customsearch/searchpredicates/fulltextpredicate</p> </td>
  </tr>
 </tbody>
</table>

**Action :** ajustez la propriété `resourceType` (ajoutez « **/coral** » comme dans l’emplacement 6.2 indiqué ci-dessus).

### Prédicats de navigateur de chemin d’accès {#path-browser-predicates}

<table>
 <tbody>
  <tr>
   <td>Nœud(s) dans le formulaire de recherche par défaut dans la version 6.1<br /> <br /> </td>
   <td>path</td>
  </tr>
  <tr>
   <td><p>Type de ressource dans la version 6.1</p> </td>
   <td><p>cq/gui/components/common/admin/customsearch/searchpredicates/pathpredicate</p> </td>
  </tr>
  <tr>
   <td>Type de ressource dans la version 6.2</td>
   <td><p>cq/gui/components<strong>/coral/</strong>common/admin/customsearch/searchpredicates/pathpredicate</p> </td>
  </tr>
 </tbody>
</table>

**Action :** ajustez la propriété `resourceType` (ajoutez « **/coral** » comme dans l’emplacement 6.2 indiqué ci-dessus).

### Prédicats de balises {#tags-predicates}

<table>
 <tbody>
  <tr>
   <td>Nœud(s) dans le formulaire de recherche par défaut dans la version 6.1<br /> <br /> </td>
   <td>balises</td>
  </tr>
  <tr>
   <td><p>Type de ressource dans la version 6.1</p> </td>
   <td><p>cq/gui/components/common/admin/customsearch/searchpredicates/tagspredicate</p> </td>
  </tr>
  <tr>
   <td>Type de ressource dans la version 6.2</td>
   <td><p>cq/gui/components<strong>/coral/</strong>common/admin/customsearch/searchpredicates/tagspredicate</p> </td>
  </tr>
 </tbody>
</table>

**Action :** ajustez la propriété **resourceType** (ajoutez « **/coral** » comme dans l’emplacement 6.2 indiqué ci-dessus).

### Prédicat de statut de page {#page-status-predicate}

<table>
 <tbody>
  <tr>
   <td>Nœud(s) dans le formulaire de recherche par défaut dans la version 6.1<br /> <br /> </td>
   <td>pagestatuspredicate</td>
  </tr>
  <tr>
   <td><p>Type de ressource dans la version 6.1</p> </td>
   <td><p>cq/gui/components/siteadmin/admin/searchpanel/searchpredicates/pagestatuspredicate</p> </td>
  </tr>
  <tr>
   <td>Type de ressource dans la version 6.2</td>
   <td>n/a</td>
  </tr>
 </tbody>
</table>

Le statut de page a été remplacé par deux prédicats de propriétés d’options, l’un pour la publication et l’autre pour le statut de LiveCopy.

**Actions :**

* Supprimez le nœud `pagestatuspredicate`.
* Copiez le nœud

   * `/libs/settings/cq/search/facets/sites/jcr:content/items/publishstatuspredicate`
   * vers `/conf/global/settings/cq/search/facets/sites/jcr:content/items`.

* Copier le nœud

   * `/libs/settings/cq/search/facets/sites/jcr:content/items/livecopystatuspredicate`
   * vers `/conf/global/settings/cq/search/facets/sites/jcr:content/items`.

* Assurez-vous de définir la propriété `listOrder` pour le nœud `analyticspredicate` sur « **8** ». Cela est nécessaire pour éviter les conflits.

### Prédicat de période {#date-range-predicates}

<table>
 <tbody>
  <tr>
   <td>Nœud(s) dans le formulaire de recherche par défaut dans la version 6.1<br /> <br /> </td>
   <td>daterangepredicate</td>
  </tr>
  <tr>
   <td>Type de ressource dans la version 6.1</td>
   <td>cq/gui/components/common/admin/customsearch/searchpredicates/daterangepredicate</td>
  </tr>
  <tr>
   <td>Type de ressource dans la version 6.2</td>
   <td><p>cq/gui/components<strong>/coral/</strong>common/admin/customsearch/searchpredicates/daterangepredicate</p> </td>
  </tr>
 </tbody>
</table>

**Action :** ajustez la propriété `resourceType` (ajoutez « **/coral** » comme dans l’emplacement 6.2 indiqué ci-dessus).

### Filtre masqué {#hidden-filter}

<table>
 <tbody>
  <tr>
   <td>Nœud(s) dans le formulaire de recherche par défaut dans la version 6.1<br /> <br /> </td>
   <td>type</td>
  </tr>
  <tr>
   <td><p>Type de ressource dans la version 6.1</p> </td>
   <td><p>granite/ui/components/foundation/form/hidden</p> </td>
  </tr>
  <tr>
   <td>Type de ressource dans la version 6.2</td>
   <td><p>granite/ui/components/foundation/form/hidden</p> </td>
  </tr>
 </tbody>
</table>

**Action :** rien à ajuster.

### Prédicat d’analyse {#analytics-predicate}

<table>
 <tbody>
  <tr>
   <td>Nœud(s) dans le formulaire de recherche par défaut dans la version 6.1<br /> <br /> </td>
   <td>analyticspredicate</td>
  </tr>
  <tr>
   <td><p>Type de ressource dans la version 6.1</p> </td>
   <td><p>cq/gui/components/siteadmin/admin/searchpanel/searchpredicates/analyticspredicate</p> </td>
  </tr>
  <tr>
   <td>Type de ressource dans la version 6.2</td>
   <td><p>cq/gui/components<strong>/coral/</strong>siteadmin/admin/searchpanel/searchpredicates/analyticspredicate</p> </td>
  </tr>
 </tbody>
</table>

**Action :** ajustez la propriété `resourceType` (ajoutez « **/coral** » comme dans l’emplacement 6.2 indiqué ci-dessus).

### Prédicat de plage {#range-predicate}

<table>
 <tbody>
  <tr>
   <td>Nœud(s) dans le formulaire de recherche par défaut dans la version 6.1<br /> <br /> </td>
   <td>n/a</td>
  </tr>
  <tr>
   <td><p>Type de ressource dans la version 6.1</p> </td>
   <td><p>cq/gui/components/siteadmin/admin/searchpanel/searchpredicates/rangepredicate</p> </td>
  </tr>
  <tr>
   <td>Type de ressource dans la version 6.2</td>
   <td><p>cq/gui/components<strong>/coral/</strong>siteadmin/admin/searchpanel/searchpredicates/rangepredicate</p> </td>
  </tr>
 </tbody>
</table>

**Action :** ajustez la propriété `resourceType` (ajoutez « **/coral** » comme dans l’emplacement 6.2 indiqué ci-dessus).

>[!NOTE]
>
>Remarque : contrairement à la version 6.1, le prédicat de plage n’affiche plus de balise dans la barre de recherche.

### Prédicat de propriété d’options {#options-property-predicate}

<table>
 <tbody>
  <tr>
   <td>Nœud(s) dans le formulaire de recherche par défaut dans la version 6.1<br /> <br /> </td>
   <td>n/a</td>
  </tr>
  <tr>
   <td><p>Type de ressource dans la version 6.1</p> </td>
   <td><p>cq/gui/components/siteadmin/admin/searchpanel/searchpredicates/optionspredicate</p> </td>
  </tr>
  <tr>
   <td>Type de ressource dans la version 6.2</td>
   <td><p>cq/gui/components<strong>/coral/</strong>siteadmin/admin/searchpanel/searchpredicates/optionspredicate</p> </td>
  </tr>
 </tbody>
</table>

**Action :** ajustez la propriété `resourceType` (ajoutez « **/coral** » comme dans l’emplacement 6.2 indiqué ci-dessus).

### Prédicat de plage de curseurs {#slider-range-predicate}

<table>
 <tbody>
  <tr>
   <td>Nœud(s) dans le formulaire de recherche par défaut dans la version 6.1<br /> <br /> </td>
   <td>n/a</td>
  </tr>
  <tr>
   <td><p>Type de ressource dans la version 6.1</p> </td>
   <td><p>cq/gui/components/siteadmin/admin/searchpanel/searchpredicates/sliderrangepredicate</p> </td>
  </tr>
  <tr>
   <td>Type de ressource dans la version 6.2</td>
   <td><p>cq/gui/components<strong>/coral/</strong>siteadmin/admin/searchpanel/searchpredicates/sliderrangepredicate</p> </td>
  </tr>
 </tbody>
</table>

**Action :** ajustez la propriété `resourceType` (ajoutez « **/coral** » comme dans l’emplacement 6.2 indiqué ci-dessus).

### Prédicat de composants {#components-predicate}

<table>
 <tbody>
  <tr>
   <td>Nœud(s) dans le formulaire de recherche par défaut dans la version 6.1<br /> <br /> </td>
   <td>n/a</td>
  </tr>
  <tr>
   <td><p>Type de ressource dans la version 6.1</p> </td>
   <td><p>cq/gui/components/siteadmin/admin/searchpanel/searchpredicates/componentspredicate</p> </td>
  </tr>
  <tr>
   <td>Type de ressource dans la version 6.2</td>
   <td><p>cq/gui/components<strong>/coral/</strong>siteadmin/admin/searchpanel/searchpredicates/componentspredicate</p> </td>
  </tr>
 </tbody>
</table>

**Action :** ajustez la propriété `resourceType` (ajoutez « **/coral** » comme dans l’emplacement 6.2 indiqué ci-dessus).

### Prédicat d’auteur {#author-predicate}

<table>
 <tbody>
  <tr>
   <td>Nœud(s) dans le formulaire de recherche par défaut dans la version 6.1<br /> <br /> </td>
   <td>n/a</td>
  </tr>
  <tr>
   <td><p>Type de ressource dans la version 6.1</p> </td>
   <td><p>cq/gui/components/siteadmin/admin/searchpanel/searchpredicates/userpredicate</p> </td>
  </tr>
  <tr>
   <td>Type de ressource dans la version 6.2</td>
   <td><p>cq/gui/components<strong>/coral/</strong>siteadmin/admin/searchpanel/searchpredicates/userpredicate</p> </td>
  </tr>
 </tbody>
</table>

**Action :** ajustez la propriété `resourceType` (ajoutez « **/coral** » comme dans l’emplacement 6.2 indiqué ci-dessus).

### Prédicat de modèles {#templates-predicate}

<table>
 <tbody>
  <tr>
   <td>Nœud(s) dans le formulaire de recherche par défaut dans la version 6.1<br /> <br /> </td>
   <td>n/a</td>
  </tr>
  <tr>
   <td><p>Type de ressource dans la version 6.1</p> </td>
   <td><p>cq/gui/components/siteadmin/admin/searchpanel/searchpredicates/templatespredicate</p> </td>
  </tr>
  <tr>
   <td>Type de ressource dans la version 6.2</td>
   <td><p>cq/gui/components<strong>/coral/</strong>siteadmin/admin/searchpanel/searchpredicates/templatespredicate</p> </td>
  </tr>
 </tbody>
</table>

**Action :** ajustez la propriété `resourceType` (ajoutez « **/coral** » comme dans l’emplacement 6.2 indiqué ci-dessus).

## Rail de recherche d’administrateurs de ressources {#assets-admin-search-rail}

Les nœuds ci-dessous font référence aux noms dans `/conf/global/settings/dam/search/facets/assets/items`.

### Prédicat de texte intégral avec pour nom de nœud « fulltext » {#fulltext-predicate-with-node-name-fulltext-1}

| Nœud(s) dans le formulaire de recherche par défaut dans la version 6.1 | fulltext |
|---|---|
| Type de ressource dans la version 6.1 | dam/gui/components/admin/customsearch/searchpredicates/fulltextpredicate |
| Type de ressource dans la version 6.2 | n/a |

Dans la version 6.1, le prédicat de texte intégral standard faisait partie du formulaire de recherche. Dans la version 6.2, le champ de texte intégral a été remplacé par OmniSearch. Ce prédicat est ignoré par programmation et peut être supprimé.

**Action :** supprimez le nœud mentionné ci-dessus.

### Prédicats de navigateur de chemin d’accès {#path-browser-predicates-1}

| Nœud(s) dans le formulaire de recherche par défaut dans la version 6.1 | pathbrowser |
|---|---|
| Type de ressource dans la version 6.1 | dam/gui/components/admin/customsearch/searchpredicates/pathbrowserpredicate |
| Type de ressource dans la version 6.2 | dam/gui/coral/components/admin/customsearch/searchpredicates/pathbrowserpredicate |

**Action :** ajustez la propriété `resourceType` (ajoutez « **/coral** » comme dans l’emplacement 6.2 indiqué ci-dessus).

### Prédicats de type MIME {#mime-type-predicates}

| Nœud(s) dans le formulaire de recherche par défaut dans la version 6.1 | mimetype |
|---|---|
| Type de ressource dans la version 6.1 | dam/gui/components/admin/customsearch/searchpredicates/optionspredicate |
| Type de ressource dans la version 6.2 | dam/gui/coral/components/admin/customsearch/searchpredicates/optionspredicate |

**Action :** ajustez la propriété `resourceType` (ajoutez « **/coral** » comme dans l’emplacement 6.2 indiqué ci-dessus).

### Prédicats de taille de fichier {#file-size-predicates}

| Nœud(s) dans le formulaire de recherche par défaut dans la version 6.1 | filesize |
|---|---|
| Type de ressource dans la version 6.1 | dam/gui/components/admin/customsearch/searchpredicates/filesizepredicate |
| Type de ressource dans la version 6.2 | dam/gui/coral/components/admin/customsearch/searchpredicates/sliderangepredicate |

**Action :** ajustez `resourceType` tel qu’indiqué dans l’emplacement de la version 6.2 ci-dessus.

### Prédicats de dernière modification de la ressource {#asset-last-modified-predicates}

| Nœud(s) dans le formulaire de recherche par défaut dans la version 6.1 | assetlastmodifiedpredicate |
|---|---|
| Type de ressource dans la version 6.1 | dam/gui/components/admin/customsearch/searchpredicates/assetlastmodifiedpredicate |
| Type de ressource dans la version 6.2 | dam/gui/coral/components/admin/customsearch/searchpredicates/assetlastmodifiedpredicate |

Action : ajustez la propriété resourceType (ajoutez « /coral » comme dans l’emplacement 6.2 indiqué ci-dessus).

### Prédicat de publication {#publish-predicate}

| Nœud(s) dans le formulaire de recherche par défaut dans la version 6.1 | publish |
|---|---|
| Type de ressource dans la version 6.1 | dam/gui/components/admin/customsearch/searchpredicates/publishpredicate |
| Type de ressource dans la version 6.2 | dam/gui/coral/components/admin/customsearch/searchpredicates/publishpredicate |

**Actions :**

* Ajustez la propriété `resourceType` (ajoutez « **/coral** » comme dans l’emplacement 6.2 indiqué ci-dessus).

* Ajoutez une propriété `optionPaths` (de type chaîne) avec pour valeur : `/libs/dam/options/predicates/publish`

* Ajoutez une propriété `singleSelect` avec pour valeur booléenne `true`.

### Prédicats de statut {#status-predicates}

| Nœud(s) dans le formulaire de recherche par défaut dans la version 6.1 | status |
|---|---|
| Type de ressource dans la version 6.1 | dam/gui/components/admin/customsearch/searchpredicates/optionspredicate |
| Type de ressource dans la version 6.2 | dam/gui/coral/components/admin/customsearch/searchpredicates/optionspredicate |

**Action :** ajustez la propriété `resourceType` (ajoutez « **/coral** » comme dans l’emplacement 6.2 indiqué ci-dessus).

### Prédicats de statut d’expiration {#expiry-status-predicates}

| Nœud(s) dans le formulaire de recherche par défaut dans la version 6.1 | expirystatus |
|---|---|
| Type de ressource dans la version 6.1 | dam/gui/components/admin/customsearch/searchpredicates/expiredassetpredicate |
| Type de ressource dans la version 6.2 | dam/gui/coral/components/admin/customsearch/searchpredicates/expiredassetpredicate |

**Action :** ajustez la propriété `resourceType` (ajoutez « **/coral** » comme dans l’emplacement 6.2 indiqué ci-dessus).

### Prédicats de validité de métadonnées {#metadata-validity-predicates}

| Nœud(s) dans le formulaire de recherche par défaut dans la version 6.1 | metadatavalidity |
|---|---|
| Type de ressource dans la version 6.1 | dam/gui/components/admin/customsearch/searchpredicates/optionspredicate |
| Type de ressource dans la version 6.2 | dam/gui/coral/components/admin/customsearch/searchpredicates/optionspredicate |

**Action :** ajustez la propriété `resourceType` (ajoutez « **/coral** » comme dans l’emplacement 6.2 indiqué ci-dessus).

### Prédicats d’évaluation {#rating-predicates}

| Nœud(s) dans le formulaire de recherche par défaut dans la version 6.1 | rating |
|---|---|
| Type de ressource dans la version 6.1 | dam/gui/components/admin/customsearch/searchpredicates/ratingpredicate |
| Type de ressource dans la version 6.2 | dam/gui/coral/components/admin/customsearch/searchpredicates/sliderangepredicate |

**Action :** ajustez la propriété `resourceType` (ajoutez « **/coral** » comme dans l’emplacement 6.2 indiqué ci-dessus).

### Prédicat d’orientation {#orientation-predicate}

| Nœud(s) dans le formulaire de recherche par défaut dans la version 6.1 | orientation |
|---|---|
| Type de ressource dans la version 6.1 | dam/gui/components/admin/customsearch/searchpredicates/tagsfilterpredicate |
| Type de ressource dans la version 6.2 | cq/gui/components/coral/common/admin/customsearch/searchpredicates/tagspredicate |

**Actions :**

* Ajustez la propriété `resourceType` (ajoutez « **/coral** » comme dans l’emplacement 6.2 indiqué ci-dessus).

* Ajoutez une propriété `fieldLabel` avec la même valeur que la propriété `text` du même nœud.

* Ajoutez une propriété `emptyText` avec la même valeur que la propriété `text` du même nœud.

* Ajoutez une propriété `rootPath` avec la même valeur que la propriété `optionPaths` du même nœud.

### Prédicat de style {#style-predicate}

| Nœud(s) dans le formulaire de recherche par défaut dans la version 6.1 | style |
|---|---|
| Type de ressource dans la version 6.1 | dam/gui/components/admin/customsearch/searchpredicates/tagsfilterpredicate |
| Type de ressource dans la version 6.2 | cq/gui/components/coral/common/admin/customsearch/searchpredicates/tagspredicate |

**Actions :**

* Ajustez la propriété `resourceType` (ajoutez « **/coral** » comme dans l’emplacement 6.2 indiqué ci-dessus).

* Ajoutez une propriété `fieldLabel` avec la même valeur que la propriété `text` du même nœud.

* Ajoutez une propriété `emptyText` avec la même valeur que la propriété `text` du même nœud.

* Ajoutez une propriété `rootPath` avec la même valeur que la propriété `optionPaths` du même nœud.

### Prédicats de format vidéo {#video-format-predicates}

| Nœud(s) dans le formulaire de recherche par défaut dans la version 6.1 | videoFormat |
|---|---|
| Type de ressource dans la version 6.1 | dam/gui/components/admin/customsearch/searchpredicates/optionspredicate |
| Type de ressource dans la version 6.2 | dam/gui/coral/components/admin/customsearch/searchpredicates/optionspredicate |

**Action :** ajustez la propriété `resourceType` (ajoutez « **/coral** » comme dans l’emplacement 6.2 indiqué ci-dessus).

### Prédicat de ressource principale {#mainasset-predicate}

| Nœud(s) dans le formulaire de recherche par défaut dans la version 6.1 | mainasset |
|---|---|
| Type de ressource dans la version 6.1 | granite/ui/components/foundation/form/hidden |
| Type de ressource dans la version 6.2 | granite/ui/components/coral/foundation/form/hidden |

**Action :** ajustez la propriété `resourceType` (ajoutez « **/coral** » comme dans l’emplacement 6.2 indiqué ci-dessus).
