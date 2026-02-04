---
title: Gestion par programmation des nœuds de préférences
description: Utilisez l’API du service Gestionnaire de préférences (Java) pour gérer les nœuds de préférences par programmation.
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: operations
role: Developer
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms,APIs & Integrations
hide: true
hidefromtoc: true
exl-id: 95a83858-c0b7-4c68-b4a9-d525bfc663c0
source-git-commit: 51342861dd01e659999c19fbe0274e8d3cbcf8c4
workflow-type: tm+mt
source-wordcount: '239'
ht-degree: 49%

---

# Gestion par programmation des nœuds de préférences {#programmatically-managing-the-preferencesnodes}

**Les exemples et les échantillons de ce document sont réservés à AEM Forms sur l’environnement JEE.**

Cette rubrique décrit comment utiliser l’API du service du Gestionnaire de préférences (Java) pour gérer les nœuds de préférences par programmation.

Vous pouvez modifier manuellement les paramètres de configuration à partir de l’interface utilisateur de l’administrateur. Pour modifier les options, accédez à `Home>Settings>User Management> Configuration>Manual Configuration`. Importez `config.xml` après avoir apporté les modifications. Vous remarquerez que toutes les modifications, à l’exception des modifications apportées au nœud `/Adobe/Adobe Experience Manager Forms/Config/UM persist` sont perdues. L’aperçu de l’importation et de l’exportation User Management ne prend pas en charge la modification des paramètres de configuration des autres composants. Désormais, ces modifications peuvent être effectuées à l’aide des API `PreferencesManagerServiceClient`.

**Résumé des étapes**
Pour gérer les nœuds de préférences par programmation, procédez comme suit :

1. Incluez les fichiers du projet.
1. Créez un client `PreferencesManagerService`.
1. Appelez les opérations de rôle ou d’autorisation appropriées.

**Incluez les fichiers du projet**

Incluez les fichiers nécessaires dans votre projet de développement. Si vous créez une application cliente à l’aide de Java, incluez les fichiers JAR nécessaires. Si vous utilisez des services web, veillez à inclure les fichiers proxy.

**Créer un `PreferencesManagerService` client**

Avant d’effectuer par programmation une opération de `PreferencesManagerService` User Management, vous devez créer un client `PreferencesManagerService`. Avec l’API Java, créez un objet `PreferencesManagerServiceClient`.

**Appeler les opérations de rôle ou d’autorisation appropriées**

Une fois le client de service créé, vous pouvez alors appeler les opérations du Gestionnaire de préférences. Le client de service vous permet de lire et de définir des autorisations.
