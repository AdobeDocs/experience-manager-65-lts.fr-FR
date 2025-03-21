---
title: Bonnes pratiques relatives au traitement des formats de fichiers pris en charge
description: Bonnes pratiques relatives au traitement des différents types de fichiers pris en charge à l’aide de [!DNL Experience Manager Assets].
contentOwner: AG
role: Admin
feature: Asset Management,Developer Tools
solution: Experience Manager, Experience Manager Assets
exl-id: 28765aeb-1303-40da-bde0-df1b4c625d37
source-git-commit: c3e9029236734e22f5d266ac26b923eafbe0a459
workflow-type: tm+mt
source-wordcount: '470'
ht-degree: 100%

---

# Bonnes pratiques relatives aux formats de fichier des ressources {#assets-file-format-best-practices}

[!DNL Adobe Experience Manager Assets] prend en charge de nombreuses bibliothèques de formats de fichiers propriétaires et tierces pour gérer les divers besoins des utilisateurs en matière de prise en charge des fichiers. Les bibliothèques Adobe prises en charge comprennent [!DNL Adobe Camera Raw], Gibson, Adobe PDF Rasterizer et [!DNL Adobe InDesign Server]. En outre, [!DNL Experience Manager Assets] prend en charge les bibliothèques tierces, y compris [!DNL ImageMagick], [!DNL TwelveMonkeys], etc.

Pour les formats de fichiers pris en charge, consultez [Formats pris en charge par AEM Assets](/help/assets/assets-formats.md).

>[!TIP]
>
>Si vous utilisez [!DNL Experience Manager] sur Adobe Managed Services (AMS), contactez l’assistance clientèle d’Adobe si vous envisagez de traiter un grand nombre de fichiers PSD ou PSB volumineux. Collaborez avec le représentant de l’assistance clientèle d’Adobe afin de mettre en œuvre ces bonnes pratiques pour votre déploiement AMS et de choisir les meilleurs outils et modèles possibles pour les formats propriétaires d’Adobe. Il se peut qu’[!DNL Experience Manager] ne puisse pas traiter des fichiers PSB à très haute résolution de plus de 30 000 x 23 000 pixels.

## Bibliothèque [!DNL Adobe Camera Raw] {#adobe-camera-raw-library}

Pour des performances optimales, Adobe recommande d’utiliser la bibliothèque [!DNL Adobe Camera Raw] pour les fichiers RAW et DNG.

[!DNL Adobe Camera Raw] prend en charge le profil colorimétrique CMJN en entrée. Cependant, cela génère la sortie dans l’espace colorimétrique RGB et ne prend en charge que la sortie au format JPEG. Cela ne permet pas de conserver l’espace colorimétrique du fichier source (CMJN, par exemple) dans les miniatures.

Pour plus d’informations, consultez [Prise en charge de Camera Raw](/help/assets/camera-raw.md).

## Bibliothèque Adobe PDF Rasterizer {#adobe-pdf-rasterizer-library}

Pour de meilleurs résultats, Adobe recommande d’utiliser la bibliothèque Adobe PDF Rasterizer pour les fichiers suivants :

* Fichiers PDF volumineux et gourmands en contenu
* Fichiers AI avec des miniatures non générées prêtes à l’emploi
* Pour les fichiers AI avec des couleurs SPOT (PMS)

Les miniatures et les aperçus générés à l’aide de PDF Rasterizer sont de meilleure qualité par rapport à la sortie matricielle prête à l’emploi. La bibliothèque PDF Rasterizer d’Adobe ne prend en charge aucune conversion d’espace colorimétrique. Quel que soit l’espace colorimétrique du fichier PDF source, PDF Rasterizer d’Adobe génère la sortie RVB uniquement.

## [!DNL Adobe InDesign Server] {#adobe-indesign-server}

Adobe vous recommande d’utiliser [!DNL Adobe InDesign Server] pour extraire des rendus spécifiques à [!DNL Adobe InDesign], tels que l’IDML et l’HTML. Pour plus d’informations, consultez [Ajout de ressources Experience Manager comme références dans Adobe InDesign](/help/assets/managing-linked-subassets.md#refai).

## [!DNL Dynamic Media] {#dynamic-media}

[!DNL Dynamic Media] génère et diffuse plusieurs variations de contenu riche en temps réel via son réseau mondial, extensible et optimisé pour garantir de bonnes performances. Il diffuse des expériences d’affichage interactif et simplifie le processus de gestion des campagnes numériques. Pour en savoir plus sur l’activation de [!DNL Dynamic Media], consultez [Configuration de Dynamic Media](/help/assets/config-dynamic.md).

Actuellement, [!DNL Dynamic Media] peut prendre en charge jusqu’à 15 Go de contenu vidéo par fichier.

## Bibliothèque ImageMagick {#imagemagick-library}

Adobe recommande d’utiliser la bibliothèque ImageMagick dans les scénarios suivants :

* Pour générer des rendus de miniature pour les fichiers EPS.
* Pour conserver les informations sur les profils d’image
* Pour conserver la transparence
* Pour traiter des fichiers PSD et PSB

Pour savoir comment installer la bibliothèque [!DNL ImageMagick] dans [!DNL Experience Manager], consultez [Fonctionnement d’ImageMagick](/help/assets/media-handlers.md#an-example-using-imagemagick). Pour une utilisation optimale, consultez [Bonnes pratiques pour la configuration d’ImageMagick](/help/assets/best-practices-for-imagemagick.md).

## Bibliothèque de transcodage d’image {#image-transcoding-library}

La bibliothèque de transcodage d’imagerie d’Adobe est une solution de traitement des images qui exécute des fonctions essentielles de manipulation graphique, y compris le codage, le transcodage, le rééchantillonnage, le redimensionnement des images et ainsi de suite.

La bibliothèque de transcodage d’imagerie prend en charge les types MIME suivants :

* JPG/JPEG
* PNG (8 bits et 16 bits)
* GIF
* BMP
* TIFF/TIFF compressé (hormis pour les images Tiff et PTiff 32 bits)
* ICO
* ICN

Pour plus d’informations, consultez [Bibliothèque de transcodage d’imagerie](/help/assets/imaging-transcoding-library.md).
