---
title: Notes de mise à jour pour  [!DNL Adobe Experience Manager] 6.5 LTS SP1
description: 'Recherchez des informations sur la mise à jour, les nouveautés, la procédure d’installation et une liste détaillée des modifications pour la version 6.5 du LTS SP1 d’ [!DNL Adobe Experience Manager] '
solution: Experience Manager
feature: Release Information
role: User,Admin,Developer
source-git-commit: 27ec3c516b0746fd7e0d82f86750fbb4ef410711
workflow-type: tm+mt
source-wordcount: '566'
ht-degree: 3%

---


# Notes de mise à jour de Adobe Experience Manager (AEM) Forms 6.5 LTS SP1 on JEE

## Informations sur la version

| **Produit** | Adobe Experience Manager Forms |
| -------------------- | ------------------------------------ |
| **Version** | 6.5 LTS SP1 |
| **Type** | Service Pack d’assistance à long terme (JEE) |
| **Catégorie de version** | Version de mise à niveau |
| **URL de téléchargement** | Distribution logicielle |

## Éléments compris dans [!DNL Experience Manager] 6.5 LTS SP1 {#what-is-included-in-aem-65ltssp1}

Adobe Experience Manager (AEM) Forms **6.5 LTS SP1 on JEE** offre de nouvelles fonctionnalités, des mises à jour de plateforme importantes demandées par les clients et les clientes, ainsi que des correctifs généraux, en mettant l’accent sur la stabilité du produit et la prise en charge à long terme.

## Éléments compris dans AEM Forms 6.5 LTS SP1

### &#x200B;1. Mises à jour de la prise en charge Java

La prise en charge des versions Java plus récentes a été introduite :

* **Java™ 17**
* **Java™ 21**

### &#x200B;2. Mises À Jour De La Prise En Charge Du Serveur D’Applications

#### Prise en charge de JBoss EAP 8

* Ajout de la prise en charge de **JBoss EAP 8**.
* Le framework de sécurité hérité **PicketBox** a été supprimé.
* Les **boutiques d’informations d’identification basées sur Elytron** sont désormais prises en charge pour une gestion sécurisée des informations d’identification.

##### Configuration : banque d’informations d’identification (basée sur Elytron)

AEM Forms sur JBoss EAP 8 utilise Elytron pour gérer les informations d’identification sécurisées. Les clients doivent configurer un magasin d’informations d’identification basé sur Elytron pour réussir le démarrage du serveur et sécuriser l’authentification de la base de données.

Pour plus d’informations sur la configuration, consultez le guide d’installation et de configuration .

### &#x200B;3. Modification de la plateforme et de la compatibilité

#### Prise en charge des spécifications de servlet

* Prise en charge de **Servlet Specification 5+**
* Conforme à la norme **Jakarta EE 9**

#### Exigence de migration de l’espace de noms

* Jakarta EE 9 introduit un changement d’espace de noms de `javax.*` à `jakarta.*`
* Tous les **DSC personnalisés** doivent être migrés vers l’espace de noms `jakarta.*`
* AEM Forms 6.5 LTS SP1 prend en charge **uniquement les serveurs d’applications Jakarta EE 9 et ultérieure**

Pour plus d’informations, voir **Migration de l’espace de noms javax vers jakarta**.

## Mise à niveau

Pour obtenir des instructions de mise à niveau détaillées, consultez le [&#x200B; Guide de mise à niveau pour AEM Forms 6.5 LTS SP1 sous JEE](https://experienceleague.adobe.com/fr/docs/experience-manager-65-lts/content/forms/upgrade-aem-forms/upgrade)

## Installation

Pour connaître les étapes d’installation et les conditions préalables requises, reportez-vous au **Guide d’installation d’AEM Forms 6.5 LTS SP1 (JEE)**.

## Plateformes prises en charge

Pour obtenir la liste complète des plateformes, systèmes d’exploitation, bases de données et serveurs d’applications pris en charge, reportez-vous à :

**Matrice des plateformes prises en charge - AEM Forms 6.5 LTS SP1 (JEE)**

## Fonctionnalités obsolètes et supprimées

* La prise en charge de **RDBMK** pour la persistance du référentiel CRX a été supprimée.
* Pour les environnements en cluster, **seul MongoMK** est pris en charge pour la persistance du référentiel.

## Migration de javax vers l’espace de noms jakarta

### Migration de `javax` vers l’espace de noms `jakarta`

À compter de **AEM Forms 6.5 LTS SP1**, seuls les serveurs d’applications qui implémentent **Jakarta Servlet API 5/6** sont pris en charge. Avec **Jakarta EE 9 et versions ultérieures**, toutes les API sont passées de l’espace de noms `javax.{}` à `jakarta.`.

Par conséquent, **tous les DSC personnalisés doivent utiliser l’espace de noms `jakarta`**. Les composants personnalisés créés à l’aide d’API `javax.{}` ne sont **pas compatibles** avec les serveurs d’applications pris en charge.

### Options de migration pour les DSC personnalisés

Vous pouvez migrer des DSC personnalisés existants à l’aide de l’une des approches suivantes :

#### Option 1 : Migration Du Code Source (Recommandé)

* Mettre à jour toutes les instructions d’importation de `javax.{}` vers `jakarta.`
* Recréer et recompiler les projets DSC personnalisés
* Redéployez les composants mis à jour sur le serveur d’applications

**Avantages :**

* Garantit la compatibilité à long terme avec Jakarta EE 9+
* Convient mieux aux projets gérés de manière active

#### Option 2 : Migration Binaire À L’Aide Du Transformateur Eclipse

* Utilisez l’outil **Eclipse Transformer** pour convertir des fichiers binaires compilés (`.jar`, `.war`) de `javax` en `jakarta`
* Aucune recompilation ou modification du code source requise
* Redéployez les fichiers binaires transformés sur le serveur d’applications

>[!NOTE]
>
> La transformation binaire est effectuée au niveau du **bytecode**.

Exemples de mappages d’importation

Vous trouverez ci-dessous des exemples courants de changements d’espace de noms requis lors de la migration :

Avant (javax)    Après (jakarta)
javax.servlet.*    jakarta.servlet.*
javax.servlet.http.*    jakarta.servlet.http.*

### Exemples de mappages d’importation

Le tableau suivant présente les modifications courantes des espaces de noms requises lors de la migration de `javax` vers `jakarta` :

| Avant (`javax`) | Après (`jakarta`) |
| ---------------------- | ------------------------ |
| `javax.servlet.*` | `jakarta.servlet.*` |
| `javax.servlet.http.*` | `jakarta.servlet.http.*` |

Utilisez ces mappages comme référence lors de la mise à jour du code source DSC personnalisé ou de la validation des fichiers binaires transformés.

