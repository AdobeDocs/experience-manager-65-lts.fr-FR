---
title: Migration vers le framework CIF (Commerce Integration Framework) AEM
description: Migrer vers le framework CIF (Commerce Integration Framework) d’AEM à partir d’une ancienne version.
solution: Experience Manager,Commerce
feature: Commerce Integration Framework
role: Admin, Developer
exl-id: 847c33c1-17d6-447a-9f2c-91f2a81a3f04
source-git-commit: fdb84a17b3af7eaa76e5a7c30d21d7a601463278
workflow-type: tm+mt
source-wordcount: '259'
ht-degree: 96%

---

# Guide de migration pour le module complémentaire Experience Manager {#cif-migration}

Ce guide permet d’identifier les zones à mettre à jour pour la migration du module complémentaire Experience Manager.

## Module complémentaire CIF

Le module complémentaire CIF est disponible via le [portail de distribution de logiciels](https://experience.adobe.com/#/downloads/content/software-distribution/fr/aem.html?fulltext=commerce*&2_group.propertyvalues.property=.%2Fjcr%3Acontent%2Fmetadata%2Fdc%3Aversion&2_group.propertyvalues.operation=equals&2_group.propertyvalues.0_values=target-version%3Aaem%2F6-5&orderby=%40jcr%3Acontent%2Fjcr%3AlastModified&orderby.sort=desc&layout=list&p.offset=0&p.limit=16). Il est compatible et fournit les mêmes fonctionnalités que le module complémentaire CIF pour Experience Manager as a Cloud Service.

Consultez la section [Prise en main d’AEM Content and Commerce](getting-started.md).

Pour prendre en charge les projets qui déploient CIF, Adobe fournit [les composants principaux CIF AEM](https://github.com/adobe/aem-core-cif-components).

## Catalogue de produits

L’importation de données de catalogue de produits n’est pas prise en charge par le module complémentaire CIF. L’utilisation du module complémentaire CIF permet aux requêtes produits et de catalogues de se faire sur demande par le biais d’appels en temps réel vers une solution de commerce externe. Accédez au chapitre Intégration pour en savoir plus sur l’intégration d’une solution de commerce.

>[!TIP]
>
>Si aucune API en temps réel n’est disponible, un cache de produit externe doté d’API doit être utilisé pour l’intégration. Exemple de [Magento open-source](https://business.adobe.com/fr/products/magento/open-source.html).

## Expériences de catalogue de produits avec rendu dans AEM

Si vous utilisez le plan directeur de catalogue avec CIF classique, vous devez mettre à jour le workflow du catalogue de produits. Le module complémentaire CIF effectue désormais le rendu à la volée des expériences de catalogue de produits à l’aide de modèles de catalogue AEM. Aucune réplication des données de produit ou des pages de produit n’est désormais nécessaire.

## Données et interaction d’achat non mises en cache

Les requêtes côté client pour les données et interactions non mises en cache (par exemple, l’ajout au panier, la recherche) doivent accéder directement au point d’entrée de commerce (solution de commerce ou couche d’intégration) via le réseau CDN ou le Dispatcher. Supprimez tous les appels pour lesquels AEM servait uniquement de proxy.
