---
title: En-têtes HTTP personnalisés
description: Découvrez comment configurer des en-têtes HTTP personnalisés dans Adobe Experience Manager Commerce.
solution: Experience Manager,Commerce
feature: Commerce Integration Framework
role: Admin, Developer
exl-id: f25cd95c-4235-4430-8a51-38be1f39b880
source-git-commit: c3e9029236734e22f5d266ac26b923eafbe0a459
workflow-type: tm+mt
source-wordcount: '272'
ht-degree: 100%

---

# En-têtes HTTP personnalisés {#custom-http-headers}

## Vue d’ensemble {#overview}

Pour mieux contrôler leur serveur principal, les auteurs peuvent configurer des en-têtes HTTP personnalisés qui seraient envoyés au moteur de commerce, ainsi que ceux déjà envoyés par CIF. Les cas d’utilisation courants incluent des configurations multi-magasin dans lesquelles vous pouvez utiliser des en-têtes HTTP pour contrôler la réponse du serveur principal de commerce.

>[!NOTE]
>
>Les développeurs peuvent toujours configurer des en-têtes HTTP personnalisés à l’aide de la configuration client GraphQL.
>

## Configuration {#configuration}

Pour configurer les en-têtes HTTP personnalisés, vous devez d’abord les définir. Les en-têtes HTTP personnalisés doivent d’abord être définis par le biais de leur ajout à la configuration de service `com.adobe.cq.cif.http.internal.HttpHeadersConfigProviderImpl` à l’aide d’une configuration OSGi.

Vous pouvez configurer les valeurs des en-têtes HTTP dans la page Configuration du service cloud pour votre projet :

1. Accédez à la page de configuration du service cloud dans Outils > Cloud Services > Configuration CIF.
1. Ouvrez une configuration existante ou créez-en une.
1. Accédez à l’onglet « Avancé » et recherchez le champ multiple « En-têtes HTTP personnalisés ». Vous pouvez sélectionner les en-têtes que vous avez définis précédemment et leur attribuer des valeurs.

Les composants qui utilisent la configuration du service cloud ci-dessus envoient ces en-têtes HTTP avec chaque requête GraphQL.

## Restrictions {#restrictions}

Bien que le service permette de définir des noms d’en-tête, y compris ceux qui sont standard, ils ne sont pas disponibles pour configuration. En d’autres termes, vous ne pouvez pas remplacer les en-têtes HTTP standard à l’aide de cette fonctionnalité. Vous trouverez une liste de noms d’en-tête restreints sous [mdn web docs : en-têtes HTTP](https://developer.mozilla.org/fr-FR/docs/Web/HTTP/Headers). En outre, deux en-têtes supplémentaires ne peuvent pas être utilisés :

* « Store » : utilisé par CIF pour identifier la boutique Adobe Commerce.
* « Preview-Version » : utilisé par CIF pour récupérer les produits intermédiaires.
