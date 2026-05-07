---
title: Activer la fonction d’activation/désactivation des fonctionnalités pour intégrer les fonctionnalités destinées aux utilisateurs et utilisatrices précoces et en version préliminaire
description: La fonction d’activation/désactivation des fonctionnalités est une fonctionnalité d’AEM qui permet aux administrateurs et administratrices d’activer de nouvelles fonctionnalités dans un environnement d’exécution.
feature: Adaptive Forms, Foundation Components
role: User, Developer
exl-id: 8b6dea41-540b-498a-b52b-e584a9255f25
source-git-commit: 26f8a32961cf18c2f1930ab7bc910333b3ccf188
workflow-type: tm+mt
source-wordcount: '298'
ht-degree: 100%

---

# Fonction d’activation/désactivation des fonctionnalités dans Adobe Experience Manager (AEM) 6.5{#enable-feature-toggle-aem-forms-65}

La fonction d’activation/désactivation des fonctionnalités est une fonctionnalité d’AEM qui permet aux administrateurs et aux administratrices d’activer ou de désactiver des fonctionnalités spécifiques de manière dynamique. Cette fonctionnalité est particulièrement utile pour gérer les **fonctionnalités destinées aux utilisateurs et utilisatrices précoces** et les **fonctionnalités de version préliminaire** sans nécessiter de déploiements ou de modifications importants de la base du code. Elle offre de la flexibilité et du contrôle sur les fonctionnalités accessibles dans un environnement AEM.

## Bouton (bascule) Activer la fonction {#enable-feature-toggle-65}

La fonction d’activation/désactivation des fonctionnalités pour les utilisateurs et les utilisatrices précoces ou pour les nouvelles fonctionnalités peut être configurée via la **console web d’AEM** en suivant les étapes ci-dessous :

1. Connectez-vous à votre instance AEM Forms.
2. Accédez à `http://<author-instance-url>:portnumber/system/console/configMgr`.
3. Recherchez **Fournisseur de fonction bascule dynamique Adobe Granite** dans le gestionnaire de configuration.
4. Cliquez sur l’icône ![icône-de-crayon](assets/illustratorcc_penciltool_cur_edit_2_17.png).
5. Dans la section [!UICONTROL Fonctions bascules activées], cliquez sur ![icône-de-crayon](assets/aem6forms_add.png).
6. Ajoutez l’identifiant du bouton d’activation de fonctionnalités, comme illustré dans l’image ci-dessous.
   ![Ajouter une fonction bascule](assets/add_toggle_number_forms.png)

   >[!NOTE]
   >
   >Vous trouverez l’identifiant de la fonction d’activation/désactivation des fonctionnalités dans le document spécifique aux fonctions destinées aux utilisateurs et aux utilisatrices précoces.

7. Cliquez sur Enregistrer.

## Désactiver la fonction d’activation/désactivation des fonctionnalités {#disable-feature-toggle-65}

Pour désactiver la fonction d’activation/désactivation des fonctionnalités pour les fonctionnalités sur lesquelles celle-ci est activée, procédez comme suit :

1. Connectez-vous à votre instance AEM Forms.
2. Accédez à `http://<author-instance-url>:portnumber/system/console/configMgr`.
3. Recherchez **Fournisseur de fonction bascule dynamique Adobe Granite** dans le gestionnaire de configuration.
4. Cliquez sur l’icône ![icône-de-crayon](assets/illustratorcc_penciltool_cur_edit_2_17.png).
5. Dans la section [!UICONTROL Fonctions bascules désactivées], cliquez sur ![icône-de-crayon](assets/aem6forms_add.png).
6. Ajoutez le numéro de la fonction bascule pour désactiver la fonction.
   ![Supprimer la fonction bascule](assets/remove_toggle_feature_forms.png)
7. Cliquez sur Enregistrer.

## Considérations techniques

Les fonctions d’activation/désactivation de fonctionnalités sont spécifiques à un environnement et sont gérées au moment de l’exécution. Il n’est donc pas nécessaire de redémarrer le serveur. Cependant, certaines fonctionnalités peuvent nécessiter d’actualiser les pages concernées ou d’effacer le cache pour refléter les modifications.
Vous pouvez accéder à la liste des fonctionnalités activées par le biais de la fonction d’activation/désactivation des fonctionnalités pour votre environnement via `http://<author-instance-url>:4502/etc.clientlibs/toggles.json`.
