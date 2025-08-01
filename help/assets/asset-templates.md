---
title: Modèles de ressources
description: Découvrez les modèles de ressources dans  [!DNL Adobe Experience Manager Assets]  et comment les utiliser pour créer des dérivés marketing.
role: User
feature: Asset Management,Developer Tools
solution: Experience Manager, Experience Manager Assets
exl-id: 8584d5ea-6ef2-4e81-8b18-5aa2d4226ea6
source-git-commit: 9ed889c74a886e1b41c379dac77bb570ef5c2c39
workflow-type: tm+mt
source-wordcount: '1557'
ht-degree: 100%

---

# Modèles de ressources {#asset-templates}

Les modèles de ressources correspondent à une catégorie spéciale de ressources qui permet de réutiliser rapidement des contenus riches pour les médias papier et numériques. Un modèle de ressource comprend deux parties : une section de message fixe et une section modifiable. La section fixe peut comprendre du contenu propriétaire, comme le logo d’une marque ou des informations sur les droits d’auteur, pour lequel la modification n’est pas activée. La section modifiable peut contenir du contenu visuel et textuel dans des champs qui peuvent être modifiés afin de personnaliser le message.

Parce qu’ils permettent de réaliser des modifications limitées tout en garantissant une harmonie d’ensemble, les modèles de ressources sont des blocs de création parfaits pour adapter et diffuser rapidement votre contenu. La réutilisation de contenu permet de réduire les coûts de gestion des canaux papier et numériques. Cela garantit en outre une expérience globale cohérente, quel que soit le canal de diffusion.

En tant que spécialiste marketing, vous pouvez stocker et gérer les modèles dans [!DNL Experience Manager Assets], et utiliser un modèle de base unique pour créer plusieurs documents papier personnalisés en toute simplicité. Vous pouvez créer différents types de dérivés marketing, par exemple, des brochures, des prospectus, des cartes postales, des cartes de visite, etc., pour transmettre de façon claire votre message marketing à votre clientèle. Vous pouvez également assembler des documents papier comportant plusieurs pages à partir de documents papier nouveaux ou existants. Surtout, vous pouvez facilement proposer simultanément des expériences numériques et imprimées pour offrir une expérience cohérente et intégrée aux utilisateurs et utilisatrices.

Si les modèles de ressources sont pour la plupart des fichiers [!DNL Adobe InDesign], il n’est pas nécessaire de maîtriser [!DNL Adobe InDesign] pour réaliser des documents de qualité. Vous n’avez pas besoin de mapper les champs de votre modèle [!DNL Adobe InDesign] avec vos champs produit, comme cela est nécessaire lors de la création de catalogues. Vous pouvez modifier les modèles en mode WYSIWYG directement depuis l’interface Web. Toutefois, pour qu’[!DNL Adobe InDesign] puisse traiter vos modifications, vous devez configurer [!DNL Experience Manager Assets] pour qu’il intègre [!DNL Adobe InDesign Server].

La possibilité de modifier des modèles [!DNL Adobe InDesign] dans l’interface Web favorise une meilleure collaboration entre les créatifs et le personnel marketing. La vitesse accrue du contenu réduit le délai de mise sur le marché des dérivés marketing.

Avec les modèles de ressources, vous pouvez réaliser les choses suivantes :

* Modifier des champs de modèle modifiables depuis l’interface Web
* Contrôlez les paramètres de base de style du texte, par exemple, la taille, le style et le type de police au niveau des balises.
* Modifier les images du modèle à l’aide du sélecteur de contenu
* Prévisualiser les modifications du modèle
* Fusionner plusieurs fichiers de modèle pour créer un artefact de plusieurs pages

Lorsque vous choisissez un modèle pour vos dérivés, [!DNL Experience Manager Assets] crée une copie du modèle qui peut être modifiée. Le modèle original est préservé, ce qui garantit que votre signalétique reste intacte et peut être réutilisée pour renforcer la cohérence de la marque.

