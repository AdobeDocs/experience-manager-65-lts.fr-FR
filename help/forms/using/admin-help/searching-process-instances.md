---
title: Rechercher des instances de processus
description: Utilisez la page Recherche de processus pour saisir les critères de recherche permettant de trouver une instance de processus.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_forms_workflow
products: SG_EXPERIENCEMANAGER/6.5/FORMS
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
hide: true
hidefromtoc: true
exl-id: e358ee51-c23f-4737-9dcf-3193ed541bbb
source-git-commit: 51342861dd01e659999c19fbe0274e8d3cbcf8c4
workflow-type: tm+mt
source-wordcount: '458'
ht-degree: 66%

---

# Rechercher des instances de processus{#searching-for-process-instances}

>[!NOTE]
> 
> Vérifiez que l’utilisateur ou l’utilisatrice dispose de droits d’administration pour accéder à la console d’administration.

Utilisez la page Recherche de processus pour saisir les critères de recherche permettant de trouver une instance de processus. Vous pouvez accéder à la page Rechercher un processus à partir de la page Forms Workflow . Vous pouvez également cliquer sur **Rechercher** sur la page Instance de processus.

Vous pouvez saisir des critères de base pour effectuer une recherche générale, des attributs spécifiques pour effectuer une recherche détaillée ou une combinaison de critères de base et d’attributs spécifiques pour effectuer une recherche combinée.

## Exécution d’une recherche générale {#perform-a-general-search}

Une recherche générale de processus est plus appropriée si vous connaissez l’ID de processus de l’instance de processus. Ou, si vous recherchez un groupe d’instances de processus associées ou si seulement quelques instances de processus sont en cours d’exécution.

Saisissez les critères de base pour effectuer une recherche générale. Si vous saisissez plusieurs critères, la recherche est effectuée avec une condition ET implicite.

1. Dans la console d’administration, cliquez sur Services > Forms Workflow > Recherche de processus.
1. Sur la page Recherche de processus, sous Recherche générale, fournissez les critères suivants :

   * **ID du processus :** entier positif qui identifie chaque instance de processus unique.
   * **Etat du processus :** sélectionnez un état dans la liste.
   * **Application :** sélectionnez une application dans la liste. Seules les applications déployées sont affichées.
   * **Nom du processus - Version :** sélectionnez un nom de processus dans le menu. Seuls les processus déployés sont affichés.

1. Cliquez sur **Rechercher**. La page Instance de processus s’affiche, répertoriant les instances trouvées.

## Exécution d’une recherche de processus détaillée {#perform-a-detailed-search-for-a-process}

Vous pouvez saisir des attributs spécifiques pour effectuer une recherche détaillée. Une recherche détaillée est plus appropriée si de nombreuses instances de processus sont en cours d’exécution et que vous devez limiter les résultats possibles en fonction de certains critères.

1. Dans la console d’administration, cliquez sur Services > Forms Workflow > Recherche de processus.
1. Sur la page Recherche de processus, sous Recherche détaillée, spécifiez votre premier jeu de critères :

   * Dans la liste Attribut, sélectionnez un attribut.
   * Dans la liste Filtre, sélectionnez un opérateur.
   * Dans la zone Valeur, saisissez une valeur appropriée pour l’attribut que vous avez sélectionné.

1. Pour ajouter une ligne, sélectionnez Plus de filtres. Un autre ensemble de listes Attribut, Filtre et Valeur s’affiche, avec une liste Condition.
1. Sous Condition, sélectionnez ET ou OU. Répétez les étapes 1 à 3 selon les besoins pour limiter davantage votre recherche.
1. Pour ajouter ou supprimer des lignes, cliquez sur Plus de filtres ou Moins de filtres. Vous pouvez utiliser entre une et quatre lignes.
1. Cliquez sur **Rechercher**. La page Instance de processus s’affiche, répertoriant les instances trouvées.

Voir aussi [À propos des statuts des instances de processus](/help/forms/using/admin-help/processes.md#about-process-instance-statuses).

## Exécution d’une recherche de processus combinée {#perform-a-combined-search-for-a-process}

Pour créer une recherche qui utilise à la fois des critères généraux et détaillés, saisissez des valeurs dans les deux zones de la page Recherche de processus . Le système applique une `AND` implicite entre les deux zones.

Si la recherche est trop étroite, aucune instance n’est trouvée.
