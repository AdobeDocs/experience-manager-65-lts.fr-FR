---
title: Architecture de l’espace de travail AEM Forms
description: Informations conceptuelles et vue d’ensemble de l’architecture de l’espace de travail AEM Forms LiveCycle.
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-workspace
solution: Experience Manager, Experience Manager Forms
feature: HTML5 Forms,Adaptive Forms,Mobile Forms
role: User, Developer
exl-id: d317274f-2c9a-4809-b43e-2efebc8fcb3f
source-git-commit: 5995dda0aac101e6c0d506ac5bba786674b0735b
workflow-type: tm+mt
source-wordcount: '224'
ht-degree: 53%

---

# Architecture de l’espace de travail AEM Forms {#aem-forms-workspace-architecture}

L’espace de travail AEM Forms est une application web hébergée sur CRX™. Lorsqu’un espace de travail est ouvert dans un navigateur, un accès à une ressource CRX est effectué et l’application est rendue sous la forme d’une page HTML dans le navigateur.

L’application accède au serveur AEM Forms sur les points d’entrée REST pour effectuer les opérations suivantes :

* Récupérer des tâches utilisateur, des points de départ de processus, l’historique des processus et des informations sur l’utilisateur ou l’utilisatrice
* Exécuter une action sur les tâches
* Interroger les tâches dans la base de données
* Mettre à jour des préférences utilisateur, etc.

Le serveur AEM Forms accède à la base de données AEM Forms via JDBC. La base de données conserve les tâches, les processus et leurs instances, les utilisateurs et utilisatrices et les informations associées.

L’espace de travail AEM Forms est constitué de composants JavaScript modulaires qui peuvent être personnalisés individuellement et réutilisés dans d’autres applications web. Les composants sont basés sur BackBone, qui est une bibliothèque JavaScript structurant les applications web. Un article détaillé décrivant l&#39;interaction des composants avec BackBone est [ici](/help/forms/using/backbone-interaction.md). L’organisation des composants dans la structure de dossiers CRX est présentée dans [cet](/help/forms/using/folder-structure.md) article.

Packages fournis pour l’espace de travail AEM Forms :

* `adobe-lc-workspace-pkg-<version>.zip` : il s’agit du package CRX, c’est-à-dire qu’il peut être déployé dans CRX en utilisant le gestionnaire de modules.
* `adobe-lc-workspace-<version>-src.zip` : il s’agit d’un fichier d’archive contenant le code complet de l’espace de travail AEM Forms et les scripts permettant de créer les packages de déploiement (Ship, Debug et Dev).
