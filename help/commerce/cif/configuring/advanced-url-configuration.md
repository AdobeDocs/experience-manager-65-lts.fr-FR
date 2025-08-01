---
title: Configurations d’URL avancées
description: Découvrez comment personnaliser les URL des pages de produits et de catégories. Cela permet aux implémentations d’optimiser les URL pour les moteurs de recherche et de promouvoir la découverte.
sub-product: Commerce
doc-type: technical-video
activity: setup
audience: administrator
feature: Commerce Integration Framework
kt: 4933
thumbnail: 34350.jpg
solution: Experience Manager,Commerce
role: Admin, Developer
exl-id: 5f6171f8-20ca-4c31-a99f-a5bc07a63baf
source-git-commit: e4cf6ae3392cef2ffd7e8fff3226b50c95f5a248
workflow-type: tm+mt
source-wordcount: '803'
ht-degree: 99%

---

# Configurations d’URL avancées {#url}

>[!NOTE]
>
>L’optimisation pour les moteurs de recherche est devenue une préoccupation essentielle pour de nombreux spécialistes du marketing. En conséquence, les questions d’optimisation du moteur de recherche doivent être traitées pour de nombreux projets AEM. Consultez les [Bonnes pratiques de gestion des URL et d’optimisation du moteur de recherche](/help/managing/seo-and-url-management.md) pour plus d’informations.

