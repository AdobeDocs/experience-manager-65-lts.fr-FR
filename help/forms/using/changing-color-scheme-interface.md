---
title: Modification des couleurs de l’interface
description: Comment modifier les couleurs de parties spécifiques de l’interface utilisateur de l’espace de travail AEM Forms.
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
exl-id: f15ead5f-d48c-401c-98c5-b58f93776f82
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
source-wordcount: '208'
ht-degree: 100%
---
# Modification des couleurs de l’interface {#changing-the-color-scheme-of-the-interface}

Vous pouvez modifier les couleurs des différentes parties de l’interface utilisateur de l’espace de travail AEM Forms selon vos besoins. Voici quelques exemples de personnalisation des couleurs. En plus des étapes décrites dans cet article, voir [Procédure générique de personnalisation d’AEM Forms Workspace](/help/forms/using/generic-steps-html-workspace-customization.md).

## Barre de navigation supérieure {#top-navigation-bar}

### Utilisation d’une image d’arrière-plan {#using-background-image}

Pour mettre à jour la barre de navigation en haut de l’espace de travail AEM Forms :

1. Créez une image d’arrière-plan pour mettre à jour la couleur. Nommez le fichier newBackground.jpg.
1. Téléchargez le fichier de l’image d’arrière-plan dans le dossier /apps/ws/images à l’aide d’un client WebDAV.

   >[!NOTE]
   >
   >Pour plus d’informations, voir [Accès WebDAV](/help/sites-administering/webdav-access.md).

1. Référencez la nouvelle image d’arrière-plan dans /apps/ws/css/newStyle.css en ajoutant le style suivant.

   ```css
   #header {
       background:#292929 url(../images/newBackground.jpg) repeat-x;
   }
   ```

### Utilisation de la propriété de couleur dans CSS {#using-color-property-in-css}

1. Ajoutez le style suivant dans newStyle.css sous /apps/ws/css.

   ```css
   #header {
   background : none;
   background-color: gray;
   }
   ```

## Composant de catégories {#category-component}

Le composant de catégories affiche les différentes catégories de vos tâches dans le panneau de gauche. Pour modifier sa couleur, définissez la couleur d’arrière-plan dans l’élément `.category` du fichier CSS.

## Composant de tâches {#task-component}

Les tâches sont affichées dans le volet du milieu appelé TaskList de tâches. Pour modifier sa couleur, modifiez le style associé au sélecteur .task dans la feuille de style.
