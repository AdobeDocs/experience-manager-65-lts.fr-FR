---
title: Application de signatures électroniques à un formulaire à l’aide de signatures tactiles
description: Découvrez comment signer les formulaires adaptatifs AEM à l’aide de la signature tactile. Vous pouvez utiliser la signature tactile et l’étape de signature pour tracer la signature sur un formulaire.
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: author
docset: aem65
feature: Adaptive Forms,Foundation Components
solution: Experience Manager, Experience Manager Forms
role: User, Developer
exl-id: 9d1a22da-2eb3-4c79-8c4d-4d0a3ed7fe3b
source-git-commit: c3e9029236734e22f5d266ac26b923eafbe0a459
workflow-type: tm+mt
source-wordcount: '718'
ht-degree: 100%

---

# Application de signatures électroniques à un formulaire à l’aide de signatures tactiles{#apply-electronic-signatures-to-a-form-using-deprecated-scribble-signatures}

<span class="preview"> Adobe recommande d’utiliser les [composants principaux](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html?lang=fr) de capture de données modernes et extensibles pour [créer de nouveaux formulaires adaptatifs](/help/forms/using/create-an-adaptive-form-core-components.md) ou [ajouter des formulaires adaptatifs à des pages AEM Sites](/help/forms/using/create-or-add-an-adaptive-form-to-aem-sites-page.md). Ces composants représentent une avancée significative dans la création de formulaires adaptatifs, ce qui garantit des expériences utilisateur impressionnantes. Cet article décrit l’ancienne approche de la création de formulaires adaptatifs à l’aide de composants de base. </span>


| Version | Lien de l’article |
| -------- | ---------------------------- |
| AEM as a Cloud Service | [Cliquez ici](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-foundation-components/add-components-to-an-adaptive-form/signing-forms-using-scribble.html?lang=fr) |
| AEM 6.5 | Cet article |


Vous pouvez utiliser le composant **Signature tactile** et le composant **Étape de signature** pour tracer la signature (saisie tactile) sur un formulaire adaptatif. Le composant Étape de signature affiche une version PDF du formulaire adaptatif. Vous avez besoin de l’option Document d’enregistrement activée ou de formulaires adaptatifs basés sur un modèle de formulaire pour utiliser le composant Étape de signature.

![Boîte de dialogue de signature tactile](/help/forms/using/assets/scribble-signature.png)

## Diverses options disponibles dans la fenêtre de signature.

* **A :** cliquez sur l’icône **Pinceau** pour tracer votre signature sur la zone de travail.
* **B :** cliquez sur l’icône **Effacer** pour effacer la signature sur la zone de travail.
* **C :** cliquez sur l’icône **Géolocalisation** pour ajouter une géolocalisation avec la signature.
* **D :** cliquez sur l’icône **Clavier** pour saisir votre nom sur la zone de travail.

Une fois que vous avez sélectionné l’icône Terminé![aem_6_3_forms_save](assets/aem_6_3_forms_save.png) dans la fenêtre de signature tactile, vous ne pouvez plus modifier la signature. Si vous souhaitez modifier la signature, vous devez ignorer la signature actuelle et la signer à nouveau à l’aide de l’option Pinceau/Clavier ci-dessus.

Vous pouvez sélectionner l’icône **Configurer** ![configurer](assets/configure.png) pour définir les proportions de la zone de travail de la signature tactile.
* Lorsque le rapport d’aspect de la zone de travail de signature tactile est inférieur à 1, les informations de géolocalisation sont ajoutées au bas de la zone de travail de signature tactile.

* Lorsque le rapport d’aspect de la zone de travail de signature tactile est supérieur à 1, les informations de géolocalisation sont ajoutées au côté droit de la zone de travail de signature tactile.

![Bas de la signature tactile](/help/forms/using/assets/scribble-signature-aspectratio.PNG)


>[!NOTE]
>
>Les signatures sont toujours enregistrées au format PNG.
>

## Configuration d’un formulaire adaptatif pour utiliser la signature tactile {#configure-an-adaptive-form-to-use-scribble-signature}