Les [composants principaux AEM CIF](https://github.com/adobe/aem-core-cif-components) offrent des configurations avancées pour personnaliser les URL des pages de produits et de catégories. De nombreuses mises en œuvre personnalisent ces URL à des fins d’optimisation pour les moteurs de recherche (SEO). La vidéo suivante explique comment configurer le `UrlProvider` service et les fonctionnalités du [mappage Sling](https://sling.apache.org/documentation/the-sling-engine/mappings-for-resource-resolution.html) pour personnaliser les URL des pages de produits et de catégories.

>[!VIDEO](https://video.tv.adobe.com/v/38579/?quality=12&captions=fre_fr)

## Configuration {#configuration}

Pour configurer le service `UrlProvider` en fonction des exigences et des besoins de SEO, un projet doit fournir une configuration OSGI pour la « configuration du fournisseur d’URL CIF ».

>[!NOTE]
>
>Depuis la version 2.0.0 des composants principaux CIF d’AEM, la configuration du fournisseur d’URL fournit uniquement des formats d’URL prédéfinis, au lieu des formats configurables en texte libre connus des versions 1.x. De plus, l’utilisation de sélecteurs pour transmettre des données dans des URL a été remplacée par des suffixes.

### Format d’URL de page de produits {#product}

Celui-ci configure les URL des pages de produits et prend en charge les options suivantes :

* `{{page}}.html/{{sku}}.html#{{variant_sku}}` (par défaut)
* `{{page}}.html/{{url_key}}.html#{{variant_sku}}`
* `{{page}}.html/{{sku}}/{{url_key}}.html#{{variant_sku}}`
* `{{page}}.html/{{url_path}}.html#{{variant_sku}}`
* `{{page}}.html/{{sku}}/{{url_path}}.html#{{variant_sku}}`

Si le [magasin de référence Venia](https://github.com/adobe/aem-cif-guides-venia) est disponible :

* `{{page}}` est remplacé par `/content/venia/us/en/products/product-page` ;
* `{{sku}}` est remplacé par le SKU du produit, par exemple `VP09`
* `{{url_key}}` est remplacé par la propriété `url_key` du produit, par exemple `lenora-crochet-shorts`
* `{{url_path}}` est remplacé par le `url_path` du produit, par exemple `venia-bottoms/venia-pants/lenora-crochet-shorts`
* `{{variant_sku}}` est remplacé par la variante actuellement sélectionnée, par exemple `VP09-KH-S`

Depuis que `url_path` a été abandonné, les formats d’URL de produit prédéfinis utilisent les `url_rewrites` d’un produit et choisissent celui qui contient le plus de segments de chemin comme alternative si `url_path` n’est pas disponible.

Avec les données d’exemple ci-dessus, une URL de variante de produit formatée à l’aide du format d’URL par défaut ressemblera à `/content/venia/us/en/products/product-page.html/VP09.html#VP09-KH-S`.

### Format d’URL de page de catégorie {#product-list}

Celui-ci configure les URL des pages de listes de catégories ou de produits et prend en charge les options suivantes :

* `{{page}}.html/{{url_path}}.html` (par défaut)
* `{{page}}.html/{{url_key}}.html`

Si le [magasin de référence Venia](https://github.com/adobe/aem-cif-guides-venia) est disponible :

* `{{page}}` est remplacé par `/content/venia/us/en/products/category-page` ;
* `{{url_key}}` est remplacé par la propriété `url_key` de la catégorie
* `{{url_path}}` est remplacé par le `url_path` de la catégorie.

Avec les données d’exemple ci-dessus, une URL de page de catégorie formatée à l’aide du format d’URL par défaut ressemble à `/content/venia/us/en/products/category-page.html/venia-bottoms/venia-pants.html`.

>[!NOTE]
> 
>`url_path` est une concaténation de `url_keys` des ancêtres d’un produit ou d’une catégorie et de `url_key` du produit ou de la catégorie séparés par une barre oblique `/`.

### Pages de catégorie/produit spécifiques {#specific-pages}

Il n’est possible de créer [plusieurs pages de catégories et de produits](multi-template-usage.md) que pour un sous-ensemble spécifique de catégories ou de produits d’un catalogue.

L’`UrlProvider` est préconfiguré pour générer des liens profonds vers ces pages sur les instances dʼauteur. Cette fonctionnalité est utile aux rédacteurs qui parcourent un site en mode Prévisualisation, se rendent sur une page produit ou de catégorie spécifique, puis repassent en mode Édition pour modifier la page.

Dans les instances de publication, en revanche, les adresses URL des pages de catalogue doivent rester stables pour ne pas perdre les gains de classement dans les moteurs de recherche, par exemple. Pour cette raison, les instances de publication ne généreront pas de liens profonds vers des pages de catalogue spécifiques par défaut. Pour modifier ce comportement, une _Stratégie de page spécifique du fournisseur d’URL CIF_ peut être configurée pour toujours générer des adresses URL de page spécifiques.

## Formats d’URL personnalisés {#custom-url-format}

Pour fournir un format dʼURL personnalisé, un projet peut implémenter soit lʼinterface de service [`ProductUrlFormat`](https://javadoc.io/doc/com.adobe.commerce.cif/core-cif-components-core/latest/com/adobe/cq/commerce/core/components/services/urls/ProductUrlFormat.html) soit l’interface de service [`CategoryUrlFormat`](https://javadoc.io/doc/com.adobe.commerce.cif/core-cif-components-core/latest/com/adobe/cq/commerce/core/components/services/urls/CategoryUrlFormat.html) et enregistrer lʼimplémentation en tant que service OSGI. Ces implémentations, si elles sont disponibles, remplaceront le format configuré et prédéfini. S’il existe plusieurs implémentations enregistrées, celle qui a le rang de service supérieur remplace celles qui ont le rang de service inférieur.

Les implémentations de format dʼURL personnalisé doivent implémenter une paire de méthodes pour créer une adresse URL à partir de paramètres donnés, et pour analyser une URL afin de renvoyer les mêmes paramètres, respectivement.

## Combinaison avec des mappages Sling {#sling-mapping}

En plus du `UrlProvider`, il est également possible de configurer des [mappages Sling](https://sling.apache.org/documentation/the-sling-engine/mappings-for-resource-resolution.html) afin de réécrire et de traiter les URL. Le projet AEM Archetype fournit également [un exemple de configuration](https://github.com/adobe/aem-cif-project-archetype/tree/master/src/main/archetype/samplecontent/src/main/content/jcr_root/etc/map.publish) afin de configurer des mappages Sling pour les ports 4503 (publication) et 80 (Dispatcher).

## Combinaison avec AEM Dispatcher {#dispatcher}

Les réécritures d’URL peuvent également être obtenues en utilisant le serveur HTTP AEM Dispatcher avec le module `mod_rewrite`. L’[archétype de projet AEM](https://github.com/adobe/aem-project-archetype) fournit une configuration de Dispatcher AEM de référence qui inclut déjà des [règles de réécriture](https://github.com/adobe/aem-project-archetype/tree/master/src/main/archetype/dispatcher.cloud) de base pour la taille générée.

## Exemple

Le projet de [magasin de référence Venia](https://github.com/adobe/aem-cif-guides-venia) comprend des exemples de configuration afin de démontrer l’utilisation d’URL personnalisées pour les pages de produits et de catégories. Cela permet à chaque projet de configurer des modèles d’URL individuels pour les pages de produits et de catégories en fonction de leurs besoins d’optimisation de moteur de recherche. Une combinaison de mappages `UrlProvider` et Sling CIF telle que décrite ci-dessus est utilisée.

>[!NOTE]
>
>Cette configuration doit être ajustée avec le domaine externe utilisé par le projet. Les mappages Sling fonctionnent en fonction du nom d’hôte et du domaine. Par conséquent, cette configuration est désactivée par défaut et doit être activée avant le déploiement. Pour ce faire, renommez le dossier `hostname.adobeaemcloud.com` de mappage Sling dans `ui.content/src/main/content/jcr_root/etc/map.publish/https` en fonction du nom de domaine utilisé et activez cette configuration en ajoutant `resource.resolver.map.location="/etc/map.publish"` à la configuration `JcrResourceResolver` du projet.

## Ressources supplémentaires

* [Magasin de référence Venia](https://github.com/adobe/aem-cif-guides-venia)
* [Mappage des ressources AEM](/help/sites-deploying/resource-mapping.md)
* [Mappages Sling](https://sling.apache.org/documentation/the-sling-engine/mappings-for-resource-resolution.html)
