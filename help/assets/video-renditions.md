---
title: Rendus vidéo
description: Découvrez comment utiliser Adobe Experience Manager Assets pour générer des rendus vidéo pour les ressources vidéo de différents formats, dont OGG, FLV, etc.
contentOwner: rbrough
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
solution: Experience Manager, Experience Manager Assets
feature: Video
role: User
exl-id: da33f43b-7375-46f1-a80f-c1891fd90312
source-git-commit: c3e9029236734e22f5d266ac26b923eafbe0a459
workflow-type: tm+mt
source-wordcount: '246'
ht-degree: 100%

---

# Rendus vidéo {#video-renditions}

Adobe Experience Manager Assets génère des rendus vidéo pour les ressources vidéo de différents formats, dont OGG, FLV, etc.

Experience Manager Assets prend en charge les rendus statiques et dynamiques (rendus avec codage DM) pour les ressources multimédias.

Les rendus statiques sont générés en mode natif à l’aide de FFMPEG (installé et disponible sur le chemin système) et stockés dans le référentiel de contenu.

Les rendus avec codage DM sont stockés dans le serveur proxy et diffusés au moment de l’exécution.

Experience Manager Assets fournit une prise en charge de lecture pour ces rendus du côté client.

Pour afficher les rendus d’une ressource vidéo spécifique, ouvrez sa page de ressource, puis sélectionnez l’icône de navigation globale. Choisissez ensuite **[!UICONTROL Rendus]** dans la liste.

![chlimage_1-478](assets/chlimage_1-478.png)

 La liste des rendus vidéo s’affiche dans le panneau **[!UICONTROL Rendus.]**

![chlimage_1-479](assets/chlimage_1-479.png)

Pour configurer le serveur proxy des rendus codés DM, [configurez les services cloud Dynamic Media](config-dynamic.md).

Pour générer des rendus vidéo avec les paramètres souhaités, [créez un profil vidéo correspondant ;](video-profiles.md).

Une fois que vous avez configuré le serveur proxy et créé les profils vidéo, vous pouvez inclure ce paramètre vidéo prédéfini dans un profil de traitement et appliquer le profil de traitement à un dossier.

>[!NOTE]
>
>La lecture audio ne fonctionne pas pour les fichiers OGG et WAV sur Microsoft® Internet Explorer 11. Une erreur `Invalid Source` apparaît sur la page des détails des ressources présentant l’extension OGG ou WAV.
>
>Sous MS® Edge et iPad, les fichiers OGG ne s’exécutent pas et génèrent une erreur de format non pris en charge.
