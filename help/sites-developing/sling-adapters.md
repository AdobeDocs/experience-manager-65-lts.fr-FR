---
title: Utilisation des adaptateurs Sling
description: Sling propose un modèle Adapter pour traduire facilement des objets qui implémentent l’interface Adaptable.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: platform
content-type: reference
solution: Experience Manager, Experience Manager Sites
feature: Developing
role: Developer
exl-id: 7eae83bd-7982-4051-821f-b43f65c5af2b
source-git-commit: cf22b13e0f7c8e66b598f85aab81b022480e60bc
workflow-type: tm+mt
source-wordcount: '1338'
ht-degree: 50%

---

# Utilisation des adaptateurs Sling{#using-sling-adapters}

[Sling](https://sling.apache.org) propose un [modèle Adapter](https://sling.apache.org/documentation/the-sling-engine/adapters.html) pour traduire facilement des objets qui implémentent l’interface [Adaptable](https://sling.apache.org/apidocs/sling5/org/apache/sling/api/adapter/Adaptable.html#adaptTo%28java.lang.Class%29). Cette interface fournit une méthode [adaptTo()](https://sling.apache.org/apidocs/sling5/org/apache/sling/api/adapter/Adaptable.html#adaptTo%28java.lang.Class%29) générique qui convertit les objets dans le type de classe qui est transmis comme argument.

Par exemple, pour convertir un objet Resource en objet Node correspondant, vous pouvez simplement procéder comme suit :

```java
Node node = resource.adaptTo(Node.class);
```

## Cas d’utilisation {#use-cases}

Il existe plusieurs scénarios d’utilisation :

* Obtenir des objets spécifiques à l’implémentation.

  Par exemple, une implémentation basée sur JCR de l’interface [`Resource`](https://sling.apache.org/apidocs/sling5/org/apache/sling/api/resource/Resource.html) permet d’accéder à l’objet [`Node`](https://developer.adobe.com/experience-manager/reference-materials/spec/javax.jcr/javadocs/jcr-2.0/javax/jcr/Node.html) JCR sous-jacent.

* Création de raccourcis d’objets qui nécessitent la transmission d’objets de contexte internes.

  Par exemple, le [`ResourceResolver`](https://sling.apache.org/apidocs/sling5/org/apache/sling/api/resource/ResourceResolver.html) basé sur JCR contient une référence au [`JCR Session`](https://developer.adobe.com/experience-manager/reference-materials/spec/javax.jcr/javadocs/jcr-2.0/javax/jcr/Session.html) de la requête, qui à son tour est nécessaire pour de nombreux objets qui peuvent fonctionner en fonction de cette session de requête, tels que le [`PageManager`](https://developer.adobe.com/experience-manager/reference-materials/6-5-lts/javadoc/com/day/cq/wcm/api/PageManager.html) ou le [`UserManager`](https://developer.adobe.com/experience-manager/reference-materials/6-5-lts/javadoc/com/day/cq/security/UserManager.html).

* Raccourci vers les services.

  Cas peu fréquent : `sling.getService()` s’avère également simple.

### Valeur renvoyée nulle {#null-return-value}

La `adaptTo()` renvoie la valeur null.

Les raisons varient, notamment :

* L’implémentation ne prend pas en charge le type de cible .
* Une fabrique de cartes qui gère ce cas est inactive (par exemple, en raison de références de service manquantes)
* Une condition interne a échoué.
* Le service n’est pas disponible.

Il est important que vous gériez le cas « null » de manière élégante. Pour les rendus jsp, il peut être acceptable que le jsp échoue si cela entraîne un élément de contenu vide.

### Mise en cache {#caching}

Pour améliorer les performances, les implémentations peuvent mettre en cache l’objet renvoyé par un appel `obj.adaptTo()`. Si `obj` est identique, l’objet renvoyé l’est également.

Cette mise en cache est exécutée pour tous les scénarios basés sur `AdapterFactory`.

Cependant, il n’existe aucune règle générale : l’objet peut être soit une nouvelle instance, soit une instance existante. Cela signifie que vous ne pouvez pas vous fier à l’un ou l’autre de ces comportements. Par conséquent, il est important, en particulier en `AdapterFactory`, que les objets soient réutilisables dans ce scénario.

### Fonctionnement {#how-it-works}

`Adaptable.adaptTo()` peut être implémenté de différentes façons :

* Par l’objet proprement dit ; implémentation de la méthode et mappage sur certains objets.
* Par une [`AdapterFactory`](https://sling.apache.org/apidocs/sling5/org/apache/sling/api/adapter/AdapterFactory.html), qui peut mapper des objets arbitraires.

  Les objets doivent cependant implémenter l’interface `Adaptable` et étendre [`SlingAdaptable`](https://developer.adobe.com/experience-manager/reference-materials/6-5-lts/javadoc/org/apache/sling/adapter/SlingAdaptable.html) (qui transmet l’appel `adaptTo` à un gestionnaire d’adaptateur central).

  Se connecte au mécanisme de `adaptTo` des classes existantes, telles que `Resource`.

* Une combinaison des deux.

Pour le premier cas, les documents Java™ peuvent indiquer quelles `adaptTo-targets` sont possibles. Cependant, pour des sous-classes spécifiques telles que la ressource basée sur JCR, cela n’est souvent pas possible. Dans ce dernier cas, les implémentations de `AdapterFactory` font généralement partie des classes privées d’un lot et ne sont donc pas exposées dans une API cliente ou répertoriées dans la documentation Java™. En théorie, il serait possible d’accéder à toutes les implémentations `AdapterFactory` à partir de l’exécutable de service [OSGi](/help/sites-deploying/configuring-osgi.md) et d’observer leurs configurations « adaptables » (sources et cibles), mais pas de les mapper entre elles. En fin de compte, cela dépend de la logique interne, qui doit être documentée, D’où la référence .

## Référence {#reference}

### Sling {#sling}

[**Resource**](https://developer.adobe.com/experience-manager/reference-materials/6-5-lts/javadoc/org/apache/sling/api/resource/Resource.html) s’adapte à :

<table>
 <tbody>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/spec/javax.jcr/javadocs/jcr-2.0/javax/jcr/Node.html">Nœud</a></td>
   <td>S’il s’agit d’une ressource basée sur un nœud JCR ou d’une propriété JCR référençant un nœud</td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/spec/javax.jcr/javadocs/jcr-2.0/javax/jcr/Property.html">Propriété</a></td>
   <td>S’il s’agit d’une ressource basée sur une propriété JCR</td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/spec/javax.jcr/javadocs/jcr-2.0/javax/jcr/Item.html">Élément</a></td>
   <td>S’il s’agit d’une ressource basée sur JCR (nœud ou propriété)</td>
  </tr>
  <tr>
   <td><a href="https://docs.oracle.com/javase/1.5.0/docs/api/java/util/Map.html">Mappage</a></td>
   <td>Elle renvoie un mappage des propriétés, s’il s’agit d’une ressource basée sur un nœud JCR (ou d’autres ressources prenant en charge les mappages de valeurs).</td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/6-5-lts/javadoc/org/apache/sling/api/resource/ValueMap.html">ValueMap</a></td>
   <td>Elle renvoie un mappage pratique des propriétés, s’il s’agit d’une ressource basée sur un nœud JCR ou d’autres mappages de valeurs prenant en charge les ressources. Elle peut également être réalisée (plus simplement) en utilisant <br /> <code><a href="https://developer.adobe.com/experience-manager/reference-materials/6-5-lts/javadoc/org/apache/sling/api/resource/ResourceUtil.html">ResourceUtil.getValueMap(Resource)</a></code> (gère la casse nulle, etc.).</td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/6-5-lts/javadoc/com/day/cq/commons/inherit/InheritanceValueMap.html">InheritanceValueMap</a></td>
   <td>Extension de <a href="https://developer.adobe.com/experience-manager/reference-materials/6-5-lts/javadoc/org/apache/sling/api/resource/ValueMap.html">ValueMap</a>, ce qui permet la prise en compte de la hiérarchie de ressources lors de la recherche de propriétés.</td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/6-5-lts/javadoc/org/apache/sling/api/resource/ModifiableValueMap.html">ModifiableValueMap</a></td>
   <td>Une extension de <a href="https://developer.adobe.com/experience-manager/reference-materials/6-5-lts/javadoc/org/apache/sling/api/resource/ValueMap.html">ValueMap</a>, qui vous permet de modifier les propriétés sur ce nœud.</td>
  </tr>
  <tr>
   <td><a href="https://docs.oracle.com/javase/1.5.0/docs/api/java/io/InputStream.html">InputStream</a></td>
   <td>Elle renvoie le contenu binaire d’une ressource de fichier lorsqu’elle est basée sur un nœud JCR (<code>nt:file</code> ou <code>nt:resource</code>), une ressource de lot ou une ressource de système de fichiers. Elle renvoie les données d’une ressource de propriété JCR binaire.</td>
  </tr>
  <tr>
   <td><a href="https://docs.oracle.com/javase/1.5.0/docs/api/java/net/URL.html">URL</a></td>
   <td>Elle renvoie une URL pour la ressource. Elle renvoie l’URL du référentiel pour une ressource basée sur un nœud JCR, l’URL du lot JAR pour une ressource de lot ou l’URL du fichier pour une ressource du système de fichiers.</td>
  </tr>
  <tr>
   <td><a href="https://docs.oracle.com/javase/1.5.0/docs/api/java/io/File.html">Fichier</a></td>
   <td>S’il s’agit d’une ressource de système de fichiers</td>
  </tr>
  <tr>
   <td><a href="https://sling.apache.org/apidocs/sling5/org/apache/sling/api/scripting/SlingScript.html">SlingScript</a></td>
   <td>Si cette ressource est un script (un fichier jsp, par exemple) pour lequel un moteur de script est enregistré auprès de sling.</td>
  </tr>
  <tr>
   <td><a href="https://www.oracle.com/java/technologies/servlet-technology.html">Servlet</a></td>
   <td>Si cette ressource est un script (un fichier jsp, par exemple) pour lequel un moteur de script est enregistré auprès de sling ou s’il s’agit d’une ressource de servlet.</td>
  </tr>
  <tr>
   <td><a href="https://docs.oracle.com/javase/1.5.0/docs/api/java/lang/String.html">String</a><br /> <a href="https://docs.oracle.com/javase/1.5.0/docs/api/java/lang/Boolean.html">Boolean</a><br /> <a href="https://docs.oracle.com/javase/1.5.0/docs/api/java/lang/Long.html">Long</a><br /> <a href="https://docs.oracle.com/javase/1.5.0/docs/api/java/lang/Double.html">Double</a><br /> <a href="https://docs.oracle.com/javase/1.5.0/docs/api/java/util/Calendar.html">Calendar</a><br /> <a href="https://developer.adobe.com/experience-manager/reference-materials/spec/javax.jcr/javadocs/jcr-2.0/javax/jcr/Value.html">Value</a><br /> <a href="https://docs.oracle.com/javase/1.5.0/docs/api/java/lang/String.html">String[]</a><br /> <a href="https://docs.oracle.com/javase/1.5.0/docs/api/java/lang/Boolean.html">Boolean[]</a><br /> <a href="https://docs.oracle.com/javase/1.5.0/docs/api/java/lang/Long.html">Long[]</a><br /> <a href="https://docs.oracle.com/javase/1.5.0/docs/api/java/util/Calendar.html">Calendar[]</a><br /> <a href="https://developer.adobe.com/experience-manager/reference-materials/spec/javax.jcr/javadocs/jcr-2.0/javax/jcr/Value.html">Value[]</a></td>
   <td>Renvoie les valeurs s’il s’agit d’une ressource basée sur une propriété JCR (et que la valeur correspond).</td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/6-5-lts/javadoc/com/day/cq/commons/LabeledResource.html">LabeledResource</a></td>
   <td>S’il s’agit d’une ressource basée sur un nœud JCR</td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/6-5-lts/javadoc/com/day/cq/wcm/api/Page.html">Page</a></td>
   <td>S’il s’agit d’une ressource basée sur un nœud JCR et que le nœud est un <code>cq:Page</code> (ou un <code>cq:PseudoPage</code>).</td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/6-5-lts/javadoc/com/day/cq/wcm/api/components/Component.html">Composant</a></td>
   <td>S’il s’agit d’une ressource de nœud <code>cq:Component</code></td>
  </tr>  
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/6-5-lts/javadoc/com/day/cq/wcm/api/designer/Design.html">Conception</a></td>
   <td>S’il s’agit d’un nœud de conception (<code>cq:Page</code>)</td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/6-5-lts/javadoc/com/day/cq/wcm/api/Template.html">Modèle</a></td>
   <td>S’il s’agit d’une ressource de nœud <code>cq:Template</code></td>
  </tr>  
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/6-5-lts/javadoc/com/day/cq/wcm/msm/api/Blueprint.html">Plan directeur</a></td>
   <td>S’il s’agit d’une ressource de nœud <code>cq:Template</code></td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/6-5-lts/javadoc/com/day/cq/dam/api/Asset.html">Asset</a></td>
   <td>S’il s’agit d’une ressource de nœud <code>dam:Asset</code></td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/6-5-lts/javadoc/com/day/cq/dam/api/Rendition.html">Rendition</a></td>
   <td>S’il s’agit d’un rendu <code>dam:Asset</code> (<code>nt:file</code> sous le dossier de rendu d’un <code>dam:Asset</code>)</td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/6-5-lts/javadoc/com/day/cq/tagging/Tag.html">Balise</a></td>
   <td>S’il s’agit d’une ressource de nœud <code>cq:Tag</code></td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/6-5-lts/javadoc/com/day/cq/security/UserManager.html">UserManager</a></td>
   <td>En fonction de la session JCR s’il s’agit d’une ressource basée sur JCR et si l’utilisateur dispose des autorisations pour accéder à UserManager.</td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/6-5-lts/javadoc/org/apache/jackrabbit/api/security/user/Authorizable.html">Authorizable</a></td>
   <td>Authorizable est la base commune de User et Group.</td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/6-5-lts/javadoc/org/apache/jackrabbit/api/security/user/User.html">User</a></td>
   <td>L’utilisateur est un élément Autorisable spécial qui peut être authentifié et emprunté l’identité.</td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/6-5-lts/javadoc/com/day/cq/search/SimpleSearch.html">SimpleSearch</a></td>
   <td>Effectue des recherches sous la ressource (ou utilise setSearchIn()) s’il s’agit d’une ressource basée sur JCR.</td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/6-5-lts/javadoc/com/day/cq/workflow/status/WorkflowStatus.html">WorkflowStatus</a></td>
   <td>Statut du workflow pour la page/le nœud de payload de workflow donné(s).</td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/6-5-lts/javadoc/com/day/cq/replication/ReplicationStatus.html">ReplicationStatus</a></td>
   <td>Statut de réplication de la ressource donnée ou de son sous-nœud <code>jcr:content</code> (coché en premier).</td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/6-5-lts/javadoc/com/day/cq/connector/ConnectorResource.html">ConnectorResource</a></td>
   <td>Elle renvoie une ressource de connecteur adaptée pour certains types, s’il s’agit d’une ressource basée sur un nœud JCR.</td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/6-5-lts/javadoc/com/day/cq/contentsync/config/package-summary.html">Config</a></td>
   <td>S’il s’agit d’une ressource de nœud <code>cq:ContentSyncConfig</code></td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/6-5-lts/javadoc/com/day/cq/contentsync/config/package-summary.html">ConfigEntry</a></td>
   <td>Si elle se situe sous une ressource de nœud <code>cq:ContentSyncConfig</code></td>
  </tr>
 </tbody>
</table>

[**ResourceResolver**](https://developer.adobe.com/experience-manager/reference-materials/6-5-lts/javadoc/org/apache/sling/api/resource/ResourceResolver.html) s’adapte à :

<table>
 <tbody>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/spec/javax.jcr/javadocs/jcr-2.0/javax/jcr/Session.html">Session</a></td>
   <td>La session JCR de la requête, s’il s’agit d’un résolveur de ressources basé sur JCR (par défaut).</td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/6-5-lts/javadoc/com/day/cq/wcm/api/PageManager.html">PageManager</a></td>
   <td> </td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/6-5-lts/javadoc/com/day/cq/wcm/api/components/ComponentManager.html">ComponentManager</a></td>
   <td> </td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/6-5-lts/javadoc/com/day/cq/wcm/api/designer/Designer.html">Designer</a></td>
   <td> </td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/6-5-lts/javadoc/com/day/cq/dam/api/AssetManager.html">AssetManager</a></td>
   <td>En fonction de la session JCR, s’il s’agit d’un résolveur de ressources basé sur JCR.</td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/6-5-lts/javadoc/com/day/cq/tagging/TagManager.html">TagManager</a></td>
   <td>En fonction de la session JCR, s’il s’agit d’un résolveur de ressources basé sur JCR.</td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/6-5-lts/javadoc/org/apache/jackrabbit/api/security/user/UserManager.html">UserManager</a></td>
   <td>UserManager permet d’accéder aux objets autorisables qui sont les utilisateurs et les groupes, et de les gérer. UserManager est lié à une session particulière.
   </td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/6-5-lts/javadoc/org/apache/jackrabbit/api/security/user/Authorizable.html">Authorizable</a> </td>
   <td>Utilisateur actuel.</td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/6-5-lts/javadoc/org/apache/jackrabbit/api/security/user/User.html">Utilisateur/utilisatrice</a><br /> </td>
   <td>Utilisateur actuel.</td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/6-5-lts/javadoc/com/day/cq/search/QueryBuilder.html">QueryBuilder</a></td>
   <td> </td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/6-5-lts/javadoc/com/day/cq/commons/Externalizer.html">Externalizer</a></td>
   <td>Pour externaliser les URL absolues, même sans l’objet de requête <br />. </td>
  </tr>
 </tbody>
</table>

[**SlingHttpServletRequest**](https://developer.adobe.com/experience-manager/reference-materials/6-5-lts/javadoc/org/apache/sling/api/SlingHttpServletRequest.html) s’adapte à :

Pas encore de cible, mais implémente l’interface Adaptable et peut être utilisé comme source dans une AdapterFactory personnalisée.

[**SlingHttpServletResponse**](https://developer.adobe.com/experience-manager/reference-materials/6-5-lts/javadoc/org/apache/sling/api/SlingHttpServletResponse.html) s’adapte à :

<table>
 <tbody>
  <tr>
   <td><a href="https://docs.oracle.com/javase/1.5.0/docs/api/org/xml/sax/ContentHandler.html">ContentHandler</a><br /> (XML)</td>
   <td>S’il s’agit d’une réponse de réécriture sling</td>
  </tr>
 </tbody>
</table>

#### WCM {#wcm}

**La [page](https://developer.adobe.com/experience-manager/reference-materials/6-5-lts/javadoc/com/day/cq/wcm/api/Page.html)** s’adapte aux éléments suivants :

<table>
 <tbody>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/6-5-lts/javadoc/org/apache/sling/api/resource/Resource.html">Resource</a><br /> </td>
   <td>Ressource de la page</td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/6-5-lts/javadoc/com/day/cq/commons/LabeledResource.html">LabeledResource</a></td>
   <td>La ressource libellée est la ressource actuelle. C’est-à-dire le même objet que celui que vous regardez.</td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/spec/javax.jcr/javadocs/jcr-2.0/javax/jcr/Node.html">Nœud</a></td>
   <td>Nœud de la page.</td>
  </tr>
  <tr>
   <td>…</td>
   <td>Tous les éléments auxquels la ressource de la page peut être adaptée.</td>
  </tr>
 </tbody>
</table>

**Le [composant](https://developer.adobe.com/experience-manager/reference-materials/6-5-lts/javadoc/com/day/cq/wcm/api/components/Component.html)** s’adapte aux éléments suivants :

| [Resource](https://developer.adobe.com/experience-manager/reference-materials/6-5-lts/javadoc/org/apache/sling/api/resource/Resource.html) | Ressource du composant. |
| --- | --- |
| [LabeledResource](https://developer.adobe.com/experience-manager/reference-materials/6-5-lts/javadoc/com/day/cq/commons/LabeledResource.html) | La ressource libellée est la ressource actuelle. C’est-à-dire le même objet que celui que vous regardez. |
| [Node](https://developer.adobe.com/experience-manager/reference-materials/spec/javax.jcr/javadocs/jcr-2.0/javax/jcr/Node.html) | Nœud du composant. |
| … | Tous les éléments auxquels la ressource du composant peut être adaptée. |

**Le [modèle](https://developer.adobe.com/experience-manager/reference-materials/6-5-lts/javadoc/com/day/cq/wcm/api/Template.html)** s’adapte aux éléments suivants :

<table>
 <tbody>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/6-5-lts/javadoc/org/apache/sling/api/resource/Resource.html">Ressource</a><a href="https://developer.adobe.com/experience-manager/reference-materials/spec/javax.jcr/javadocs/jcr-2.0/javax/jcr/Node.html"><br /> </a></td>
   <td>Ressource du modèle.</td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/6-5-lts/javadoc/com/day/cq/commons/LabeledResource.html">LabeledResource</a></td>
   <td>La ressource libellée est la ressource actuelle. C’est-à-dire le même objet que celui que vous regardez.</td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/spec/javax.jcr/javadocs/jcr-2.0/javax/jcr/Node.html">Nœud</a></td>
   <td>Nœud de ce modèle.</td>
  </tr>
  <tr>
   <td>…</td>
   <td>Tous les éléments auxquels la ressource du modèle peut être adaptée.</td>
  </tr>
 </tbody>
</table>

#### Sécurité {#security}

**Authorizable**, **User et &#x200B;** Group** s’adaptent à :

| [Node](https://developer.adobe.com/experience-manager/reference-materials/spec/javax.jcr/javadocs/jcr-2.0/javax/jcr/Node.html) | Renvoie le nœud racine de l’utilisateur/du groupe. |
| --- | --- |
| [ReplicationStatus](https://developer.adobe.com/experience-manager/reference-materials/6-5-lts/javadoc/com/day/cq/replication/ReplicationStatus.html) | Elle renvoie l’état de réplication du nœud racine utilisateur/groupe. |

#### Gestion des ressources numériques (DAM) {#dam}

**Asset** s’adapte à :

| [Resource](https://developer.adobe.com/experience-manager/reference-materials/6-5-lts/javadoc/org/apache/sling/api/resource/Resource.html) | Ressource de l’actif. |
| --- | --- |
| [Node](https://developer.adobe.com/experience-manager/reference-materials/spec/javax.jcr/javadocs/jcr-2.0/javax/jcr/Node.html) | Nœud de la ressource. |
| … | Tous les éléments auxquels la ressource de l’actif peut être adaptée. |

#### Balise {#tagging}

**Tag** s’adapte à :

| [Resource](https://developer.adobe.com/experience-manager/reference-materials/6-5-lts/javadoc/org/apache/sling/api/resource/Resource.html) | Ressource de la balise. |
| --- | --- |
| [Node](https://developer.adobe.com/experience-manager/reference-materials/spec/javax.jcr/javadocs/jcr-2.0/javax/jcr/Node.html) | Nœud de la balise. |
| … | Tous les éléments auxquels la ressource de la balise peut être adaptée. |

#### Autres {#other}

En outre, Sling/JCR/OCM fournit également un ` [AdapterFactory](https://sling.apache.org/site/adapters.html#Adapters-AdapterFactory)` pour les objets OCM ([Object Content Mapping](https://jackrabbit.apache.org/jcr/object-content-mapping.html)) personnalisés.
