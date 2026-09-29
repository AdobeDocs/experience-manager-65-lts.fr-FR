---
title: Le framework de protection CSRF
description: Le framework utilise des jetons pour garantir que la demande du client est légitime
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: introduction
content-type: reference
solution: Experience Manager, Experience Manager Sites
feature: Developing
role: Developer
exl-id: d6bd4028-56c9-4e09-9bba-1199a41b41b8
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
  - id: c45915cf-e157-4af7-a80d-97b905bcb3a5
    internal-label: Experience Manager Sites
feature_v2:
  - id: c5d917df-d8bd-5e97-a117-6dde1e9f7103
    internal-label: Developing
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 2e690827bfa8f3d8227860de4efb802758ae0095
workflow-type: tm+mt
source-wordcount: '278'
ht-degree: 88%
---
# Le framework de protection CSRF{#the-csrf-protection-framework}

Outre le filtre référent Apache Sling, Adobe fournit également un nouveau framework de protection CSRF pour se protéger contre ce type d’attaque.

Le framework utilise des jetons pour garantir que la demande du client est légitime. Les jetons sont générés lorsque le formulaire est envoyé au client et validé lorsque le formulaire est renvoyé au serveur.

>[!NOTE]
>
>Il n’y a aucun jeton sur les instances de publication pour les utilisateurs anonymes.

## Conditions requises {#requirements}

### Dépendances {#dependencies}

Tout composant associé à la dépendance `granite.jquery` bénéficie automatiquement du framework de protection CSRF. Si ce n’est pas le cas pour l’un de vos composants, vous devez déclarer une dépendance à `granite.csrf.standalone` avant de pouvoir utiliser le framework.

### Réplication de la clé de chiffrement {#replicating-crypto-keys}

Pour utiliser les jetons, vous devez répliquer le HMAC binaire sur toutes les instances de votre déploiement. Voir [Répliquer la clé HMAC](/help/sites-administering/encapsulated-token.md#replicating-the-hmac-key) pour plus d’informations.

>[!NOTE]
>
>Assurez-vous également d’effectuer les modifications de configuration du Dispatcher nécessaires pour utiliser le framework de protection CSRF :
>
>* [Configurer le Dispatcher Adobe Experience Manager afin d’empêcher les attaques CSRF](https://experienceleague.adobe.com/fr/docs/experience-manager-dispatcher/using/configuring/configuring-dispatcher-to-prevent-csrf)
>* [Vue d’ensemble du Dispatcher](https://experienceleague.adobe.com/fr/docs/experience-manager-dispatcher/using/dispatcher)

>[!NOTE]
>
>Si vous utilisez le cache de manifeste avec votre application web, veillez à ajouter « **&ast;** » au manifeste pour vous assurer que le jeton ne prend pas l’appel de génération de jeton CSRF hors ligne. Pour plus d’informations, consultez ce [lien](https://www.w3.org/TR/offline-Webapps/).
>
>Pour plus d’informations sur les attaques CSRF et les moyens de s’en protéger, consultez la page [Cross-Site Request Forgery OWASP](https://owasp.org/www-community/attacks/csrf).