1. Créez une option Document d’enregistrement activée ou un formulaire adaptatif basé sur modèle de formulaire. Pour obtenir des informations détaillées, voir [Création d’un formulaire adaptatif](../../forms/using/creating-adaptive-form.md).
1. Faites glisser et déposez le composant **Signature tactile** du navigateur de composant vers le formulaire adaptatif.
1. Sélectionnez l’icône **Configurer** ![configurer](assets/configure.png). Vous ouvrez ainsi le navigateur de propriétés qui affiche les propriétés du composant Signature tactile. Configurez les propriétés du composant Signature tactile.
1. Faites glisser et déposez le composant Étape de signature du navigateur de composant vers le formulaire adaptatif.

   >[!NOTE]
   >
   >Le composant Étape de signature prend toute la largeur disponible pour le formulaire. Il est recommandé de ne pas avoir d’autre composant sur la section contenant le composant Étape de signature. 
   >

1. Dans l’explorateur de contenu, sélectionnez **Conteneur de formulaires**, puis l’icône **Configurer** ![configurer](/help/forms/using/assets/configure.png). L’explorateur de propriétés s’ouvre et affiche les propriétés du conteneur de formulaires adaptatifs. Accédez à **Conteneur de formulaires adaptatifs** > **Signature électronique** et désélectionnez l’option **Activer Adobe Sign**. Sélectionnez l’icône Terminé ![aem_6_3_forms_save](assets/aem_6_3_forms_save.png) pour enregistrer les modifications.

   >[!NOTE]
   >
   >Lorsque vous ajoutez un composant Étape de signature à un formulaire adaptatif, l’option Activer Adobe Sign est sélectionnée automatiquement.
   >

1. Sélectionnez l’icône **Configurer**![Configurer](assets/configure.png). Elle ouvre l’explorateur de propriétés et affiche les propriétés Étape de signature. Configurez les propriétés suivantes :

   * **Nom de l’élément** : spécifiez le nom du composant.

   * **Titre :** indiquez le titre unique du composant.
   * **Message du modèle :** indiquez le message à afficher lorsque la signature PDF est chargée. Les services Adobe Sign mettent un certain temps à préparer et charger la signature PDF.
   * **Service de signature :** sélectionnez l’option **Signature tactile**.

   * **Classe CSS** : spécifiez la classe CSS de la bibliothèque client, le cas échéant. Utilisez des [thèmes](../../forms/using/themes.md) et des [styles en ligne](../../forms/using/inline-style-adaptive-forms.md) au lieu de la classe CSS.

   Sélectionnez l’icône Terminé ![aem_6_3_forms_save](assets/aem_6_3_forms_save.png) pour enregistrer les modifications. La signature est configurée correctement.

   Désormais, lorsque vous remplissez un formulaire, une version PDF du formulaire adaptatif est affichée et les options pour signer le document PDF sont fournies. Pour plus d’informations, voir [Signature d’un formulaire adaptatif en utilisant la signature tactile](../../forms/using/signing-forms-using-scribble.md#sign-an-adaptive-form-using-scribble-signature).

## Signature d’un formulaire adaptatif en utilisant la signature tactile {#sign-an-adaptive-form-using-scribble-signature}

1. Une fois que vous avez renseigné le formulaire adaptatif et que vous avez atteint la page Étape de signature, l’écran de signature s’affiche.

   ![Boîte de dialogue de signature tactile](/help/forms/using/assets/esignscribblesign.jpg)

1. Cliquez sur **[!UICONTROL Signer]**. La boîte de dialogue de signature tactile apparaît. Signez le formulaire et cliquez sur l’icône Terminé ![aem_6_3_forms_save](assets/aem_6_3_forms_save.png) pour enregistrer la signature.

   ![Boîte de dialogue de signature tactile](/help/forms/using/assets/scribblewidget.png)

1. Cliquez sur Terminer pour terminer le processus de signature.

   ![Terminer le processus de signature](/help/forms/using/assets/scribblecomplete.jpg)

Les signatures sont ajoutées au formulaire, et le contrôle de formulaire passe au panneau suivant.
