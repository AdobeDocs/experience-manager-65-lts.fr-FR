---
title: Utiliser les versions de page de contenu
description: Créez, comparez et restaurez des versions d'une page dans Adobe Experience Manager.
solution: Experience Manager, Experience Manager Sites
feature: Authoring
role: User,Admin,Architect,Developer
exl-id: ba5cc5fb-934f-4144-8e28-7aa5fdd9b92a
source-git-commit: 438d383aa7a08334d9977411fd37395f89133834
workflow-type: tm+mt
source-wordcount: '1567'
ht-degree: 100%

---

# Utilisation des versions de page{#working-with-page-versions}

Le contrôle de version permet de créer un « instantané » d’une page à un moment donné. Avec le contrôle de version, vous pouvez effectuer les opérations suivantes :

* Créez une version d’une page.
* Restaurer une version précédente d’une page. Par exemple :
   * pour annuler une modification que vous avez apportée à la page.
* Comparer la version actuelle d’une page à une version précédente :
   * pour mettre en évidence des différences dans le texte et les images.

>[!NOTE]
>
>Seul le contenu est versionné dans le référentiel AEM. Les ressources dynamiques telles que le code, la feuille de style CSS et le code JavaScript ne sont pas versionnées.
>
>* Lors de l’affichage des versions, le contenu est affiché avec le code, la feuille de style CSS et le code JavaScript actuels du référentiel.
>* Lors de la restauration de versions, seul le contenu est restauré et le code, la feuille de style CSS et le code JavaScript actuels du référentiel lui sont appliqués.

## Création d’une version {#creating-a-new-version}

Vous pouvez créer une version de votre ressource depuis :

