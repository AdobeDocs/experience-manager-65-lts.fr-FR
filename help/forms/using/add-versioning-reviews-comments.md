---
title: Ajoutez des versions, des commentaires et des annotations à un formulaire adaptatif AEM 6.5.
description: Utilisez les composants principaux des formulaires adaptatifs d’AEM pour ajouter des commentaires, des annotations et des versions à un formulaire adaptatif.
feature: Adaptive Forms, Core Components
role: User, Developer, Admin
exl-id: 53645880-92e2-4dfd-9c5d-50c849d6e32b
source-git-commit: c3e9029236734e22f5d266ac26b923eafbe0a459
workflow-type: tm+mt
source-wordcount: '612'
ht-degree: 0%

---

# Contrôle de version, révision et commentaires sur un formulaire adaptatif

<span class="preview">Cette fonctionnalité n’est pas activée par défaut. Vous pouvez écrire à partir de votre adresse officielle à aem-forms-ea@adobe.com pour demander l’accès à la fonctionnalité.</span>

Les composants principaux de formulaire adaptatif permettent aux auteurs de formulaires d’ajouter des contrôles de version, des commentaires et des annotations aux formulaires. Ces fonctionnalités simplifient le développement de formulaires en permettant aux utilisateurs et utilisatrices de créer et de gérer plusieurs versions, de collaborer par le biais de commentaires et d’ajouter des notes à des sections de formulaire spécifiques, ce qui améliore l’expérience de création de formulaires.

## Prérequis {#prerequisite-versioning}

Pour utiliser les fonctions de contrôle de version, de commentaires et d’annotation dans un formulaire adaptatif, assurez-vous que les [composants principaux des formulaires adaptatifs](/help/forms/using/enable-adaptive-forms-core-components.md) sont activés dans votre environnement AEM Forms.

## Contrôle de version de formulaire adaptatif {#adaptive-form-versioning}

Le contrôle de version des formulaires adaptatifs permet d’ajouter des versions à un formulaire. Les auteurs de formulaires peuvent facilement créer plusieurs versions d’un formulaire et utiliser celle qui convient aux objectifs commerciaux. En outre, les utilisateurs et utilisatrices du formulaire peuvent également rétablir les versions précédentes du formulaire. Il permet également aux créateurs et aux créatrices de comparer deux versions d’un formulaire en les prévisualisant, ce qui leur permet de mieux analyser les formulaires du point de vue de l’interface utilisateur. Examinons en détail chaque fonctionnalité de contrôle de version de formulaire adaptatif :

### Création d’une version de formulaire {#create-a-form-version}

Pour créer une version d’un formulaire, procédez comme suit :

1. Dans votre environnement AEM Forms, accédez à **[!UICONTROL Formulaire]**>>**[!UICONTROL Forms et documents]** puis sélectionnez votre **Formulaire**.
1. Dans la liste déroulante de sélection du panneau de gauche, sélectionnez **[!UICONTROL Versions]**.
   ![Sélectionner un formulaire](assets/select-a-form.png)
1. Cliquez sur les **trois points** situés sur le panneau inférieur gauche, puis sur **[!UICONTROL Enregistrer comme version]**.
1. Fournissez un libellé à la version de formulaire. Vous pouvez également ajouter des informations sur le formulaire par le biais d’un commentaire.
   ![Créer une version de formulaire](assets/create-a-form-version.png)

### Mise à jour d’une version de formulaire {#update-a-form-version}

Une fois que vous avez modifié et mis à jour votre formulaire, vous ajoutez une nouvelle version au formulaire. Suivez les étapes indiquées dans la dernière section pour attribuer un nom à une nouvelle version du formulaire, comme illustré dans l’image :

![Mettre à jour une version de formulaire](assets/update-a-form-version.png)

### Rétablissement d’une version de formulaire {#revert-a-form-version}

Pour rétablir une version de formulaire à la version précédente, sélectionnez une version de formulaire, puis cliquez sur **[!UICONTROL Rétablir cette version]**.

![Rétablir la version du formulaire](assets/revert-form-version.png)

### Comparer les versions de formulaire {#compare-form-versions}

Les auteurs de formulaires peuvent comparer deux versions différentes d’un formulaire à des fins de prévisualisation. Pour comparer des versions, sélectionnez une version de formulaire et cliquez sur **[!UICONTROL Comparer avec la version actuelle]**. Il affiche deux versions de formulaire différentes en mode Aperçu.

![Comparer les versions de formulaire](assets/compare-form-versions.png)

## Ajouter des commentaires {#add-comments}

Une révision est un mécanisme qui permet à un ou plusieurs réviseurs d’ajouter des commentaires sur les formulaires. Tout utilisateur de formulaire peut ajouter des commentaires sur un formulaire ou réviser un formulaire au moyen de commentaires. Pour ajouter un commentaire sur un formulaire, sélectionnez un **[!UICONTROL Formulaire]** et ajoutez un **[!UICONTROL Commentaire]** au formulaire.

>[!NOTE]
> Lorsque vous utilisez des commentaires dans les composants principaux de formulaires adaptatifs comme décrit ci-dessus, la fonctionnalité de formulaire, [ajout de réviseurs aux formulaires](/help/forms/using/create-reviews-forms.md) est désactivée.


![Ajouter des commentaires sur un formulaire](assets/form-comments.png)

## Ajouter des annotations {#adaptive-form-annotations}

Dans de nombreux cas, les utilisateurs et utilisatrices du groupe de formulaires doivent ajouter des annotations à un formulaire à des fins de révision, par exemple sur un onglet spécifique ou sur les composants d’un formulaire. Dans ce cas, les auteurs peuvent utiliser des annotations.
Pour ajouter des annotations à un formulaire, procédez comme suit :

1. Ouvrez un formulaire en mode **[!UICONTROL Modifier]**.

1. Cliquez sur l’icône **ajouter** située sur le rail supérieur droit, comme indiqué dans l’image.
   ![Annotation](assets/annotation.png)

1. Cliquez maintenant sur l’icône **ajouter** située dans le rail supérieur gauche, comme illustré dans l’image, pour ajouter l’annotation.
   ![&#x200B; Ajouter une annotation &#x200B;](assets/add-annotation.png)

1. Vous pouvez maintenant ajouter des commentaires, dessiner des esquisses avec plusieurs couleurs pour former des composants.

1. Pour afficher toutes les annotations ajoutées à un formulaire, sélectionnez votre formulaire et vous verrez que les annotations ajoutées dans le panneau de gauche, comme illustré dans l’image.

   ![Voir annotations ajoutées](assets/see-annotations.png)

## Voir également

* [Comparaison des composants principaux de Forms adaptatif](/help/forms/using/compare-forms-core-components.md)
