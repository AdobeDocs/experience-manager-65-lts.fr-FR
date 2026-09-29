---
title: Définition des paramètres de sécurité
description: Découvrez comment définir des paramètres de sécurité pour protéger les fichiers de données XML. La fonction de paramètre de sécurité contrôle les entités externes dans les entrées XML.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_forms
products: SG_EXPERIENCEMANAGER/6.5/FORMS
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms,Document Security
role: User, Developer
hide: true
removedfrom6.5.2025: 'yes'
exl-id: 75257aa3-9917-4145-ab8c-88965f01d0f6
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
  - id: e8f6de9b-cf88-4405-8d10-15efa08c230e
    internal-label: Experience Manager Forms
feature_v2:
  - id: 50158d81-1c06-57f7-8bd7-e8ff76a93f85
    internal-label: Document Security
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
source-wordcount: '101'
ht-degree: 100%
---
# Définition des paramètres de sécurité {#specifying-security-settings}

>[!NOTE]
> 
> Vérifiez que l’utilisateur ou l’utilisatrice dispose de droits d’administration pour accéder à la console d’administration.

Forms vous permet de contrôler la résolution des entités externes dans les entrées XML. Par défaut, elles sont résolues, mais vous pouvez modifier ce comportement pour accroître la sécurité de votre système AEM Forms.

**Empêcher le traitement des fichiers de données XML contenant des références à des entités externes**

1. Dans la console d’administration, cliquez sur **[!UICONTROL Services > Forms]**.
1. Désélectionnez la case Résoudre les entités externes.
1. Cliquez sur **[!UICONTROL Enregistrer]**.