Vous pouvez exporter le fichier mis à jour dans le dossier parent au format INDD, PDF ou JPG. Vous pouvez également télécharger ces différents formats sur approuvé votre système de fichiers local.

## Créer un dérivé {#creating-a-collateral}

Imaginez un scénario dans lequel vous souhaitez créer des supports numériques imprimables, tels que des brochures, des dépliants et des publicités pour une campagne à venir, et les partager avec les magasins d’usine du monde entier. La création de supports basés sur un modèle permet d’offrir une expérience client unifiée sur tous les canaux. Les graphistes peuvent créer des modèles pour la campagne (document d’une seule page ou de plusieurs pages) à l’aide d’une solution de création, comme [!DNL InDesign], et les charger vers [!DNL Experience Manager Assets] pour vous. Avant de créer un dérivé, vous devez charger un ou plusieurs modèles INDD et les rendre disponibles dans [!DNL Experience Manager] à l’avance.

1. Dans l’interface [!DNL Experience Manager], sélectionnez [!UICONTROL Ressources].

1. Dans les options, choisissez **[!UICONTROL Modèles]**.

   ![chlimage_1-101](assets/chlimage_1-306.png)

1. Cliquez sur **[!UICONTROL Créer]**, puis choisissez dans le menu le type de dérivé que vous souhaitez créer. Par exemple, choisissez **[!UICONTROL Brochure]**.

   ![chlimage_1-102](assets/chlimage_1-307.png)

1. Demandez au moins un modèle INDD téléchargé vers et disponible dans [!DNL Experience Manager] à l’avance. Choisissez un modèle pour votre brochure, puis cliquez sur **[!UICONTROL Suivant]**.
1. Entrez un nom et éventuellement une description pour la brochure.

   ![chlimage_1-104](assets/chlimage_1-309.png)

1. (Facultatif) Cliquez sur **[!UICONTROL Balises]** et sélectionnez une ou plusieurs balises pour la brochure. Cliquez sur **[!UICONTROL Confirmer]** pour confirmer votre sélection.
1. Cliquez sur **[!UICONTROL Créer]**. Une boîte de dialogue confirme qu’une nouvelle brochure est créée. Cliquez sur **[!UICONTROL Ouvrir]** pour ouvrir la brochure en mode Édition.

   <!--![chlimage_1-106](assets/.png) -->

   Vous pouvez également fermer la boîte de dialogue et accéder au dossier de la page Modèles avec lequel vous avez commencé pour afficher la brochure que vous avez créée. Le type d’élément apparaît sur sa vignette en mode carte. Par exemple, dans ce cas, le mot [!UICONTROL Brochure] est affiché dans la miniature.

   ![chlimage_1-107](assets/chlimage_1-312.png)

## Modifier un dérivé {#editing-a-collateral}

Vous pouvez modifier un dérivé immédiatement après sa création. Vous pouvez aussi choisir de l’ouvrir depuis la page [!UICONTROL Modèles] ou la page des détails du fichier.

