---
title: Supprimer des formulaires et des ressources associées
description: Découvrez comment supprimer un formulaire ou une ressource dans AEM Forms et quel est l’impact de cette suppression sur les ressources et les formulaires XFA référencés et de référence.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-manager
role: Admin,User
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
exl-id: e9b7e1b1-23a3-4da9-a5b4-c30f70441341
source-git-commit: c3e9029236734e22f5d266ac26b923eafbe0a459
workflow-type: tm+mt
source-wordcount: '369'
ht-degree: 100%

---

# Supprimer des formulaires et des ressources associées {#deleting-forms-and-related-resources}

Vous pouvez supprimer des formulaires et des ressources pour supprimer ces dernières du référentiel. L’opération de suppression fonctionne pour tous les types de ressources et les dossiers.

Si vous supprimez une ressource de l’instance de création, elle est également supprimée de l’instance de publication. Le serveur AEM Forms se compose des instances de création et de publication. L’instance de création est destinée à la création et la gestion d’éléments et de ressources de formulaire. L’instance de publication contient les ressources de formulaire publiées et les ressources associées disponibles pour les utilisatrices et utilisateurs finaux.

## Suppression d’un formulaire {#how-to-delete-a-form}

1. Connectez-vous à l’interface utilisateur d’AEM Forms en accédant à `https://[hostname]:'port'/aem/forms.html.`.
1. Recherchez et sélectionnez le formulaire que vous souhaitez supprimer. Cliquez sur Supprimer ![aem6forms_delete2](assets/aem6forms_delete2.png) dans la barre d’outils et confirmez l’opération de suppression.

   >[!NOTE]
   >
   >Vous pouvez supprimer un seul formulaire à la fois. Vous pouvez supprimer plusieurs formulaires séparément ou supprimer le dossier parent.

1. Avant de supprimer une ressource, AEM Forms vérifie les références et demande une confirmation explicite. Cliquez sur Forcer la suppression si vous souhaitez supprimer la ressource sans tenir compte du statut de la relation.

   >[!NOTE]
   >
   >La suppression d’une ressource référencée par d’autres ressources peut entraîner des problèmes fonctionnels.

   >[!NOTE]
   >
   >Si la ressource sélectionnée correspond à un dossier qui contient une ressource de ce type dans sa hiérarchie, supprimez les autres ressources séparément ou supprimez le dossier entier.

## Impact de la suppression d’un formulaire XFA référencé {#impact-of-deleting-a-referenced-xfa-form}

Dans AEM Forms, un modèle de formulaire XFA peut être référencé par un formulaire adaptatif ou un autre modèle de formulaire XFA. Un modèle peut également faire référence à une ressource ou à un autre modèle XFA.

Il n’est pas conseillé de supprimer un formulaire XFA qui est référencé par un formulaire adaptatif, car cela peut endommager le formulaire adaptatif. Lorsqu’un formulaire adaptatif fait référence à un formulaire XFA, leurs champs sont liés. Après la suppression du formulaire XFA, le formulaire adaptatif ne peut pas synchroniser ses champs avec les champs XFA et affiche un message d’erreur pour ces champs. Pour plus d’informations sur l’impact de la suppression d’un formulaire XFA référencé et sur les formulaires adaptatifs erronés, reportez-vous à la section [Mise à jour des formulaires XFA référencés](/help/forms/using/get-xdp-pdf-documents-aem.md#p-updating-referenced-xfa-forms-p).

Pour supprimer un tel formulaire XFA, mettez à jour le formulaire adaptatif et supprimez les liaisons avec les champs XFA.
