---
title: Architecture de contenu
description: Quelques conseils pour la conception de votre contenu (un indice - tout est contenu)
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: best-practices
solution: Experience Manager, Experience Manager Sites
feature: Developing
role: Developer
exl-id: eb47f730-ac26-47a0-9bd7-3b7e94c79ecd
source-git-commit: cc96a14ebaf9f895a798b5f4904f5b4769b990bb
workflow-type: tm+mt
source-wordcount: '407'
ht-degree: 49%

---

# l’architecture de contenu ;{#content-architecture}

## Suivre le modèle de David {#follow-david-s-model}

David Nuescheler a écrit le modèle de David il y a des années, mais ses idées sont toujours valables aujourd’hui. Voici les principes fondamentaux du modèle de David :

* D’abord les données, ensuite la structure. OK.
* Piloter la hiérarchie de contenu ; ne pas la laisser se produire.
* Les espaces de travail sont destinés à `clone()`, `merge()` et `update()`.
* Attention aux parents portant le même nom.
* Les références peuvent être considérées comme dangereuses.
* Les fichiers sont des fichiers.
* Les identifiants sont diaboliques.

Pour consulter le modèle de David, accédez au wiki Jackrabbit à l’adresse [https://wiki.apache.org/jackrabbit/DavidsModel](https://wiki.apache.org/jackrabbit/DavidsModel).

### Tout est du contenu. {#everything-is-content}

Tout doit être stocké dans le référentiel plutôt que de s’appuyer sur des sources de données tierces distinctes, telles que des bases de données. Une telle approche s’applique au contenu créé, aux données binaires telles que les images, le code et les configurations. Il nous permet d’utiliser un ensemble d’API pour gérer tout le contenu et gérer la promotion de ce contenu par le biais de la réplication. Vous obtenez également une source unique de sauvegarde, de journalisation, etc.

### Utiliser le principe de conception « priorité au modèle de contenu » {#use-the-content-model-first-design-principle}

Lors de la mise au point d’une fonctionnalité, commencez toujours par concevoir la structure du contenu JCR, puis tâchez de lire et d’écrire votre contenu à l’aide des servlets Sling par défaut. Une telle approche vous permet de vous assurer que votre implémentation fonctionne bien avec des mécanismes de contrôle d’accès prêts à l’emploi et vous permet d’éviter de générer des servlets de style CRUD inutiles.

### Soyez RESTful {#be-restful}

Définissez les servlets en fonction des types de ressources plutôt que des chemins d’accès. Cette approche permet d’utiliser les contrôles d’accès JCR, de respecter les principes REST, ainsi que d’utiliser la ressource et le résolveur de ressources qui nous sont fournis dans la requête. Cette approche vous permet de modifier les scripts qui effectuent le rendu des URL côté serveur sans modifier les URL côté client. Pour plus de sécurité, les détails d’implémentation côté serveur sont également masqués au client.

### Évitez de définir de nouveaux types de nœud {#avoid-defining-new-node-types}

Les types de nœud fonctionnent à un niveau inférieur dans la couche d’infrastructure. La plupart des exigences sont satisfaites en utilisant un `sling:resourceType` affecté à un type de nœud `nt:unstructured`, `oak:Unstructured`, `sling:Folder` ou `cq:Page`. Les types de nœud correspondent au schéma dans le référentiel. Changer de type de nœud peut s’avérer coûteux à terme.

### Respect des conventions de nommage dans le JCR {#adhere-to-naming-conventions-in-the-jcr}

Le respect des conventions de nommage ajoute de l’homogénéité à votre codebase en réduisant le taux d’incidence des défauts et en augmentant la vitesse de l’équipe de développement qui travaille sur le système. Adobe respecte les conventions suivantes dans le cadre du développement d’AEM :

* Noms des nœuds

   * Tout en minuscules.
   * Séparation des mots à l’aide de tirets.

* Noms des propriétés

   * Majuscule, en commençant par une lettre minuscule.

* Composants (JSP/HTML)

   * Tout en minuscules.
   * Séparation des mots à l’aide de tirets.