* le [rail chronologie](#creating-a-new-version-timeline) ;
* l’option [Créer](#creating-a-new-version-create-with-a-selected-resource) (lorsqu’une ressource est sélectionnée).

### Création d’une version – Chronologie {#creating-a-new-version-timeline}

1. Accédez à la page pour laquelle créer une version.
1. Sélectionnez la page en [mode de sélection](/help/sites-authoring/basic-handling.md#viewing-and-selecting-resources).
1. Ouvrez la colonne **Chronologie**.
1. Cliquez sur la flèche près du champ de commentaire pour afficher les options :

   ![Chronologie - Enregistrer comme version](assets/screen-shot_2019-03-05at112335.png)

1. Sélectionnez **Enregistrer comme version**.
1. Saisissez un **Libellé** et un **Commentaire** si nécessaire.

   ![Créer une version - ajouter un libellé et un commentaire](assets/chlimage_1-42.png)

1. Confirmez la nouvelle version avec l’option **Créer**.

   Les informations dans la frise chronologique sont mises à jour pour indiquer la nouvelle version.

### Création d’une version – Création avec une ressource sélectionnée {#creating-a-new-version-create-with-a-selected-resource}

1. Accédez à la page pour laquelle créer une version.
1. Sélectionnez la page en [mode de sélection](/help/sites-authoring/basic-handling.md#viewing-and-selecting-resources).
1. Sélectionnez l’option **Créer** dans la barre d’outils pour ouvrir la boîte de dialogue.
1. Dans la boîte de dialogue, vous pouvez saisir un **libellé** et un **commentaire** si nécessaire.

   ![Saisir un libellé et un commentaire](assets/screen_shot_2012-02-15at105050am.png)

1. Confirmez la nouvelle version avec l’option **Créer**.

   La frise chronologique s’ouvre avec les informations mises à jour afin d’indiquer la nouvelle version.

## Rétablissement de versions {#reinstating-versions}

Une fois que vous avez créé une version de votre page, différentes méthodes permettent de rétablir une version antérieure :

* l’option **Revenir à cette version** depuis le rail [Chronologie](/help/sites-authoring/basic-handling.md#timeline)

  Rétablissez une version antérieure d’une page sélectionnée.

* les options **Restaurer** de la [barre d’outils d’actions](/help/sites-authoring/basic-handling.md#actions-toolbar) en haut de la page

   * **Restaurer la version**

     Rétablissez des versions de pages spécifiées dans le dossier actuellement sélectionné ; cela peut également inclure la restauration de pages qui ont été supprimées précédemment.

   * **Restaurer l’arborescence**

     Rétablissez une version d’une arborescence complète à une date et une heure spécifiées ; cela peut inclure des pages qui ont été supprimées précédemment.

>[!NOTE]
>
>Lors du rétablissement d’une page, la version créée fait partie d’une nouvelle branche.
>
>Illustration :
>
>1. Créez des versions d’une page.
>1. Les libellés et les noms de nœud de version initiaux sont 1.0, 1.1, 1.2, etc.
>1. Rétablissez la première version, soit, dans ce cas, 1.0.
>1. Créez à nouveau de nouvelles versions.
>1. Les libellés et noms de nœud générés sont désormais 1.0.0, 1.0.1, 1.0.2, etc.

### Rétablissement d’une version {#revert-to-a-version}

Pour **rétablir** la version précédente d’une page sélectionnée :

1. Naviguez pour afficher la page pour laquelle restaurer une ancienne version.
1. Sélectionnez la page en [mode de sélection](/help/sites-authoring/basic-handling.md#viewing-and-selecting-resources).
1. Ouvrez la colonne **Chronologie**, puis sélectionnez **Afficher tout** ou **Versions**. Les versions de la page sélectionnée sont répertoriées.
1. Sélectionnez la version à restaurer. Les options possibles s’affichent :

   ![Revenir à cette version](assets/screen-shot_2019-03-05at112505.png)

1. Sélectionnez **Revenir à cette version**. La version sélectionnée est restaurée et les informations de la chronologie sont mises à jour.

### Restaurer la version {#restore-version}

Cette méthode permet de rétablir des versions de pages spécifiées dans le dossier actuel ; cela peut également inclure la restauration de pages qui ont été supprimées précédemment :

1. Recherchez et [sélectionnez](/help/sites-authoring/basic-handling.md#viewing-and-selecting-resources) le dossier souhaité.

1. Sélectionnez **Restaurer**, puis **Restaurer la version** dans la [barre d’outils d’actions](/help/sites-authoring/basic-handling.md#actions-toolbar) en haut de la page.

   >[!NOTE]
   >
   >Si :
   >
   >* vous avez sélectionné une seule page, qui n’a jamais eu de page enfant,
   >* ou aucune des pages du dossier ne comporte de version,
   >
   >l’affichage sera vide, car aucune version n’est applicable.

1. Les versions disponibles sont répertoriées :

   ![Restaurer la version : liste de toutes les pages dans le dossier](/help/sites-authoring/assets/versions-restore-version-01.png)

1. Pour une page spécifique, utilisez le sélecteur déroulant sous **RESTAURER VERS LA VERSION** pour sélectionner la version requise pour cette page.

   ![Restaurer la version – Sélectionner la version](/help/sites-authoring/assets/versions-restore-version-02.png)

1. Dans l’affichage principal, sélectionnez la page à restaurer :

   ![Restaurer la version – Sélectionner la page](/help/sites-authoring/assets/versions-restore-version-03.png)

1. Sélectionnez **Restaurer** pour la version sélectionnée de la page sélectionnée à restaurer en tant que version actuelle.

>[!NOTE]
>
>L’ordre dans lequel vous sélectionnez une page requise et la version associée est interchangeable.

### Restaurer l’arborescence {#restore-tree}

Cette méthode permet de restaurer une version d’une arborescence à une date et une heure spécifiées ; cela peut inclure des pages qui ont été supprimées précédemment :

1. Recherchez et [sélectionnez](/help/sites-authoring/basic-handling.md#viewing-and-selecting-resources) le dossier souhaité.

1. Sélectionnez **Restaurer**, puis **Restaurer l’arborescence** dans la [barre d’outils d’actions](/help/sites-authoring/basic-handling.md#actions-toolbar) en haut de la page. La dernière version de l’arborescence apparaît :

   ![Restaurer l’arborescence](/help/sites-authoring/assets/versions-restore-tree-02.png)

1. Utilisez le sélecteur de date et d’heure dans **Dernières versions en date** pour sélectionner une autre version de l’arborescence : celle qui doit être restaurée.

1. Définissez l’indicateur **Pages non versionnées préservées** selon les besoins :

   * Si cette option est active (sélectionnée), toute page non versionnée est conservée et n’est pas concernée par la restauration.

   * Si elle est inactive (non sélectionnée), toute page non versionnée est supprimée, car elle n’existait pas dans l’arborescence versionnée.

1. Sélectionnez **Restaurer** pour la version sélectionnée de l’arborescence à restaurer comme version *actuelle*.

## Aperçu d’une version {#previewing-a-version}

Vous pouvez prévisualiser une version spécifique :

1. Accédez à la page que vous souhaitez comparer.
1. Sélectionnez la page en [mode de sélection](/help/sites-authoring/basic-handling.md#viewing-and-selecting-resources).
1. Ouvrez la colonne **Chronologie**, puis sélectionnez **Afficher tout** ou **Versions**.
1. Les versions de page sont répertoriées. Sélectionnez la version que vous souhaitez prévisualiser :

   ![Sélectionner la version à prévisualiser](assets/screen-shot_2019-03-05at112505-1.png)

1. Sélectionnez **Aperçu**. La page s’affiche dans un nouvel onglet.

   >[!CAUTION]
   >
   >Si une page a été déplacée, vous ne pouvez plus afficher l’aperçu des versions antérieures au déplacement.
   >
   >* Si vous rencontrez des problèmes avec un aperçu, vérifiez la variable [Frise chronologique](/help/sites-authoring/basic-handling.md#timeline) de la page afin de voir si la page a été déplacée.

## Comparaison d’une ancienne version avec la page actuelle {#comparing-a-version-with-current-page}

Pour comparer une version précédente à la page actuelle :

1. Accédez à la page que vous souhaitez comparer.
1. Sélectionnez la page en [mode de sélection](/help/sites-authoring/basic-handling.md#viewing-and-selecting-resources).
1. Ouvrez la colonne **Chronologie**, puis sélectionnez **Afficher tout** ou **Versions**.
1. Les versions de page sont répertoriées. Sélectionnez la version que vous souhaitez comparer :

   ![Versions de page répertoriées - sélectionner la version](assets/screen-shot_2019-03-05at112505-2.png)

1. Sélectionner **Comparer avec la version actuelle**. L’[outil de comparaison des pages](/help/sites-authoring/page-diff.md) s’ouvre et affiche les différences.

## Distorsion du temps Timewarp {#timewarp}

La fonction de distorsion du temps Timewarp permet de simuler l’état *publié* d’une page à des moments spécifiques dans le passé.

>[!TIP]
>
>[La fonction de distorsion du temps peut également être utilisée avec les lancements pour prévisualiser les futurs ](/help/sites-authoring/launches.md) lors de l’exécution d’AEM 6.5.10.0 ou version ultérieure.

La création de contenu est un processus continu et collaboratif. Le but de Timewarp est de permettre aux auteurs et aux autrices de suivre le site web publié au fil du temps, pour les aider à comprendre les changements du contenu. Cette fonctionnalité utilise les versions de page pour déterminer l’état de l’environnement de publication :

* Le système recherche la version de page qui était active à l’heure sélectionnée.
   * Cette version de page a été créée/activée *avant* le moment sélectionné dans Timewarp.
* Si vous accédez à une page qui a été supprimée, celle-ci sera également affichée, à condition toutefois que ses anciennes versions soient toujours disponibles dans le référentiel.
* Si aucune version publiée n’a été trouvée, Timewarp revient à l’état actuel de la page dans l’environnement de création (et ce, afin d’éviter une erreur/page 404 qui rendrait impossible la navigation).

### Utilisation de Timewarp {#using-timewarp}

Timewarp est un [mode](/help/sites-authoring/author-environment-tools.md#page-modes) de l’éditeur de page. Pour le démarrer, il vous suffit de l’activer comme vous le feriez pour tout autre mode.

1. Démarrez l’éditeur de la page sur laquelle vous souhaitez démarrer Timewarp, puis sélectionnez **Timewarp** dans la sélection de mode.

   ![Sélectionner Timewarp dans la sélection du mode](assets/wwpv-01.png)

1. Dans la boîte de dialogue, définissez une date et une heure cibles, puis cliquez sur **Définir la date**. Si vous ne sélectionnez pas d’heure, l’heure actuelle est utilisée par défaut.

   ![Définir la date](assets/wwpv-02.png)

1. La page s’affiche en fonction de la date définie. Le mode Timewarp est indiqué à partir de la barre d’état bleue située en haut de la fenêtre. Utilisez les liens de la barre d’état pour sélectionner une nouvelle date cible ou quitter le mode Timewarp.

   ![Indicateur Timewarp](assets/wwpv-03.png)

### Limites du mode Timewarp {#timewarp-limitations}

Timewarp s’efforce de reproduire au mieux une page à un moment donné. Toutefois, en raison de la complexité de la création continue de contenu dans AEM, cela n’est pas toujours possible. Ces restrictions doivent être prises en compte lors de l’utilisation de Timewarp.

* **Timewarp fonctionne sur la base de pages publiées** : toutes les fonctionnalités de Timewarp ne sont disponibles que si vous avez publié la page précédemment. Dans le cas contraire, Timewarp affiche la page actuelle dans l’environnement de création.
* **Timewarp utilise des versions de page** : si vous accédez à une page qui a été supprimée du référentiel, elle s’affiche correctement si d’anciennes versions sont toujours disponibles dans le référentiel.
* **Les versions supprimées affectent Timewarp** : si des versions sont supprimées du référentiel, Timewarp n’est pas en mesure d’afficher la vue correcte.

* **Timewarp est en lecture seule** : vous ne pouvez pas modifier l’ancienne version de la page. Elle est disponible uniquement à des fins d’affichage. Si vous souhaitez restaurer l’ancienne version, vous devrez procéder manuellement à l’aide de la fonction [Restaurer](#reverting-to-a-page-version).

* **Timewarp est basé uniquement sur le contenu de page** : si des éléments destinés au rendu du site web ont été modifiés, la vue est différente de ce qu’elle était initialement, étant donné que ces éléments n’ont pas de suivi de version dans le référentiel. Ces éléments incluent le code, les éléments CSS et les ressources/images, entre autres.

>[!CAUTION]
>
>Timewarp est un outil conçu pour aider les auteurs à comprendre et à créer du contenu. Il ne s’agit pas d’un journal d’audit et il n’est pas destiné à des fins juridiques.
