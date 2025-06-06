---
title: Sécurité
description: La sécurité des applications commence pendant la phase de développement.
solution: Experience Manager, Experience Manager Sites
feature: Developing,Security
role: Developer
exl-id: abc2747f-cfd8-4ee1-bbc0-5ad89beb383a
source-git-commit: a869ffbc6015fd230285838d260434d9c0ffbcb0
workflow-type: tm+mt
source-wordcount: '392'
ht-degree: 99%

---

# Sécurité{#security}

La sécurité des applications commence pendant la phase de développement. Adobe recommande d’appliquer les bonnes pratiques de sécurité suivantes.

## Utiliser la session de requête {#use-request-session}

Selon le principe de moindre privilège, Adobe recommande d’effectuer chaque accès au référentiel en utilisant la session liée à la requête de l’utilisateur et au contrôle d’accès approprié.

## la fonctionnalité Protection contre les failles cross-site scripting (XSS) {#protect-against-cross-site-scripting-xss}

Les scripts de site à site (XSS) permettent aux pirates d’injecter du code dans des pages web consultées par d’autres utilisateurs. Cette vulnérabilité de sécurité peut être exploitée par des utilisateurs et utilisatrices web malveillants pour contourner les contrôles d’accès.

AEM applique le principe de filtrage de tout le contenu fourni par l’utilisateur ou l’utilisatrice en sortie. La prévention contre les failles XSS se voit accorder la priorité la plus élevée lors des phases de développement et de test.

Le mécanisme de protection XSS proposé par AEM est basé sur la [Bibliothèque Java™ AntiSamy](https://wiki.owasp.org/index.php/Category:OWASP_AntiSamy_Project) fournie par [OWASP (Open Web Application Security Project)](https://owasp.org/). La configuration par défaut d’AntiSamy se trouve à l’adresse

`/libs/cq/xssprotection/config.xml`

Il est important que vous adaptiez cette configuration à vos besoins en matière de sécurité en recouvrant le fichier de configuration. Vous trouverez toutes les informations nécessaires pour satisfaire vos exigences en matière de sécurité dans la [documentation officielle d’AntiSamy](https://wiki.owasp.org/index.php/Category:OWASP_AntiSamy_Project).

>[!NOTE]
>
>Adobe recommande vivement de toujours accéder à l’API de protection XSS en utilisant l’interface [XSSAPI fournie par AEM](https://developer.adobe.com/experience-manager/reference-materials/6-5-lts/javadoc/com/adobe/granite/xss/XSSAPI.html).

En outre, un pare-feu d’application web, tel que le [mod_security pour Apache](https://www.modsecurity.org), peut fournir un contrôle centralisé fiable sur la sécurité de l’environnement de déploiement, ainsi qu’une protection contre les attaques XSS qui n’étaient pas détectées précédemment.

## Accéder aux informations du service cloud {#access-to-cloud-service-information}

>[!NOTE]
>
>Les listes de contrôle d’accès des informations du service cloud et les paramètres OSGi requis pour sécuriser votre instance sont automatisés dans le cadre du [mode Prêt pour la production](/help/sites-administering/production-ready.md). Cela signifie que vous ne devez pas apporter de modifications manuelles à la configuration. Cependant, il est conseillé de les passer en revue avant le déploiement proprement dit.

Lorsque vous [intégrer votre instance AEM à Adobe Experience Cloud](/help/sites-administering/marketing-cloud.md), vous utilisez les [configurations du service cloud](/help/sites-developing/extending-cloud-config.md). Les informations relatives à ces configurations, ainsi que les statistiques collectées, sont stockées dans le référentiel. Si vous utilisez cette fonctionnalité, Adobe vous recommande de déterminer si la sécurité par défaut de ces informations correspond à vos besoins.

Le module webservicesupport écrit des statistiques et des informations de configuration sous :

`/etc/cloudservices`

Avec les autorisations par défaut :

* Environnement de création : `read` pour `contributors`

* Environnement de publication : `read` pour `everyone`

## Protection contre les attaques CRSF {#protect-against-cross-site-request-forgery-attacks}

Pour plus d’informations sur les mécanismes de sécurité mis en œuvre par AEM pour limiter les attaques CSRF, reportez-vous à la section [Filtre du référent Sling](/help/sites-administering/security-checklist.md#protect-against-cross-site-request-forgery) de la liste de contrôle de sécurité et à la [documentation du framework de protection CSRF](/help/sites-developing/csrf-protection.md).
