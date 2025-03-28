---
title: Planification
description: Découvrez ce que vous devez savoir pour planifier vos tests d’Adobe Experience Manager.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: testing
content-type: reference
solution: Experience Manager, Experience Manager Sites
feature: Developing
role: Developer
exl-id: 82199140-e464-45a5-9c00-dda2d8efde74
source-git-commit: c3e9029236734e22f5d266ac26b923eafbe0a459
workflow-type: tm+mt
source-wordcount: '979'
ht-degree: 100%

---

# Planification{#planning}

Ce document décrit ce que vous devez savoir pour planifier votre test. En outre, vous devez répondre aux questions suivantes avant d’effectuer vos tests :

* [Quels environnements de test sont nécessaires ?](/help/sites-developing/test-environments.md)
* [Définition de cas de test](/help/sites-developing/test-cases.md)
* [Les tests - Quand et avec qui ?](/help/sites-developing/when-who.md)

## Avant de commencer {#before-you-start}

Avant de commencer l’analyse réelle et la définition des tests, passez en revue les informations suivantes :

**Architecte AEM** - Consultez la section Concepts de base pour vous familiariser avec l’architecture et les principes de bases d’AEM.

**Documentation** - Pour de plus amples informations, consultez n’importe quelle section de la documentation ou les articles de procédure.

**Principes de base du test** - Vous devez connaître les principes de base relatifs aux test de logiciels et à l’assurance qualité. Vous devriez de préférence avoir de l’expérience dans le test des projets.

Il existe de nombreux sites web, livres et cours traitant de ces principes, qui ne seront donc pas traités en détail dans ce document.

**Idées préconçues à éviter** - On part généralement du principe que votre site web devra satisfaire, chaque jour, des millions de requêtes. Dans certaines circonstances, cela peut être vrai, mais vous ne devez pas prendre cela pour acquis.

Bien qu’il ne soit pas possible de prédire les futurs chiffres avec une précision totale, vous pouvez observer votre site existant et le trafic enregistré pour vous faire une idée. Vous pouvez ensuite faire des estimations en fonction du facteur prévu/espéré en matière d’augmentation du trafic.

**La qualité comme maître-mot** - Il est essentiel que la personne qui réalise les tests fasse preuve d’une totale neutralité et se contente de rapporter les résultats des tests effectués.

Il est de la responsabilité du chef de projet de déterminer les mesures à prendre en fonction des résultats et d’agir en conséquence.

**L’engagement au cœur** - Bien qu’il appartienne au chef ou à la cheffe de projet de s’assurer que toutes les parties s’impliquent pleinement dans toutes les réunions (de statut, ateliers, etc.), vous devez tâcher de vous impliquer le plus tôt possible dans le cycle de projet, y compris pour les processus de collecte d’informations et d’analyse des exigences.

**Impliquer le client** Dans le même esprit, tâchez d’impliquer le client (dans la mesure du possible) lors de la définition de votre protocole et de vos scénarios de test.

## Types de tests {#types-of-tests}

Il existe différentes classifications standard de tests, appropriées pour tester un projet AEM. Familiarisez-vous avec ces éléments pour choisir ce que vous utiliserez :

>[!NOTE]
>
>Ils sont répertoriés dans leur ordre chronologique d’application.

**Tests unitaires** - Tests (généralement) effectués par l’équipe de développement pour s’assurer que les différents éléments se comportent correctement, bien que de manière isolée.

**Tests d’intégration** - Teste les modules lorsqu’ils sont combinés. Ces tests sont effectués après les tests unitaires, mais avant les tests du système.

**Tests de détection de fumée** - Il s’agit de tests « quick-and-dirty » destinés à prouver que le logiciel est en cours d’exécution et qu’une fonctionnalité de haut niveau est disponible. Ces tests ne portent pas sur les détails.

**Tests fonctionnels** - Utilisés pour tester les fonctionnalités du logiciel. Une série de tests sera conçue pour couvrir tous les détails fonctionnels, avec des entrées attendues, inattendues et/ou erronées.

