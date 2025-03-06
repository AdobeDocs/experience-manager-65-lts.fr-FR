---
title: Conventions de dénomination pour le test des ressources
description: Les nœuds dans le référentiel sont soumis aux conventions de dénomination de Java Content Repository. Toutefois, Adobe Experience Manager impose d’autres conventions pour le nom des nœuds de ressource.
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
topic-tags: authoring
content-type: reference
solution: Experience Manager, Experience Manager Sites
feature: Authoring
role: User
exl-id: 37de1a8b-b7db-469e-98a7-20ddb6218510
source-git-commit: c3e9029236734e22f5d266ac26b923eafbe0a459
workflow-type: tm+mt
source-wordcount: '131'
ht-degree: 100%

---

# Conventions de dénomination pour le test des ressources{#naming-conventions-for-assets-testing}

Les nœuds dans le référentiel sont soumis aux conventions de dénomination de [Java Content Repository](/help/sites-developing/the-basics.md#java-content-repository). Toutefois, Adobe Experience Manager impose d’autres conventions pour le nom des nœuds de ressource.

## Interface utilisateur classique {#classic-ui}

L’IU classique impose des restrictions plus strictes :

* Valide le nom de la ressource avec un nom de nœud explicite lorsque l’une des conditions suivantes se vérifie :

   * un titre de ressource est fourni pour une conversion en nom de nœud ;
   * un nom de nœud explicite est fourni.

* Caractères valides (seuls ces caractères sont réellement valides lors de la création d’une ressource dans l’interface utilisateur classique) :

   * « a » à « z »
   * « A » à « Z »
   * « 0 » à « 9 »
   * _ (trait de soulignement)
   * `-` (tiret/moins)
