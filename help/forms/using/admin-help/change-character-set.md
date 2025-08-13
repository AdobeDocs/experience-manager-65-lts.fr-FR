---
title: Modifier le jeu de caractères
description: Vous pouvez indiquer le jeu de caractères utilisé pour encoder le flux de sortie. Découvrez comment modifier le jeu de caractères.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_output
products: SG_EXPERIENCEMANAGER/6.5/FORMS
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
hide: true
hidefromtoc: true
exl-id: 1d614736-5897-4fd3-9ca4-94b115139ba3
source-git-commit: bc91f56d447d1f2c26c160f5c414fd0e6054f84c
workflow-type: tm+mt
source-wordcount: '144'
ht-degree: 100%

---

# Modifier le jeu de caractères {#change-the-character-set}

>[!NOTE]
> 
> Vérifiez que l’utilisateur ou l’utilisatrice dispose de droits d’administration pour accéder à la console d’administration.

Vous pouvez indiquer le jeu de caractères utilisé pour encoder le flux de sortie.

1. Dans la console d’administration, cliquez sur **[!UICONTROL Services > Output]**.
1. Sous Internationalisation, dans la liste Jeu de caractères, sélectionnez un jeu de caractères. Ce paramètre dépend des paramètres `TransformationFormat` et `PrintFormat` spécifiés via l’API. Pour spécifier un jeu de caractères ne figurant pas dans la liste, sélectionnez Personnalisé et spécifiez la valeur d’encodage dans la zone qui s’affiche.

   Si le paramètre `TransformationFormat` prend la valeur PDF et PDF/A ou que le paramètre `PrintFormat` prend la valeur PCL, PostScript, Zebra label, IPL, DPL, TPCL, GenericColorPCL ou GenericPSLevel3, seuls des jeux de caractères spécifiques sont pris en charge.

   Le jeu de caractères doit être un nom canonique valide. La valeur par défaut est ISO-8859-1.

1. Cliquez sur **[!UICONTROL Enregistrer]**.