1. Pour ouvrir un dérivé pour le modifier, procédez de l’une des façons suivantes :

   * Ouvrez le dérivé (ici, une brochure) créé à l’étape 7 de la section [Création d’un dérivé](/help/assets/asset-templates.md#creating-a-collateral).
   * Depuis la page Modèles, accédez au dossier où vous avez créé le dérivé, puis cliquez sur l’action rapide [!UICONTROL Modifier] dans la miniature d’un dérivé.
   * Dans la page des détails du dérivé, cliquez sur **[!UICONTROL Modifier]** dans la barre d’outils.
   * Sélectionnez le dérivé et cliquez sur **[!UICONTROL Modifier]** dans la barre d’outils.

   <!--![chlimage_1-108](assets/chlimage_1-313.png) -->

   L’outil de recherche de ressources et l’éditeur de texte sont affichés à gauche de la page. L’éditeur de texte s’ouvre par défaut.

   Utilisez l’éditeur de texte pour modifier le texte que vous souhaitez afficher dans le champ de texte. Vous pouvez modifier la taille, le style, la couleur et le type de police au niveau de la balise.

   Pour utiiliser l’outil de recherche de ressources, vous pouvez rechercher des images dans [!DNL Experience Manager Assets] et remplacer les images modifiables du modèle par d’autres que vous aurez choisies.

   ![chlimage_1-109](assets/chlimage_1-314.png)

   Les images modifiables sont affichées à droite. Pour qu’un champ soit modifiable dans [!DNL Experience Manager Assets], le champ correspondant dans le modèle doit être « marqué » dans [!DNL InDesign]. Plus exactement, il doit être marqué comme étant modifiable dans [!DNL InDesign].

   >[!NOTE]
   >
   >Vérifiez que votre déploiement [!DNL Experience Manager] est intégré avec [!DNL InDesign Server] pour qu’[!DNL Experience Manager Assets] puisse extraire les données du modèle [!DNL InDesign] et les rendre modifiables. Pour plus d’informations, consultez [Intégration d’Experience Manager Assets à InDesign Server](/help/assets/indesign.md).

1. Pour modifier le texte d’un champ modifiable, cliquez sur le champ de texte dans la liste des champs modifiables, puis modifiez le texte dans le champ.

   ![chlimage_1-111](assets/chlimage_1-316.png)

   Vous pouvez modifier les propriétés de texte, par exemple la taille, la couleur ou le style de police à l’aide des options fournies.

1. Sélectionnez **[!UICONTROL Aperçu]** afin de prévisualiser les modifications du texte.

1. Pour permuter une image, cliquez sur l’**[!UICONTROL outil de recherche de ressources]**. ![chlimage_1-113](assets/chlimage_1-318.png).

1. Sélectionnez le champ d’image dans la liste des champs modifiables, puis faites glisser l’image souhaitée du sélecteur de ressource vers le champ modifiable.

   ![chlimage_1-114](assets/chlimage_1-319.png)

   Vous pouvez également rechercher des images à l’aide de mots-clés, de balises ou selon leur statut de publication. Vous pouvez parcourir le référentiel d’[!DNL Experience Manager Assets] et accéder à l’emplacement de l’image souhaitée.

   ![chlimage_1-115](assets/chlimage_1-320.png)

1. Sélectionnez **[!UICONTROL Aperçu]** afin de prévisualiser l’image.
1. Pour modifier une page en particulier dans un dérivé contenant plusieurs pages, utilisez l’outil de navigation au bas de la page.

1. Cliquez sur **[!UICONTROL Aperçu]** dans la barre d’outils pour prévisualiser toutes les modifications. Cliquez sur **[!UICONTROL Terminé]** pour enregistrer les modifications effectuées dans le dérivé.

   >[!NOTE]
   >
   >Les options Aperçu et Terminé sont activées uniquement lorsqu’il ne manque aucune icône aux champs d’image modifiables dans le dérivé. Si des icônes sont manquantes dans votre dérivé, c’est qu’[!DNL Experience Manager] est incapable de résoudre les images du modèle [!DNL InDesign]. Généralement, [!DNL Experience Manager] ne peut pas résoudre les images dans les cas suivants :
   >
   >* Les images ne sont pas incorporées au modèle [!DNL InDesign] sous-jacent.
   >* Les images ne sont pas liées depuis le système de fichiers local.
   >
   >Pour permettre à [!DNL Experience Manager] de résoudre les images, procédez de la façon suivante :
   >
   >* Incorporez les images lorsque vous créez les modèles [!DNL InDesign] (reportez-vous à la section [À propos des liens et des objets graphiques incorporés](https://helpx.adobe.com/fr/indesign/using/graphics-links.html)).
   >* Montez [!DNL Experience Manager] sur votre système de fichiers local, puis mappez les icônes manquantes avec les ressources existantes dans [!DNL Experience Manager].

1. Pour générer un rendu PDF pour la brochure, sélectionnez l’option Acrobat dans la boîte de dialogue, puis cliquez sur **[!UICONTROL Continuer]**.
1. Le dérivé est créé dans le dossier de départ. Pour afficher les rendus, ouvrez l’élément et choisissez **[!UICONTROL Rendus]** de la liste GlobalNav.

   ![chlimage_1-118](assets/chlimage_1-323.png)

1. Sélectionnez le rendu PDF dans la liste des rendus afin de pouvoir télécharger le fichier PDF. Ouvrez le fichier PDF pour réviser le dérivé.

   ![chlimage_1-119](assets/chlimage_1-324.png)

## Fusion de plusieurs dérivés {#merge-collateral}

1. Dans l’interface [!DNL Experience Manager], cliquez sur [!UICONTROL Ressources] dans la page Navigation.

1. Dans les options, choisissez **[!UICONTROL Modèles]**.

1. Sélectionnez **[!UICONTROL Créer]**, puis dans le menu, sélectionnez **[!UICONTROL Fusionner]**.

   ![chlimage_1-120](assets/chlimage_1-325.png)

1. Dans la page [!UICONTROL Fusion de modèles], sélectionnez **[!UICONTROL Fusion]** ![ajout de ressources](assets/do-not-localize/assets_add_icon.png).

1. Accédez à l’emplacement du dérivé que vous souhaitez fusionner, sélectionnez les miniatures des dérivés que vous souhaitez fusionner pour les sélectionner.

   ![chlimage_1-122](assets/chlimage_1-327.png)

   Vous pouvez également rechercher des modèles avec la boîte de dialogue OmniSearch.

   Vous pouvez parcourir le référentiel ou les collections d’[!DNL Experience Manager Assets], puis accéder à l’emplacement des modèles souhaités et les sélectionner pour les fusionner.

   Vous pouvez appliquer divers filtres pour rechercher les modèles souhaités. Par exemple, vous pouvez rechercher des modèles en fonction du type de fichier ou des balises.

1. Sélectionnez **[!UICONTROL Suivant]** dans la barre d’outils.
1. Dans l’écran **[!UICONTROL Aperçu et réorganisation]**, réorganisez les modèles si nécessaire et prévisualisez la sélection de modèles à fusionner. Dans la barre d’outils, sélectionnez **[!UICONTROL Suivant]**.

   ![chlimage_1-126](assets/chlimage_1-331.png)

1. Dans l’écran [!UICONTROL Configurer le modèle], entrez un nom pour le dérivé. Vous pouvez également spécifier les balises que vous considérez appropriées. Pour exporter le résultat au format PDF, sélectionnez **[!UICONTROL Acrobat (.PDF)]**. Par défaut, le dérivé est exporté aux formats JPG et [!DNL InDesign]. Pour modifier la miniature affichée pour le dérivé à plusieurs pages, cliquez sur **[!UICONTROL Modifier la miniature]**.

   ![chlimage_1-127](assets/chlimage_1-332.png)

1. Sélectionnez **[!UICONTROL Enregistrer]**, puis fermez la boîte de dialogue en sélectionnant **[!UICONTROL OK]**. Le dérivé à plusieurs pages est créé dans le dossier de départ.

   >[!NOTE]
   >
   >Vous ne pouvez pas modifier ultérieurement un dérivé fusionné ni l’utiliser pour créer d’autres dérivés.

## Bonnes pratiques et restrictions {#best-practices-limitations-tips}

* L’éditeur [!DNL InDesign] dans [!DNL Experience Manager] fonctionne au niveau de la balise et tout le texte sous une seule balise est considéré comme une seule entité. Pour préserver le formatage et les styles du texte lors de la modification, marquez séparément chaque paragraphe (ou chaque texte avec un style différent).
