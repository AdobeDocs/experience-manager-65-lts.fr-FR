---
title: Application de paramètres prédéfinis d’image Dynamic Media
description: 'Découvrez comment activer des ressources pour afficher des images selon des tailles et des formats différents, ou avec d’autres propriétés d’image générées dynamiquement. '
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
topic-tags: dynamic-media
content-type: reference
feature: Image Presets
role: User,Admin
solution: Experience Manager, Experience Manager Assets
exl-id: f4d3a5f1-9348-433f-9c9f-84075a7ab912
source-git-commit: c3e9029236734e22f5d266ac26b923eafbe0a459
workflow-type: tm+mt
source-wordcount: '344'
ht-degree: 100%

---

# Application de paramètres prédéfinis d’image Dynamic Media {#applying-image-presets}

Les paramètres d’image prédéfinis permettent aux ressources d’afficher des images selon des tailles et des formats différents, ou avec d’autres propriétés d’image générées dynamiquement. Vous pouvez choisir un paramètre prédéfini lorsque vous exportez des images. Le paramètre prédéfini reformate les images selon les spécifications définies par votre administration.

Vous pouvez en outre sélectionner un paramètre prédéfini d’image réactif (signalé par le bouton **[!UICONTROL RESS]** une fois que vous l’avez sélectionné).

Cette section décrit comment utiliser les paramètres d’image prédéfinis. [L’administration peut créer et configurer des paramètres prédéfinis d’image](managing-image-presets.md).

>[!NOTE]
>
>L’imagerie dynamique fonctionne avec vos paramètres d’image prédéfinis et utilise des informations à la dernière milliseconde de la diffusion pour réduire davantage encore la taille du fichier d’image en fonction de la vitesse de connexion du réseau et du navigateur. Voir [Imagerie numérique](imaging-faq.md) pour plus d’informations.

Vous pouvez appliquer un paramètre d’image prédéfini à une image lorsque vous la prévisualisez.

>[!NOTE]
>
>Dans Dynamic Media en mode Scene7, les paramètres prédéfinis d’image sont pris en charge uniquement pour les ressources d’image.

**Pour appliquer les paramètres prédéfinis d’image Dynamic Media :**

1. Ouvrez la ressource et, dans le rail de gauche, sélectionnez le menu déroulant, puis l’option **[!UICONTROL Rendus]**.

   >[!NOTE]
   >
   >* Les rendus statiques apparaissent dans la moitié supérieure du volet. Les rendus dynamiques apparaissent dans la moitié inférieure. Vous ne pouvez utiliser l’URL pour afficher l’image qu’avec les rendus dynamiques.  Le bouton **[!UICONTROL URL]** n’apparaît que si vous sélectionnez un rendu dynamique. Le bouton **[!UICONTROL RESS]** s’affiche uniquement si vous sélectionnez un paramètre d’image prédéfini réactif.
   >
   >* Le système affiche plusieurs rendus lorsque vous sélectionnez **[!UICONTROL Rendus]** dans l’affichage des détails d’une ressource. Vous pouvez augmenter le nombre de paramètres prédéfinis visibles. Consultez la section [Augmentation du nombre de paramètres prédéfinis d’image affichés](managing-image-presets.md#increasing-or-decreasing-the-number-of-image-presets-that-display).

   ![chlimage_1-208](assets/chlimage_1-208.png)

1. Procédez de l’une des manières suivantes :

   * Sélectionnez un rendu dynamique afin de pouvoir prévisualiser le paramètre prédéfini d’image.
   * Pour afficher la fenêtre pop-up, sélectionnez **[!UICONTROL URL]**, **[!UICONTROL Incorporer]** ou **[!UICONTROL RESS]**.

   >[!NOTE]
   >
   >Si la ressource *et* le paramètre prédéfini d’image ne sont pas encore publiés, le bouton **[!UICONTROL URL]** (ou les boutons **[!UICONTROL URL]** et **[!UICONTROL RESS]**, le cas échéant) n’est pas disponible.
   >
   >Notez également que les paramètres prédéfinis de l’image sont automatiquement publiés sur un serveur Dynamic Media 
