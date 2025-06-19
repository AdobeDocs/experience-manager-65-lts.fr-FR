---
title: Modifier le logo de l’organisation pour l’identité graphique
description: Pour attribuer une marque à l’espace de travail AEM Forms, remplacez le logo par défaut par celui de votre organisation.
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-workspace
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
exl-id: 3aa4aca3-3c94-4936-ba9c-484bbb196256
source-git-commit: b8576049fba41b3bec16046316938274a5046513
workflow-type: tm+mt
source-wordcount: '115'
ht-degree: 100%

---

# Modifier le logo de l’organisation pour l’identité graphique {#changing-the-organization-logo-for-branding}

Le logo de l’organisation s’affiche dans le coin supérieur gauche de l’espace de travail AEM Forms. Pour mettre à jour le logo, suivez les [Étapes génériques de personnalisation de l’espace de travail AEM Forms](/help/forms/using/generic-steps-html-workspace-customization.md#generic-steps-for-html-workspace-customization), puis les étapes ci-après.

1. Créez un logo et nommez le fichier `NewWorkspace.png`. Placez le fichier image dans le dossier /apps/ws/images à l’aide d’un client WebDAV.

   >[!NOTE]
   >
   >La taille recommandée de l’image de logo est de 218 px × 20 px.

   >[!NOTE]
   >
   >Pour plus d’informations, voir [Accès WebDAV](/help/sites-administering/webdav-access.md).

1. Reportez-vous à l’image du nouveau logo dans la feuille de style sous /apps/ws/css/newStyle.css en ajoutant le style suivant.

   ```css
   #logo {
   
          background: url(../images/NewWorkspace.png) no-repeat 14px 11px;
   
   }
   ```
