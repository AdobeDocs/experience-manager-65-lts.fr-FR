---
title: Mettre à jour le code et les personnalisations
description: Découvrez la mise à niveau de code et les personnalisations dans AEM.
contentOwner: sarchiz
topic-tags: upgrading
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
docset: aem65
targetaudience: target-audience upgrader
feature: Upgrading
solution: Experience Manager, Experience Manager Sites
role: Admin
source-git-commit: 3d4e458e4c96c547b94c08d100271ca6cf96f707
workflow-type: tm+mt
source-wordcount: '1006'
ht-degree: 51%

---

# Mettre à jour le code et les personnalisations{#upgrading-code-and-customizations}

Lors de la planification d’une mise à niveau, les aspects suivants d’une mise en œuvre doivent être étudiés et abordés.

* [Mise à niveau de la base de code](#upgrade-code-base)
* [Procédure de test](#testing-procedure)

## Présentation {#overview}

1. **AEM Analyzer** - Exécutez AEM Analyzer comme défini sur la page [Évaluation de la complexité de la mise à niveau avec AEM Analyzer](/help/sites-deploying/pattern-detector.md). Vous obtenez un rapport AEM Analyzer qui contient plus de détails sur les zones qui doivent être traitées en plus des API/lots indisponibles dans la version cible d’AEM. Le rapport AEM Analyzer vous donne une indication des incompatibilités éventuelles de votre code. S’il n’en existe pas, votre déploiement est compatible avec AEM 6.5 LTS. Vous pouvez toujours choisir d’effectuer un nouveau développement pour utiliser AEM 6.5 LTS, mais vous n’en avez pas besoin uniquement pour maintenir la compatibilité.
1. **Développement de la base de code pour LTS 6.5**- Créez une branche ou un référentiel dédié à la base de code pour la version AEM cible. Utilisez les informations de la compatibilité avant la mise à niveau pour prévoir les zones de code à mettre à jour.
1. **Compilation avec 6.5 LTS Uber jar**- Mettez à jour les POM de base de code pour pointer vers AEM 6.5 LTS Uber jar et compilez le code en fonction de celui-ci.
1. **Déployer dans un environnement LTS 6.5** - Une instance LTS 6.5 d’AEM (auteur + publication) nette doit être configurée dans un environnement Dev/QA. La base de code à jour et un échantillon représentatif de contenu (de l’exploitation actuelle) doivent être déployés.
1. **Validation du contrôle qualité et correction des bogues** - Le contrôle qualité doit valider l’application sur les instances d’auteur et de publication du LTS AEM 6.5. Tous les bugs détectés doivent être corrigés et intégrés dans la base de code LTS d’AEM 6.5. Répétez le cycle de développement jusqu’à ce que tous les bugs soient corrigés.

Avant de procéder à la mise à niveau, vous devez disposer d’une base de code d’application stable qui a été minutieusement testée par rapport à AEM 6.5 LTS.

## Mise à niveau de la base de code {#upgrade-code-base}

### Création d’une branche dédiée pour le code LTS 6.5 dans le {#create-a-dedicated-branch-for-6.5-lts-code-in-version-control} de contrôle de version

Tout le code et toutes les configurations nécessaires pour votre mise en oeuvre d’AEM doivent être gérés à l’aide d’une forme de gestion de versions. Une branche dédiée à la gestion de versions doit être créée pour gérer les modifications nécessaires pour la base de code dans la version cible d’AEM. Les tests itératifs de la base de code par rapport à la version cible d’AEM et les correctifs de bugs ultérieurs sont gérés dans cette branche.

### Mise à jour de la version AEM Uber Jar {#update-the-aem-uber-jar-version}

AEM Uber jar inclut toutes les API d’AEM en tant que dépendance unique dans le fichier `pom.xml` de votre projet Maven. Il est toujours recommandé d’inclure Uber Jar en tant que dépendance unique au lieu d’inclure les dépendances d’API d’AEM individuelles. Lors de la mise à niveau de la base de code, modifiez la version d’Uber Jar afin qu’elle pointe vers la version 6.5 LTS d’AEM. Mettez à jour toutes les API ou méthodes obsolètes afin qu’elles soient compatibles avec la version cible d’AEM. Recompilez la base de code sur la nouvelle version d’Uber Jar.

```
<dependency>
    <groupId>com.adobe.aem</groupId>
    <artifactId>uber-jar</artifactId>
    <version>6.6.0</version>
    <classifier>apis</classifier>
    <scope>provided</scope>
</dependency>
```

>[!NOTE]
>
>Il existe une légère différence dans la manière dont les Uber Jars AEM 6.5 et AEM 6.5 LTS sont compilés. Consultez la section ci-dessous :

**Uber Jars pour AEM 6.5**

1. `uber-jar-6.5.x.jar` : contient toutes les API publiques d’AEM 6.5.
1. `uber-jar-6.5.x-apis-with-deprecations.jar` - Inclut les API publiques et les API obsolètes d’AEM 6.5.

**Uber Jars pour AEM 6.5 LTS**

Pour AEM 6.5 LTS, il existe à nouveau deux types de fichiers Uber Jars :

1. `uber-jar-6.6.x-apis.jar` : contient toutes les API publiques d’AEM 6.5 LTS.
1. `uber-jar-6.6.x-deprecated-apis.jar` - Inclut uniquement les API obsolètes d’AEM 6.5 LTS.

**Principale différence : AEM 6.5 par rapport à AEM 6.5 LTS Uber Jars**

* Dans AEM 6.5, si des API publiques et obsolètes sont nécessaires, vous pouvez utiliser inclure un seul fichier jar, `uber-jar-6.5.x-apis-with-deprecations.jar` dans votre fichier `pom.xml`.
* Dans AEM 6.5 LTS, si vous avez besoin à la fois d’API publiques et obsolètes, vous devez inclure deux fichiers jar distincts, `uber-jar-6.6.x-apis.jar` pour les API publiques et `uber-jar-6.6.x-deprecated-apis.jar` pour les API obsolètes.

**Coordonnées Maven pour le fichier Jar des API obsolètes**

```
<dependency>
    <groupId>com.adobe.aem</groupId>
    <artifactId>uber-jar</artifactId>
    <version>6.6.0</version>
    <classifier>apis</classifier>
    <scope>provided</scope>
</dependency>
```

### Notes du développeur {#developer-notes}

* Le LTS AEM 6.5 n’inclut pas de bibliothèque Google guava prête à l’emploi. La version requise peut être installée selon les besoins.
* Le bundle Sling XSS utilise désormais la bibliothèque Java HTML Sanitizer et l’utilisation de la méthode `XSSAPI#filterHTML()` doit être utilisée pour effectuer le rendu du contenu HTML en toute sécurité et non pour transmettre des données à d’autres API.

## Procédure de test {#testing-procedure}

Un plan de test complet doit être préparé pour tester les mises à niveau. Le test de la base de code et de l’application mises à niveau doit d’abord être effectué dans les environnements inférieurs. Tous les bugs détectés doivent être corrigés itérativement jusqu’à ce que la base de code soit stable, après quoi les environnements de niveau supérieur doivent être mis à niveau.

### Test de la procédure de mise à niveau {#testing-upgrade-procedure}

La procédure de mise à niveau décrite ici doit être testée sur les environnements de développement et d’assurance qualité, comme indiqué dans votre runbook personnalisé (voir [Planification de la mise à niveau](/help/sites-deploying/upgrade-planning.md)). La procédure de mise à niveau doit être répétée jusqu’à ce que toutes les étapes soient documentées dans le runbook de mise à niveau et que le processus de mise à niveau soit fluide.

### Zones de test de l’implémentation  {#implementation-test-areas-}

Vous trouverez ci-dessous les zones critiques de toute implémentation d’AEM qui doivent être couvertes par votre plan de test une fois l’environnement mis à niveau et la base de code mise à niveau déployée.

<table>
 <tbody>
  <tr>
   <td><strong>Zone de test fonctionnelle</strong></td>
   <td><strong>Description</strong></td>
  </tr>
  <tr>
   <td>Sites publiés</td>
   <td>Test de l’implémentation d’AEM et du code associé au niveau de la publication<br /> par le biais du Dispatcher. Le test doit inclure des critères pour les mises à jour de page et<br /> l’invalidation du cache.</td>
  </tr>
  <tr>
   <td>Création</td>
   <td>Test de l’implémentation d’AEM et du code associé au niveau de création. Ce test doit inclure la page, la création de composants et les boîtes de dialogue.</td>
  </tr>
  <tr>
   <td>Intégrations aux solutions Experience Cloud</td>
   <td>la validation des intégrations avec des produits tels qu’Analytics ;</td>
  </tr>
  <tr>
   <td>Intégrations à des systèmes tiers</td>
   <td>Validez toutes les intégrations tierces sur les niveaux de création et de publication.</td>
  </tr>
  <tr>
   <td>Authentification, sécurité et autorisations</td>
   <td>Tous les mécanismes d’authentification tels que LDAP/SAML doivent être validés.<br /> Les autorisations et les groupes doivent être testés sur les niveaux de création et de publication.<br />.</td>
  </tr>
  <tr>
   <td>Requêtes</td>
   <td>Les index et requêtes personnalisés doivent être testés avec les performances des requêtes.</td>
  </tr>
  <tr>
   <td>Personnalisations de l’interface utilisateur</td>
   <td>Toutes les extensions ou personnalisations de l’interface utilisateur d’AEM dans l’environnement de création.</td>
  </tr>
  <tr>
   <td>Workflows</td>
   <td>Workflow et fonctionnalités personnalisés ou prêts à l’emploi.</td>
  </tr>
  <tr>
   <td>Test de performance</td>
   <td>Les tests de chargement doivent être effectués sur les niveaux de création et de publication qui simulent des scénarios en situation réelle.</td>
  </tr>
 </tbody>
</table>

### Documentation du plan de test et des résultats {#document-test-plan-and-results}

Vous devez créer un plan de tests qui couvre les zones de tests d’implémentation décrites ci-dessus. Souvent, il est logique de séparer le plan de test par les listes de tâches de création et de publication. Ce plan de test doit être exécuté sur les environnements de développement, d’assurance qualité et d’évaluation avant la mise à niveau des environnements de production. Les résultats de test et les mesures de performances doivent être enregistrés dans des environnements inférieurs afin de fournir une comparaison lors de la mise à niveau des environnements d’évaluation et de production.
