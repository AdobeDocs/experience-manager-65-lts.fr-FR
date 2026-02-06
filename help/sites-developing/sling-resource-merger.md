---
title: Utilisation de Sling Resource Merger dans AEM
description: Sling Resource Merger propose des services pour accéder à des ressources et les fusionner.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: platform
content-type: reference
solution: Experience Manager, Experience Manager Sites
feature: Developing
role: Developer
exl-id: 6fb6e522-fb81-4ba2-90b2-aad68f8bfa9e
source-git-commit: 9bc1cad84bb14b7513ede1fff2c1a37768dac442
workflow-type: tm+mt
source-wordcount: '1238'
ht-degree: 39%

---

# Utilisation de Sling Resource Merger dans AEM{#using-the-sling-resource-merger-in-aem}

## Objectif {#purpose}

Sling Resource Merger propose des services pour accéder à des ressources et les fusionner. Il fournit des mécanismes de différenciation pour les deux éléments ci-après :

* Les **[recouvrements](/help/sites-developing/overlays.md)** de ressources à l’aide de [chemins de recherche configurés](/help/sites-developing/overlays.md#configuring-the-search-paths).

* **Remplacements** de boîtes de dialogue de composant pour l’interface utilisateur tactile (`cq:dialog`), à l’aide de la hiérarchie des types de ressource (par le biais de la propriété `sling:resourceSuperType`).

Sling Resource Merger combine les ressources de recouvrement et de remplacement (et leurs propriétés) avec les ressources et propriétés d’origine :

* Le contenu de la définition personnalisée a une priorité supérieure à l’original. En d’autres termes, il *recouvre* ou *remplace*.

* Si nécessaire, les [propriétés](#properties) définies dans la personnalisation indiquent comment utiliser le contenu fusionné à partir de l’original.

>[!CAUTION]
>
>Sling Resource Merger et les méthodes connexes ne peuvent être utilisées qu’avec [Granite](https://developer.adobe.com/experience-manager/reference-materials/6-5/granite-ui/api/index.html). Cela signifie également qu’ils ne sont adaptés qu’à l’IU tactile standard ; les remplacements définis de cette manière, en particulier, ne s’appliquent qu’à la boîte de dialogue tactile d’un composant.
>
>Pour remplacer d’autres zones (y compris d’autres parties d’un composant tactile ou de l’IU classique), copiez le nœud et la structure appropriés de l’original. Placez la copie à l’endroit où vous définissez la personnalisation.

### Objectifs pour AEM {#goals-for-aem}

Sling Resource Merger est utilisé dans AEM pour deux raisons principales :

* S’assurer que les changements de personnalisation ne sont pas effectués dans `/libs`.
* Réduire la structure qui est répliquée à partir de `/libs`.

  Lors de l’utilisation de Sling Resource Merger, il n’est pas recommandé de copier toute la structure depuis `/libs`. En effet, cela entraînerait le stockage d’une trop grande quantité d’informations dans la personnalisation (généralement `/apps`). La duplication des informations augmente inutilement le risque de problèmes lors de la mise à niveau du système.

>[!NOTE]
>
>Les remplacements ne dépendent pas des chemins de recherche. Ils utilisent la propriété `sling:resourceSuperType` pour établir la connexion.
>
>Cependant, les remplacements sont souvent définis sous `/apps`, car une pratique recommandée dans AEM consiste à définir des personnalisations sous `/apps`. En effet, vous ne devez rien modifier sous `/libs`.

>[!CAUTION]
>
>*Ne modifiez rien* dans le chemin d’accès `/libs`.
>
>Cela est dû au fait que le contenu de `/libs` sera écrasé la prochaine fois que vous mettrez à niveau votre instance. Et elle peut très bien être remplacée lorsque vous appliquez un correctif ou un pack de fonctionnalités.
>
>La méthode recommandée pour la configuration et d’autres modifications est la suivante :
>
>1. Recréez l’élément requis (tel qu’il existe dans `/libs`) sous `/apps`.
>
>1. Apportez les modifications désirées dans `/apps`.
>

### Propriétés {#properties}

Resource Merger fournit les propriétés suivantes :

* `sling:hideProperties` (`String` ou `String[]`)

  Indique la propriété, ou la liste des propriétés, à masquer.

  Le caractère générique `*` masque tout.

* `sling:hideResource` (`Boolean`)

  Elle indique si les ressources sont complètement masquées, y compris ses enfants.

* `sling:hideChildren` (`String` ou `String[]`)

  Il contient le nœud enfant, ou la liste des nœuds enfants, à masquer. Les propriétés du nœud sont conservées.

  Le caractère générique `*` masque tout.

* `sling:orderBefore` (`String`)

  Il contient le nom du nœud frère devant lequel le nœud actif est positionné.

Ces propriétés affectent la manière dont les ressources/propriétés d’origine correspondantes (à partir de `/libs`) sont utilisées par le recouvrement/remplacement (souvent en `/apps`).

### Création de la structure {#creating-the-structure}

Pour créer un recouvrement ou un remplacement, vous devez recréer le nœud d’origine, avec la structure équivalente, sous la destination (qui est généralement `/apps`). Par exemple :

* Recouvrement

   * La définition de l’entrée de navigation pour la console Sites, comme illustrée dans le rail, est définie à l’emplacement suivant :

     `/libs/cq/core/content/nav/sites/jcr:title`

   * Pour superposer, créez le nœud suivant :

     `/apps/cq/core/content/nav/sites`

     Mettez ensuite la propriété `jcr:title` à jour selon les besoins.

* Remplacement

   * La définition de la boîte de dialogue tactile de la console Textes est la suivante :

     `/libs/foundation/components/text/cq:dialog`

   * Pour remplacer, créez le nœud suivant. Par exemple :

     `/apps/the-project/components/text/cq:dialog`

Pour créer l’un ou l’autre, il vous suffit de recréer la structure du squelette. Pour simplifier la recréation de la structure, tous les nœuds intermédiaires peuvent être de type `nt:unstructured` (ils ne doivent pas nécessairement refléter le type de nœud d’origine). Par exemple, dans `/libs`.

Ainsi, dans l’exemple de recouvrement ci-dessus, les nœuds suivants sont nécessaires :

```shell
/apps
  /cq
    /core
      /content
        /nav
          /sites
```

>[!NOTE]
>
>Lors de l’utilisation de Sling Resource Merger (c’est-à-dire, lorsque vous employez l’interface utilisateur tactile standard), il n’est pas recommandé de copier l’intégralité de la structure depuis `/libs`. C&#39;est parce que cela entraînerait la conservation d&#39;une trop grande quantité d&#39;information au `/apps`. Par conséquent, cela peut entraîner des problèmes lorsque le système est mis à niveau.

### Cas d’utilisation {#use-cases}

Avec les fonctionnalités standard, ces cas d’utilisation vous permettent d’effectuer les opérations suivantes :

* **Ajouter une propriété**

  La propriété n’existe pas dans la définition de `/libs`, mais est requise dans le recouvrement/remplacement `/apps`.

   1. Créez le nœud correspondant dans `/apps`.
   1. Créez la propriété sur ce nœud.

* **Redéfinir une propriété (pas les propriétés créées automatiquement)**

  La propriété est définie dans `/libs`, mais une nouvelle valeur est requise dans le recouvrement/remplacement `/apps`.

   1. Créez le nœud correspondant dans `/apps`.
   1. Créez la propriété correspondante sur ce nœud (sous `apps`)

      * La propriété a une priorité basée sur la configuration du résolveur de ressource Sling.
      * La modification du type de propriété est prise en charge.

        Si vous utilisez un type de propriété différent de celui utilisé dans `/libs`, c’est le type que vous avez défini qui est utilisé.

  >[!NOTE]
  >
  >La modification du type de propriété est prise en charge.

* **Redéfinir une propriété créée automatiquement**

  Par défaut, les propriétés créées automatiquement (telles que `jcr:primaryType`) ne sont pas soumises à une opération de recouvrement/remplacement pour s’assurer que le type de nœud actuellement sous `/libs` est respecté. Pour imposer un recouvrement/remplacement, vous devez recréer le nœud dans `/apps`, masquer explicitement la propriété et la redéfinir :

   1. Créez le nœud correspondant sous `/apps` avec la propriété `jcr:primaryType` souhaitée.
   1. Créez la propriété `sling:hideProperties` sur ce nœud, avec la valeur définie sur celle de la propriété créée automatiquement ; par exemple, `jcr:primaryType`

      Cette propriété, définie sous `/apps`, est désormais prioritaire sur celle définie sous `/libs`

* **Redéfinir un nœud et ses enfants**

  Le nœud et ses enfants sont définis dans `/libs`, mais une nouvelle configuration est requise dans le recouvrement/remplacement `/apps`.

   1. Combinez les actions des éléments suivants :

      1. Masquer les enfants d’un nœud (en conservant les propriétés du nœud)
      1. Redéfinition de la propriété / des propriétés

* **Masquer une propriété**

  La propriété est définie dans `/libs`, mais n’est pas requise dans le recouvrement/remplacement `/apps`.

   1. Créez le nœud correspondant dans `/apps`.
   1. Créez une propriété `sling:hideProperties` de type `String` ou `String[]`. Permet de spécifier les propriétés à masquer/ignorer. Vous pouvez également utiliser des caractères génériques. Par exemple :

      * `*`
      * `["*"]`
      * `jcr:title`
      * `["jcr:title", "jcr:description"]`

* **Masquer un nœud et ses enfants**

  Le nœud et ses enfants sont définis dans `/libs`, mais ne sont pas requis dans le recouvrement/remplacement `/apps`.

   1. Créez le nœud correspondant sous `/apps`
   1. Créez une propriété `sling:hideResource`

      * type : `Boolean`
      * value : `true`

* **Masquer les enfants d’un nœud (tout en conservant les propriétés du nœud)**

  Le nœud, ses propriétés et ses enfants sont définis dans `/libs`. Le nœud et ses propriétés sont requis dans le recouvrement/remplacement `/apps`, mais certains ou tous les nœuds enfants ne sont pas requis dans le recouvrement/remplacement `/apps`.

   1. Créez le nœud correspondant sous `/apps`
   1. Créez la propriété `sling:hideChildren` :

      * type : `String[]`
      * value : liste des nœuds enfants (tels que définis dans `/libs`) à masquer/ignorer

      Le caractère générique &amp;ast; peut être utilisé pour masquer ou ignorer tous les nœuds enfants.

* **Réorganiser les nœuds**

  Le nœud et ses frères sont définis dans `/libs`. Pour modifier l’ordre, recréez le nœud dans la superposition ou le remplacement de `/apps`. Définissez sa nouvelle position en référençant le nœud frère approprié dans `/libs`.


   * Utilisez la propriété `sling:orderBefore` :

      1. Créez le nœud correspondant sous `/apps`
      1. Créez la propriété `sling:orderBefore` :

         Indique le nœud (comme dans `/libs`) devant lequel le nœud actif est positionné :

         * type : `String`
         * value : `<before-SiblingName>`

### Appeler Sling Resource Merger à partir de votre code {#invoking-the-sling-resource-merger-from-your-code}

Sling Resource Merger comprend deux fournisseurs de ressources personnalisés : un pour les recouvrements et un autre pour les remplacements. Chaque peut être appelé dans votre code à l’aide d’un point de montage :

>[!NOTE]
>
>Lors de l’accès à votre ressource , il est recommandé d’utiliser le point de montage approprié.
>
>Cette approche appelle Sling Resource Merger et renvoie la ressource entièrement fusionnée. Cela réduit également la quantité de structure que vous devez copier à partir de `/libs`.

* Recouvrement :

   * Objectif : fusionner les ressources en fonction de leur chemin de recherche
   * Point de montage :`/mnt/overlay`
   * Usage : `mount point + relative path`
   * Exemple :

      * `getResource('/mnt/overlay' + '<relative-path-to-resource>');`

* Remplacement :

   * Objectif : fusionner les ressources en fonction de leur super-type
   * Point de montage :`/mnt/overide`
   * Usage : `mount point + absolute path`
   * Exemple :

      * `getResource('/mnt/override' + '<absolute-path-to-resource>');`

### Exemple d’utilisation {#example-of-usage}

Voici quelques exemples traités :

* Recouvrement :

   * [Personnalisation des consoles](/help/sites-developing/customizing-consoles-touch.md)
   * [Personnalisation de la création de pages](/help/sites-developing/customizing-page-authoring-touch.md)

* Remplacement :

   * [Configuration de vos propriétés de page](/help/sites-developing/page-properties-views.md#configuring-your-page-properties)
