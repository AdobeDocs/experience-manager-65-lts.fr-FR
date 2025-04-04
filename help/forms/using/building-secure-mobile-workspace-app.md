---
title: Création d’une application AEM Forms sécurisée pour iOS
description: Découvrez comment créer une application AEM Forms sécurisée pour iOS en archivant le projet Xcode. Cette action crée le programme d’installation (un fichier .ipa) et la liste des propriétés (un fichier .plist).
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-app
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
exl-id: 5cfb956a-454c-4bed-a410-003c716c46ed
source-git-commit: c3e9029236734e22f5d266ac26b923eafbe0a459
workflow-type: tm+mt
source-wordcount: '360'
ht-degree: 100%

---

# Création d’une application AEM Forms sécurisée pour iOS {#building-a-secure-aem-forms-app-for-ios}

Vous devez archiver le projet Xcode pour l’application AEM Forms afin de créer le programme d’installation (un fichier .ipa) et un fichier de liste de propriétés (un fichier .plist). Le fichier de liste de propriétés contient des informations de configuration de l’application interne hébergée, telles que le nom et l’emplacement d’hébergement de l’application. Pour plus d’informations sur le fichier de liste de propriétés, voir [À propos des fichiers de liste de propriétés d’informations](https://developer.apple.com/library/ios/#documentation/general/Reference/InfoPlistKeyReference/Articles/AboutInformationPropertyListFiles.html).

1. Connectez-vous au site Web suivant :

   [https://developer.apple.com/account/ios/identifier/bundle](https://developer.apple.com/account/ios/identifier/bundle)

1. Créez un ID d’application. Pour obtenir des instructions détaillées sur la création d’un ID d’application, voir [Création et configuration des ID d’application](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/MaintainingProfiles/MaintainingProfiles.html).
1. Pour configurer l’identifiant de bundle de l’application iOS pour votre application, cliquez sur **[!UICONTROL Configuration de l’ID d’application]**.
1. Au bas de la page web, sélectionnez **[!UICONTROL Activation pour la protection des données]**. Spécifiez les options de protection des données.

   Cliquez sur **[!UICONTROL Terminé]**.

1. Accédez à Approvisionnement > Distribution et créez un nouveau profil à l’aide de l’ID d’application configuré à l’étape 3.
1. Téléchargez le profil d’approvisionnement et ajoutez-le à Xcode et à l’iPad.
1. Ouvrez une session sur l’ordinateur Mac sur lequel Xcode et le SDK iOS sont installés et configurés.
1. Ouvrez le projet `AEM Forms.xcodeproj` dans Xcode.
1. Cliquez sur **[!UICONTROL AEM Forms]**, sous **[!UICONTROL TARGETS]**, sélectionnez **[!UICONTROL AEM Forms]**. Sélectionnez l’onglet **[!UICONTROL Paramètres de construction]**, recherchez la section **[!UICONTROL Droit de signature du code]**, puis dans la liste déroulante Droits, sélectionnez l’option **[!UICONTROL LC Enterprise]**.
1. Trouvez et ouvrez le fichier `LC Enterprise.entitlements` dans Xcode pour le modifier. Dans l’onglet **Droits XCode**, ajoutez la même paire de valeurs clés que dans vos profils d’approvisionnement.
1. Dans l’onglet **[!UICONTROL Paramètres de création]**, cliquez sur **[!UICONTROL Tous]** puis cliquez sur **[!UICONTROL Combiné]**.
1. Dans la liste **[!UICONTROL Paramètres]**, développez **[!UICONTROL Signature de code]**.
1. Pour **[!UICONTROL Identité de signature de code]**, sélectionnez la signature appropriée. Vérifiez que la même signature est sélectionnée pour **[!UICONTROL Débogage]**, **[!UICONTROL Version finale]** et **[!UICONTROL N’importe quel SDK iOS]**.
1. Dans la liste **[!UICONTROL PROJET]**, sélectionnez **[!UICONTROL AEM Forms]** et vérifiez que la signature adéquate est sélectionnée pour **[!UICONTROL Identité de signature de code]**, **[!UICONTROL Débogage]**, **[!UICONTROL Version]** et **[!UICONTROL N’importe quel SDK iOS]**.
1. Générer et distribuer une application AEM Forms. Pour obtenir des instructions détaillées sur la génération et la distribution d’une application AEM Forms, consultez [Générer le programme d’installation de l’application AEM Forms](setup-xcode-project-build-installer.md#build-the-installer-for-the-mobile-workspace-app).
