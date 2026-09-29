---
title: Configurer les messages de validation
description: Découvrez comment spécifier l’affichage des messages de validation et leur emplacement par rapport au formulaire renvoyé dans le navigateur web.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_forms
products: SG_EXPERIENCEMANAGER/6.5/FORMS
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
hide: true
removedfrom6.5.2025: 'yes'
exl-id: 1172f1f2-b297-4021-a9ee-507b0a4e628a
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
  - id: e8f6de9b-cf88-4405-8d10-15efa08c230e
    internal-label: Experience Manager Forms
feature_v2:
  - id: e72c079d-d036-46d5-b43d-29b276a174c2
    internal-label: Authoring and publishing content
subfeature_v2:
  - id: a26f372d-6d7c-452b-81df-594dd4365ae1
    internal-label: Adaptive Forms
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 2e690827bfa8f3d8227860de4efb802758ae0095
workflow-type: tm+mt
source-wordcount: '364'
ht-degree: 100%
---
# Configurer les messages de validation {#configuring-validation-messages}

>[!NOTE]
> 
> Vérifiez que l’utilisateur ou l’utilisatrice dispose de droits d’administration pour accéder à la console d’administration.

Pour les formulaires rendus au format HTML, les erreurs de validation de formulaire qui se produisent s’affichent pour l’utilisateur ou l’utilisatrice. Vous pouvez personnaliser le type d’affichage des messages de validation. Selon l’endroit où les messages de validation sont affichés, vous pouvez également contrôler l’emplacement du message dans le formulaire et la taille de la bordure du cadre.

## Définition du type d’affichage des messages de validation {#specify-how-validation-messages-are-displayed}

1. Dans la console d’administration, cliquez sur Services > Formulaires.
1. Sous Sortie de validation, dans la liste Rapport, sélectionnez l’une des options suivantes :

   **Zone de message :** pour que les messages de validation s’affichent dans une boîte de dialogue distincte.

   **Cadre :** pour que les messages de validation s’affichent à l’intérieur d’un cadre dans la même fenêtre.

   **Aucun cadre :** pour que les messages de validation s’affichent dans la même fenêtre. Il s’agit de la valeur par défaut.

   **Via API (avec données) :** pour renvoyer les messages de validation via l’API (avec des données). Les messages de validation ne s’affichent pas à l’écran.

   **Via API (avec formulaire) :** pour renvoyer les messages de validation via l’API (avec le formulaire). Les messages de validation ne s’affichent pas à l’écran.

   **Aucun :** pour ne pas afficher de messages de validation.

1. Cliquez sur Enregistrer.

## Définition de l’emplacement des messages de validation par rapport au formulaire renvoyé dans le navigateur web {#specify-the-location-of-validation-messages-relative-to-the-form-returned-in-the-web-browser}

Lorsque l’option Rapport est définie sur Cadre ou Aucun cadre, vous pouvez indiquer l’emplacement des messages de validation.

1. Sous Sortie de validation, dans la liste Position, sélectionnez l’une des options suivantes :

   **Gauche :** pour afficher les messages de validation dans la partie gauche du navigateur web.

   **Droite :** pour afficher les messages de validation dans la partie droite du navigateur web.

   **En haut** : pour afficher les messages de validation dans la partie supérieure du navigateur web. Il s’agit de la valeur par défaut.

   **En bas** : pour afficher les messages de validation dans la partie inférieure du navigateur web.

1. Cliquez sur Enregistrer.

## Définition de la taille du cadre {#specify-the-frame-border-size}

Lorsque l’option Rapport est définie sur Cadre, vous pouvez indiquer la taille du cadre.

1. Sous Sortie de validation, dans la zone Taille de la bordure, indiquez la taille de la bordure du cadre, en pixels.

   La taille de la bordure doit être égale ou supérieure à zéro. La valeur par défaut est 1.

1. Cliquez sur Enregistrer.
