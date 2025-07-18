---
title: Générez l’application Android AEM Forms.
description: Procédure d’installation du projet Android Studio et de génération du fichier .apk pour l’application AEM Forms pour Android
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-app
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
exl-id: a804ba9b-c5c6-4d76-96e4-5d729b673ca4
source-git-commit: b8576049fba41b3bec16046316938274a5046513
workflow-type: tm+mt
source-wordcount: '703'
ht-degree: 100%

---

# Générez l’application Android AEM Forms. {#build-the-aem-forms-android-app}

Pour créer l’application Android pour AEM Forms, procédez comme suit dans la séquence recommandée.

1. [Téléchargement du package de code source de l’application AEM Forms](#download-android-zip)
1. [Définition des variables d’environnement](#set-environment-variable-android)
1. [Génération d’une application AEM Forms standard](#set-up-the-xcode-project)

## Téléchargement du package de code source de l’application AEM Forms {#download-android-zip}

Le package de code source de l’application AEM Forms fait référence à l’archive `adobe-lc-mobileworkspace-src-<version>.zip`. Cette archive comprend le code source requis pour créer une application AEM Forms personnalisée. L’archive est incluse dans le package `adobe-aemfd-forms-app-src-pkg-<version>.zip`, disponible sur la Distribution logicielle.

Pour télécharger le fichier `adobe-aemfd-forms-app-src-pkg-<version>.zip`, effectuez les étapes suivantes :

1. Ouvrez la [Distribution de logiciels](https://experience.adobe.com/downloads). Vous avez besoin d’un Adobe ID pour vous connecter à la Distribution de logiciels.
1. Sélectionnez **[!UICONTROL Adobe Experience Manager]** situé dans le menu d’en-tête.
1. Dans la section **[!UICONTROL Filtres]** :
   1. Sélectionnez **[!UICONTROL Forms]** dans la liste déroulante **[!UICONTROL Solution]**.
   2. Sélectionnez la version et le type du package. Vous pouvez également utiliser l’option **[!UICONTROL Rechercher des téléchargements]** pour filtrer les résultats.
1. Sélectionnez le nom de package applicable à votre système d’exploitation, sélectionnez **[!UICONTROL Accepter les conditions du CLUF]**, puis sélectionnez **[!UICONTROL Télécharger]**.
1. Ouvrez [Package Manager](/help/sites-administering/package-manager.md) et cliquez sur **[!UICONTROL Télécharger le package]** pour télécharger le package.
1. Sélectionnez le package et cliquez sur **[!UICONTROL Installer]**.
1. Pour télécharger l’archive du code source, ouvrez **https://&lt;server>:&lt;port>/crx/de/content/forms/mobileapps/src/adobe-lc-mobileworkspace-src-&lt;version>.zip** dans votre navigateur. Le fichier .zip de l’application Android est téléchargé sur votre appareil.
1. Extrayez le contenu du fichier .zip dans un dossier de votre système de fichiers local. Par exemple, *C:\&lt;Folder Structure>\adobe-lc-mobileworkspace-src-2.4.20*.

L’image suivante affiche la structure du dossier `adobe-lc-mobileworkspace-src-<version>.zip\android`.

![structure_dossier_zip_android](assets/zip_android_folder_structure.png)

## Définir les variables d’environnement {#set-environment-variable-android}

Définissez les variables d’environnement suivantes avant de démarrer le processus de génération pour l’application AEM Forms :

* Définissez la variable d’environnement JAVA_HOME sur l’emplacement du logiciel JDK sur le système de fichiers local. Par exemple, C:\Program Files\Java\jdk1.8.0_181
* Définissez la variable d’environnement système `ANDROID_SDK_ROOT` sur l’emplacement du SDK pour Android. Par exemple, C:\Users\&amp;lt;username>\AppData\Local\Android\Sdk.
* Définissez la variable d’environnement système `Path` pour inclure les outils de la plateforme et les emplacements de dossier d’outils pour Android. Par exemple, C:\Users\&amp;lt;username>\AppData\Local\Android\Sdk\platform-tools et C:\Users\&amp;lt;username>\AppData\Local\Android\Sdk\tools.

## Génération d’une application AEM Forms standard {#set-up-the-xcode-project}

Une fois que vous avez enregistré le fichier adobe-lc-mobileworkspace-src-&lt;version>.zip sur le système de fichiers local et défini les variables d’environnement, créez l’application Android AEM Forms standard à l’aide de l’une des options suivantes :

* [Génération de l’application AEM Forms à l’aide d’Android Studio](#using-android-studio)
* [Génération du fichier .apk à l’aide d’Android Studio](#generate-apk-android-studio)

### Générer l’application AEM Forms à l’aide d’Android Studio {#using-android-studio}

Pour créer une application AEM Forms à l’aide d’Android Studio, procédez comme suit :

1. Lancez l’application Android Studio sur votre ordinateur.
1. Cliquez sur **Ouvrir un projet Android Studio existant**. Si la boîte de dialogue pour ouvrir un projet existant ne s’affiche pas automatiquement, sélectionnez **Fichier** > **Ouvrir**.
1. Accédez à *adobe-lc-mobileworkspace-src-&lt;version>.zip/android* sur le système de fichiers local et cliquez sur **OK**.

   L’option **android** s’affiche dans le volet de gauche.

   ![android_dossier_studio](assets/android_folder_studio.png)

1. Sélectionnez **Android** dans le volet de gauche, puis cliquez sur **Exécuter** > **Exécuter « Android »**.
1. Sélectionnez l’appareil Android dans la section Appareils connectés de la boîte de dialogue Sélectionner une cible de déploiement, puis cliquez sur OK.

   Une fois que vous avez généré l’environnement de développement, vous pouvez maintenant appliquer des personnalisations sur l’application. Utilisez les articles suivants pour personnaliser l’application :

   * [Personnalisation de l’identité graphique](/help/forms/using/branding-customization.md)
   * [Personnalisation du thème](/help/forms/using/theme-customization.md)
   * [Personnalisation de mouvement](/help/forms/using/gesture-customization.md)

   Après avoir appliqué les personnalisations appropriées à votre application, vous pouvez générer le fichier .apk pour le distribuer.

### Générez le fichier .apk à l’aide d’Android Studio {#generate-apk-android-studio}

Pour générer le fichier .apk à l’aide d’Android Studio, procédez comme suit :

1. Lancez l’application Android Studio sur votre ordinateur.
1. Sélectionnez **Ouvrir un projet Android Studio existant**. Si la boîte de dialogue pour ouvrir un projet existant ne s’affiche pas automatiquement, sélectionnez **Fichier** > **Ouvrir**.
1. Accédez à *adobe-lc-mobileworkspace-src-&lt;version>.zip/android* sur le système de fichiers local et cliquez sur **OK**.

   L’option android s’affiche dans le volet de gauche.

1. Pour générer le fichier .apk, sélectionnez **Créer** > **Créer l’APK**.

   (Facultatif) Sélectionnez **Générer** > **Générer un APK signé** pour générer une [version signée](https://developer.android.com/studio/publish/app-signing) du fichier .apk.

## Utilisation d’Android Debug Bridge {#build-android-debug-bridge}

Une fois le fichier .apk généré, exécutez la commande suivante pour installer l’application sur un appareil Android en utilisant [Android Debug Bridge](https://developer.android.com/tools/adb).

**Utilisateurs de Windows :** `adb install %HOMEPATH%\Projects\[your-project]\adobe-lc-mobileworkspace-src-[version]\android\build\outputs\apk\android-debug.apk`

**Utilisateurs et utilisatrices de Mac :** `adb install [User_Home]/Projects/[your-project]/adobe-lc-mobileworkspace-src-[version]/android/build/outputs/apk/android-debug.apk`
