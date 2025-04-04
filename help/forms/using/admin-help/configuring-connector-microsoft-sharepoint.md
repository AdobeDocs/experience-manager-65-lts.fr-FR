---
title: Configuration de Connector for Microsoft SharePoint
description: Configurez Connector for Microsoft SharePoint pour activer la communication entre AEM forms et Microsoft SharePoint.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/connecting_to_a_content_management_system
products: SG_EXPERIENCEMANAGER/6.5/FORMS
solution: Experience Manager, Experience Manager Forms
role: User, Developer
feature: Adaptive Forms
hide: true
hidefromtoc: true
exl-id: d1575576-3a05-496c-b683-bb5badc02711
source-git-commit: bc91f56d447d1f2c26c160f5c414fd0e6054f84c
workflow-type: tm+mt
source-wordcount: '214'
ht-degree: 100%

---

# Configuration de Connector for Microsoft SharePoint {#configuring-connector-for-microsoft-sharepoint}

>[!NOTE]
> 
> Vérifiez que l’utilisateur ou l’utilisatrice dispose de droits d’administration pour accéder à la console d’administration.

Connecteur pour Microsoft SharePoint permet la communication entre AEM forms et Microsoft SharePoint. Pour plus d’informations, voir Connecteurs pour ECM, dans le [Guide de référence des services](https://help.adobe.com/fr_FR/livecycle/11.0/Services/index.html).

1. Dans la console d’administration, cliquez sur Services > Connecteur pour Microsoft SharePoint.
1. Spécifiez les paramètres suivants pour votre serveur SharePoint :

   **Nom d’hôte du serveur SharePoint :** numéro de port du nom d’hôte de l’application web sur le serveur SharePoint, au format `[hostname]:'port'`.

   **Nom d’utilisateur** : compte d’utilisateur servant à la connexion au serveur SharePoint.

   **Mot de passe** : mot de passe du compte d’utilisateur servant à la connexion au serveur SharePoint.

   **Nom de domaine :** domaine où se trouve le serveur SharePoint.

1. Cliquez sur Enregistrer.

## Service de configuration Microsoft SharePoint {#microsoft-sharepoint-configuration-service}

Le service de configuration Microsoft SharePoint `(MSSharePointConfigService)` vous permet de spécifier les informations d’identification de l’utilisateur AEM Forms disposant des droits d’emprunt d’identité. Pour plus d’informations sur les droits d’emprunt d’identité, consultez [Configuration du connecteur pour Microsoft SharePoint](https://help.adobe.com/fr/AEMForms/6.1/SharePointConfig/index.html). Suivez les étapes suivantes pour définir les paramètres de `MSSharePointConfigService` :

1. Dans Administration Console, cliquez sur Services > Applications et services > Gestion des services.
1. Parcourez la liste des services et cliquez sur `MSSharePointConfigService`.
1. Spécifiez les paramètres suivants sur la page Configuration :

   * Nom d’utilisateur ou d’utilisatrice pour un utilisateur ou une utilisatrice disposant de droits d’emprunt d’identité
   * Mot de passe pour ce même utilisateur ou cette même utilisatrice

1. Cliquez sur Enregistrer.
