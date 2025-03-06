---
title: Activation de la détection des ressources en double
description: Découvrez comment activer la détection des ressources en double dans Experience Manager.
contentOwner: AG
role: User, Admin
feature: Asset Management,Asset Reports
hide: true
solution: Experience Manager, Experience Manager Assets
exl-id: ba54ecc2-a158-462a-8724-f6103b692edc
source-git-commit: c3e9029236734e22f5d266ac26b923eafbe0a459
workflow-type: tm+mt
source-wordcount: '165'
ht-degree: 100%

---

# Activation de la détection des ressources en double {#enable-detection-of-duplicate-assets}

Si vous essayez de charger une ressource qui existe dans [!DNL Adobe Experience Manager Assets], la fonctionnalité de détection des doublons l’identifie comme un doublon. Par défaut, la détection des doublons est désactivée. Pour activer la fonctionnalité, procédez comme suit :

1. Ouvrez la page d’[!DNL Experience Manager] de configuration de la console Web en accédant à `https://[aem_server]:[port]/system/console/configMgr`.
1. Modifiez la configuration du servlet **[!UICONTROL Ressource de création de gestion des ressources numériques Day CQ]**.
1. Sélectionnez l’option **[!UICONTROL Détecter les doublons]**, puis cliquez sur **[!UICONTROL Enregistrer]**.

   ![Sélection de l’option de détection des doublons dans le servlet](assets/chlimage_1-377.png)

   * : sélection de l’option de détection des doublons dans le servlet.*

La fonctionnalité de détection des doublons est maintenant activée dans [!DNL Assets]. Lorsqu’un utilisateur tente de charger un fichier qui existe dans [!DNL Experience Manager], le système recherche un éventuel conflit et le signale. Les ressources sont identifiées à l’aide du hachage SHA-1 stocké dans `jcr:content/metadata/dam:sha1`, ce qui signifie que les ressources en double sont détectées quels que soient les noms de fichiers.

>[!MORELIKETHIS]
>
>* [Duplication de ressources dans un référentiel existant (tutoriel d’un membre de la communauté)](https://experience-aem.blogspot.com/2019/06/aem-65-find-duplicate-assets-binaries-in-existing-repository.html)
>* [Détection des ressources en double dans AEM as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/assets/admin/detect-duplicate-assets.html?lang=fr)
