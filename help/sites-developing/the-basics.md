---
title: Concepts de base d’AEM
description: Vue d’ensemble des concepts de base de la structure d’Adobe Experience Manager (AEM) et des méthodes de développement sur AEM, notamment le fonctionnement de JCR, de Sling, d’OSGi, de Dispatcher, des workflows et de MSM.
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: introduction
content-type: reference
solution: Experience Manager, Experience Manager Sites
feature: Developing
role: Developer
exl-id: fe3735ff-5c9b-4eb8-bf1d-f2189ec7e26f
source-git-commit: a869ffbc6015fd230285838d260434d9c0ffbcb0
workflow-type: tm+mt
source-wordcount: '3251'
ht-degree: 99%

---

# Concepts de base d’AEM {#aem-core-concepts}

>[!NOTE]
>
>Avant de vous familiariser avec les concepts de base d’Adobe Experience Manager (AEM), Adobe recommande de suivre le tutoriel WKND du document [Prise en main du développement AEM Sites](/help/sites-developing/getting-started.md). Il donne une vue d’ensemble du processus de développement AEM et présente les concepts de base.

## Conditions préalables pour le développement sur AEM {#prerequisites-for-developing-on-aem}

Vous avez besoin des compétences suivantes pour développer sur AEM :

* Connaissances de base des techniques des applications web, notamment :

   * le cycle de requête-réponse (XMLHttpRequest/XMLHttpResponse)
   * HTML
   * CSS
   * JavaScript

* connaissance du fonctionnement d’Experience Server (CRX), y compris de l’explorateur de contenu
* Pour développer dans l’interface utilisateur classique, des connaissances de base de JSP (JavaServer Pages), notamment la capacité à comprendre et modifier des exemples JSP simples, sont également requises.

Il est également recommandé de lire et de suivre les [Recommandations et bonnes pratiques](/help/sites-developing/dev-guidelines-bestpractices.md).

## Java™ Content Repository {#java-content-repository}

