---
title: Publier des pages
description: Une fois que vous avez créé et révisé votre contenu dans l’environnement de création, rendez-le disponible sur votre site web public.
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: page-authoring
content-type: reference
docset: aem65
solution: Experience Manager, Experience Manager Sites
feature: Authoring
role: User
exl-id: 20aea30b-9cfe-45c1-aa8d-08085f8e3e7d
source-git-commit: c3e9029236734e22f5d266ac26b923eafbe0a459
workflow-type: tm+mt
source-wordcount: '1028'
ht-degree: 100%

---

# Publier des pages{#publishing-pages}

Une fois le contenu créé et révisé dans l’environnement de création, rendez-le disponible sur votre site web public (votre environnement de publication).

On parle alors de publication d’une page. Lorsque vous souhaitez supprimer une page de l’environnement de publication, on parle de dépublication. Lorsque vous publiez et dépubliez, la page reste disponible dans l’environnement de création pour d’autres modifications jusqu’à ce que vous la supprimiez.

Vous pouvez publier/dépublier une page tout de suite ou à une date/heure postérieures prédéfinies.

>[!NOTE]
>
>Certains termes liés à la publication peuvent être déroutants :
>
>* **Publier/dépublier**
>  Termes principalement utilisés pour évoquer les opérations qui rendent votre contenu publiquement accessible dans votre environnement de publication (ou non).
>
>* **Activer/Désactiver**
>  Ces termes sont synonymes de publication/dépublication.
>
>* **Répliquer/Réplication**
>  Termes techniques indiquant le déplacement des données (contenu de la page, fichiers, code et commentaires de l’utilisateur, par exemple) d’un environnement à un autre ; lors de la publication ou de la réplication inverse des commentaires utilisateur, par exemple.
>

>[!NOTE]
>
>Si vous ne disposez pas des privilèges requis pour publier une page spécifique :
>
>* Un workflow sera déclenché pour informer la personne appropriée de votre demande de publication.
>* Un message s’affichera (pendant une courte période) pour vous en informer.
>

## Publier une page {#publishing-a-page}

Il existe deux méthodes pour activer une page :

