---
title: Activer le bouton (bascule) de fonctionnalités pour intégrer les fonctionnalités destinées aux utilisateurs et utilisatrices précoces et en version préliminaire
description: Le bouton (bascule) des fonctionnalités est une fonctionnalité d’AEM qui permet aux administrateurs d’activer de nouvelles fonctionnalités dans un environnement d’exécution.
feature: Adaptive Forms, Foundation Components
role: User, Developer
hidefromtoc: true
source-git-commit: 1444b0fc0811cbb187d2a4d83b626444e44ef73f
workflow-type: tm+mt
source-wordcount: '293'
ht-degree: 8%

---

# Basculement de fonctionnalité dans Adobe Experience Manager (AEM) 6.5{#enable-feature-toggle-aem-forms-65}

Le bouton (bascule) des fonctionnalités est une fonctionnalité d’AEM qui permet aux administrateurs d’activer ou de désactiver des fonctionnalités spécifiques de manière dynamique. Cette fonctionnalité est particulièrement utile pour gérer les **fonctionnalités destinées aux utilisateurs et utilisatrices précoces** et **fonctionnalités de version préliminaire** sans nécessiter de déploiements ou de modifications majeurs de la base de code. Elle offre flexibilité et contrôle sur les fonctionnalités accessibles dans un environnement AEM.

## Bouton (bascule) Activer la fonction {#enable-feature-toggle-65}

Les basculements de fonctionnalités pour les utilisateurs et utilisatrices précoces ou les nouvelles fonctionnalités peuvent être configurés via la **console web d’AEM** en suivant les étapes ci-dessous :

1. Connectez-vous à l’instance AEM Forms.
2. Accédez à `http://<author-instance-url>:portnumber/system/console/configMgr`.
3. Recherchez **Fournisseur de basculement dynamique Adobe Granite** dans le gestionnaire de configuration.
4. Cliquez sur l’icône ![icône-crayon](assets/illustratorcc_penciltool_cur_edit_2_17.png).
5. Dans la section [!UICONTROL Activation des bascules], cliquez sur ![icône-crayon](assets/aem6forms_add.png).
6. Ajoutez l’ID de basculement de la fonctionnalité, comme illustré dans l’image ci-dessous.
   ![Ajouter un bouton](assets/add_toggle_number_forms.png)

   >[!NOTE]
   >
   >Vous trouverez l’ID de basculement de fonction dans le document spécifique aux fonctions destinées aux utilisateurs et utilisatrices précoces.

7. Cliquez sur Enregistrer.

## Désactiver le bouton (bascule) des fonctionnalités {#disable-feature-toggle-65}

Pour désactiver la ou les fonctionnalités dont le ou les boutons d’activation sont activés, procédez comme suit :

1. Connectez-vous à l’instance AEM Forms.
2. Accédez à `http://<author-instance-url>:portnumber/system/console/configMgr`.
3. Recherchez **Fournisseur de basculement dynamique Adobe Granite** dans le gestionnaire de configuration.
4. Cliquez sur l’icône ![icône-crayon](assets/illustratorcc_penciltool_cur_edit_2_17.png).
5. Dans la section [!UICONTROL Activation/désactivation des bascules], cliquez sur ![icône-crayon](assets/aem6forms_add.png).
6. Ajoutez le numéro du bouton (bascule) de la fonction à désactiver.
   ![Supprimer le bouton bascule](assets/remove_toggle_feature_forms.png)
7. Cliquez sur Enregistrer.

## Considérations Techniques

Les bascules de fonctionnalités sont spécifiques à un environnement et sont gérées au moment de l’exécution. Il n’est donc pas nécessaire de redémarrer le serveur. Cependant, certaines fonctionnalités peuvent nécessiter d’actualiser les pages appropriées ou d’effacer le cache pour refléter les modifications.
Vous pouvez accéder à la liste des fonctionnalités activées par le biais du bouton (bascule) des fonctionnalités pour votre environnement via `http://<author-instance-url>:4502/etc.clientlibs/toggles.json`.
