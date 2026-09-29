---
title: Comment créer des projets AEM à l’aide d’Apache Maven
description: Ce document décrit comment configurer un projet AEM basé sur Apache Maven.
solution: Experience Manager, Experience Manager Sites
feature: Developing,Developer Tools
role: Developer
exl-id: ddc629ac-cf76-4608-9e9b-c8bd3e89da3c
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
  - id: c45915cf-e157-4af7-a80d-97b905bcb3a5
    internal-label: Experience Manager Sites
feature_v2:
  - id: c5d917df-d8bd-5e97-a117-6dde1e9f7103
    internal-label: Developing
  - id: f2d27a5f-0d67-4d85-8a24-86a8d8a3574b
    internal-label: Developer tools
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 2e690827bfa8f3d8227860de4efb802758ae0095
workflow-type: tm+mt
source-wordcount: '171'
ht-degree: 46%
---
# Comment créer des projets AEM à l’aide d’Apache Maven {#how-to-build-aem-projects-using-apache-maven}

AEM 6.5 suit les bonnes pratiques les plus récentes en matière de gestion de packages et de structure de projet. Il utilise l’archétype de projet AEM le plus récent pour les implémentations On-Premise et AMS.

>[!TIP]
>
>Pour plus d’informations, voir :
>
>* L’article [Structure de projet &#x200B;](https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-service/content/implementing/developing/aem-project-content-package-structure) dans la documentation AEM as a Cloud Service pour savoir comment structurer des projets AEM modernes
>* La documentation sur l’[Archétype de projet AEM](https://experienceleague.adobe.com/fr/docs/experience-manager-core-components/using/developing/archetype/overview) pour savoir comment démarrer un nouveau projet AEM à l’aide de l’archétype
>* L’article [Plug-in de module de contenu Maven d’Adobe](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/implementing/developer-tools/maven-plugin#developer-tools) dans la documentation d’AEM as a Cloud Service pour savoir comment déployer les applications AEM.
>
>Les trois documents s’appliquent à AEM 6.5.
