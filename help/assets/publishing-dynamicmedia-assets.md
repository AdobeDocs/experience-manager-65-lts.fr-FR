---
title: Publication de ressources Dynamic Media
description: Découvrez comment publier des ressources Dynamic Media, telles que des vidéos et des images, y compris la diffusion HTTP/2 de ces ressources.
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
topic-tags: dynamic-media
content-type: reference
role: User, Admin
feature: Publishing
solution: Experience Manager, Experience Manager Assets
exl-id: 7b31db6e-1b3f-4dfe-8b87-8d70548e9c42
source-git-commit: c3e9029236734e22f5d266ac26b923eafbe0a459
workflow-type: tm+mt
source-wordcount: '478'
ht-degree: 100%

---

# Publication de ressources Dynamic Media {#publishing-dynamic-media-assets}

Vous publiez vos ressources Dynamic Media en sélectionnant celles que vous avez déjà chargées et en appuyant sur **[!UICONTROL Publier]** ou **[!UICONTROL Publication rapide]**. Une fois vos ressources Dynamic Media publiées, vous pouvez les inclure dans une page web au moyen d’une URL ou d’une incorporation de code sur la page.

Vous pouvez également publier immédiatement les ressources que vous chargez, sans intervention de l’utilisateur. Consultez la section [Configuration de Dynamic Media en mode Scene7](config-dms7.md).
Vous pouvez également publier des ressources de manière sélective sur Dynamic Media exclusivement ou dans Adobe Experience Manager exclusivement, à l’aide d’une **[!UICONTROL Publication sélective]** au niveau des dossiers. Voir [Utilisation de la publication sélective dans Dynamic Media](/help/assets/selective-publishing.md).

En **[!UICONTROL mode Carte]**, une petite icône en forme de globe apparaît directement sous le nom d’une ressource et à gauche de la date et de l’heure pour indiquer qu’elle est publiée. Dans la vue **[!UICONTROL Liste]**, une colonne **[!UICONTROL Publié]** indique les ressources qui sont publiées et celles qui ne le sont pas.

>[!NOTE]
>
>Si une ressource a déjà été publiée, utilisez Experience Manager pour déplacer cette ressource vers un autre dossier et la republier depuis son nouvel emplacement. L’emplacement d’origine de la ressource publiée est toujours disponible, ainsi que la ressource récemment republiée. Toutefois, la ressource publiée d’origine est « perdue » pour Experience Manager et elle ne peut pas être dépubliée. Il est donc recommandé de dépublier les ressources avant de les déplacer vers un autre dossier.

Si vous envisagez de publier des ressources vidéo immédiatement après les avoir codées, vérifiez que l’encodage est terminé. Lorsque les vidéos sont en cours d’encodage, le système vous informe qu’un workflow de traitement vidéo est en cours. Lorsque l’encodage vidéo est terminé, vous pouvez prévisualiser les rendus vidéo. À ce stade, vous pouvez publier en toute sécurité les vidéos, sans entraîner aucune erreur de publication.

Consultez également la section [Liaison d’URL à une application web](linking-urls-to-yourwebapplication.md).

Consultez également la section [Incorporation de la visionneuse de vidéos ou d’images Dynamic Media dans une page web](embed-code.md).

>[!NOTE]
>
>* Pour utiliser l’URL, les ressources doivent être publiées. Si les ressources ne sont pas publiées, la copie et le collage de l’URL ne fonctionnent pas dans un navigateur web.
>* Les paramètres d’image prédéfinis et les paramètres de visionneuse prédéfinis doivent être activés et publiés pour une diffusion en direct.
>

Pour plus d’informations sur la publication d’une visionneuse ou d’une ressource, reportez-vous à la section [Publication de ressources](manage-assets.md).

## Diffusion de ressources Dynamic Media via HTTP/2 {#http-delivery-of-dynamic-media-assets}

Experience Manager prend à présent en charge la diffusion de tout le contenu Dynamic Media (images et vidéo) sur HTTP/2. En d’autres termes, une URL publiée ou un code intégré pour l’image ou la vidéo peut être intégré à toute application qui accepte une ressource hébergée. Cette ressource publiée est ensuite diffusée au moyen du protocole HTTP/2. Cette méthode de distribution améliore la communication entre les navigateurs et les serveurs, ce qui permet d’améliorer les temps de réponse et de chargement de toutes vos ressources Dynamic Media.

Pour en savoir plus, consultez la [Foire aux questions sur la diffusion HTTP/2 du contenu](/help/sites-administering/scene7-http2faq.md).
