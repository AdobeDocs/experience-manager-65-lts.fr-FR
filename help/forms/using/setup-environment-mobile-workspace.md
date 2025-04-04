---
title: Configurer l’environnement de l’application AEM Forms
description: Matériel, logiciels et licences pour créer et déployer l’application AEM Forms.
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-app
docset: aem65
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: Admin, User, Developer
exl-id: 41799183-ef5a-4990-bd7b-7b58cafe3960
source-git-commit: c3e9029236734e22f5d266ac26b923eafbe0a459
workflow-type: tm+mt
source-wordcount: '211'
ht-degree: 100%

---

# Configurer l’environnement de l’application AEM Forms{#set-up-environment-for-aem-forms-app}

Vous avez besoin du matériel, des logiciels et licences ci-dessous pour générer et déployer l’application AEM Forms :

## Pour les périphériques Windows {#for-windows-devices}

* Microsoft® Windows 10
* Microsoft® Visual Studio 2015
* Outils Microsoft® Visual Studio pour Apache Cordova

## Pour les périphériques iOS {#for-ios-devices}

* Ordinateur Apple Mac à processeur Intel avec macOS X 10.9.5 ou version supérieure
* SDK iOS 8.4 ou version supérieure
* Version Xcode : Xcode 6.4 pour OS X ou version supérieure
* Adhésion au programme pour développeurs et développeuses iOS en entreprise
* Certificat d’entreprise pour la distribution d’applications iOS en interne
* Apple iPad avec iOS 8.4 ou version ultérieure

## Pour périphériques Android™ {#for-android-devices}

* Android™ Development Toolkit (lot ADT) peut être téléchargé depuis [https://developer.android.com/studio](https://developer.android.com/studio).
* Si l’environnement est configuré sur un système Mac, ADT doit être installé dans le dossier Applications.
* Si ADT est installé à un autre emplacement sur Mac ou si l’environnement est configuré sur un système Windows, le chemin du SDK ADT doit être mis à jour dans le fichier `local.properties`. Ce fichier est disponible dans le dossier `src\android` de l’archive source extraite `mobileworkspace-src.zip`. Dans ce fichier, pointez la variable `sdk.dir` vers l’emplacement d’ADT SDK sur votre bureau.

>[!NOTE]
>
>Le fichier adobe-lc-mobileworkspace-src.zip contient le PhoneGAP SDK 5.0. Assurez-vous que le PhoneGap SDK n’est pas préinstallé.
