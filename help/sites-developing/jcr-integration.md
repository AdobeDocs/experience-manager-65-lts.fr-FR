---
title: Intégration JCR
description: Découvrez quelques conseils pour savoir quand vous devez intégrer Adobe Experience Manager au niveau JCR.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: best-practices
solution: Experience Manager, Experience Manager Sites
feature: Developing
role: Developer
exl-id: 6c5715f8-ff7e-47c3-8469-f97b6ea6fe03
source-git-commit: c3e9029236734e22f5d266ac26b923eafbe0a459
workflow-type: tm+mt
source-wordcount: '303'
ht-degree: 100%

---

# Intégration JCR{#jcr-integration}

## Préférence de l’API de ressource Sling à l’API JCR {#prefer-the-sling-resource-api-to-jcr-api}

L’API Sling fonctionne à un niveau plus avancé et plus abstrait que l’API JCR. Ainsi, votre code est plus réutilisable et indépendant du stockage sous-jacent. Cela facilite l’inclusion de données virtuelles externes via le mécanisme ResourceProvider si nécessaire.

## Éviter les requêtes dans la mesure du possible {#avoid-queries-wherever-possible}

Pour récupérer des données, il est toujours plus simple de naviguer dans le référentiel plutôt que d’exécuter une requête. Dans certains cas, les requêtes sont nécessaires, par exemple, une requête d’utilisateur final ou s’il faut trouver du contenu structuré à travers le référentiel entier, mais pour toutes les autres situations, il est préférable de naviguer jusqu’aux nœuds demandés. Les requêtes devraient toujours être évitées en matière de rendus, comme les composants de navigation, une « liste d’éléments récents », le nombre d’éléments, etc. Dans ce cas, il est préférable de parcourir la hiérarchie ou de pré-mettre en cache le résultat afin qu’il puisse être utilisé directement lors du rendu.

## Limiter la portée de l’observation JCR {#restrict-the-scope-of-jcr-observation}

Lors de l’écoute des événements dans le référentiel, il est important de réduire la portée autant que possible. Par exemple, il est préférable d’écouter un événement au niveau `/etc/mycompany` plutôt que `/etc`. N’écoutez jamais les événements à la racine du référentiel. En outre, assurez-vous que les méthodes de rappel s’exécutent aussi rapidement que possible quand il n’y a pas de requêtes.

## Élimination de l’utilisation de l’accès administrateur JCR {#eliminate-use-of-jcr-admin-access}

Depuis la version AEM 6. la connexion à l’administration a été abandonnée, de même que l’obtention d’une session administrative à partir de ResourceResolverFactory. Au contraire, les comptes de service doivent être créés pour les opérations de back-office qui nécessiteraient ce type d’accès, et ResourceResolverFactory peut être utilisé pour obtenir un ResourceResolver pour ce compte.
