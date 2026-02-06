---
title: Utiliser les xtypes (IU classique)
description: Découvrez tous les xtypes disponibles avec Adobe Experience Manager.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: components
content-type: reference
solution: Experience Manager, Experience Manager Sites
feature: Developing
role: Developer
exl-id: 4a78de53-33bf-4999-ba3c-7d0bc33196a4
source-git-commit: 24bd1f57da3f9ce613ee28276d1ae9465b6dfba6
workflow-type: tm+mt
source-wordcount: '3668'
ht-degree: 59%

---

# Utiliser les xtypes (IU classique){#using-xtypes-classic-ui}

Cette page présente tous les xtypes disponibles avec Adobe Experience Manager (AEM).

Dans le langage ExtJS, un xtype est un nom symbolique donné à une classe. Vous pouvez lire le paragraphe « Composant XTypes » de la [Présentation d’ExtJS 2](https://docs.sencha.com/) pour obtenir une explication détaillée sur les xtypes et leur utilisation.

Pour plus d’informations sur tous les widgets disponibles dans AEM, consultez la [documentation relative à l’API de widget](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html).

Pour savoir dans quels composants un xtype donné est utilisé dans AEM, vous pouvez utiliser la requête `Xpath` suivante dans CRXDE. Remplacez simplement &#39;checkbox&#39; par le xtype qui vous intéresse :

`//element(*, cq:Widget)[@xtype='checkbox']`

>[!NOTE]
>
>Cette page décrit l’utilisation des xtypes ExtJS dans l’IU classique.
>
>Adobe recommande d’utiliser l’[IU optimisée pour les écrans tactiles](/help/sites-developing/touch-ui-concepts.md), une version standard et moderne qui repose sur l’[IU Coral](/help/sites-developing/touch-ui-concepts.md#coral-ui) et l’[IU Granite](/help/sites-developing/touch-ui-concepts.md#granite-ui-foundation-components).

## xtypes {#xtypes}

Les xtypes disponibles dans Adobe Experience Manager sont répertoriés ci-dessous :

* `annotation`

  [CQ.wcm.Annotation](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  La `Annotation` est une fenêtre spéciale. Son corps contient un formulaire et son pied de page un groupe de boutons. Les boîtes de dialogue sont généralement utilisées pour modifier le contenu, mais elles peuvent également afficher des informations.

* `arraystore`

  [CQ.Ext.data.ArrayStore](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Anciennement appelé `SimpleStore`.

  Petite classe d’aide permettant de faciliter la création des [CQ.Ext.data.Store](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)s à partir de données de tableau. Un `ArrayStore` est automatiquement configuré avec un [CQ.Ext.data.ArrayReader](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html).

* `asseteditor`

  [CQ.dam.AssetEditor](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Le `Asset Editor` est utilisé par l’administrateur de gestion des ressources numériques.

* `assetreferencesearchdialog`

  [CQ.wcm.AssetReferenceSearchDialog](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  La `AssetReferenceSearchDialog` est une boîte de dialogue qui s’affiche lorsqu’une page fait référence à des ressources ou à des balises.

* `blueprintconfig`

  [CQ.wcm.msm.BlueprintConfig](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  L’`BlueprintConfig` fournit un panneau pour afficher les Live Copies d’un plan directeur et modifier les propriétés de ce plan directeur (déclencheur de synchronisation et actions de synchronisation).

* `blueprintstatus`

  [CQ.wcm.msm.BlueprintStatus](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  BlueprintStatus fournit un panneau pour afficher et modifier un plan directeur et ses relations avec les Live Copies. La navigation se fait par le biais d’un [CQ.wcm.msm.BlueprintStatus.Tree](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html), la modification par le biais d’un [CQ.wcm.msm.BlueprintConfig](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) et d’un [CQ.wcm.msm.LiveCopyProperties](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html).

* `box`

  [CQ.Ext.BoxComponent](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Classe de base pour n’importe quel [composant](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) qui doit être dimensionné comme une boîte, en utilisant la largeur et la hauteur.

  BoxComponent fournit des réglages de modèle de boîte automatiques pour le dimensionnement et le positionnement et fonctionne correctement dans le modèle de rendu des composants.

* `browsedialog`

  [CQ.BrowseDialog](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  BrowseDialog permet de parcourir le référentiel afin de sélectionner un chemin. Il est généralement utilisé par l’intermédiaire d’un [BrowseField](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html).

* `browsefield`

  [CQ.form.BrowseField](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  **Obsolète : utilisez plutôt [CQ.form.PathField](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)**.

* `bulkeditor`

  [CQ.wcm.BulkEditor](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Le `BulkEditor` fournit un moteur de recherche et une grille pour modifier les résultats de la recherche.

  Le `BulkEditor` doit être inséré dans un formulaire HTML (requis par la fonctionnalité d&#39;import). Cela fonctionne parfaitement avec un [CQ.Dialog](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html).

* `bulkeditorform`

  [CQ.wcm.BulkEditorForm](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  BulkEditorForm fournit [CQ.wcm.BulkEditor](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) accompagné d’un formulaire HTML. Version autonome de [CQ.wcm.BulkEditor](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html). Un formulaire HTML est requis pour le bouton d’importation.

* `button`

  [CQ.Ext.Button](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Classe de bouton unique

* `buttongroup`

  [CQ.Ext.ButtonGroup](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Conteneur pour un groupe de boutons

* `chart`

  [CQ.Ext.chart.Chart](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Le package CQ.Ext.chart fournit la fonctionnalité de visualisation des données avec une représentation graphique basée sur Flash. Chaque graphique est directement lié à un CQ.Ext.data.Store, ce qui permet la mise à jour automatique du graphique. Pour modifier l’aspect d’un graphique, reportez-vous aux options de configuration [chartStyle](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) et [extraStyle](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html).

* `checkbox`

  [CQ.Ext.form.Checkbox](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Champ de case à cocher unique. Peut être utilisé comme remplacement direct des champs de case à cocher traditionnels.

* `checkboxgroup`

  [CQ.Ext.form.CheckboxGroup](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Conteneur de regroupement pour les commandes [CQ.Ext.form.Checkbox](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html).

* `clearcombo`

  [CQ.form.ClearableComboBox](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  ClearableComboBox est une zone de liste non modifiable avec un déclencheur pour effacer sa valeur.

* `colorfield`

  [CQ.form.ColorField](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  ColorField permet de saisir une valeur hexadécimale directement ou à l’aide d’un [CQ.Ext.ColorMenu](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html).

* `colorlist`

  [CQ.form.ColorList](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  ColorList permet de sélectionner une couleur dans une liste modifiable.

* `colormenu`

  [CQ.Ext.menu.ColorMenu](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Menu contenant un composant [CQ.Ext.ColorPalette](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html).

* `colorpalette`

  [CQ.Ext.ColorPalette](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Classe de palette de couleurs simple pour sélectionner les couleurs. La palette peut être rendue dans n’importe quel conteneur.

* `combo`

  [CQ.Ext.form.ComboBox](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Commande combobox prenant en charge la saisie automatique, le chargement à distance, la pagination et de nombreuses autres fonctionnalités.

  Une ComboBox fonctionne de la même manière qu’un champ &lt;select> HTML traditionnel. La différence est que pour envoyer le [valueField](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html), vous devez spécifier un [hiddenName](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) pour créer une entrée masquée.

* `component`

  [CQ.Ext.Component](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Classe de base pour tous les composants `Ext`. Toutes les sous-classes de Component peuvent participer au cycle de vie automatisé du composant `Ext` de création, de rendu et de destruction fourni par la classe [Container](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html). Les composants peuvent être ajoutés à un conteneur par l’intermédiaire de l’option de configuration [éléments](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) au moment de la création du conteneur.

* `componentextractor`

  [CQ.wcm.ComponentExtractor](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  ComponentExtractor permet d’extraire des composants d’un site ou d’une page web.

* `componentselector`

  [CQ.form.ComponentSelector](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Sélection groupée et ordonnée de composants disponibles.

* `componentstyles`

  [CQ.form.ComponentStyles](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

* `compositefield`

  [CQ.form.CompositeField](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Classe de base pour les champs de formulaires complexes basés sur les panneaux qui comprennent un champ de formulaire ou un groupe de champs de formulaires.

* `container`

  [CQ.Ext.Container](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Classe de base pour n’importe quel [CQ.Ext.BoxComponent](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) qui peut contenir d’autres composants. Les conteneurs gèrent le comportement de base des éléments contenus, à savoir l’ajout, l’insertion et la suppression d’éléments.

  Les classes de conteneur les plus utilisées sont les suivantes : [CQ.Ext.Panel](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html), [CQ.Ext.Window](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) et [CQ.Ext.TabPanel](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html).

* `contentfinder`

  [CQ.wcm.ContentFinder](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  ContentFinder est un [viewport](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) de deux colonnes spécialisé qui contient l’outil de recherche de contenu réel à gauche et le cadre de contenu à droite.

* `contentfindertab`

  [CQ.wcm.ContentFinderTab](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  ContentFinderTab est un panneau spécialisé qui fournit les fonctions utilisées dans les panneaux à onglets du [CQ.wcm.ContentFinder](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html). En règle générale, il comprend un formulaire de recherche (la zone de requête) et une vue de données pour afficher la recherche.

* `cq.workflow.model.combo`

  [CQ.wcm.WorkflowModelCombo](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  WorkflowModelCombo est un [CQ.Ext.form.ComboBox](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) personnalisé qui affiche la liste des modèles de workflow disponibles.

* `cq.workflow.model.selector`

  [CQ.wcm.WorkflowModelSelector](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  WorkflowModelSelector combine un WorkflowModelCombo avec une image miniature du workflow et des boutons permettant de créer et de modifier des modèles de workflow.

* `createsitewizard`

  [CQ.wcm.CreateSiteWizard](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

   CreateSiteWizard est un assistant détaillé pour créer des sites (MSM).

* `createversiondialog`

  [CQ.wcm.CreateVersionDialog](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  CreateVersionDialog est une boîte de dialogue qui permet de créer une version d’une page.

* `customcontentpanel`

  [CQ.CustomContentPanel](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  CustomContentPanel est un panneau spécial à utiliser dans [CQ.Dialog](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) : son contenu est récupéré depuis et vers une URL différente des autres champs de la boîte de dialogue.

* `cycle`

  [CQ.Ext.CycleButton](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

   SplitButton spécialisé contenant un menu d’éléments [CQ.Ext.menu.CheckItem](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html). Le bouton fait défiler automatiquement chaque élément de menu à chaque clic, augmentant l’événement [change](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) du bouton (ou appelant la fonction [changeHandler](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) du bouton, si disponible) pour l’élément de menu actif.

* `dataview`

  [CQ.Ext.DataView](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Mécanisme pour l’affichage des données à l’aide des modèles de mise en page personnalisés et le formatage. DataView utilise un [CQ.Ext.XTemplate](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) comme mécanisme de modélisation interne et il est lié à un [CQ.Ext.data.Store](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) de façon à ce que l’affichage soit automatiquement mis à jour à mesure que les données de la boutique sont modifiées.

* `datefield`

  [CQ.Ext.form.DateField](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Elle fournit un champ de saisie de date avec un menu déroulant [CQ.Ext.DatePicker](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) et la validation de date automatique.

* `datemenu`

  [CQ.Ext.menu.DateMenu](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Menu contenant un composant [CQ.Ext.DatePicker](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html).

* `datepicker`

  [CQ.Ext.DatePicker](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Sélecteur de date pop-up. Cette classe est utilisée par la classe [DateField](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) pour permettre la navigation et la sélection de dates valides.

* `datetime`

  [CQ.form.DateTime](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  DateTime permet de saisir une date et une heure en combinant [CQ.Ext.form.DateField](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) et [CQ.Ext.form.TimeField](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html).

* `dialog`

  [CQ.Dialog](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  La boîte de dialogue est une fenêtre spéciale. Son corps contient un formulaire et son pied de page un groupe de boutons. Les boîtes de dialogue sont généralement utilisées pour modifier le contenu, mais elles peuvent également afficher des informations.

* `dialogfieldset`

  [CQ.form.DialogFieldSet](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  DialogFieldSet est un [FieldSet](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) à utiliser dans les [boîtes de dialogue](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html).

* `directstore`

  [CQ.Ext.data.DirectStore](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Une petite classe d’aide permettant de créer un [CQ.Ext.data.Store](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) configuré avec un [CQ.Ext.data.DirectProxy](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) et un [CQ.Ext.data.JsonReader](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) pour faciliter l’interaction avec un [CQ.Ext.Direct](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) côté serveur [Provider](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html).

* `displayfield`

  [CQ.Ext.form.DisplayField](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Champ de texte en affichage seul qui n’est ni validé ni envoyé.

* `editbar`

  [CQ.wcm.EditBar](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  EditBar permet de modifier du contenu à l’aide des boutons figurant dans une barre.

  Bien que non répertorié ici, EditBar comporte tous les membres de [CQ.wcm.EditBase](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html).

* `editor`

  [CQ.Ext.Editor](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Champ d’éditeur de base qui gère l’affichage/le masquage sur demande et dispose d’une logique intégrée de dimensionnement et de gestion des événements.

* `editorgrid`

  [CQ.Ext.grid.EditorGridPanel](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Cette classe étend la [classe GridPanel](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) pour fournir des modifications de cellule sur les [colonnes](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) sélectionnées. Les colonnes modifiables sont spécifiées en fournissant un [éditeur](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) dans la [configuration des colonnes](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html).

* `editrollover`

  [CQ.wcm.EditRollover](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  EditRollover permet à l’utilisateur ou utilisatrice de modifier le contenu en double-cliquant et propose d’autres actions de modification via un menu contextuel. La zone modifiable est indiquée par un cadre lorsque la souris survole le contenu.

* `feedimporter`

  [CQ.wcm.FeedImporter](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  FeedImporter permet d’importer des flux RSS ou Atom et de créer des pages pour chaque entrée de flux.

* `field`

  [CQ.Ext.form.Field](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Classe de base pour les champs de formulaire qui offre une gestion d’événement par défaut, le dimensionnement, la manipulation des valeurs et d’autres fonctionnalités.

* `fieldset`

  [CQ.Ext.form.FieldSet](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Conteneur standard utilisé pour regrouper les éléments dans un [formulaire](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html).

* `fileuploaddialogbutton`

  [CQ.form.FileUploadDialogButton](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  FileUploadDialogButton crée un bouton qui ouvre une boîte de dialogue pour charger un fichier via FileUploadField. Peut être utilisé dans des boîtes de dialogue de modification où le chargement doit se produire dans un formulaire distinct.

* `fileuploadfield`

  [CQ.form.FileUploadField](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  FileUploadField permet de sélectionner un fichier unique à charger.

* `findreplacedialog`

  [CQ.wcm.FindReplaceDialog](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  FindReplaceDialog est une boîte de dialogue permettant de rechercher et de remplacer des jetons dans une page et ses pages enfants.

* `flash`

  [CQ.Ext.FlashComponent](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

* `grid`

  [CQ.Ext.grid.GridPanel](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Cette classe représente l’interface principale d’un contrôle de grille basé sur un composant pour représenter des données sous forme tabulaire avec des lignes et des colonnes.

* `groupingstore`

  [CQ.Ext.data.GroupingStore](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Mise en œuvre de boutique spéciale qui permet le regroupement des enregistrements par l’un des champs disponibles. Utilisé avec un [CQ.Ext.grid.GroupingView](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) pour prouver le modèle de données d’un GridPanel groupé.

* `heavymovedialog`

  [CQ.wcm.HeavyMoveDialog](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  HeavyMoveDialog est une boîte de dialogue permettant de déplacer une page et ses pages enfants, en prenant également en compte la réactivation des pages précédemment activées (déplacement lourd ou « heavy move » en anglais).

* `hidden`

  [CQ.Ext.form.Hidden](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Champ masqué de base pour stocker les valeurs masquées dans des formulaires qui doivent être transmises lors de l’envoi des formulaires.

* `historybutton`

  [CQ.HistoryButton](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  HistoryButton est une petite classe d’aide qui fournit facilement des boutons Précédent et Suivant. En règle générale, deux instances associées sont requises : l’instance de bouton vers l’avant est un bouton simple associé à l’instance de bouton vers l’arrière qui gère l’historique.

* `htmleditor`

  [CQ.Ext.form.HtmlEditor](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Il fournit un composant HTML Editor allégé. Safari ne prend pas en charge certaines fonctionnalités de barre d’outils. Par conséquent, le système les masque automatiquement si nécessaire. Indiqué dans les options de configuration, le cas échéant.

  Les boutons de la barre d’outils de l’éditeur ont des infos-bulle définies dans la propriété [buttonTips](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html).

* `iframedialog`

  [CQ.IframeDialog](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Boîte de dialogue basique affichant le contenu d’un iframe et permettant la présence de formulaires dans les iframes.

* `iframepanel`

  [CQ.IframePanel](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Panneau contenant un iframe. Il permet de créer facilement des iframes, un événement de chargement d’iframe et un accès facile au contenu de l’iframe.

* `inlinetextfield`

  [CQ.form.InlineTextField](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  InlineField est un champ de texte qui s’affiche en tant que libellé lorsqu’il n’est pas dans le focus.

* `jsonstore`

  [CQ.Ext.data.JsonStore](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Petite classe d’aide permettant de faciliter la création de [CQ.Ext.data.Store](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)s à partir de données JSON. Un JsonStore est automatiquement configuré avec un [CQ.Ext.data.JsonReader](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html).

* `label`

  [CQ.Ext.form.Label](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Champ de libellé de base.

* `languagecopydialog`

  [CQ.wcm.LanguageCopyDialog](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  LanguageCopyDialog est une boîte de dialogue permettant de copier les arborescences de langues.

* `linkchecker`

  [CQ.wcm.LinkChecker](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  LinkChecker est un outil permettant de vérifier les liens externes dans un site.

* `listview`

  [CQ.Ext.list.ListView](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  CQ.Ext.list.ListView est une implémentation rapide et légère d’une vue de type [grille](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html).

* `livecopyproperties`

  [CQ.wcm.msm.LiveCopyProperties](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  LiveCopyProperties fournit un panneau pour afficher et modifier les propriétés des Live Copies (héritage des relations, déclencheur de synchronisation et actions de synchronisation).

* `lvbooleancolumn`

  [CQ.Ext.list.BooleanColumn](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Une classe de définition de colonne qui renvoie des champs de données booléens. Voir l’option de configuration [xtype](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) de [CQ.Ext.list.Column](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) pour plus d’informations.

* `lvcolumn`

  [CQ.Ext.list.Column](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Cette classe encapsule les données de configuration de colonne à utiliser dans l’initialisation d’une [ListView](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html).

* `lvdatecolumn`

  [CQ.Ext.list.DateColumn](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Une classe de définition de colonne qui renvoie une date transmise en fonction des paramètres régionaux par défaut ou d’un [format](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) configuré. Voir l’option de configuration [xtype](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) de [CQ.Ext.list.Column](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) pour plus d’informations.

* `lvnumbercolumn`

  [CQ.Ext.list.NumberColumn](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Une classe de définition de colonne qui renvoie un champ de données numérique selon une chaîne de [format](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html). Voir l’option de configuration [xtype](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) de [CQ.Ext.list.Column](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) pour plus d’informations.

* `mediabrowsedialog`

  [CQ.MediaBrowseDialog](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  **Obsolète : utilisez plutôt l’[outil de recherche de contenu](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) pour parcourir les médias.**

  MediaBrowseDialog est une boîte de dialogue permettant de parcourir la bibliothèque de médias.

* `menu`

  [CQ.Ext.menu.Menu](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Un objet de menu. Conteneur auquel vous pouvez ajouter des éléments de menu. Le menu peut également servir de classe de base lorsque vous souhaitez un menu spécialisé basé sur un autre composant (comme [CQ.Ext.menu.DateMenu](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) par exemple).

  Les menus peuvent contenir des [éléments de menu](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) ou des [composants](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) généraux.

* `menubaseitem`

  [CQ.Ext.menu.BaseItem](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Classe de base pour tous les éléments dont le rendu est effectué dans les menus. BaseItem fournit le rendu par défaut, la gestion des états activée et les options de configuration de base partagées par tous les composants du menu.

* `menucheckitem`

  [CQ.Ext.menu.CheckItem](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Il ajoute un élément de menu qui contient une case à cocher par défaut, mais peut également faire partie d’un groupe de cases d’option.

* `menuitem`

  [CQ.Ext.menu.Item](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Classe de base pour tous les éléments de menu qui nécessitent des fonctionnalités liées au menu (comme des sous-menus) et ne sont pas des éléments d’affichage statique. L’élément étend les fonctionnalités de base de [CQ.Ext.menu.BaseItem](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) en ajoutant l’activation spécifique au menu et la gestion des clics.

* `menuseparator`

  [CQ.Ext.menu.Separator](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Il ajoute une barre de séparation à un menu, utilisée pour diviser les groupes logiques d’éléments de menu. En règle générale, vous l&#39;ajoutez en utilisant « - » dans votre appel à add() ou dans votre configuration d&#39;éléments plutôt que d&#39;en créer un directement.

* `menutextitem`

  [CQ.Ext.menu.TextItem](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Elle ajoute une chaîne de texte statique à un menu, utilisée comme en-tête ou séparateur de groupes.

* `metadata`

  [CQ.dam.form.Metadata](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  `Metadata` fournit un ensemble de champs permettant de déterminer les informations requises pour un champ de métadonnées tel qu’il est utilisé, par exemple, sur les pages de l’Éditeur de ressources.

  Il fournit les champs suivants :

* `multifield`

  [CQ.form.MultiField](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  L’`MultiField` est une liste modifiable de champs de formulaire permettant de modifier les propriétés à plusieurs valeurs.

* `mvt`

  [CQ.form.MVT](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Le composant de test multivarié peut être utilisé pour définir et modifier un ensemble d’images qui sont présentées comme des bannières alternatives. Les statistiques de taux de clics sont rassemblées par bannière.

* `notificationinbox`

  [CQ.wcm.NotificationInbox](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Le `NotificationInbox` permet à l’utilisateur de s’abonner aux actions de gestion de contenu web et de gérer les notifications.

* `numberfield`

  [CQ.Ext.form.NumberField](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Champ numérique qui fournit le filtrage de frappe automatique et la validation numérique.

* `offlineimporter`

  [CQ.wcm.OfflineImporter](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Le `OfflineImporter` est un outil permettant d’importer et de convertir des documents Microsoft® Word en pages AEM. Cette fonction permet de modifier le contenu hors ligne à l’aide d’un traitement de texte.

* `ownerdraw`

  [CQ.form.OwnerDraw](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Le `OwnerDraw` peut contenir du code HTML personnalisé (saisi directement ou récupéré à partir d’une URL).

* `paging`

  [CQ.Ext.PagingToolbar](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  À mesure qu’augmente la quantité d’enregistrements, le temps requis par le navigateur pour en effectuer le rendu augmente. La pagination est utilisée pour réduire la quantité de données échangées avec le client.

* `panel`

  [CQ.Ext.Panel](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Un `panel` est un conteneur qui possède des fonctionnalités et des composants structurels spécifiques qui en font la base parfaite pour les interfaces utilisateur orientées application.

  De par leur héritage, les panneaux proviennent de [CQ.Ext.Container](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html).

* `paragraphreference`

  [CQ.form.ParagraphReference](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Le champ de référence de paragraphe permet de parcourir les pages et de sélectionner l’un de leurs paragraphes. Il se compose d’un champ de déclenchement et d’une boîte de dialogue de navigation de paragraphe associée.

* `password`

  [CQ.form.Password](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Le `Password` est similaire à un [CQ.Ext.form.TextField](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) mais conserve sa valeur privée, ce qui permet de saisir des données sensibles.

* `pathcompletion`

  [CQ.form.PathCompletion](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  **Obsolète : utilisez plutôt [CQ.form.PathField](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)**.

* `pathfield`

  [CQ.form.PathField](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Le `PathField` est un champ de saisie conçu pour les chemins d’accès avec fin de chemin et un bouton permettant d’ouvrir un [CQ.BrowseDialog](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) pour parcourir le référentiel du serveur. Il peut également parcourir des paragraphes de page pour générer des liens avancés.

* `progress`

  [CQ.Ext.ProgressBar](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Un composant de barre de progression pouvant être mis à jour. La barre de progression prend en charge deux modes différents : manuel et automatique.

  En mode manuel, vous êtes responsable de l’affichage, de la mise à jour (via [updateProgress](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)) et de l’effacement de la barre de progression selon les besoins à partir de votre propre code. Cette méthode est la plus appropriée lorsque vous souhaitez afficher la progression.

* `propertygrid`

  [CQ.Ext.grid.PropertyGrid](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

   Mise en œuvre de grille spécialisée conçue pour imiter la grille de propriété classique figurant généralement dans les IDE de développement. Chaque ligne dans la grille représente une propriété d’un objet, et les données sont stockées sous la forme d’un ensemble de paires nom/valeur dans [CQ.Ext.grid.PropertyRecord](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html).

* `propgrid`

  [CQ.PropertyGrid](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  La `PropertyGrid` est une grille générique utilisée pour afficher et modifier les propriétés des objets.

* `quicktip`

  [CQ.Ext.QuickTip](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  `@xtype quicktip` - Classe d’info-bulle spécialisée pour les info-bulles qui peuvent être spécifiées dans les balises et gérées automatiquement par l’instance [CQ.Ext.QuickTips](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) globale. Consultez l’en-tête de classe QuickTips pour en savoir plus sur l’utilisation et consulter des exemples supplémentaires.

* `radio`

  [CQ.Ext.form.Radio](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Champ de `radio` unique. Identique à la case à cocher, mais fournie à titre de commodité pour définir automatiquement le type d’entrée. Le navigateur regroupe automatiquement les boutons radio lorsque chaque bouton radio du groupe utilise le même nom.


* `radiogroup`

  [CQ.Ext.form.RadioGroup](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Conteneur de regroupement pour les contrôles [CQ.Ext.form.Radio](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html).

* `referencesdialog`

  [CQ.wcm.ReferencesDialog](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  La `ReferencesDialog` est une boîte de dialogue permettant d’afficher les références sur une page.

* `restoretreedialog`

  [CQ.wcm.RestoreTreeDialog](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  L’`RestoreTreeDialog` est une boîte de dialogue permettant de restaurer une version précédente d’une arborescence.

* `restoreversiondialog`

  [CQ.wcm.RestoreVersionDialog](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  RestoreVersionDialog est une boîte de dialogue permettant de restaurer une version précédente d’une page.

* `richtext`

  [CQ.form.RichText](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  L’`RichText` fournit un champ de formulaire pour la modification des informations de texte stylisé (texte enrichi).

  Le composant `RichText` fournit actuellement les fonctionnalités suivantes :

* `rolloutplan`

  [CQ.wcm.msm.RolloutPlan](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  RolloutPlan fournit une boîte de dialogue pour surveiller la progression du déploiement d’une page. Un [CQ.wcm.msm.RolloutWizard](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) démarre le plan de déploiement.

* `rolloutwizard`

  [CQ.wcm.msm.RolloutWizard](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Le `RolloutWizard` fournit un assistant pour déployer une page. RolloutWizard démarre un [CQ.wcm.msm.RolloutPlan](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html).

* `searchfield`

  [CQ.form.SearchField](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  La `SearchField` contient un champ de recherche qui fournit les résultats dans une liste déroulante. Vous pouvez l’utiliser pour effectuer une recherche dans le référentiel.

* `selection`

  [CQ.form.Selection](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  L’`Selection` permet à l’utilisateur de choisir entre plusieurs options. Les options peuvent faire partie de la configuration ou être chargées à partir d’une réponse JSON. La sélection peut être rendue sous forme de liste déroulante (sélectionner) ou de zone de liste modifiable (sélectionner plus entrée de texte libre).

* `sidekick`

  [CQ.wcm.Sidekick](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Le `Sidekick` est un helper flottant qui fournit à l’utilisateur des outils courants pour la modification de pages.

* `siteadmin`

  [CQ.wcm.SiteAdmin](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  `SiteAdmin` est une console fournissant des fonctions d’administration de gestion de contenu web.

* `siteimporter`

  [CQ.wcm.SiteImporter](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Le `SiteImporter` permet d’importer des sites web complets et de créer des projets initiaux.

* `sizefield`

  [CQ.form.SizeField](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  La `SizeField` permet à l’utilisateur de saisir la largeur et la hauteur (par exemple, pour une image).

* `slider`

  [CQ.Ext.Slider](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Slider qui prend en charge l’orientation verticale ou horizontale, les réglages de clavier, l’alignement configurable, le clic sur les axes et l’animation. Il peut être ajouté en tant qu’élément à n’importe quel conteneur. Par exemple, utilisation : ...

* `slideshow`

  [CQ.form.Slideshow](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Le composant Diaporama vous permet de définir et de modifier un ensemble d’images et de titres d’image. Les utilisateurs peuvent voir la visionneuse sous forme de diaporama.

  Le composant Diaporama repose sur le composant [CQ.form.SmartImage](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html).

* `smartfile`

  [CQ.form.SmartFile](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  SmartFile est un téléchargeur de fichiers intelligent.

  Si un plug-in Flash (version 9 ou ultérieure) est installé, les chargements sont exécutés à l’aide de la bibliothèque SWFupload qui permet de gérer facilement les chargements.

* `smartimage`

  [CQ.form.SmartImage](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  SmartImage est un téléchargeur d’images intelligent. Il fournit des outils pour traiter une image chargée, par exemple un outil pour définir des images à zones cliquables et un recadrage d’image.

  Le composant est conçu pour être utilisé dans un onglet de boîte de dialogue distinct.

* `spacer`

  [CQ.Ext.Spacer](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Utilisé pour fournir un espace dimensionnable dans une mise en page.

* `spinner`

  [CQ.form.Spinner](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Le `Spinner` est un champ de déclenchement pour les valeurs numériques, de date ou d’heure. La valeur peut être augmentée et diminuée en utilisant les déclencheurs haut et bas fournis, la roulette de défilement ou les touches.

* `splitbutton`

  [CQ.Ext.SplitButton](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  `splitbutton` qui fournit une flèche déroulante intégrée pouvant déclencher un événement séparément de l’événement de clic par défaut du bouton. En règle générale, il est utilisé pour afficher un menu déroulant qui fournit des options supplémentaires à l’action du bouton principal, mais tout gestionnaire personnalisé peut fournir la mise en œuvre `arrowclick`.

* `static`

  [CQ.Static](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Le `Static` peut être utilisé pour afficher du texte arbitraire ou HTML.

* `statistics`

  [CQ.wcm.Statistics](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Le `Statistics` affiche les impressions de page sous la forme d’un graphique. Le widget permet de sélectionner une période. Les statistiques doivent être affichées pour cette période.

* `store`

  [CQ.Ext.data.Store](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  La classe `Store` encapsule un cache côté client d’objets [Record](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) qui fournissent des données d’entrée pour des composants tels que [GridPanel](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html), [ComboBox](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) ou [DataView](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html).

* `suggestfield`

  [CQ.form.SuggestField](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  L’`SuggestField` fournit à l’utilisateur des suggestions basées sur sa saisie.

* `switcher`

  [CQ.Switcher](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Le `Switcher` fournit un groupe de boutons pour la barre d’en-tête d’une console afin de basculer entre les sites web, Digital Assets, les outils, le workflow et la sécurité.

* `tableedit`

  [CQ.form.TableEdit](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  **Obsolète : utilisez plutôt [CQ.form.TableEdit2.](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)**

* `tableedit2`

  [CQ.form.TableEdit2](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Le `TableEdit2` fournit un widget pour la création de tableaux.

* `tabpanel`

  [CQ.Ext.TabPanel](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Conteneur d’onglets de base. TabPanels peut être utilisé exactement comme un [CQ.Ext.Panel](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) standard pour la mise en page, mais offre également une prise en charge spéciale pour contenir des composants enfants ([`items`](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)).

* `tags`

  [CQ.tagging.TagInputField](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  ```
  CQ.tagging.TagInputField
  ```

   est un widget de formulaire qui permet de saisir des balises. Il dispose d’un menu pop-up permettant de faire une sélection parmi les balises existantes, et comprend la saisie semi-automatique ainsi que de nombreuses autres fonctionnalités.

* `textarea`

  [CQ.Ext.form.TextArea](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Champ de texte multiligne. Peut être utilisé comme remplacement direct des champs de `textarea` traditionnels et ajoute la prise en charge du dimensionnement automatique.

* `textbutton`

  [CQ.TextButton](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Le `TextButton` fournit un lien de texte avec les fonctionnalités d’un [CQ.Ext.Button](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html).

* `textfield`

  [CQ.Ext.form.TextField](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Champ de texte de base. Peut être utilisé comme remplacement direct pour les entrées de texte classiques ou comme classe de base pour des contrôles d’entrée plus sophistiqués (comme [CQ.Ext.form.TextArea](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) et [CQ.Ext.form.ComboBox](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)).

* `thumbnail`

  [CQ.form.Thumbnail](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

* `timefield`

  [CQ.Ext.form.TimeField](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Elle fournit un champ d’entrée temporelle avec une liste déroulante temporelle et la validation temporelle automatique. Exemple d’utilisation : ...

* `tip`

  [CQ.Ext.Tip](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Classe de base pour [CQ.Ext.QuickTip](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) et [CQ.Ext.Tooltip](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) qui fournit la mise en page de base et le positionnement dont toutes les classes basées sur les conseils ont besoin. Cette classe peut être utilisée directement pour obtenir des conseils simples et positionnés de manière statique.

* `titleseparator`

  [CQ.menu.TitleSeparator](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Il ajoute une barre de séparation à un menu, utilisée pour diviser les groupes logiques d’éléments de menu. Le séparateur peut en outre avoir un titre.

* `toolbar`

  [CQ.Ext.Toolbar](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Classe de `Toolbar` de base. Bien que le [`defaultType`](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) de Toolbar soit [`button`](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html), les éléments Toolbar (les éléments enfants du conteneur Toolbar) peuvent être quasiment tout type de composant. Les éléments de la barre d’outils peuvent être créés explicitement via leurs constructeurs.

* `tooltip`

  [CQ.Ext.ToolTip](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Implémentation `tooltip` standard permettant de fournir des informations supplémentaires lorsque vous passez la souris sur un élément cible. @xtype tooltip.

* `treegrid`

  [CQ.tree.TreeGrid](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  @xtype `treegrid`

* `treepanel`

  [CQ.Ext.tree.TreePanel](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Le `TreePanel` fournit une représentation de l’interface utilisateur sous forme d’arborescence des données sous forme d’arborescence.

  Les [TreeNode](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) ajoutés à la `TreePanel` peuvent chacun contenir des métadonnées utilisées par votre application dans leur propriété [attributes](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html).

* `trigger`

  [CQ.Ext.form.TriggerField](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Il fournit un wrapper pratique pour les `TextFields` qui ajoute un bouton de déclenchement cliquable (qui ressemble par défaut à une zone de liste modifiable). Le déclencheur ne comporte aucune action par défaut. Vous devez donc attribuer une fonction pour implémenter le gestionnaire de clics de déclencheur en remplaçant [onTriggerClick](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html). Vous pouvez créer un `TriggerField` directement, car il s’affiche exactement comme une zone de liste modifiable.

* `uploaddialog`

  [CQ.UploadDialog](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Le `UploadDialog` permet à l’utilisateur de charger des fichiers dans le référentiel. Crée une boîte de dialogue de chargement.

* `userinfo`

  [CQ.UserInfo](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Élément de barre d’outils pour afficher le nom d’utilisateur actuel et autoriser des actions d’utilisateur comme la modification des propriétés et l’emprunt d’identité.

* `viewport`

  [CQ.Ext.Viewport](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Conteneur spécialisé représentant la zone d’application visible (le viewport du navigateur).

  Le `Viewport` s’affiche dans le corps du document et se dimensionne automatiquement à la taille de la fenêtre du navigateur et gère le redimensionnement de la fenêtre. Un seul viewport peut être créé.

* `window`

  [CQ.Ext.Window](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Panneau spécialisé destiné à être utilisé comme fenêtre d’application. Les fenêtres sont flottantes, [redimensionnables](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) et [glissables](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) par défaut. Les fenêtres peuvent être [agrandies](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) pour remplir le viewport, restaurées à leur taille antérieure et [réduites](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html).

* `xmlstore`

  [CQ.Ext.data.XmlStore](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Petite classe d’aide permettant de faciliter la création de [CQ.Ext.data.Store](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)s à partir de données XML. Un `XmlStore` est automatiquement configuré avec un [CQ.Ext.data.XmlReader](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html).

  `cqinclude` - Un pseudo xtype qui inclut des définitions de widget provenant d’un chemin différent dans le référentiel. Elle est le plus souvent utilisée dans les boîtes de dialogue de page. Il n’existe aucune classe de widget JavaScript pour ce xtype. La classe `CQ.Util` le traite à l’aide de la fonction `formatData()` .