La norme Java™ Content Repository (JCR), [JSR 283](https://developer.adobe.com/experience-manager/reference-materials/spec/jcr/2.0/index.html), spécifie un moyen, indépendant du fournisseur et de l’implémentation, d’accéder au contenu d’un référentiel de contenu à un niveau granulaire et de manière bidirectionnelle.

La spécification est gérée par Adobe Research (Suisse) AG.

Le package [JCR API 2.0](https://developer.adobe.com/experience-manager/reference-materials/spec/javax.jcr/javadocs/jcr-2.0/index.html), javax.jcr.&ast; est utilisé pour l’accès direct et la manipulation du contenu du référentiel.

## Experience Server (CRX) et Jackrabbit {#experience-server-crx-and-jackrabbit}

Experience Server fournit les services d’expérience sur lesquels AEM est basé et qui servent à créer des applications personnalisées. Il incorpore également le référentiel de contenu basé sur Jackrabbit.

[Apache Jackrabbit](https://jackrabbit.apache.org/jcr/index.html) est une mise en œuvre open source, entièrement conforme, de l’API JCR 2.0.

## Traitement des requêtes Sling {#sling-request-processing}

### Introduction à Sling {#introduction-to-sling}

AEM repose sur [Sling](https://sling.apache.org/index.html), un framework d’application web basé sur des principes REST. Il facilite le développement d’applications orientées contenu. Sling utilise un référentiel JCR, tel qu’Apache Jackrabbit, ou dans le cas d’AEM, le référentiel de contenu CRX, comme magasin de données. The Apache Software Foundation a contribué au développement de Sling. Plus d’informations sont disponibles sur Apache.

Avec Sling, le type de contenu à diffuser n’est pas la première considération en matière de traitement. Il s’agit plutôt de savoir si l’URL se résout en un objet de contenu pour lequel un script peut ensuite être identifié afin d’effectuer le rendu. Cela offre une excellente prise en charge aux auteurs et autrices de contenu web pour créer des pages facilement personnalisées selon leurs besoins.

Les avantages liés à cette flexibilité sont évidents dans les applications comportant un vaste éventail d’éléments de contenu différents ou dans les cas où des pages facilement personnalisables sont nécessaires. En particulier lors de la mise en œuvre d’un système de gestion de contenu web tel que WCM dans la solution AEM.

Voir [Découvrir Sling en 15 minutes](https://sling.apache.org/documentation/getting-started/discover-sling-in-15-minutes.html) pour connaître les premières étapes de développement avec Sling.

Le diagramme ci-après explique la résolution du script Sling. Il montre comment passer de la requête HTTP au nœud de contenu, du nœud de contenu au type de ressource, du type de ressource au script, ainsi que les variables de script disponibles.

![Présentation de la résolution du script Apache Sling](assets/sling-cheatsheet-01.png)

Le diagramme suivant explique tous les paramètres de requête masqués, mais puissants, que vous pouvez utiliser avec SlingPostServlet. Il inclut le gestionnaire par défaut pour toutes les requêtes POST qui vous donne des options infinies pour créer, modifier, supprimer, copier et déplacer des nœuds dans le référentiel.

![Utilisation de SlingPostServlet](assets/sling-cheatsheet-02.png)

### Sling est centré sur le contenu {#sling-is-content-centric}

Sling est *axé sur le contenu*. Cela signifie que le traitement est axé sur le contenu, car chaque requête (HTTP) est mappée sur le contenu sous la forme d’une ressource JCR (un nœud de référentiel) :

* La première cible est la ressource (nœud JCR) qui contient le contenu.
* Ensuite, la représentation, ou script, est localisée à partir des propriétés de la ressource en combinaison avec certaines parties de la requête (par exemple des sélecteurs et/ou l’extension).

### Sling RESTful {#restful-sling}

En raison de son approche centrée sur le contenu, Sling implémente un serveur orienté REST et propose ainsi un nouveau concept dans les frameworks d’applications web. Les avantages sont les suivants :

* Niveau RESTful, et pas seulement en surface ; les ressources et les représentations sont correctement modélisées dans le serveur
* Supprime un ou plusieurs modèles de données.

   * Auparavant, les éléments suivants étaient nécessaires : structure de l’URL, objets métier, schéma de base de données ;
   * Cela est désormais réduit à : URL = ressource = structure JCR

### Décomposition d’URL {#url-decomposition}

Dans Sling, le traitement est piloté par l’URL de la requête utilisateur. C’est l’URL qui définit le contenu à afficher par les scripts appropriés. Pour ce faire, les informations sont extraites de l’URL.

Si nous analysons l’URL suivante :

```xml
https://myhost/tools/spy.printable.a4.html/a/b?x=12
```

Nous pouvons la diviser en plusieurs parties composites :

| protocol | host | content path | selectors | Extension |  | Suffixe |  | params |
|---|---|---|---|---|---|---|---|---|
| https:// | myhost | tools/spy | .printable.a4. | html | / | a/b | ? | x=12 |

**protocol** HTTP

**host** Nom du site web.

**content path** Chemin d’accès spécifiant le contenu à rendre. Utilisé avec l’extension. Dans cet exemple, il se traduit par `tools/spy.html`.

**selectors** : utilisé pour les méthodes secondaires de rendu du contenu. Dans cet exemple, il s’agit de la version imprimable au format A4.

**extension** Format de contenu ; spécifie également le script à utiliser pour le rendu.

**suffix** Peut servir à spécifier des informations supplémentaires.

**params** : tout paramètre requis pour le contenu dynamique.

#### De l’URL au contenu et aux scripts {#from-url-to-content-and-scripts}

En suivant ces principes :

* Le mappage utilise le chemin d’accès au contenu extrait de la requête pour localiser la ressource.
* Lorsque la ressource appropriée est localisée, le type de ressource sling est extrait et utilisé pour localiser le script à appliquer au rendu du contenu.

L’image ci-dessous illustre le mécanisme utilisé, décrit plus en détail dans les sections suivantes.

![chlimage_1-86](assets/chlimage_1-86a.png)

Avec Sling, vous spécifiez le script à appliquer pour le rendu d’une entité donnée (en définissant la propriété `sling:resourceType` dans le nœud JCR). Ce mécanisme offre plus de liberté que celui selon lequel le script accède aux entités de données (comme le ferait une instruction SQL dans un script PHP) puisqu’une ressource peut avoir plusieurs rendus.

#### Mappage des requêtes vers les ressources {#mapping-requests-to-resources}

La requête est décomposée et les informations nécessaires sont extraites. Recherche du référentiel pour la ressource demandée (nœud de contenu) :

* Tout d’abord, Sling vérifie s’il existe un nœud à l’emplacement spécifié dans la demande. Par exemple, `../content/corporate/jobs/developer.html`.
* Si aucun nœud n’est identifié, l’extension est supprimée et la recherche recommence. Par exemple, `../content/corporate/jobs/developer`.
* Si aucun nœud n’est identifié, Sling renvoie le code 404 (Not Found).

Sling permet également à des éléments autres que des nœuds JCR d’être des ressources, mais il s’agit là d’une fonctionnalité avancée.

### Localisation du script {#locating-the-script}

Lorsque la ressource appropriée (nœud de contenu) est localisée, le **type de ressource sling** est extrait. Il s’agit d’un chemin d’accès qui localise le script à utiliser pour le rendu du contenu.

Le chemin spécifié par le `sling:resourceType` peut être :

* absolu
* relatif à un paramètre de configuration

  Les chemins relatifs sont recommandés par Adobe car ils contribuent à plus de portabilité.

Tous les scripts Sling sont stockés dans des sous-dossiers `/apps` ou `/libs` qui font l’objet d’une recherche dans cet ordre (voir [Personnalisation de composants et d’autres éléments](/help/sites-developing/dev-guidelines-bestpractices.md#customizing-components-and-other-elements)).

Un certain nombre d’autres points sont à noter :

* Si la méthode (GET, POST) est requise, elle est indiquée en majuscules selon la spécification HTTP, par exemple jobs.POST.esp (voir ci-dessous).
* Plusieurs moteurs de script sont pris en charge :

   * HTL (HTML Template Language : il s’agit du système de modèle côté serveur préféré et recommandé d’Adobe Experience Manager pour le langage HTML) : `.html`
   * Pages ECMAScript (JavaScript) (exécution côté serveur) : `.esp, .ecma`
   * Pages de serveur Java™ (exécution côté serveur) : `.jsp`
   * Compileur de servlet Java™ (exécution côté serveur) : `.java`
   * Modèles JavaScript (exécution côté client) : `.jst`

La liste des moteurs de script pris en charge par l’instance donnée d’AEM figure dans la Felix Management Console (`http://<host>:<port>/system/console/slingscripting`).

En outre, Apache Sling prend en charge l’intégration à d’autres moteurs de script courants (par exemple, Groovy, JRuby, Freemarker) et offre un moyen d’intégrer de nouveaux moteurs de script.

En reprenant l’exemple ci-dessus, si `sling:resourceType` est `hr/jobs` alors pour :

* Les requêtes GET/HEAD et les URL se terminant par .htmp (types de requête par défaut, format par défaut)

  Le script sera /apps/hr/jobs/jobs.esp ; la dernière section de sling:resourceType forme le nom du fichier.

* Requêtes POST (tous les types de requête, à l’exclusion des GET/HEAD, le nom de la méthode doit être en majuscules)

  POST sera utilisé dans le nom du script.

  Le script est `/apps/hr/jobs/jobs.POST.esp`.

* URL dans d’autres formats, qui ne se terminent pas par .html

  Par exemple, `../content/corporate/jobs/developer.pdf`

  Le script est `/apps/hr/jobs/jobs.pdf.esp` ; le suffixe est ajouté au nom du script.

* URL avec sélecteurs

  Les sélecteurs peuvent être utilisés pour afficher le même contenu dans un autre format. Par exemple une version imprimable, un flux RSS ou un résumé.

  Si nous étudions une version imprimable dans laquelle le sélecteur peut être *imprimé*, comme dans `../content/corporate/jobs/developer.print.html`.

  Le script est `/apps/hr/jobs/jobs.print.esp` ; le sélecteur est ajouté au nom du script.

* Si aucun sling:resourceType n’a été défini :

   * le chemin d’accès au contenu est utilisé pour rechercher un script correspondant (si ResourceTypeProvider basé sur un chemin est actif) ;

     par exemple, le script pour `../content/corporate/jobs/developer.html` génère une recherche dans `/apps/content/corporate/jobs/` ;

   * le type de nœud principal est utilisé.

* Si aucun script n’est trouvé, le script par défaut est utilisé.

  Le rendu par défaut est pris en charge sous la forme de texte brut (.txt), HTML (.html) et JSON (.json) qui répertorie toutes les propriétés du nœud (correctement mises en forme). Le rendu par défaut pour l’extension .res, ou les requêtes sans extension de requête, consiste à spouler la ressource (si possible).
* Pour la gestion des erreurs HTTP (codes 403 ou 404), Sling recherche un script dans :

   * l’emplacement /apps/sling/servlet/errorhandler pour les [scripts personnalisés](/help/sites-developing/customizing-errorhandler-pages.md)
   * ou l’emplacement des scripts standard /libs/sling/servlet/errorhandler/403.esp, ou 404.esp, respectivement.

Si plusieurs scripts s’appliquent pour une requête donnée, celui avec la meilleure correspondance est sélectionné. Plus une correspondance est précise, mieux c’est. En d’autres termes, plus il y a de correspondances avec les sélecteurs, mieux c’est, indépendamment de toute correspondance entre l’extension de la requête ou le nom de la méthode.

Par exemple, envisagez une demande d’accès à la ressource
`/content/corporate/jobs/developer.print.a4.html`
de type
`sling:resourceType="hr/jobs"`

En supposant que les scripts suivants sont présents au bon emplacement :

1. `GET.esp`
1. `jobs.esp`
1. `html.esp`
1. `print.esp`
1. `print.html.esp`
1. `print/a4.esp`
1. `print/a4/html.esp`
1. `print/a4.html.esp`

L’ordre de préférence serait (8) – (7) – (6) – (5) – (4) – (3) – (2) – (1).

En plus des types de ressources (principalement définis par la propriété `sling:resourceType`), il existe également le super type de ressource. Il est généralement indiqué par la propriété `sling:resourceSuperType`. Ces super types sont aussi pris en compte lors de la recherche d’un script. Les super types de ressources présentent l’avantage de former une hiérarchie de ressources où le type de ressource par défaut `sling/servlet/default` (utilisé par les servlets par défaut) est effectivement la racine.

Le super type de ressource d’une ressource peut être défini de deux manières :

* par la propriété `sling:resourceSuperType` de la ressource ;
* par la propriété `sling:resourceSuperType` du nœud vers lequel pointe `sling:resourceType`.

Par exemple :

* /

   * a
   * b

      * sling:resourceSuperType = a

   * c

      * sling:resourceSuperType = b

   * x

      * sling:resourceType = c

   * y

      * sling:resourceType = c
      * sling:resourceSuperType = a

La hiérarchie de type de :

* `/x`
   * est `[ c, b, a, <default>]`
* alors que pour `/y`
   * la hiérarchie est `[ c, a, <default>]`.

Ceci est dû au fait que `/y` possède la propriété `sling:resourceSuperType` contrairement à `/x`, et donc son super-type est issu de son type de ressource.

#### Les scripts Sling ne peuvent pas être appelés directement. {#sling-scripts-cannot-be-called-directly}

Dans Sling, les scripts ne peuvent pas être appelés directement, car cela violerait le concept strict d’un serveur REST ; vous mélangeriez les ressources et les représentations.

Si vous appelez la représentation (le script) directement, vous masquez la ressource dans le script, donc le framework (Sling) ne peut plus la détecter. Vous perdez ainsi certaines fonctionnalités :

* Le traitement automatique des méthodes HTTP autres que GET, notamment :

   * les méthodes POST, PUT, DELETE qui sont gérées avec une implémentation par défaut de Sling ;
   * le script `POST.jsp` dans votre emplacement sling:resourceType.

* L’architecture de votre code perd de son intégrité et de sa structure qui sont primordiales dans les développements à grande échelle.

### API Sling {#sling-api}

Elle utilise le package API Sling org.apache.sling.&ast; et les bibliothèques de balises.

### Référencement d’éléments existants avec sling:include {#referencing-existing-elements-using-sling-include}

En dernier lieu, il faut considérer la nécessité de référencer les éléments existants dans les scripts.

Des scripts plus complexes (agrégation de scripts) doivent accéder à plusieurs ressources (navigation, barre latérale, pied de page, éléments d’une liste, par exemple) en ajoutant la *ressource*.

Pour ce faire, utilisez la commande sling:include(&quot;/&lt;chemin>/&lt;ressource>&quot;). Cela permet d’inclure de façon efficace la définition de la ressource référencée, comme dans l’instruction suivante qui fait référence à une définition existante pour le rendu des images :

```xml
%><sling:include resourceType="geometrixx/components/image/img"/><%
```

## OSGI {#osgi}

OSGi désigne une architecture permettant de développer et de déployer des applications et des bibliothèques modulaires (également connu sous le nom de Dynamic Module System for Java™). Les conteneurs OSGi vous permettent de décomposer votre application en modules distincts (des fichiers jar contenant des méta-informations supplémentaires appelés « bundles » dans le jargon OSGi) et de gérer les interdépendances qui existent entre eux avec :

* Services mis en œuvre dans le conteneur
* Contrat entre le conteneur et votre application

Ces services et contrats fournissent une architecture qui permet à des éléments particuliers de se découvrir dynamiquement les uns les autres à des fins de collaboration.

Un framework OSGi vous offre ensuite le chargement/déchargement dynamique, la configuration et le contrôle de ces lots, sans nécessiter de redémarrage.

>[!NOTE]
>
>Vous trouverez des informations complètes sur la technologie OSGi sur le [site web d’OSGi](https://www.osgi.org).
>
>En particulier, la page Basic Education (formation de base) contient un ensemble de présentations et de tutoriels.

Cette architecture vous permet d’étendre Sling avec des modules spécifiques à l’application. Sling, et donc CQ5, utilise l’implémentation [Apache Felix](https://felix.apache.org/documentation/index.html) d’OSGI (Open Services Gateway Initiative) et est basé sur les spécifications OSGi Service Platform Release 4, Version 4.2. Les deux sont des groupes de lots OSGi qui s’exécutent dans un framework OSGi.

Vous pouvez ainsi effectuer les actions suivantes sur l’un des packages de votre installation :

* installation
* démarrer
* arrêter
* mise à jour
* désinstallation
* afficher le statut
* accéder à des informations plus détaillées (par exemple, nom symbolique, version et emplacement) pour des bundles en particulier

Pour plus d’informations, reportez-vous aux sections [Console web](/help/sites-deploying/web-console.md), [Configuration OSGI](/help/sites-deploying/configuring-osgi.md) et [Paramètres de configuration OSGi](/help/sites-deploying/osgi-configuration-settings.md).

## Objets de développement dans l’environnement AEM {#development-objects-in-the-aem-environment}

Les éléments suivants présentent un intérêt pour le développement :

**Élément** Un élément est un nœud ou une propriété.

Pour plus d’informations sur la manipulation des objets Élément, reportez-vous aux [documents Java™](https://developer.adobe.com/experience-manager/reference-materials/spec/javax.jcr/javadocs/jcr-2.0/javax/jcr/Item.html) de l’interface javax.jcr.Item.

**Nœud (et leurs propriétés)** Les nœuds et leurs propriétés sont définis dans la spécification JCR API 2.0 (JSR 283). Ils stockent le contenu, les définitions d’objets, les scripts de rendu ainsi que d’autres données.

Les nœuds définissent la structure du contenu et leurs propriétés stockent le contenu réel et les métadonnées.

Les nœuds de contenu pilotent le rendu. Sling récupère le nœud de contenu de la requête entrante. La propriété sling:resourceType de ce nœud pointe vers le composant de rendu Sling à utiliser.

Un nœud, qui est un nom JCR, est également appelé « ressource » dans l’environnement Sling.

Par exemple, pour obtenir les propriétés du nœud actif, vous pouvez utiliser le code suivant dans votre script :

`PropertyIterator properties = currentNode.getProperties();`

currentNode étant l’objet du nœud actif.

Pour plus d’informations sur la manipulation d’objets de nœud, voir [documents Java™](https://developer.adobe.com/experience-manager/reference-materials/spec/javax.jcr/javadocs/jcr-2.0/javax/jcr/Node.html).

**Widget** Dans AEM, toutes les entrées utilisateur sont gérées par des widgets. Ils sont souvent utilisés pour contrôler la modification d’un élément de contenu.

Les boîtes de dialogue sont créées en combinant des widgets.

AEM a été développé à l’aide de la bibliothèque de widgets ExtJS.

**Boîte de dialogue** Une boîte de dialogue est un type spécial de widget.

Pour modifier le contenu, AEM utilise des boîtes de dialogue définies par le développeur de l’application. Ils combinent une série de widgets pour présenter à l’utilisateur età l’utilisatrice tous les champs et actions nécessaires pour modifier le contenu associé.

Les boîtes de dialogue sont également utilisées pour modifier les métadonnées et par divers outils d’administration.

**Composant** Un composant logiciel est un élément système offrant un service ou un événement prédéfini et capable de communiquer avec d’autres composants.

Dans AEM, un composant est souvent utilisé pour effectuer le rendu du contenu d’une ressource. Lorsque la ressource est une page, le composant chargé de son rendu est appelé « composant de niveau supérieur » ou « composant de page ». Cependant, un composant n’a pas à effectuer le rendu du contenu ni à être lié à une ressource spécifique. Par exemple, un composant de navigation affiche des informations sur plusieurs ressources.

La définition d’un composant comprend ce qui suit :

* le code utilisé pour effectuer le rendu du contenu ;
* une boîte de dialogue pour la saisie de l’utilisateur ou de l’utilisatrice et la configuration du contenu obtenu.

**Modèle** Un modèle est la base d’un type de page spécifique. Lors de la création d’une page dans l’onglet Sites web, l’utilisateur ou l’utilisatrice doit sélectionner un modèle. La nouvelle page est créée en copiant ce modèle.

Un modèle est une hiérarchie de nœuds ayant la même structure que la page à créer, mais sans contenu réel.

Il définit le composant de page utilisé pour afficher la page et le contenu par défaut (contenu principal de premier niveau). Le contenu définit la manière dont il est rendu, AEM étant centré sur le contenu.

**Composant de page (composant de niveau supérieur)** Composant à utiliser pour effectuer le rendu de la page.

**Page** Une page est une « instance » d’un modèle.

Une page comporte un nœud de hiérarchie de type cq:Page et un nœud de contenu de type cq:PageContent. La propriété sling:resourceType du nœud de contenu pointe vers le composant Page utilisé pour le rendu de la page.

Par exemple, pour obtenir le nom de la page active, vous pouvez utiliser le code suivant dans votre script :

S`tring pageName = currentPage.getName();`

currentPage étant l’objet de la page active. Pour plus d’informations sur la manipulation des objets Page, voir les [documents Java™](https://developer.adobe.com/experience-manager/reference-materials/6-5-lts/javadoc/com/day/cq/wcm/api/Page.html).

**Gestionnaire de pages** Le gestionnaire de pages est une interface qui fournit des méthodes pour les opérations au niveau de la page.

Par exemple, pour obtenir la page contenant une ressource, vous pouvez utiliser le code suivant dans votre script :

Page myPage = pageManager.getContainerPage(myResource);

pageManager étant l’objet de gestionnaire de pages et myResource un objet de ressource. Pour plus d’informations sur les méthodes fournies par le gestionnaire de pages, reportez-vous aux [documents Java™](https://developer.adobe.com/experience-manager/reference-materials/6-5-lts/javadoc/com/day/cq/wcm/api/PageManager.html).

## Structure dans le référentiel {#structure-within-the-repository}

La liste suivante propose une vue d’ensemble de la structure que vous verrez dans le référentiel.

>[!CAUTION]
>
>Les modifications apportées à cette structure, ou aux fichiers qu’elle contient, doivent être entreprises avec prudence.
>
>Des modifications sont nécessaires lorsque vous développez, mais vous devez veiller à bien comprendre les implications de toute modification que vous apportez.

>[!CAUTION]
>
>Vous ne devez rien modifier dans le chemin `/libs`. Pour la configuration et d’autres modifications, copiez l’élément de `/libs` dans `/apps` et apportez des modifications dans `/apps`.

* `/apps`

   Application connexe qui inclut des définitions de composants spécifiques à votre site web. Les composants que vous développez peuvent être basés sur les composants prêts à l’emploi disponibles dans `/libs/foundation/components`.

* `/content`

  Contenu créé pour votre site web.

* `/etc`

* `/home`

  Informations sur les utilisateurs et les groupes.

* `/libs`

   Bibliothèques et définitions appartenant au noyau d’AEM. Les sous-dossiers dans `/libs` représentent les fonctionnalités d’AEM prêtes à l’emploi telles que la recherche ou la réplication. Le contenu de `/libs` ne doit pas être modifié car il affecte le fonctionnement d’AEM. Les fonctionnalités spécifiques à votre site web doivent être développées sous `/apps` (voir [Personnalisation de composants et d’autres éléments](/help/sites-developing/dev-guidelines-bestpractices.md#customizing-components-and-other-elements)).

* `/tmp`

  Espace de travail temporaire.

* `/var`

  Fichiers qui évoluent et sont mis à jour par le système, tels que les journaux d’audit, les statistiques, la gestion des événements.

## Environnements {#environments}

Avec AEM, un environnement de production se compose souvent de deux types d’instances : [une instance de création et une instance de publication](/help/sites-deploying/deploy.md#author-and-publish-installs).

## Le dispatcher {#the-dispatcher}

Le dispatcher est un outil Adobe qui sert à la mise en cache et/ou l’équilibrage de charge. Vous trouverez plus d’informations sous [le Dispatcher](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/dispatcher.html?lang=fr).

## FileVault (système de révision source) {#filevault-source-revision-system}

FileVault fournit à votre référentiel JCR des fonctions de mappage du système de fichiers et de gestion des versions. Il peut être utilisé pour gérer des projets de développement AEM avec une prise en charge complète du stockage et du contrôle de version du code de projet, du contenu, des configurations, etc., dans les systèmes de contrôle de version standard (par exemple, Subversion).

Voir la documentation [Outil FileVault](/help/sites-developing/ht-vlttool.md) pour plus d’informations.

## Workflows {#workflows}

Votre contenu est souvent soumis à des processus organisationnels, y compris des étapes telles que l’approbation et la validation par différents participants. Ces processus peuvent être représentés sous forme de workflows, [définis et développés dans AEM](/help/sites-developing/workflows-models.md), puis appliqués aux [pages de contenu appropriées](/help/sites-administering/workflows.md) ou aux [ressources numériques](/help/assets/assets-workflow.md) selon les besoins.

Le moteur de workflow permet de gérer l’implémentation de vos workflows et leur application ultérieure dans votre contenu.

## Gestion de plusieurs sites {#multi-site-management}

Multi Site Manager (MSM) permet de gérer facilement plusieurs sites web partageant du contenu commun. MSM vous permet de définir des relations entre les sites, de sorte que les modifications de contenu d’un site soient automatiquement répliquées sur d’autres sites.

Par exemple, les sites web sont souvent proposés dans plusieurs langues à l’intention d’un public international. Lorsque le nombre de sites dans la même langue est faible (de trois à cinq), un processus manuel de synchronisation du contenu entre les sites est possible. Cependant, lorsque le nombre de sites augmente ou que plusieurs langues sont impliquées, il devient plus efficace d’automatiser le processus.

* Gérez efficacement les différentes versions linguistiques d’un site web.
* Mettez automatiquement à jour un ou plusieurs sites à partir d’un site source :

   * Appliquez une structure de base et diffusez du contenu similaire sur plusieurs sites.
   * Optimisez l’utilisation des ressources disponibles.
   * Conservez une harmonie visuelle entre les sites.
   * Concentrez vos efforts sur la gestion du contenu qui diffère entre les sites.

Pour plus d’informations, consultez la section [Multi Site Manager](/help/sites-administering/msm.md).
