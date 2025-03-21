---
title: Création de projets de traduction pour des fragments de contenu
description: Découvrez comment traduire du contenu dans Adobe Experience Manager.
contentOwner: AEM Docs
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
topic-tags: managing-assets
content-type: reference
feature: Content Fragments
role: User, Admin
solution: Experience Manager, Experience Manager Assets
exl-id: cad7253d-95fb-47eb-b1c9-2d22a9e34481
source-git-commit: c3e9029236734e22f5d266ac26b923eafbe0a459
workflow-type: tm+mt
source-wordcount: '984'
ht-degree: 100%

---

# Création de projets de traduction pour des fragments de contenu {#creating-translation-projects-for-content-fragments}

Outre les ressources, Adobe Experience Manager (AEM) Assets prend en charge les workflow de copie de langue pour les [fragments de contenu](/help/assets/content-fragments/content-fragments.md) (y compris les variations). Aucune optimisation supplémentaire n’est nécessaire pour exécuter des workflows de copie de langue sur des fragments de contenu. Dans chaque workflow, l’intégralité du fragment de contenu est envoyée pour traduction.

Les types de workflows que vous pouvez exécuter sur des fragments de contenu sont exactement similaires aux types de workflows que vous exécutez pour les ressources. En outre, les options disponibles dans chaque type de workflow correspondent aux options disponibles sous les types de workflow correspondants pour les ressources.

Vous pouvez exécuter les types de workflows de copie de langue suivants sur les fragments de contenu :

**Créer et traduire**

Dans ce workflow, les fragments de contenu à traduire sont copiés dans la racine de la langue vers laquelle vous souhaitez effectuer la traduction. En outre, en fonction des options que vous choisissez, un projet de traduction est créé pour les fragments de contenu dans la console Projets. Selon les paramètres, le projet de traduction peut être démarré manuellement ou exécuté automatiquement dès sa création.

**Mise à jour des copies de langue**

Lorsque le fragment de contenu source est mis à jour ou modifié, le fragment de contenu correspondant spécifique à la langue/aux paramètres régionaux doit être retraduit. Le workflow de mise à jour des copies de langue traduit un groupe de fragments de contenu supplémentaire et l’intégre à une copie de langue pour des paramètres régionaux spécifiques. Dans ce cas, les fragments de contenu traduits sont ajoutées au dossier cible qui contient déjà des fragments de contenu précédemment traduits.

## Workflow Créer et traduire {#create-and-translate-workflow}

Le workflow de création et de traduction des copies de langue comprend les options suivantes. Les étapes de procédure associées à chaque option sont similaires aux étapes de procédure associées à l’option correspondante pour les ressources.