* [depuis la console Sites web ;](#activating-a-page-from-the-websites-console)
* [depuis le sidekick sur la page elle-même.](#activating-a-page-from-sidekick)

>[!NOTE]
>
>Vous pouvez également activer une sous-arborescence de plusieurs pages à l’aide de l’option [Activer l’arborescence](#howtoactivateacompletesectiontreeofyourwebsite) sur la console Outils.

### Activer une page à partir de la console Sites web {#activating-a-page-from-the-websites-console}

Vous pouvez activer des pages dans la console Sites web. Après avoir ouvert une page et modifié son contenu, revenez à la console Sites web :

1. Dans la console Sites web, sélectionnez la page à activer.
1. Sélectionner **Activer**, dans le menu supérieur ou dans le menu déroulant de l’élément de page sélectionné.

   Pour activer le contenu de la page et toutes ses pages secondaires, utilisez la console [**Outils**](/help/sites-classic-ui-authoring/classic-page-author-publish-pages.md#howtoactivateacompletesectiontreeofyourwebsite).

   ![screen_shot_2012-02-08at13817pm](assets/screen_shot_2012-02-08at13817pm.png)

   >[!NOTE]
   >
   >Si nécessaire, AEM demande d’activer ou de réactiver les ressources liées à la page. Vous pouvez cocher ou décocher les cases pour activer ces ressources.
   >
   >

1. Si nécessaire, AEM demande d’activer ou de réactiver les ressources liées à la page. Vous pouvez cocher ou décocher les cases pour activer ces ressources.

   ![chlimage_1-100](assets/chlimage_1-100.png)

1. La gestion du contenu web d’AEM active le contenu sélectionné. La ou les pages publiées s’affichent dans la [console Sites web](/help/sites-classic-ui-authoring/author-env-basic-handling.md#page-information-on-the-websites-console) (en vert) avec des informations sur l’utilisateur ou l’utilisatrice qui a activé le contenu, ainsi que la date et l’heure d’activation.

   ![screen_shot_2012-02-08at14335pm](assets/screen_shot_2012-02-08at14335pm.png)

### Activer une page à partir du sidekick {#activating-a-page-from-sidekick}

Vous pouvez également activer une page lorsqu’elle est ouverte pour modification.

Après avoir ouvert la page et modifié son contenu, effectuez les actions suivantes :

1. Sélectionnez l’onglet **Page** dans le sidekick.
1. Cliquez sur **Activer la page**.
Un message s’affiche dans le coin supérieur droit de la fenêtre pour confirmer l’activation de la page.

## Annuler la publication d’une page {#unpublishing-a-page}

Pour supprimer une page de l’environnement de publication, désactivez son contenu.

Pour désactiver une page :

1. Dans la console Sites web, sélectionnez la page à désactiver.
1. Sélectionner **Désactiver**, dans le menu supérieur ou dans le menu déroulant de l’élément de page sélectionné. On vous invite à confirmer la suppression.

   ![screen_shot_2012-02-08at14859pm](assets/screen_shot_2012-02-08at14859pm.png)

1. Actualisez la [console Sites web](/help/sites-classic-ui-authoring/author-env-basic-handling.md#page-information-on-the-websites-console) et le contenu est marqué en rouge, ce qui indique qu’il n’est plus publié.

   ![screen_shot_2012-02-08at15018pm](assets/screen_shot_2012-02-08at15018pm.png)

## Activation/Désactivation différée {#activate-deactivate-later}

### Activer plus tard {#activate-later}

Pour planifier l’activation à une heure ultérieure :

1. Dans la console Sites web, accédez au menu **Activer** et sélectionnez ensuite **Activer plus tard**.
1. Dans la boîte de dialogue qui s’ouvre, indiquez la date et l’heure d’activation, puis cliquez sur **OK**. Ceci crée une version de la page qui sera activée à l’heure spécifiée.

   ![screen_shot_2012-02-08at14751pm](assets/screen_shot_2012-02-08at14751pm.png)

L’activation différée lance un workflow pour activer cette version de la page à l’heure indiquée. A l’inverse, la désactivation différée lance un workflow pour désactiver cette version de la page à une heure spécifique.

Pour annuler cette activation/désactivation, rendez-vous dans la [console Workflow](/help/sites-administering/workflows-administering.md#main-pars_title_3-yjqslz-refd) pour mettre un terme au workflow correspondant.

### Désactiver plus tard {#deactivate-later}

Pour planifier la désactivation à une heure ultérieure :

1. Dans la console Sites Web, accédez au menu **Désactiver** et sélectionnez **Désactiver plus tard**.

1. Dans la boîte de dialogue qui s’ouvre alors, indiquez la date et l’heure de désactivation, puis cliquez sur **OK**.

   ![screen_shot_2012-02-08at15129pm](assets/screen_shot_2012-02-08at15129pm.png)

La **Désactivation différée** lance un workflow pour désactiver cette version de la page à une heure spécifique.

Pour annuler cette désactivation, rendez-vous dans la [console Workflow](/help/sites-administering/workflows-administering.md#main-pars_title_3-yjqslz-refd) pour mettre un terme au workflow correspondant.

## Activation/désactivation planifiée (heure d’activation/de désactivation) {#scheduled-activation-deactivation-on-off-time}

Pour programmer les heures de publication/dépublication d’une page, utilisez les options **Heure d’activation** et **Heure de désactivation** dans les [Propriétés de la page](/help/sites-classic-ui-authoring/classic-page-author-edit-page-properties.md).

### Définition du statut de publication de la page {#determining-page-publication-status-classic-ui}

Le statut est visible à partir de la [console Sites web](/help/sites-classic-ui-authoring/author-env-basic-handling.md#page-information-on-the-websites-console). Les couleurs indiquent le statut de publication.

## Activer une section (arborescence) complète de votre site web {#activating-a-complete-section-tree-of-your-website}

Dans l’onglet **Sites web**, vous pouvez activer les pages individuelles. Lorsque vous avez saisi ou mis à jour un nombre considérable de pages de contenu (toutes résidant sous la même page racine), il peut s’avérer plus facile d’activer l’arborescence entière en une seule action. Vous pouvez également effectuer une exécution d’essai pour émuler une activation et mettre en surbrillance les pages qui seront activées.

1. Ouvrez la console **Outils** en la sélectionnant sur la page **Bienvenue** et en double-cliquant ensuite sur **Réplication** pour ouvrir la console (`https://localhost:4502/etc/replication.html`).

   ![screen_shot_2012-02-08at125033pm](assets/screen_shot_2012-02-08at125033pm.png)

1. Dans la console **Réplication**, cliquez sur **Activer l’arborescence**.

   La fenêtre suivante (`https://localhost:4502/etc/replication/treeactivation.html`) s’affiche.

   ![screen_shot_2012-02-08at125033pm-1](assets/screen_shot_2012-02-08at125033pm-1.png)

1. Entrez le **Chemin de début**. Ceci permet de spécifier le chemin d’accès à la racine de la section à activer (publier). Cette page, et toutes les pages sous-jacentes, sont prises en compte pour l’activation (ou utilisées dans le cadre de l’émulation si une Exécution d’essai est sélectionnée).
1. Activez les critères de sélection suivant vos besoins :

   * **Modifié uniquement** : active uniquement les pages qui ont été modifiées.
   * **Activé uniquement** : active uniquement les pages qui ont (déjà) été activées. Cette option agit, en quelque sorte, comme une réactivation.
   * **Ignorer désactivé** : ignore les pages qui ont été désactivées.

1. Sélectionnez l’action à effectuer :

   1. Sélectionnez **Exécution d’essai** pour vérifier quelles pages *devraient* être activées. Il s’agit seulement d’une émulation, aucune page ne sera activée.

   1. Sélectionnez **Activer** pour activer les pages.
