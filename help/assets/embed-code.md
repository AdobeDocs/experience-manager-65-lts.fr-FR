---
title: Incorporation de la visionneuse de vidéos ou d’images Dynamic Media, ou de la visionneuse dimensionnelle dans une page web
description: Découvrez comment incorporer des images 3D, des images ou des vidéos Dynamic Media dans une page web.
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
topic-tags: dynamic-media
content-type: reference
feature: Viewers
role: User, Admin
solution: Experience Manager, Experience Manager Assets
exl-id: b98729d3-111a-446b-915a-ca85b3cd75f0
source-git-commit: c3e9029236734e22f5d266ac26b923eafbe0a459
workflow-type: tm+mt
source-wordcount: '383'
ht-degree: 100%

---

# Incorporation de la visionneuse de vidéos ou d’images Dynamic Media, ou de la visionneuse dimensionnelle dans une page web {#embedding-the-video-or-image-viewer-on-a-web-page}

Utilisez la fonction **[!UICONTROL Code intégré]** lorsque vous souhaitez lire une vidéo ou afficher une ressource incorporée dans une page web. Vous copiez le code intégré dans le Presse-papiers afin de le coller dans vos pages web. Vous ne pouvez pas modifier le code dans la boîte de dialogue **[!UICONTROL Code intégré]**.

Vous devez incorporer les URL uniquement si vous *n’utilisez pas* Adobe Experience Manager comme outil de gestion de contenu web. Dans le cas contraire, [vous pouvez ajouter les ressources directement à votre page](adding-dynamic-media-assets-to-pages.md).

Voir [Liaison d’URL à une application web](linking-urls-to-yourwebapplication.md).

Consultez [Diffusion d’images optimisées pour un site réactif](responsive-site.md).

>[!NOTE]
>
>Vous ne pouvez pas copier le code intégré tant que la ressource sélectionnée n’a pas été publiée. En outre, vous devez également publier le paramètre de visionneuse prédéfini ou le paramètre d’image prédéfini.
>
>Consultez la section [Publication de ressources](publishing-dynamicmedia-assets.md).
>
>Voir [Publication de paramètres de visionneuse prédéfinis](managing-viewer-presets.md#publishing-viewer-presets).
>
>Voir [Publication de paramètres d’image prédéfinis](managing-image-presets.md#publishing-image-presets).

**Pour incorporer la visionneuse de vidéos ou d’images ou la visionneuse dimensionnelle Dynamic Media dans une page Web :**

1. Accédez à la ressource vidéo ou d’image *publiée* dont vous souhaitez copier le code intégré.

   N’oubliez pas que le code intégré n’est disponible à la copie qu’*après* la première *publication* des ressources. En outre, le paramètre de visionneuse prédéfini ou le paramètre d’image prédéfini doit également être publié.

   Consultez la section [Publication de ressources](publishing-dynamicmedia-assets.md).

   Voir [Publication de paramètres de visionneuse prédéfinis](managing-viewer-presets.md#publishing-viewer-presets).

   Voir [Publication de paramètres d’image prédéfinis](managing-image-presets.md#publishing-image-presets).

1. Dans le rail de gauche, sélectionnez le menu déroulant et sélectionnez ensuite **[!UICONTROL Visionneuses]**.
1. Dans le rail de gauche, sélectionnez un nom de paramètre prédéfini de la visionneuse. Le paramètre de visionneuse prédéfini est appliqué à la ressource.
1. Sélectionnez **[!UICONTROL Incorporer]**.
1. Dans la boîte de dialogue **[!UICONTROL Code intégré]**, copiez l’ensemble du code dans le Presse-papiers, puis sélectionnez **[!UICONTROL Fermer]**.
1. Collez le code intégré dans vos pages web.

## Utilisation de HTTP/2 pour diffuser vos ressources Dynamic Media {#using-http-to-deliver-your-dynamic-media-assets}

HTTP/2 est le nouveau protocole Web mis à jour qui améliore la communication entre les navigateurs et les serveurs. Il permet un transfert plus rapide des informations et réduit la puissance de traitement nécessaire. Les ressources Dynamic Media peuvent désormais être diffusées sur HTTP/2, un protocole qui garantit de meilleurs temps de réponse et de chargement.

Voir [Diffusion du contenu sur HTTP2](http2.md) pour tout savoir sur l’utilisation du protocole HTTP/2 avec votre compte Dynamic Media.
