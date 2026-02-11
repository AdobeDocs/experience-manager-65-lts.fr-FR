---
title: Workflow d’installation et de mise à niveau pour AEM Forms sous JEE
description: Workflow d’installation et de mise à niveau pour AEM Forms 6.5 LTS on JEE (JBoss), avec une liste consolidée des fichiers PDF pertinents et leur objectif.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: installing
geptopics: SG_AEMFORMS/categories/jee
docset: aem65
role: Admin
solution: Experience Manager, Experience Manager Forms
feature: AEM Forms on JEE,AEM Forms Upgrade
exl-id: 6d8c0e24-7f08-4e66-bb12-2cf1cfe1d5d3
source-git-commit: fb9f6ef794da7f3b242e9e81a6c2505692c16cd8
workflow-type: tm+mt
source-wordcount: '481'
ht-degree: 3%

---


# Workflow d’installation et de mise à niveau pour AEM Forms sous JEE {#aem-forms-jee-installation-upgrade-documentation}

## Application {#applies-to}

Cette documentation s’applique à **AEM 6.5 LTS Forms**.

Utilisez le workflow et les tableaux suivants pour sélectionner le ou les guides appropriés pour votre scénario. Certains documents sont publiés en tant que PDF ; d’autres documents peuvent être ajoutés au fil du temps lorsqu’ils sont disponibles.

## Workflow d’installation et de mise à niveau {#installation-upgrade-workflow}

1. Passez en revue la section [ Plateformes prises en charge par AEM Forms sur JEE ](/help/forms/using/aem-forms-jee-supported-platforms.md) et assurez-vous que votre système répond aux combinaisons logicielles/matérielles requises.
2. Déterminez si vous effectuez une **nouvelle installation** ou une **mise à niveau**.
3. Pour le chemin d’accès choisi, suivez la séquence décrite ci-dessous (certains scénarios nécessitent plusieurs guides).

## Étapes de préinstallation et de mise à niveau {#start-here}

| Guide | Description |
| --- | --- |
| [Plateformes prises en charge pour AEM Forms sur JEE](/help/forms/using/aem-forms-jee-supported-platforms.md) | Répertorie les combinaisons logicielles et matérielles prises en charge par AEM Forms sur JEE. Utilisez cette option pour valider les conditions préalables avant de commencer une installation ou une mise à niveau. |
| [Topologies d’architecture et de déploiement pour AEM Forms](/help/forms/using/aem-forms-architecture-deployment.md) | Décrit les architectures et les topologies de déploiement recommandées afin que vous puissiez choisir une approche qui correspond à votre environnement (par exemple, serveur unique ou cluster). |
| [Choix d’un type de persistance pour une installation AEM Forms](/help/forms/using/choosing-persistence-type-for-aem-forms.md) | Permet de sélectionner un type de persistance approprié pour la topologie d’installation avant de commencer. |

## Comment installer Adobe Experience Manager Forms (AEM Forms) sur JEE sur JBoss ? {#installing-aem-forms-jee-jboss}

### Clé en main {#install-jee-jboss-turnkey}

| Guide | Description |
| --- | --- |
| [Installation et déploiement d’AEM Forms 6.5 LTS sur JEE à l’aide de JBoss clé en main (PDF)](https://helpx.adobe.com/content/dam/help/en/experience-manager/65LTS/forms/install-turnkey.pdf) | Utilisez pour une **nouvelle installation clé en main** sur JBoss. Ce document fournit des instructions pour l’installation et le déploiement d’AEM Forms sur JEE à l’aide de la distribution clé en main de JBoss. |

### Serveur unique (non clé en main) {#install-jee-jboss-single-server}

| Guide | Description |
| --- | --- |
| [Préparation à l’installation d’AEM Forms (serveur unique) (PDF)](https://helpx.adobe.com/content/dam/help/en/experience-manager/65LTS/forms/prepare-install-single-server.pdf) | Utilisez **avant** une **nouvelle installation sur un serveur unique (non clé en main)**. Ce document répertorie les conditions préalables et les étapes de préparation de l’environnement pour installer AEM Forms sur JEE dans une topologie à serveur unique. |
| [Installation et déploiement d’AEM Forms sur JEE pour JBoss (PDF)](https://helpx.adobe.com/content/dam/help/en/experience-manager/65LTS/forms/install-jboss.pdf) | À utiliser pour l’**installation et le déploiement détaillés** d’AEM Forms sur JEE sur JBoss (**clé en main**). Pour les installations sur un seul serveur, suivez ce guide **après** avoir terminé *Préparation à l’installation d’AEM Forms sur un seul serveur)*. |

<!--
| Preparing to Install AEM Forms (Server Cluster) (PDF) (**TBD**) | Use **before** a **fresh cluster installation**. Describes prerequisites and environment preparation steps for installing AEM Forms on JEE in a server cluster topology. *(Link will be added once the PDF is available.)* |
| [Configuring AEM Forms on JEE on JBoss Cluster (PDF)](https://helpx.adobe.com/content/dam/help/en/experience-manager/65LTS/forms/cluster-jboss.pdf) | Use when setting up and configuring a **JBoss cluster topology** for AEM Forms on JEE. |
-->

## Comment mettre à niveau Adobe Experience Manager Forms (AEM Forms) sur JEE sur JBoss ? {#upgrading-aem-forms-jee-jboss}

### Clé en main {#upgrade-jee-jboss-turnkey}

| Guide | Description |
| --- | --- |
| [Mise à niveau vers AEM Forms 6.5 LTS on JEE pour JBoss clé en main (PDF)](https://helpx.adobe.com/content/dam/help/en/experience-manager/65LTS/forms/upgrade-turnkey.pdf) | À utiliser pour une **mise à niveau clé en main**. Ce document fournit des instructions de mise à niveau d’une installation AEM Forms on JEE JBoss clé en main. |

### Serveur unique {#upgrade-jee-jboss-single-server}

| Guide | Description |
| --- | --- |
| [Préparation à la mise à niveau d’AEM Forms (PDF)](https://helpx.adobe.com/content/dam/help/en/experience-manager/65LTS/forms/prepare-upgrade.pdf) | Utilisez **avant** une **mise à niveau sur un seul serveur**. Décrit comment préparer l’environnement avant la mise à niveau vers AEM 6.5 LTS Forms. Elle s’applique aux environnements qui exécutent AEM Forms sur JEE en mode d’installation sur un seul serveur. |
| [Mise à niveau vers AEM Forms sur JEE pour JBoss (PDF)](https://helpx.adobe.com/content/dam/help/en/experience-manager/65LTS/forms/upgrade-jboss.pdf) | À utiliser pour la **procédure de mise à niveau étape par étape** sur JBoss en mode d’installation **serveur unique**. Suivez ce guide **après** terminé *Préparation à la mise à niveau d’AEM Forms*. |

<!--
| Preparing to Install AEM Forms (Server Cluster) (PDF) (**TBD**) | Use **before** a **cluster upgrade**. Describes how to prepare the environment for a server cluster before upgrading to AEM 6.5 LTS Forms. It applies to environments running AEM Forms on JEE in a server cluster installation mode. *(Link will be added once the PDF is available.)* |
| Upgrading to AEM Forms on JEE for JBoss (Cluster) (PDF) (**TBD**) | Use for the **step-by-step upgrade procedure** on JBoss in a **clustered** installation mode. Follow this guide **after** completing *Preparing to Install AEM Forms (Server Cluster)*. *(Link will be added once the PDF is available.)* | -->

