---
title: Questions fréquentes
description: Questions fréquentes sur AEM 6.5 LTS.
solution: Experience Manager
feature: Release Information
role: User,Admin,Developer
exl-id: d18c9dc3-fdcc-4558-b9b6-ecf1ce61048a
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
feature_v2:
  - id: ed762d86-a04b-452b-a08f-86359bb8ff27
    internal-label: Configuration and operations
subfeature_v2:
  - id: c21ccc2b-e0c8-4853-bf41-f12259ed93f8
    internal-label: Release information
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 2e690827bfa8f3d8227860de4efb802758ae0095
workflow-type: tm+mt
source-wordcount: '546'
ht-degree: 91%
---
# Questions fréquentes sur AEM 6.5 LTS {#faq}

Cette page est destinée à répondre à des questions fréquentes sur AEM 6.5 LTS.

## Pourquoi Adobe a-t-il publié 6.5 LTS pour AEM ?

Adobe accorde une grande importance à la sécurité et à la stabilité des applications fournies. La prise en charge à long terme d’AEM 6.5 pose les bases des futures mises à jour d’AEM 6.5. AEM 6.5 LTS inclut notamment la prise en charge d’Oracle Java 17 et Java 21, et sera la branche AEM qui recevra les nouvelles fonctionnalités et innovations d’AEM.

## Je suis un client ou une cliente On-Premise. Que se passe-t-il si je ne mets pas à niveau vers AEM 6.5 LTS ?

AEM 6.5 LTS comprend d’importantes mises à jour de sécurité et de stabilité, notamment la prise en charge d’Oracle Java 17 et Java 21. Il est recommandé aux entreprises de planifier une mise à niveau vers la version 6.5 LTS. Adobe continuera à prendre en charge AEM 6.5 jusqu’au 28 février 2027. Consultez la [feuille de route](https://experienceleague.adobe.com/en/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap#aem65) pour plus d’informations.

## Mes personnalisations et intégrations existantes seront-elles impactées si j’effectue la mise à niveau vers AEM 6.5 LTS ?

Bien qu’AEM 6.5 LTS vise à maintenir la rétrocompatibilité, certaines fonctionnalités et artefacts hérités ont été supprimés.
Il est essentiel de consulter les [notes de mise à jour](/help/release-notes/release-notes.md#deprecated-and-removed-features) et d’utiliser l’[outil AEM Analyzer](/help/sites-deploying/aem-analyzer.md) pour évaluer l’impact sur vos personnalisations et intégrations.

## Comment assurer une transition en douceur vers AEM 6.5 LTS ?

Pour garantir une transition en douceur, il est recommandé de :

* Passer en revue attentivement les [notes de mise à jour](/help/release-notes/release-notes.md) et la documentation.
* Utiliser l’[outil AEM Analyzer](/help/sites-deploying/aem-analyzer.md) pour évaluer la complexité de la mise à niveau.
* Planifiez et allouez suffisamment de temps et de ressources pour le processus de mise à niveau.
* Collaborer avec le support Adobe et participer aux sessions d’accompagnement pour obtenir des conseils et de l’aide.

## Que sont les packs de services AEM 6.5 LTS ?

Les packs de services AEM 6.5 LTS sont une mise à jour cumulative qui inclut tous les correctifs et améliorations apportés à AEM 6.5 LTS depuis sa version initiale. Il est recommandé d’appliquer le dernier pack de services pour vous assurer que votre instance AEM est à jour avec les derniers correctifs de sécurité et fonctionnalités.

## Je suis actuellement sur AEM 6.5, puis-je effectuer la mise à niveau directement vers le pack de services AEM 6.5 LTS sans effectuer la mise à niveau vers la version AEM 6.5 LTS GA ?

Oui, vous pouvez effectuer directement la mise à niveau d’AEM 6.5 vers n’importe quel pack de services AEM 6.5 LTS. Nous vous recommandons de consulter les [notes de mise à jour](/help/release-notes/release-notes.md) et la section [Mise à niveau vers AEM 6.5 LTS](/help/sites-deploying/upgrade.md).

## Je suis actuellement sur AEM 6.5 LTS GA, dois-je apporter des modifications au code pour effectuer la mise à niveau vers les packs de services AEM 6.5 LTS ?

Non, vous n’avez pas besoin d’apporter de modifications au code pour effectuer la mise à niveau d’AEM 6.5 LTS vers les packs de services AEM 6.5 LTS. Cependant, nous recommandons toujours de consulter les [notes de mise à jour](/help/release-notes/release-notes.md) et de tester vos personnalisations et intégrations dans un environnement d’évaluation avant d’appliquer le pack de services à votre instance de production.

## Je souhaite repartir de zéro avec une nouvelle configuration AEM 6.5 LTS. Puis-je commencer directement avec le pack de services AEM 6.5 LTS ?

Oui, vous pouvez configurer directement un nouveau pack de services AEM 6.5 LTS sans configurer le build AEM 6.5 LTS GA. Nous recommandons de consulter les [notes de mise à jour](/help/release-notes/release-notes.md) et la section [Installation autonome personnalisée](/help/sites-deploying/custom-standalone-install.md) pour plus d’informations.
