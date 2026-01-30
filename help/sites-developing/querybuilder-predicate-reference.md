---
title: Référence des prédicats de Query Builder
description: Référence des prédicats pour l’API Query Builder.
contentOwner: sarchiz
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: platform
solution: Experience Manager, Experience Manager Sites
feature: Developing,Search,Query Builder
role: Developer
exl-id: c044d541-24d6-4975-9b38-6a4317a16358
source-git-commit: a85b54d5a7c3b00f95f439941a390dcfee883187
workflow-type: tm+mt
source-wordcount: '2291'
ht-degree: 65%

---

# Référence des prédicats de Query Builder{#query-builder-predicate-reference}

>[!CAUTION]
>
>Les informations contenues dans cette page ne sont pas exhaustives.
>
>Pour plus d’informations, reportez-vous à la liste figurant dans **Prédicats disponibles** dans la console de débogage Query Builder, par exemple, à l’adresse :
>* [http://localhost:4502/libs/cq/search/content/querydebug.html](http://localhost:4502/libs/cq/search/content/querydebug.html)
>
>Pour obtenir un exemple, reportez-vous à :
>
>* [http://localhost:4502/system/console/services?filter=%28component.factory%3Dcom.day.cq.search.eval.PredicateEvaluator%2F*%29](http://localhost:4502/system/console/services?filter=%28component.factory%3Dcom.day.cq.search.eval.PredicateEvaluator%2F*%29)

## Général {#general}

* [root](#root)
* [group](#group)
* [orderby](#orderby)

## Prédicats {#predicates}

* [boolproperty](/help/sites-developing/querybuilder-predicate-reference.md#boolproperty)
* [contentfragment](/help/sites-developing/querybuilder-predicate-reference.md#contentfragment)
* [dateComparison](/help/sites-developing/querybuilder-predicate-reference.md#datecomparison)
* [daterange](/help/sites-developing/querybuilder-predicate-reference.md#daterange)
* [excludepaths](/help/sites-developing/querybuilder-predicate-reference.md#excludepaths)
* [fulltext](/help/sites-developing/querybuilder-predicate-reference.md#fulltext)
* [hasPermission](/help/sites-developing/querybuilder-predicate-reference.md#haspermission)
* [language](/help/sites-developing/querybuilder-predicate-reference.md#language)
* [mainasset](/help/sites-developing/querybuilder-predicate-reference.md#mainasset)
* [memberOf](/help/sites-developing/querybuilder-predicate-reference.md#memberof)
* [nodename](/help/sites-developing/querybuilder-predicate-reference.md#nodename)
* [notexpired](/help/sites-developing/querybuilder-predicate-reference.md#notexpired)
* [path](/help/sites-developing/querybuilder-predicate-reference.md#path)
* [property](/help/sites-developing/querybuilder-predicate-reference.md#property)
* [rangeproperty](/help/sites-developing/querybuilder-predicate-reference.md#rangeproperty)
* [relativedaterange](/help/sites-developing/querybuilder-predicate-reference.md#relativedaterange)
* [savedquery](/help/sites-developing/querybuilder-predicate-reference.md#savedquery)
* [similar](/help/sites-developing/querybuilder-predicate-reference.md#similar)
* [tag](/help/sites-developing/querybuilder-predicate-reference.md#tag)
* [tagid](/help/sites-developing/querybuilder-predicate-reference.md#tagid)
* [tagsearch](/help/sites-developing/querybuilder-predicate-reference.md#tagsearch)
* [type](/help/sites-developing/querybuilder-predicate-reference.md#type)

### `boolproperty` {#boolproperty}

Correspond aux propriétés BOOLEAN JCR. Accepte uniquement les valeurs « `true` » et « `false` ». Si elle est définie sur « `false` », elle correspond si la valeur de la propriété est « `false` » ou si la propriété n’existe pas. Utile pour vérifier les indicateurs booléens qui sont définis uniquement lorsqu’ils sont activés.

Le paramètre « `operation` » hérité n’a aucune signification.

Elle prend en charge l’extraction de facettes. Fournit des compartiments pour chaque valeur `true` ou `false`, mais uniquement pour les propriétés existantes.

#### Propriétés {#properties}

* **boolproperty**
Chemin d’accès relatif à une propriété, par exemple, `myFeatureEnabled` ou `jcr:content/myFeatureEnabled`.

* **value**
Valeur pour laquelle vérifier la propriété : « `true` » ou « `false` ».

### `contentfragment` {#contentfragment}

Limite le résultat aux fragments de contenu.

Il ne prend pas en charge le filtrage.

Il ne prend pas en charge l’extraction de facettes.

#### Propriétés {#properties-1}

* **contentfragment**
Peut être utilisé avec n’importe quelle valeur pour rechercher des fragments de contenu.

### `dateComparison` {#datecomparison}

Compare entre elles deux propriétés DATE JCR. Vous pouvez tester si elles sont égales, inégales, supérieures ou supérieures ou égales.

Un prédicat de filtrage uniquement et qui ne peut pas utiliser d’index de recherche.

#### Propriétés {#properties-2}

* **property1**

  Chemin d’accès à la première propriété date.

* **property2**

  Chemin d’accès à la deuxième propriété date.

* **operation**

  « `equals` » pour une correspondance exacte, « `!=` » pour une comparaison inégale, « `greater` » lorsque la property1 est plus grande que la property2, « `>=` » lorsque la property1 est plus grande ou égale à la property2. La valeur par défaut est « `equals` ».

### `daterange` {#daterange}

Fait correspondre les propriétés JCR DATE à un intervalle de date et d’heure. Utilise le ISO8601
format des dates et des heures ( `YYYY-MM-DDTHH:mm:ss.SSSZ`) et autorise les représentations partielles, comme les `YYYY-MM-DD`. Vous pouvez également fournir la date et l’heure sous la forme du nombre de millisecondes écoulées depuis 1970 dans le fuseau horaire UTC, le format d’heure UNIX®.

Vous pouvez rechercher tout ce qui se trouve entre deux horodatages, un élément plus récent ou plus ancien qu’une date donnée, et également choisir entre des intervalles inclusifs et ouverts.

Elle prend en charge l’extraction de facettes. Fournit des compartiments « aujourd’hui », « cette semaine », « ce mois-ci », « les 3 derniers mois », « cette année », « l’année dernière » et « plus tôt que l’année dernière ».

Il ne prend pas en charge le filtrage.

#### Propriétés {#properties-3}

* **property**

  Chemin d’accès relatif à une propriété `DATE` ; par exemple, `jcr:lastModified`.

* **lowerBound**

  Limite de date inférieure pour laquelle la propriété doit être vérifiée ; par exemple, `2014-10-01`.

* **lowerOperation**

  « `>` » (plus récent) ou « `>=` » (à cette date ou plus récent) ; applicable à `lowerBound`. La valeur par défaut est « `>` ».

* **upperBound**

  Limite supérieure pour laquelle la propriété doit être vérifiée ; par exemple, `2014-10-01T12:15:00`.

* **upperOperation**

  « `<` » (antérieur) ou « `<=` » (à cette date ou antérieur) ; applicable à `upperBound`. La valeur par défaut est « `<` ».

* **timeZone**

  ID du fuseau horaire à utiliser lorsqu’il n’est pas indiqué sous la forme d’une chaîne de date ISO-8601. La valeur par défaut est le fuseau horaire par défaut du système.

### `excludepaths` {#excludepaths}

Exclut des nœuds du résultat lorsque leur chemin d’accès correspond à une expression régulière.

Un prédicat de filtrage uniquement et qui ne peut pas utiliser d’index de recherche.

Il ne prend pas en charge l’extraction de facettes.

#### Propriétés {#properties-4}

* **excludepaths**

  Expression régulière comparée à des chemins de résultat, en excluant les correspondances du résultat.

### `fulltext` {#fulltext}

Il recherche des termes dans l’index en texte intégral.

Il ne prend pas en charge le filtrage.

Il ne prend pas en charge l’extraction de facettes.

#### Propriétés {#properties-5}

* **fulltext**

  Termes de recherche en texte intégral.

* **relPath**

  Chemin d’accès relatif devant faire l’objet d’une recherche dans la propriété ou le sous-nœud. Cette propriété est facultative.

### `group` {#group}

Permet de créer des conditions imbriquées. Les groupes peuvent contenir des groupes imbriqués. Tout le contenu d’une requête Query Builder se trouve implicitement dans un groupe racine qui peut également posséder des paramètres `p.or` et `p.not`.

Exemple pour la correspondance de l’une des deux propriétés par rapport à une valeur :

```
group.p.or=true
group.1_property=jcr:title
group.1_property.value=My Page
group.2_property=navTitle
group.2_property.value=My Page
```

Conceptuellement `(1_property` OU `2_property)`.

Exemple pour les groupes imbriqués :

```
fulltext=Management
group.p.or=true
group.1_group.path=/content/geometrixx/en
group.1_group.type=cq:Page
group.2_group.path=/content/dam/geometrixx
group.2_group.type=dam:Asset
```

Recherche le terme « **Management** » dans les pages de `/content/geometrixx/en` ou dans les ressources de `/content/dam/geometrixx`.

Conceptuellement `fulltext AND ( (path AND type) OR (path AND type) )`. De telles jointures OR nécessitent de bons index pour des raisons de performances.

#### Propriétés {#properties-6}

* **p.or**

  Si « `true` » est défini, un seul prédicat du groupe doit correspondre. La valeur par défaut est « `false` », ce qui signifie que tout doit correspondre.

* **p.not**

  Si « `true` » est défini, le groupe est annulé (la valeur par défaut est « `false` »).

* **&lt;predicate>**

  Ajoute des prédicats imbriqués.

* **N_&lt;predicate>**

  Ajoute plusieurs prédicats imbriqués simultanément, comme `1_property, 2_property, ...`.

### hasPermission {#haspermission}

Limite les résultats aux éléments dont la session en cours possède les [privilèges JCR](https://www.adobe.io/experience-manager/reference-materials/spec/jcr/2.0/16_Access_Control_Management.html#16.2.3%20Standard%20Privileges) spécifiés.

Un prédicat de filtrage uniquement et qui ne peut pas utiliser d’index de recherche. Il ne prend pas en charge l’extraction de facettes.

#### Propriétés {#properties-7}

* **hasPermission**

  Privilèges JCR séparés par des virgules qui doivent TOUS être associés à la session utilisateur en cours pour le nœud en question. Par exemple, `jcr:write`, `jcr:modifyAccessControl`.

### `language` {#language}

Recherche les pages CQ dans une langue spécifique. Cela permet d’examiner à la fois la propriété de langue de la page et le chemin d’accès à la page qui inclut souvent la langue ou les paramètres régionaux dans une structure de site de niveau supérieur.

Un prédicat de filtrage uniquement et qui ne peut pas utiliser d’index de recherche.

Elle prend en charge l’extraction de facettes. Fournit des compartiments pour chaque code de langue unique.

#### Propriétés {#properties-8}

* **language**

  Code de langue ISO ; par exemple, « `de` ».

### `mainasset` {#mainasset}

Vérifie si un nœud est une ressource principale DAM et non une sous-ressource. En gros, chaque nœud ne se trouve pas dans un nœud « sous-ressources ». Ne vérifie pas le type de nœud `dam:Asset`. Pour utiliser ce prédicat, définissez « `mainasset=true` » ou « `mainasset=false` », il n’y a pas d’autres propriétés.

Un prédicat de filtrage uniquement et qui ne peut pas utiliser d’index de recherche.

Elle prend en charge l’extraction de facettes et fournit deux compartiments pour les ressources principales et secondaires.

#### Propriétés {#properties-9}

* **mainasset**

  Booléen, « `true` » pour les ressources principales, « `false` » pour les sous-ressources.

### memberOf {#memberof}

Recherche les éléments membres d’une [collection de ressources Sling](https://developer.adobe.com/experience-manager/reference-materials/6-5-lts/javadoc/org/apache/sling/resource/collection/ResourceCollection.html) spécifique.

Un prédicat de filtrage uniquement et qui ne peut pas utiliser d’index de recherche. Il ne prend pas en charge l’extraction de facettes.

#### Propriétés {#properties-10}

* **memberOf**

  Chemin d’accès à la collection de ressources Sling.

### `nodename` {#nodename}

Correspond aux noms des noeuds JCR.

Elle prend en charge l’extraction de facettes. Fournit des compartiments pour chaque nom de nœud unique (nom de fichier).

#### Propriétés {#properties-11}

* **nodename**

  Modèle de nom de nœud qui autorise les caractères génériques : `*` = n’importe quel caractère, ou aucun, `?` = n’importe quel caractère, `[abc]` = uniquement les caractères entre crochets.

### `notexpired` {#notexpired}

Met en correspondance des éléments en vérifiant si une propriété DATE JCR est supérieure ou égale à l’heure actuelle du serveur. Peut être utilisé pour effectuer une vérification sur une propriété date de type `expiresAt` et se limiter uniquement à celles qui n’ont pas encore expiré ( `notexpired=true`) ou qui ont déjà expiré ( `notexpired=false`).

Il ne prend pas en charge le filtrage.

Elle prend en charge l’extraction de facettes de la même manière que le prédicat daterange.

#### Propriétés {#properties-12}

* **notexpired**

  Booléen, « `true` » pour les propriétés qui n’ont pas encore expiré (date future ou égale à celle indiquée), « `false` » pour les propriétés qui ont expiré (date dans le passé) (obligatoire).

* **property**

  Chemin d’accès relatif à la propriété `DATE` à vérifier (obligatoire).

### `orderby` {#orderby}

Permet de trier les résultats. Si un classement basé sur plusieurs propriétés est requis, ce prédicat doit être ajouté plusieurs fois à l’aide du préfixe numérique, tel que `1_orderby=first`, `2_oderby=second`.

#### Propriétés {#properties-13}

* **orderby**

  Nom de propriété JCR indiqué par un caractère @ initial, par exemple `@jcr:lastModified` ou `@jcr:content/jcr:title`, ou un autre prédicat dans la requête, par exemple `2_property`, sur la base duquel le tri doit être effectué.

* **sort**

  Sens du tri, soit « `desc` » pour décroissant, soit « `asc` » pour croissant (valeur par défaut).

* **case**

  Si cette valeur est définie sur « `ignore` », le tri ne respecte pas la casse, ce qui signifie que « a » vient avant « B »; si cette valeur est vide ou ignorée, le tri respecte la casse, ce qui signifie que « B » vient avant « a ».

### `path` {#path}

Recherche dans un chemin donné.

Il ne prend pas en charge l’extraction de facettes.

#### Propriétés {#properties-14}

* **path**

  Modèle de chemin. Lorsqu’elle est `exact=false` (par défaut), la recherche correspond à l’ensemble de la sous-arborescence sous le chemin spécifié, ce qui revient à ajouter des `//*` dans XPath, mais cela n’inclut pas le chemin de base lui-même. Lorsqu’elle est `exact=true`, la recherche ne correspond qu’au chemin exact, qui peut inclure des caractères génériques `*`. Si `self` est défini, la recherche inclut le nœud de base et sa sous-arborescence entière.


* **exact**

  Si la `exact` est définie sur true (activé), le chemin d’accès exact doit correspondre, mais il peut contenir des caractères génériques simples ( `*`), qui correspondent aux noms, mais pas « `/` » ; si elle est définie sur false (par défaut) tous les descendants sont inclus (facultatif).

* **flat**

  Effectue uniquement des recherches dans les enfants directs (revient à ajouter « `/*` » dans `xpath`) (utilisé uniquement si « `exact` » n’est pas défini sur true, facultatif).

* **self**

  Effectue des recherches dans la sous-arborescence, mais inclut le nœud de base indiqué comme chemin d’accès (pas de caractères génériques).

### `property` {#property}

Met en correspondance des propriétés JCR et leurs valeurs.

Elle prend en charge l’extraction de facettes. Fournit des compartiments pour chaque valeur de propriété dans les résultats.

#### Propriétés {#properties-15}

* **property**

  Chemin d’accès relatif à une propriété ; par exemple, `jcr:title`.

* **value**

  Valeur dont la propriété doit être vérifiée ; suit le type de propriété JCR pour les conversions de chaînes.

* **N_value**

  Utilisez `1_value`, `2_value`, ... pour rechercher plusieurs valeurs (combinées avec `OR` par défaut, avec `AND` si et=true) (à partir de la version 5.3).

* **and**

  Définissez cette valeur sur true pour combiner plusieurs valeurs (`N_value`) avec AND (à partir de la version 5.3).

* **operation**

  Utilisez `equals` pour une correspondance exacte (par défaut) et `unequals` pour une comparaison des inégalités. Utilisez `like` pour appliquer la fonction XPath `jcr:like` facultative. Utilisez `not` pour l’absence de correspondance (par exemple, `not(@prop)` dans XPath) ; dans ce cas, le paramètre `value` est ignoré. Utilisez `exists` pour vérifier si une propriété existe : `true` (par défaut) requiert la propriété et `false` est équivalent à `not`.

* **depth**

  Nombre de niveaux de caractères génériques sous lesquels la propriété et le chemin d’accès relatif peuvent exister. Par exemple, `property=size depth=2` vérifie le nœud et la taille, le nœud/&ast;/size et le nœud/&ast;/&ast;/size.

### `rangeproperty` {#rangeproperty}

Met en correspondance une propriété JCR par rapport à un intervalle. S’applique aux propriétés de type linéaire, telles que `LONG`, `DOUBLE` et `DECIMAL`. Pour `DATE`, reportez-vous au prédicat daterange qui présente une entrée de format de date optimisée.

Vous pouvez définir une limite inférieure et une limite supérieure ou seulement l’une d’elles. L’opération (par exemple, « inférieure à », ou « inférieure ou égale à ») peut également être spécifiée individuellement pour les limites inférieure et supérieure.

Il ne prend pas en charge l’extraction de facettes.

#### Propriétés {#properties-16}

* **property**

  Chemin d’accès relatif à la propriété.

* **lowerBound**

  Limite inférieure pour laquelle la propriété doit être vérifiée.

* **lowerOperation**

  « `>` » (par défaut) ou « `>=` » s’applique à la `lowerValue`

* **upperBound**

  Limite supérieure pour laquelle la propriété doit être vérifiée.

* **upperOperation**

  « `<` » (par défaut) ou « `<=` » s’applique à la `lowerValue`

* **decimal**

  « `true` » si la propriété vérifiée est de type Décimal

### `relativedaterange` {#relativedaterange}

Fait correspondre `JCR DATE` propriétés par rapport à un intervalle de date et d’heure à l’aide de décalages temporels relatifs à l’heure actuelle du serveur. Vous pouvez spécifier `lowerBound` et `upperBound` à l’aide d’une valeur en millisecondes ou de l’`1s 2m 3h 4d 5w 6M 7y` de syntaxe bugzilla. Préfixe avec « `-` » pour indiquer un décalage négatif avant l’heure actuelle. Si vous spécifiez uniquement `lowerBound` ou `upperBound`, l’autre propriété est définie par défaut sur 0, ce qui signifie l’heure actuelle.

Par exemple :

* `upperBound=1h` (et pas de `lowerBound`) sélectionnerait tous les éléments dans l’heure suivante.
* `lowerBound=-1d` (et pas de `upperBound`) sélectionnerait tous les éléments dans les dernières 24 heures.
* `lowerBound=-6M` et `upperBound=-3M` sélectionneraient tous les éléments entre 6 mois et 3 mois.
* `lowerBound=-1500` et `upperBound=5500` sélectionneraient tous les éléments entre 1 500 millisecondes dans le passé et 5 500 millisecondes dans le futur.
* `lowerBound=1d` et `upperBound=2d` sélectionneraient tous les éléments du jour d’après-demain ;

Il ne tient pas compte des années bissextiles et tous les mois comptent 30 jours.

Il ne prend pas en charge le filtrage.

Elle prend en charge l’extraction de facettes de la même manière que le prédicat daterange.

#### Propriétés {#properties-17}

* **upperBound**

  Limite de date supérieure en millisecondes ou `1s 2m 3h 4d 5w 6M 7y` (une seconde, deux minutes, trois heures, quatre jours, cinq semaines, six mois, sept ans) par rapport à l’heure actuelle du serveur ; utilisez « - » pour un décalage négatif.

* **lowerBound**

  Limite de date inférieure en millisecondes ou `1s 2m 3h 4d 5w 6M 7y` (une seconde, deux minutes, trois heures, quatre jours, cinq semaines, six mois, sept ans) par rapport à l’heure actuelle du serveur ; utilisez « - » pour un décalage négatif.

### `root` {#root}

Groupe de prédicats racine. Il prend en charge toutes les fonctionnalités d’un groupe et vous permet de définir des paramètres de requête globaux.

Le nom « root » n’est jamais utilisé dans une requête ; il est implicite.

#### Propriétés {#properties-18}

* **p.offset**

  Nombre indiquant le début de la page de résultats, c’est-à-dire le nombre d’éléments à ignorer.

* **p.limit**

  Nombre indiquant la taille de la page.

* **p.guessTotal**

  Pour éviter le coût du calcul d’un total de résultats complet, ne comptez pas toutes les correspondances. Au lieu de cela, définissez un total maximal à compter jusqu’à (par exemple, `1000`) pour donner aux utilisateurs une taille approximative et des totaux exacts pour des résultats plus petits. Ou définissez-le sur `true` pour compter uniquement jusqu’au minimum requis : `p.offset + p.limit`.


* **p.excerpt**

  Si la valeur est définie sur « `true` », l’extrait de texte complet est inclus dans les résultats.

* **p.hits**

   (uniquement pour le servlet JSON) Sélectionne la manière dont les accès sont écrits au format JSON, avec ces éléments standard (extensibles via le service ResultHitWriter) :

   * **simple** :

     Éléments minimaux tels que `path`, `title`, `lastmodified`, `excerpt` (s’ils sont définis).

   * **full** :

     Les résultats sont rendus au format Sling JSON pour chaque nœud, avec des `jcr:path` indiquant le chemin d’accès. Par défaut, la réponse inclut uniquement les propriétés directes du nœud ; utilisez `p.nodedepth=N` pour inclure du contenu plus profond, où `0` renvoie l’ensemble de la sous-arborescence. Définissez `p.acls=true` pour inclure les autorisations JCR de la session en cours pour chaque élément (`create` = `add_node`, `modify` = `set_property`, `delete` = `remove`).


   * **selective** :

     La réponse inclut uniquement les propriétés répertoriées dans `p.properties`, qui est une liste de chemins d’accès relatifs séparés par des espaces (à utiliser `+` dans les URL). Si un chemin relatif a une profondeur supérieure à 1, la sortie l’imbrique en tant qu’objets enfants. La propriété spéciale `jcr:path` inclut toujours le chemin d’accès.


### `savedquery` {#savedquery}

Il inclut tous les prédicats d’une requête persistante de Query Builder dans la requête actuelle en tant que prédicat de sous-groupe.

Il n’exécute pas de requête supplémentaire, mais étend la requête actuelle.

Les requêtes peuvent être conservées par programmation à l’aide de `QueryBuilder#storeQuery()`. Ce format peut être soit une propriété String multiligne, soit un nœud `nt:file` contenant la requête en tant que fichier texte au format des propriétés Java™.

Il ne prend pas en charge l’extraction de facettes pour les prédicats de la requête enregistrée.

#### Propriétés {#properties-19}

* **savedquery**

  Chemin d’accès à la requête enregistrée (propriété String ou nœud `nt:file`).

### `similar` {#similar}

Recherche par analogie à l’aide du `rep:similar()` du Xpath JCR.

Il ne prend pas en charge le filtrage. Il ne prend pas en charge l’extraction de facettes.

#### Propriétés {#properties-20}

* **similar**
Chemin d’accès absolu au nœud pour lequel des nœuds similaires sont recherchés.

* **local**
Un chemin relatif vers un nœud descendant ou `.` pour le nœud actif (facultatif, la valeur par défaut est« `.` »).

### `tag` {#tag}

Recherche du contenu identifié avec une ou plusieurs balises, en spécifiant les chemins d’accès aux titres des balises.

Elle prend en charge l’extraction de facettes. Fournit des compartiments pour chaque balise, en utilisant le chemin d’accès vers le titre de balise active.

#### Propriétés {#properties-21}

* **tag**

  Chemin d’accès au titre de la balise à rechercher ; par exemple, « Propriétés de ressource : Orientation / Paysage ».

* **N_value**

  Utilisez `1_value`, `2_value`, ... pour rechercher plusieurs balises (combinées avec `OR` par défaut, avec `AND` si et=true) (depuis la version 5.6).

* **property**

  Propriété (ou chemin d’accès relatif à la propriété) à examiner (par défaut : « `cq:tags` »)

### `tagid` {#tagid}

Recherche du contenu identifié avec une ou plusieurs balises, en spécifiant les chemins d’accès aux ID des balise.

Elle prend en charge l’extraction de facettes. Fournit des compartiments pour chaque balise, en utilisant le chemin d’accès à l’ID de la balise active.

#### Propriétés {#properties-22}

* **tagid**

  Identifiant de balise afin que vous puissiez rechercher, par exemple, « `properties:orientation/landscape` ».

* **N_value**

  Utilisez `1_value`, `2_value`, ... pour rechercher plusieurs `tagids` (combinées avec `OR` par défaut, avec `AND` si and=true) (à partir de la version 5.6).

* **property**

  Propriété (ou chemin d’accès relatif à la propriété) à examiner (par défaut : « `cq:tags` »).

### `tagsearch` {#tagsearch}

Recherche du contenu identifié avec une ou plusieurs balises, en spécifiant des mots-clés. Recherche d’abord les balises qui contiennent ces mots-clés dans leurs titres, puis limite le résultat aux seuls éléments balisés.

Il ne prend pas en charge l’extraction de facettes.

#### Propriétés {#Properties-1}

* **tagsearch**

  Mot-clé à rechercher dans les titres de nœud.

* **property**

  Propriété (ou chemin d’accès relatif à la propriété) à examiner (par défaut `cq:tags`).

* **lang**

  Pour rechercher uniquement dans un titre de balise localisé donné (par exemple, `de`).

* **all**

  (Booléen) Recherche le texte intégral d’une balise, c’est-à-dire tous les titres, la description, etc. A la priorité sur « l `ang` ».

### `type` {#type}

Limite les résultats à un type de nœud JCR spécifique, à la fois au type de nœud principal ou au type de mixin , et trouve des sous-types de ce type de nœud. Les index de recherche de référentiel doivent couvrir les types de nœuds pour une exécution efficace.

Elle prend en charge l’extraction de facettes. Fournit des compartiments pour chaque type unique dans les résultats.

#### Propriétés {#Properties-2}

* **type**

  Type de nœud ou nom de mixin à rechercher ; par exemple, `cq:Page`.
