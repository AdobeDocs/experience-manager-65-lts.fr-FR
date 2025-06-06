---
title: Éditeur
description: Découvrez comment revenir à l’éditeur de l’interface utilisateur classique.
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: operations
content-type: reference
docset: aem65
solution: Experience Manager, Experience Manager Sites
feature: Administering
role: Admin
exl-id: 54a97ac0-db9e-4903-b395-b1af87cfd151
source-git-commit: c3e9029236734e22f5d266ac26b923eafbe0a459
workflow-type: tm+mt
source-wordcount: '108'
ht-degree: 100%

---

# Éditeur{#editor}

Par défaut, la possibilité de basculer vers l’interface utilisateur classique à partir de l’éditeur a été désactivée.

Pour réactiver l’option **Ouvrir dans l’interface utilisateur classique** dans le menu **Informations sur la page**, procédez comme suit.

1. À l’aide de CRXDE Lite, recherchez le nœud suivant :

   `/libs/wcm/core/content/editor/jcr:content/content/items/content/header/items/headerbar/items/pageinfopopover/items/list/items/classicui`

   Par exemple :

   ` [https://localhost:4502/crx/de/index.jsp#/libs/wcm/core/content/editor/jcr%3Acontent/content/items/content/header/items/headerbar/items/pageinfopopover/items/list/items/classicui](https://localhost:4502/crx/de/index.jsp#/libs/wcm/core/content/editor/jcr%3Acontent/content/items/content/header/items/headerbar/items/pageinfopopover/items/list/items/classicui)`

1. Créez un recouvrement à l’aide de l’option **Nœud de recouvrement** ; par exemple :

   * **Chemin** : `/apps/wcm/core/content/editor/jcr:content/content/items/content/header/items/headerbar/items/pageinfopopover/items/list/items/classicui`
   * **Emplacement du recouvrement** : `/apps/`
   * **Faire correspondre les types de nœud** : actif (cochez la case)

1. Ajoutez la propriété de texte à valeurs multiples ci-dessous au nœud de recouvrement :

   `sling:hideProperties = ["granite:hidden"]`

1. L’option **Ouvrir dans l’IU classique** est toujours disponible dans le menu des **Informations de la page** lors de la modification des pages.

   ![Ouvrir dans l’option de l’interface utilisateur classique à partir des informations sur la page](assets/syui-03-2019-02-27-15-19-48.png)
