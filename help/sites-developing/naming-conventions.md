---
title: Conventions de dénomination des nœuds dans le référentiel de contenu Java
description: Les nœuds dans le référentiel sont soumis aux conventions de dénomination du référentiel de contenu Java.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: platform
content-type: reference
solution: Experience Manager, Experience Manager Sites
feature: Developing
role: Developer
exl-id: 36025dac-890e-45ba-adea-a230a5231a0b
source-git-commit: a869ffbc6015fd230285838d260434d9c0ffbcb0
workflow-type: tm+mt
source-wordcount: '284'
ht-degree: 99%

---

# Conventions de dénomination {#naming-conventions}

Les nœuds dans le référentiel sont soumis aux conventions de dénomination de [Java Content Repository](/help/sites-developing/the-basics.md#java-content-repository). Toutefois, AEM impose d’autres conventions pour le nom des nœuds de page.

## Conventions de dénomination pour les pages {#naming-conventions-for-pages}

Ces conventions de dénomination sont implémentées à différents niveaux :

* JcrUtil : l’implémentation AEM des [utilitaires JCR](#jcr-utilities).
* PageManager : le [Gestionnaire de pages](#page-manager) fournit des méthodes pour les opérations au niveau de la page.
* Selon l’interface utilisateur utilisée :

   * [IU tactile standard](#standard-ui)
   * [Interface utilisateur classique](#classic-ui)

### Utilitaires JCR {#jcr-utilities}

[JcrUtil](https://developer.adobe.com/experience-manager/reference-materials/6-5-lts/javadoc/index.html?com/day/cq/commons/jcr/JcrUtil.html) est l’implémentation AEM des utilitaires JCR. Les mappages de caractères qu’il contrôle et les validations suivantes présentent un intérêt particulier pour la validation des noms :

* `isValidName`

   * Vérifie si le nom n’est pas vide et s’il contient uniquement des caractères valides.
   * Peut être utilisé pour vérifier si un nom proposé est valide.

* `createValidName`

   * Crée un libellé valide à partir d’une chaîne arbitraire.
   * Peut être utilisé pour créer un nom à partir d’un titre.

### Gestionnaire de pages {#page-manager}

[PageManager](https://developer.adobe.com/experience-manager/reference-materials/6-5-lts/javadoc/com/day/cq/wcm/api/PageManager.html) fournit des méthodes pour les opérations au niveau de la page, sur la base de [JCRUtil](#jcr-utilities).

### Interface utilisateur standard {#standard-ui}

L’interface utilisateur tactile standard :

* Valide le nom en fonction des restrictions imposées par PageManager quand :

   * un titre de page est fourni pour être converti en nom de nœud ;
   * un nom de nœud explicite est fourni.

### Interface utilisateur classique {#classic-ui}

L’IU classique impose des restrictions plus strictes :

* Valide le nom lorsqu’un nom de nœud explicite se présente dans l’une des situations suivantes :

   * un titre de page est fourni pour être converti en nom de nœud ;
   * un nom de nœud explicite est fourni.

* Caractères valides (seuls ces caractères sont effectivement valides lorsqu’une page est créée dans l’IU classique, même si `PageManagerImpl` autorise des caractères supplémentaires) :

   * « a » à « z »
   * « A » à « Z »
   * « 0 » à « 9 »
   * _ (trait de soulignement)
   * `-` (tiret/moins)
