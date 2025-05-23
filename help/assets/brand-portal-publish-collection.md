---
title: Publication de collections sur Brand Portal
description: Découvrez comment publier ou annuler la publication des ressources sur Brand Portal.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
topic-tags: brand-portal
content-type: reference
docset: aem65
feature: Brand Portal
role: User
solution: Experience Manager, Experience Manager Assets
exl-id: 1456a32e-c98f-4106-8546-799614c51a59
source-git-commit: c3e9029236734e22f5d266ac26b923eafbe0a459
workflow-type: tm+mt
source-wordcount: '321'
ht-degree: 100%

---

# Publication de collections sur Brand Portal {#publish-collections-to-brand-portal}

En tant qu’administrateur ou administratrice Adobe Experience Manager (AEM) Assets, vous pouvez publier des collections sur l’instance AEM Assets Brand Portal pour votre organisation. Cependant, vous devez d’abord intégrer AEM Assets à Brand Portal. Pour plus de détails, consultez [Configuration d’AEM Assets avec Brand Portal](/help/assets/configure-aem-assets-with-brand-portal.md).

Si vous apportez des modifications ultérieures à la collection d’origine dans AEM Assets, les changements ne sont reflétés dans Brand Portal que lorsque vous republiez la collection. Cette fonction assure que les modifications en cours ne sont pas disponibles dans Brand Portal. Seules les modifications approuvées publiées par un administrateur sont disponibles dans Brand Portal.

>[!NOTE]
>
>Les fragments de contenu ne peuvent pas être publiés sur Brand Portal. Par conséquent, si vous sélectionnez un ou plusieurs fragments de contenu sur l’auteur AEM, l’action **Publier sur Brand Portal** n’est pas disponible.
>
>Si des collections contenant des fragments de contenu sont publiées sur Brand Portal à partir de l’instance de création AEM, tout le contenu du dossier, à l’exception des fragments de contenu, est répliqué sur l’interface Brand Portal.

## Publication d’une collection dans Brand Portal {#publish-a-collection-to-brand-portal}

1. Dans l’interface utilisateur AEM Assets, cliquez sur le logo AEM.
1. Dans la console **Navigation**, accédez à **Ressources > Collections**.
1. Dans la console Collections, sélectionnez les collections que vous souhaitez publier dans Brand Portal.

   ![select_collection](assets/select_collection.png)

1. Dans la barre d’outils, cliquez sur **Publier sur Brand Portal**.
1. Dans la boîte de dialogue de confirmation, cliquez sur **Publier**.
1. Fermez le message de confirmation.
1. Connectez-vous à Brand Portal en tant qu’administrateur. La collection publiée est disponible dans la console Collections.

   ![collection publiée](assets/published_collection.png)

## Dépublication de collections {#unpublish-collections}

Vous pouvez dépublier les collections que vous publiez depuis AEM Assets dans Brand Portal. Une fois la collection d’origine dépubliée, sa copie n’est plus disponible pour les utilisateurs de Brand Portal.

1. Dans la console Collections de votre instance AEM Assets, sélectionnez la collection que vous souhaitez dépublier.

   ![select_collection-1](assets/select_collection-1.png)

1. Dans la barre d’outils, cliquez sur l’icône **Supprimer de Brand Portal**.
1. Dans la boîte de dialogue, cliquez sur **Dépublier**.
1. Fermez le message de confirmation. La collection est supprimée de l’interface de Brand Portal.
