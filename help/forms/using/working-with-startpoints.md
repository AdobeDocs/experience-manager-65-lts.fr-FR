---
title: Utilisation des points de départ
description: Étapes à suivre pour utiliser un processus Adobe Experience Manager Forms de votre appareil mobile défini dans Workbench.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-app
docset: aem65
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
exl-id: 88a4a75f-2cd7-44b8-a9d0-9a7077173c67
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
source-git-commit: 2b710c6ef8d291a42b4a7658bf84f5e764422d5c
workflow-type: tm+mt
source-wordcount: '292'
ht-degree: 80%
---
# Utilisation des points de départ{#working-with-startpoints}

>[!NOTE]
>
>Les versions Android et iOS de l’application AEM Forms ont été interrompues. L’application Android a été dépubliée à partir de Google Play en septembre 2026 et l’application iOS a été supprimée d’Apple App Store.
>Ces applications ne peuvent plus être installées. Pour obtenir de l’aide sur l’application Android, contactez [aemformsapp-android@adobe.com](mailto:aemformsapp-android@adobe.com).

Un point de départ appelle un processus créé dans Workbench. Il est associé à un formulaire qui appelle le processus lors de l’envoi du formulaire.

>[!NOTE]
>
>Les termes « points de départ », « processus de démarrage » et « formulaire » sont indifféremment utilisés pour désigner ce concept.

Pour lancer un processus à partir de l’application Adobe Experience Manager (AEM) Forms, vous devez disposer d’un point de départ de type **Espace de travail** dans votre processus. En outre, vous devez sélectionner l’option **[!UICONTROL Visible dans Mobile Workspace]** pour le point de départ.

![mws_startpoint_select_option](assets/mws_startpoint_select_option.png)

**Pour démarrer un processus défini dans Workbench**

1. Pour afficher les points de départ disponibles dans l’application AEM Forms, accédez à [Écran d’accueil](../../forms/using/home-screen.md).
1. Sur l’écran d’**[!UICONTROL Accueil]**, la liste **[!UICONTROL Tous les formulaires]** s’affiche par défaut.

   Le point de départ est associé à un formulaire. Sélectionnez le formulaire associé au point de départ dans la liste pour l’ouvrir.

   Le formulaire associé au point de départ s’ouvre.

1. Saisissez les informations dans le **[!UICONTROL formulaire]** Point de départ.

   Vous pouvez ajouter des annotations à cette tâche à l’aide du bouton de la [pièce jointe](../../forms/using/add-attachments.md).

1. Une fois que vous avez rempli le formulaire, cliquez sur le bouton **[!UICONTROL Envoyer]**.

Si l’application est hors ligne, le formulaire et ses données sont enregistrés dans le dossier de boîte d’envoi.

Si l’application est en ligne, la tâche est synchronisée avec le serveur AEM Forms et affectée à l’utilisateur ou l’utilisatrice spécifié dans le processus.

Pour utiliser la tâche dans votre liste de tâches, voir [Ouvrir une tâche](/help/forms/using/open-task.md).
