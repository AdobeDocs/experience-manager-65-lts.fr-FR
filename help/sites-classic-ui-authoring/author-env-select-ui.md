---
title: Choisir votre interface utilisateur
description: Pour offrir davantage de confort aux auteurs et autrices, l’IU destinée aux écrans tactiles permet de basculer vers l’IU classique lorsque cela s’avère nécessaire.
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: introduction
content-type: reference
solution: Experience Manager, Experience Manager Sites
feature: Authoring
role: User
exl-id: 781b580a-e4d1-419e-afb1-884c8fb634b9
source-git-commit: c3e9029236734e22f5d266ac26b923eafbe0a459
workflow-type: tm+mt
source-wordcount: '195'
ht-degree: 100%

---

# Choisir votre interface utilisateur{#selecting-your-ui}

L’interface utilisateur activée pour les écrans tactiles remplace l’IU classique, il appartient donc à l’utilisateur ou à l’administrateur de l’instance AEM de choisir explicitement s’il faut continuer à utiliser cette dernière. Étant donné que l’IU classique n’est plus gérée, il n’est plus possible pour l’auteur de basculer simplement de l’IU classique vers son équivalent dans l’IU activée pour les écrans tactiles.

Pour offrir davantage de confort à ces utilisateurs, l’IU destinée aux écrans tactiles permet de basculer vers l’IU classique lorsque cela s’avère nécessaire. Voir [Sélection de l’interface utilisateur](/help/sites-authoring/select-ui.md) dans la documentation de création standard pour plus d’informations.

>[!NOTE]
>
>Les instances mises à niveau à partir d’une version précédente conservent l’IU classique pour la création de pages.
>
>Après la mise à niveau, la création de pages ne bascule pas automatiquement vers l’IU tactile. Vous pouvez cependant configurer ce basculement à l’aide de la [configuration OSGi](/help/sites-deploying/configuring-osgi.md) du **service du mode Interface utilisateur de création de Gestion de contenu web** (service `AuthoringUIMode`). Consultez [IU par défaut en fonction de l’éditeur](#uioverridesfortheeditor).

## Configurer l’UI par défaut pour votre instance {#configuring-the-default-ui-for-your-instance}

Un administrateur ou une administratrice système peut configurer l’interface utilisateur qui s’affiche au démarrage et lors de la connexion à l’aide du [Mappage racine](/help/sites-deploying/osgi-configuration-settings.md#daycqrootmapping).

Ceci peut être remplacé par les paramètres par défaut de l’utilisateur ou de l’utilisatrice, ou les paramètres de session.