* Créer uniquement la structure : pour les étapes de la procédure, reportez-vous à [Création de structure uniquement pour les ressources](translation-projects.md#create-structure-only).
* Créer un projet de traduction : pour les étapes de la procédure, reportez-vous à [Créer un projet de traduction pour les ressources](translation-projects.md#create-a-new-translation-project).
* Ajouter à un projet de traduction existant : pour les étapes de la procédure, reportez-vous à [Ajout à un projet de traduction existant pour les ressources.](translation-projects.md#add-to-existing-translation-project)

## Workflow de mise à jour des copies de langue {#update-language-copies-workflow}

Le processus de mise à jour des copies de langue comprend les options suivantes. Les étapes de procédure associées à chaque option sont similaires aux étapes de procédure associées à l’option correspondante pour les ressources.

* Créer un projet de traduction : pour les étapes de cette procédure, consultez [Créer un projet de traduction pour les ressources](translation-projects.md#create-a-new-translation-project) (workflow de mise à jour).
* Ajouter à un projet de traduction existant : pour les étapes de la procédure, reportez-vous à [Ajout à un projet de traduction existant pour les ressources](translation-projects.md#add-to-existing-translation-project) (workflow de mise à jour).

Vous pouvez également créer des copies de langue temporaires pour les fragments de la même manière que vous créez des copies temporaires pour les ressources. Pour plus d’informations, voir [Création de copies de langue temporaires pour les ressources](translation-projects.md#creating-temporary-language-copies).

## Traduction de fragments de supports variés {#translating-mixed-media-fragments}

AEM vous permet de traduire des fragments de contenu qui incluent divers types de ressources et collections multimédia. Si vous traduisez un fragment de contenu qui comprend des ressources intégrées, les copies traduites de ces ressources sont stockées dans la racine de la langue cible.

Si le fragment de contenu inclut une collection, les ressources de la collection sont traduites avec le fragment de contenu. Les copies traduites des ressources sont stockées à la racine de la langue cible appropriée à un emplacement correspondant à l’emplacement physique des ressources source dans la racine de la langue source.

Pour pouvoir traduire des fragments de contenu contenant des supports variés, modifiez d’abord le framework de traduction par défaut afin de permettre la traduction des ressources et collections intégrées associées aux fragments de contenu.

1. Cliquez sur le logo AEM et accédez à **[!UICONTROL Outils > Déploiement > Services Cloud]**.
1. Localisez **[!UICONTROL Intégration de traduction]** sous **[!UICONTROL Adobe Marketing Cloud]**, puis cliquez sur **[!UICONTROL Afficher les configurations]**.

   ![chlimage_1-444](assets/chlimage_1-444.png)

1. Dans la liste des configurations disponibles, cliquez sur **[!UICONTROL Configuration par défaut (configuration de l’intégration de traduction)]** afin d’ouvrir la page **[!UICONTROL Configuration par défaut]**.

   ![chlimage_1-445](assets/chlimage_1-445.png)

1. Cliquez sur le bouton **[!UICONTROL Modifier]** de la barre d’outils afin d’afficher la boîte de dialogue **[!UICONTROL Configuration de traduction]**.

   ![chlimage_1-446](assets/chlimage_1-446.png)

1. Accédez à l’onglet **[!UICONTROL Ressources]** et sélectionnez **[!UICONTROL Ressources multimédias intégrées et collections associées]** dans la liste **[!UICONTROL Traduire des ressources de fragments de contenu]**. Pour enregistrer les modifications, cliquez sur **[!UICONTROL OK]**.

   ![chlimage_1-447](assets/chlimage_1-447.png)

1. Depuis le dossier racine Anglais, ouvrez un fragment de contenu.

   ![chlimage_1-448](assets/chlimage_1-448.png)

1. Cliquez sur l’icône **[!UICONTROL Insérer une ressource]**.

   ![chlimage_1-449](assets/chlimage_1-449.png)

1. Insérez une ressource dans le fragment de contenu.

   ![insérer une ressource dans le fragment de contenu](assets/column-view.png)

1. Cliquez sur l’icône **[!UICONTROL Associer le contenu]**.

   ![chlimage_1-451](assets/chlimage_1-451.png)

1. Cliquez sur **[!UICONTROL Associer le contenu]**.

   ![chlimage_1-452](assets/chlimage_1-452.png)

1. Sélectionnez une collection et incluez-la dans le fragment de contenu. Cliquez sur **[!UICONTROL Enregistrer]**.

   ![chlimage_1-453](assets/chlimage_1-453.png)

1. Sélectionnez le fragment de contenu, puis cliquez sur l’icône **[!UICONTROL Navigation globale]**.
1. Sélectionnez **[!UICONTROL Références]** dans le menu pour afficher le volet **[!UICONTROL Références]**.

   ![chlimage_1-454](assets/chlimage_1-454.png)

1. Cliquez sur **[!UICONTROL Copies de langue]** sous **[!UICONTROL Copies]** afin d’afficher les copies de langue.

   ![chlimage_1-455](assets/chlimage_1-455.png)

1. Cliquez sur **[!UICONTROL Créer et traduire]** en bas du panneau pour afficher la boîte de dialogue **[!UICONTROL Créer et traduire]**.

   ![chlimage_1-456](assets/chlimage_1-456.png)

1. Sélectionnez la langue cible dans la liste **[!UICONTROL Langues cible]**.

   ![chlimage_1-457](assets/chlimage_1-457.png)

1. Sélectionnez le type de projet de traduction dans la liste **[!UICONTROL Projet]**.

   ![chlimage_1-458](assets/chlimage_1-458.png)

1. Indiquez le titre du projet dans la boîte de dialogue **[!UICONTROL Titre du projet]**, puis cliquez sur **Créer**.

   ![chlimage_1-459](assets/chlimage_1-459.png)

1. Accédez à la console **[!UICONTROL Projets]**, puis ouvrez le dossier du projet de traduction que vous avez créé.

   ![chlimage_1-460](assets/chlimage_1-460.png)

1. Cliquez sur la mosaïque du projet pour ouvrir la page Détails du projet.

   ![chlimage_1-461](assets/chlimage_1-461.png)

1. Dans la mosaïque Tâche de traduction, vérifiez le nombre de ressources à traduire.
1. Dans la mosaïque **[!UICONTROL Tâche de traduction]**, démarrez la tâche de traduction.

   ![chlimage_1-462](assets/chlimage_1-462.png)

1. Cliquez sur les ellipses en bas de la mosaïque Tâche de traduction afin d’afficher le statut de la tâche de traduction.

   ![chlimage_1-463](assets/chlimage_1-463.png)

1. Cliquez sur le fragment de contenu pour vérifier le chemin d’accès des ressources associées traduites.

   ![chlimage_1-464](assets/chlimage_1-464.png)

1. Examinez la copie de langue pour la collection dans la console Collections.

   ![chlimage_1-465](assets/chlimage_1-465.png)

   Notez que seul le contenu de la collection est traduit. La collection elle-même n’est pas traduite.

1. Accédez au chemin d’accès de la ressource associée traduite. Vérifiez que la ressource traduite est stockée à la racine de la langue cible.

   ![chlimage_1-466](assets/chlimage_1-466.png)

1. Accédez aux ressources de la collection qui sont traduites avec le fragment de contenu. Vérifiez que les copies traduites des ressources sont stockées à la racine de la langue cible appropriée.

   ![chlimage_1-467](assets/chlimage_1-467.png)

   >[!NOTE]
   >
   >Les procédures d’ajout d’un fragment de contenu à un projet existant ou d’exécution de workflows de mise à jour sont similaires aux procédures correspondantes pour les ressources. Pour plus d’informations sur ces procédures, voir les procédures décrites pour les ressources.
