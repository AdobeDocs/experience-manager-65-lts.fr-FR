---
title: Configurer le service d’informations système
description: Découvrez comment configurer le service d’informations système.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/system_information_service
products: SG_EXPERIENCEMANAGER/6.5/FORMS
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
hide: true
removedfrom6.5.2025: 'yes'
exl-id: e31614a9-d670-4d22-88ba-8953797f6e14
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
source-wordcount: '114'
ht-degree: 100%
---
# Configurer le service d’informations système {#set-up-the-system-information-service}

>[!NOTE]
> 
> Vérifiez que l’utilisateur ou l’utilisatrice dispose de droits d’administration pour accéder à la console d’administration.

Le service d’informations système fournit des API REST pour récupérer des informations. Pour utiliser le service d’informations système, activez le point d’entrée REST à partir d’Administration Console. Pour activer le point d’entrée REST, effectuez les étapes suivantes :

1. Connectez-vous à Administration Console. L’URL par défaut de la console d’administration est `https://[hostname]:'port'/adminui.`.
1. Accédez à Services > Applications et services > Gestion des services.
1. Sur la page Gestion des services, cliquez sur le service **SystemInfo**.
1. Dans la liste de l’onglet Points d’entrée, sélectionnez REST, puis cliquez sur **Ajouter**.
1. Sur l’écran Ajouter un point d’entrée REST, cliquez sur **Ajouter**.