Les tests boîte noire sont des tests fonctionnels d’une unité, d’un composant ou d’un module complet, effectués sans connaissance du fonctionnement interne de l’élément en question.

**Tests du système** - Ces tests sont réalisés sur l’ensemble du système une fois qu’il a été totalement intégré et installé sur une plateforme appropriée.

Ils testent les fonctionnalités sur la base d’une boîte noire.

**Tests de performance** - Les tests de performance sont essentiels dans le cadre du test d’AEM.

Ils sont utilisés pour illustrer les performances dans différentes conditions :

* Normales

  Conditions que le site rencontrera, disons, 90 % du temps. Par exemple, lorsque seule une partie des auteurs ou autrices utilise le système.

* Crête

  Conditions qui seront vécues pendant une durée proportionnellement courte en raison de circonstances spéciales. Ce sera le cas, par exemple, lorsque tous les auteurs et toutes les autrices utilisent le système simultanément ou lorsque du nouveau contenu est publié et qu’un nombre croissant de visiteurs et visiteuses affichent votre site.

* Extrême

  Peut être utilisé pour émuler les prévisions de performances lorsque du nouveau contenu extrêmement intéressant est publié sur votre site web. Un pic extrême peut alors être observé - bien que cela ne soit pas toujours totalement prévisible.

  Ces cas de figure se produisent parfois lorsque des billets pour des événements spécifiques sont mis à disposition ou qu’un site web très attendu est publié pour la première fois.

Les résultats sont ensuite utilisés pour régler l’application.

**Tests de contrainte** - Les tests de contrainte sont effectués pour vérifier le comportement d’un composant ou d’une application dans des conditions extrêmes. On a notamment recours à ces tests pour illustrer la manière dont le comportement se détériorera lors de l’échec de l’élément, ainsi que la façon dont cela se produira.

**Tests de régression** - Les tests de régression sont utilisés pour confirmer qu’une fonctionnalité déjà éprouvée dans une version précédente du logiciel fonctionne toujours correctement.

L’automatisation est particulièrement adaptée dans ce cas (dans la mesure du possible) afin de s’assurer qu’ils peuvent être reproduits rapidement et de manière cohérente.

**Tests d’acceptation** - Les tests d’acceptation constituent une catégorie spéciale, dans la mesure où ils sont utilisés pour indiquer que le client a accepté le projet.

La liste des tests d’acceptation peut contenir une combinaison de tests des différentes catégories ci-dessus et être sélectionnée afin de vérifier que le projet répond aux exigences du client ou de la cliente.

Voir [Acceptation et approbation](/help/sites-developing/acceptance-signoff.md) pour plus de détails.

## Prise en main {#getting-started}

Avant de commencer vos cas de test détaillés et votre plan de test, vous pouvez :

**Définir les objectifs** - Définir vos objectifs de haut niveau pour servir de référence aux processus d’optimisation à mesure que les tests sont réalisés. Vous pouvez :

* tester la fonctionnalité en fonction de la spécification détaillée des exigences ;
* tester les performances en fonction des [mesures cibles](/help/managing/best-practices-further-reference.md#key-performance-indicators-and-target-metrics).

entre autres.

**Collecter des statistiques de trafic à partir du site web existant** - Ces informations peuvent être extraites des fichiers journaux - Consultez la section Surveillance des performances pour plus d’informations.

Ces valeurs vous donnent une indication quant au trafic actuel (volume et étendue) sur le site web existant et peuvent être utilisées comme référence pour le nouveau site web.

**Collecter des statistiques de trafic à partir de sites web externes** - Si possible, vous pouvez essayer de collecter des statistiques de trafic auprès d’autres sites web à des fins de comparaison. Notez toutefois que ces chiffres ne sont pas toujours publiés.

**Confirmer les mesures cibles** - Les mesures sont utilisées pour définir des mesures quantitatives pour la qualité du site web, étant donné qu’elles représentent les objectifs de performance à atteindre.

Elles doivent être définies au début du projet, avec le client ou la cliente. Voir [Mesures cibles](/help/sites-developing/planning.md) pour en savoir plus.
