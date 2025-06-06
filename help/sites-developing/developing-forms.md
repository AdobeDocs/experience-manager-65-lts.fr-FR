---
title: Développer des formulaires (IU classique)
description: Découvrez comment développer des formulaires pour l’interface utilisateur classique d’Adobe Experience Manager.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: components
content-type: reference
docset: aem65
solution: Experience Manager, Experience Manager Sites
feature: Developing
role: Developer
exl-id: d1475168-6625-4d27-9c3b-01e415c2f398
source-git-commit: a869ffbc6015fd230285838d260434d9c0ffbcb0
workflow-type: tm+mt
source-wordcount: '1930'
ht-degree: 99%

---

# Développer des formulaires (IU classique){#developing-forms-classic-ui}

La structure de base d’un formulaire est la suivante :

* Début du formulaire
* Éléments de formulaire
* Fin du formulaire

Toutes ces actions sont effectuées avec une série de [composants de formulaire](/help/sites-authoring/default-components.md#form) par défaut, disponibles dans une installation AEM standard.

Outre le [développement de nouveaux composants](/help/sites-developing/developing-components-samples.md) utilisables sur vos formulaires, vous pouvez :

* [précharger des valeurs dans votre formulaire ;](#preloading-form-values)
* [précharger plusieurs valeurs dans (certains) champs ;](#preloading-form-fields-with-multiple-values)
* [développer de nouvelles actions ;](#developing-your-own-form-actions)
* [développer de nouvelles contraintes ;](#developing-your-own-form-constraints)
* [afficher ou masquer des champs de formulaire spécifiques.](#showing-and-hiding-form-components)

[Utilisation de scripts](#developing-scripts-for-use-with-forms) pour étendre les fonctionnalités lorsque cela s’avère nécessaire

>[!NOTE]
>
>Ce document est axé sur le développement de formulaires à l’aide des [Composants de base](/help/sites-authoring/default-components-foundation.md) dans l’interface utilisateur classique. Adobe recommande d’utiliser les nouveaux [Composants principaux](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html?lang=fr) et de [masquer les conditions](/help/sites-developing/hide-conditions.md) pour développer des formulaires dans l’interface utilisateur tactile.

## Préchargement des valeurs de formulaire {#preloading-form-values}

Le composant de début de formulaire fournit un champ pour le **Chemin de chargement**, un chemin facultatif qui pointe vers un nœud du référentiel.

Le chemin de chargement est le chemin d’accès aux propriétés de nœud qui est utilisé pour charger des valeurs prédéfinies dans plusieurs champs du formulaire.

Il s’agit d’un champ facultatif qui permet de spécifier le chemin à un nœud dans le référentiel. Lorsque ce nœud comporte des propriétés qui correspondent aux noms des champs, les champs adéquats du formulaire sont préchargés avec la valeur de ces propriétés. S’il n’existe aucune correspondance, le champ contient la valeur par défaut.

>[!NOTE]
>
>Une [action de formulaire](#developing-your-own-form-actions) peut également définir la ressource à partir de laquelle les valeurs initiales doivent être chargées. Pour ce faire, `FormsHelper#setFormLoadResource` est utilisé dans `init.jsp`.
>
>Si ce n’est pas le cas, le formulaire sera renseigné à partir du chemin d’accès défini dans le composant de début du formulaire par le créateur ou la créatrice.

### Préchargement des champs de formulaire avec plusieurs valeurs {#preloading-form-fields-with-multiple-values}

Plusieurs champs de formulaire ont également le **Chemin de chargement des éléments**, un autre chemin d’accès facultatif qui pointe vers un nœud du référentiel.

Le **Chemin de chargement des éléments** est le chemin d’accès aux propriétés de nœud qui sert à charger des valeurs prédéfinies dans ce champ spécifique du formulaire ; par exemple, une [liste déroulante](/help/sites-authoring/default-components-foundation.md#dropdown-list), un [groupe de cases à cocher](/help/sites-authoring/default-components-foundation.md#checkbox-group) ou un [groupe de boutons radio](/help/sites-authoring/default-components-foundation.md#radio-group).

#### Exemple : préchargement d’une liste déroulante avec plusieurs valeurs {#example-preloading-a-dropdown-list-with-multiple-values}

Vous pouvez configurer une liste déroulante avec différentes valeurs à sélectionner.

Le **Chemin de chargement des éléments** peut servir à accéder à une liste à partir d’un dossier du référentiel et les précharger dans le champ :

1. Créez un dossier sling (`sling:Folder`)
par exemple, `/etc/designs/<myDesign>/formlistvalues`

1. Ajoutez une nouvelle propriété (`myList`, par exemple) de type chaîne à plusieurs valeurs (`String[]`) pour contenir la liste déroulante des éléments. Le contenu peut être également importé à l’aide d’un script (script JSP ou curl dans un script shell).

1. Utilisez le chemin complet dans le champ **Chemin de chargement des éléments**
Par exemple, `/etc/designs/geometrixx/formlistvalues/myList`

Notez que si les valeurs de `String[]` sont formatées comme suit :

* `AL=Alabama`
* `AK=Alaska`

etc., et AEM génère la liste comme suit :

* `<option value="AL">Alabama</option>`
* `<option value="AK">Alaska</option>`

Cette fonctionnalité peut, par exemple, être utilisée dans un paramètre multilingue.

### Développement de vos propres actions de formulaire {#developing-your-own-form-actions}

Un formulaire requiert une action. Une action définit l’opération exécutée lorsque le formulaire est envoyé avec les données de l’utilisateur ou de l’utilisatrice.

Une série d’actions est fournie avec une installation AEM standard ; vous pouvez les voir sous :

`/libs/foundation/components/form/actions`

et dans la liste **Type d’action** du composant **Formulaire** :

![chlimage_1-8](assets/chlimage_1-8.png)

Cette section vous explique comment développer votre propre action de formulaire à inclure dans cette liste.

Vous pouvez ajouter votre propre action sous `/apps` en procédant comme suit :

1. Créez un nœud de type `sling:Folder`. Renseignez un nom qui indique l’action à implémenter.

   Par exemple :

   `/apps/myProject/components/customFormAction`

1. Sur ce nœud, définissez les propriétés suivantes, puis cliquez sur **Enregistrer tout** pour conserver vos modifications :

   * `sling:resourceType` - Défini comme `foundation/components/form/action`

   * `componentGroup` : Définissez cette propriété sur `.hidden`.

   * Facultatif :

      * `jcr:title` : indiquez un titre de votre choix ; il sera affiché dans la liste de sélection déroulante. S’il n’est pas défini, c’est le nom du nœud qui est affiché.

      * `jcr:description` : indiquez la description de votre choix.

1. Dans ce dossier, créez un nœud de boîte de dialogue :

   1. Ajoutez des champs afin que le créateur ou la créatrice puisse modifier la boîte de dialogue des formulaires une fois l’action sélectionnée.

1. Dans le dossier, créez l’une des options suivantes :

   1. Créer un script de publication.
Le nom du script est `post.POST.<extension>`, par exemple `post.POST.jsp`
Le script de publication est appelé lorsqu’un formulaire est envoyé pour traitement. Il contient le code qui gère les données en provenance du formulaire `POST`.

   1. Ajouter un script de transfert qui est appelé lors de l’envoi du formulaire.
Le nom du script est `forward.<extension`>, par exemple `forward.jsp`
Ce script peut définir un chemin d’accès. La requête actuelle est ensuite transmise au chemin d’accès spécifié.

   L’appel nécessaire est `FormsHelper#setForwardPath` (2 variantes). Un cas de figure classique consiste à effectuer une validation, ou appliquer une logique, pour trouver le chemin cible, puis à effectuer un transfert vers ce chemin, laissant au servlet POST Sling par défaut le soin de procéder au stockage proprement dit dans JCR.

   Un autre servlet peut également procéder au traitement. Dans ce cas, l’action de formulaire et le fichier `forward.jsp` font simplement office de code de collage. Il peut s’agir, par exemple, de l’action mail à l’adresse `/libs/foundation/components/form/actions/mail`, qui transfère les détails à `<currentpath>.mail.html` où réside un servlet de messagerie.

   De ce fait :

   * un fichier `post.POST.jsp` est utile pour les petites opérations qui sont entièrement effectuées par l’action proprement dite.
   * Le fichier `forward.jsp`, en revanche, est utile lorsque la délégation seule est requise.

   L’ordre d’exécution des scripts est le suivant :

   * Lors du rendu du formulaire (`GET`) :

      1. `init.jsp`
      1. pour toutes les contraintes du champ : `clientvalidation.jsp`
      1. validationRT du formulaire : `clientvalidation.jsp`
      1. le formulaire est chargé via la ressource de chargement si elle est définie
      1. `addfields.jsp` pendant le rendu de `<form></form>`

   * lors de la gestion d’un formulaire `POST` :

      1. `init.jsp`
      1. pour toutes les contraintes du champ : `servervalidation.jsp`
      1. validationRT du formulaire : `servervalidation.jsp`
      1. `forward.jsp`
      1. si un chemin de transfert a été défini, (`FormsHelper.setForwardPath`), transférez la requête, puis appelez `cleanup.jsp`

      1. si aucun chemin de transfert n’a été défini, appelez `post.POST.jsp` (se termine ici, aucun fichier `cleanup.jsp` n’est appelé)

1. De nouveau, dans le dossier, vous pouvez éventuellement ajouter l’un des éléments suivants :

   1. Un script pour ajouter des champs.
Le nom du script est `addfields.<extension>`, par exemple `addfields.jsp`
Un script `addfields` est appelé immédiatement après l’écriture du HTML pour le début du formulaire. Cela permet à l’action d’ajouter les champs de saisie personnalisés ou tout autre code HTML à l’intérieur du formulaire.

   1. Un script d’initialisation.
Le nom du script est `init.<extension>`, par exemple `init.jsp`
Ce script est appelé lors du rendu du formulaire. Il peut être utilisé pour initialiser des caractéristiques d’action.

   1. Un script de nettoyage.
Le nom du script est `cleanup.<extension>`, par exemple `cleanup.jsp`
Ce script peut être utilisé pour effectuer le nettoyage.

1. Utilisez le composant **Forms** dans un système de paragraphes (parsys). La liste déroulante **Type d’action** comprend désormais votre nouvelle action.

   >[!NOTE]
   >
   >Pour afficher les actions par défaut qui font partie du produit :
   >
   >
   >`/libs/foundation/components/form/actions`

### Développement de vos propres contraintes de formulaire {#developing-your-own-form-constraints}

Les contraintes peuvent être imposées à deux niveaux :

* Pour les [champs individuels (voir la procédure suivante)](#constraints-for-individual-fields)
* En tant que [validation globale du formulaire](#form-global-constraints) :

#### Contraintes pour les champs individuels {#constraints-for-individual-fields}

Vous pouvez ajouter vos propres contraintes pour un champ spécifique (sous `/apps`), en procédant comme suit :

1. Créez un nœud de type `sling:Folder`. Renseignez un nom qui indique la contrainte à implémenter.

   Par exemple :

   `/apps/myProject/components/customFormConstraint`

1. Sur ce nœud, définissez les propriétés suivantes, puis cliquez sur **Enregistrer tout** pour conserver vos modifications :

   * `sling:resourceType` - Défini sur `foundation/components/form/constraint`

   * `constraintMessage` : message personnalisé qui s’affiche si le champ n’est pas valide, suivant la contrainte, lorsque le formulaire est envoyé.

   * Facultatif :

      * `jcr:title` : indiquez le titre de votre choix ; il sera affiché dans la liste de sélection. S’il n’est pas défini, c’est le nom du nœud qui est affiché.
      * `hint` : informations supplémentaires à l’intention de l’utilisateur, concernant la façon d’utiliser le champ

1. Les scripts suivants peuvent s’avérer nécessaires à l’intérieur de ce dossier :

   * Un script de validation client :
Le nom du script est `clientvalidation.<extension>`, par exemple `clientvalidation.jsp`
Il est appelé lorsque le champ de formulaire est rendu. Il peut être utilisé pour créer le JavaScript client afin de valider le champ sur le client.

   * Un script de validation du serveur :
Le nom du script est `servervalidation.<extension>`, par exemple `servervalidation.jsp`
Il est appelé lorsque le formulaire est envoyé. Il peut être utilisé pour valider le champ sur le serveur après son envoi.

>[!NOTE]
>
>Vous trouverez des exemples de contraintes sous :
>
>`/libs/foundation/components/form/constraints`

#### Contraintes globales du formulaire {#form-global-constraints}

La validation globale du formulaire est spécifiée en configurant un type de ressource dans le composant de début de formulaire (`validationRT`). Par exemple :

`apps/myProject/components/form/validation`

Vous pouvez ensuite définir :

* un `clientvalidation.jsp`, injecté après les scripts de validation de client du champ
* et un `servervalidation.jsp`, également appelé après les validations des différents champs lors d’un `POST`.

### Affichage et masquage des composants de formulaire {#showing-and-hiding-form-components}

Vous pouvez configurer votre formulaire pour afficher ou masquer des composants de formulaire en fonction de la valeur d’autres champs du formulaire.

La modification de la visibilité d’un champ de formulaire est utile lorsque le champ n’est nécessaire que dans des conditions spécifiques. Par exemple, sur un formulaire de commentaire, une question demande aux clientes et aux clients s’ils souhaitent que des informations sur les produits leur soient envoyées par e-mail. Lorsque vous sélectionnez oui, un champ de texte s’affiche pour permettre au client ou à la cliente de saisir son adresse e-mail.

Utilisez la boîte de dialogue **Modifier les règles Afficher / Masquer** pour spécifier dans quelles conditions un composant de formulaire est affiché ou masqué.

![showhideeditor](assets/showhideeditor.png)

Utilisez les champs situés en haut de la boîte de dialogue pour spécifier les informations suivantes :

* Si vous spécifiez des conditions pour masquer ou afficher le composant.
* Si une ou toutes les conditions sont définies sur « true » pour afficher ou masquer le composant.

Une ou plusieurs conditions s’affichent sous ces champs. Une condition compare la valeur d’un autre composant de formulaire (sur le même formulaire) à une autre valeur. Si la valeur réelle dans le champ remplit la condition, cette dernière est évaluée comme étant vraie. Les conditions comprennent les informations suivantes :

* Titre du champ de formulaire testé.
* Un opérateur.
* Une valeur est comparée à la valeur du champ.

Par exemple, un composant Groupe de cases d’option avec le titre `Receive email notifications?`* * contient des boutons radio `Yes` et `No`. Un composant de champ de texte avec le titre `Email Address` utilise la condition suivante selon laquelle il est visible lorsque l’option `Yes` est sélectionnée :

![showhidecondition](assets/showhidecondition.png)

Dans JavaScript, les conditions utilisent la valeur de la propriété Nom de l’élément pour faire référence aux champs. Dans l’exemple précédent, la propriété Nom de l’élément du composant Groupe de cases d’option est `contact`. Le code suivant est le code JavaScript équivalent pour cet exemple :

`((contact == "Yes"))`

**Pour afficher ou masquer un composant de formulaire :**

1. Modifiez le composant de formulaire spécifique.

1. Sélectionnez **Afficher/masquer** pour ouvrir la boîte de dialogue **Modifier Afficher/Masquer les règles** :

   * Dans la première liste déroulante, sélectionnez **Afficher** ou **Masquer** pour indiquer si vos conditions déterminent si le composant doit être affiché ou masqué.

   * Dans la liste déroulante située à la fin de la ligne supérieure, sélectionnez :

      * **all** : si toutes les conditions doivent être vraies pour afficher ou masquer le composant.
      * **any** : si une ou plusieurs conditions doivent être vraies pour afficher ou masquer le composant

   * Sur la ligne de condition (une valeur est présentée par défaut), sélectionnez un composant, un opérateur, puis spécifiez une valeur.
   * Ajoutez d’autres conditions si nécessaire en cliquant sur **Ajouter une condition**.

   Par exemple :

   ![chlimage_1-9](assets/chlimage_1-9.png)

1. Cliquez sur **OK** pour enregistrer la définition.

1. Après avoir enregistré votre définition, un lien **Modifier des règles** s’affiche en regard de l’option **Afficher/masquer** dans les propriétés du composant de formulaire. Cliquez sur ce lien pour ouvrir la boîte de dialogue **Modifier Afficher/Masquer les règles** et apporter des modifications.

   Pour enregistrer toutes les modifications, cliquez sur **OK**.

   ![chlimage_1-10](assets/chlimage_1-10.png)

   >[!CAUTION]
   >
   >Les effets de l’affichage ou du masquage des définitions peuvent être consultés et testés :
   >
   >* dans le mode **Aperçu** de l’environnement de création (une page doit être rechargée la première fois que vous basculez vers ce mode) ;
   >
   >* dans l’environnement de publication

#### Gestion des références de composants rompues {#handling-broken-component-references}

Les conditions Afficher / Masquer utilisent la valeur de la propriété Nom de l’élément pour faire référence aux autres composants dans le formulaire. La configuration Afficher / Masquer n’est pas valide lorsque l’une des conditions fait référence à un composant qui est supprimé ou dont la propriété Nom de l’élément a été modifiée. Dans ce cas, vous devez mettre à jour manuellement les conditions, sans quoi une erreur se produira au chargement du formulaire.

Lorsque la configuration Afficher / Masquer n’est pas valide, elle est uniquement fournie sous la forme de code JavaScript. Modifiez le code pour résoudre les problèmes. Le code utilise la propriété Nom de l’élément utilisée initialement pour faire référence aux composants.

### Développement de scripts à utiliser avec des formulaires {#developing-scripts-for-use-with-forms}

Pour plus d’informations sur les éléments d’API pouvant être utilisés lors de la rédaction de scripts, consultez les [javadocs relatifs aux formulaires](https://developer.adobe.com/experience-manager/reference-materials/6-5-lts/javadoc/com/day/cq/wcm/foundation/forms/package-summary.html).

Vous pouvez utiliser ceci pour des actions telles que l’appel d’un service avant l’envoi du formulaire et l’annulation du service en cas d’échec :

* Définissez le type de ressource de validation.
* Insérez un script pour la validation :

   * Dans le fichier JSP, appelez le service Web et créez un objet `com.day.cq.wcm.foundation.forms.ValidationInfo` contenant vos messages d’erreur. S’il existe des erreurs, les données du formulaire ne sont pas publiées.
