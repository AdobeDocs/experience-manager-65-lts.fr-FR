---
title: Fragments de document
description: Dans Correspondence Management, les fragments de document (texte, liste, conditions et fragments de disposition, par exemple) permettent de former les composants statiques, dynamiques et répétables de la correspondance client.
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: correspondence-management
feature: Correspondence Management
solution: Experience Manager, Experience Manager Forms
role: Admin, User, Developer
exl-id: 568a1513-1de9-4f68-be09-f47cd5b30847
source-git-commit: c3e9029236734e22f5d266ac26b923eafbe0a459
workflow-type: tm+mt
source-wordcount: '239'
ht-degree: 100%

---

# Fragments de document {#document-fragments}

Les fragments de document sont des éléments ou composants réutilisables d’une correspondance qui permettent de composer des communications interactives ou des lettres. Les fragments de document sont composés des types suivants :

* **Texte** : Un actif de texte est un élément de contenu comprenant un ou plusieurs paragraphes de texte. Un paragraphe peut être statique ou dynamique.

   * [Textes dans les communications interactives](/help/forms/using/texts-interactive-communications.md)

* **Condition** : les conditions vous permettent de définir le contenu à inclure lors de la création d’une correspondance, en fonction des données fournies. La condition est décrite en termes de variables de contrôle. Une variable de contrôle peut être un élément de dictionnaire de données ou un espace réservé.

   * [Conditions dans les communications interactives](/help/forms/using/conditions-interactive-communications.md)

* **Liste :** la liste est un groupe de fragments du document, incluant du texte, des listes, des conditions et des images. L’ordre des éléments de la liste peut être fixe ou modifiable. Lors de la création d’une lettre, vous pouvez utiliser certains ou tous les éléments de liste pour répliquer un modèle d’éléments réutilisable.
* **Fragment de disposition** : il s’agit d’une mise en page pouvant être utilisée dans une ou plusieurs lettres. Un fragment de disposition est utilisé pour créer des modèles répétables, en particulier des tableaux dynamiques. La disposition peut comporter des champs de formulaire types comme « Adresse » et « Numéro de référence ». Elle contient également des sous-formulaires vides indiquant les zones cible. Les dispositions (XDP) sont créées dans Designer, puis sont téléchargées sur AEM Forms.
