---
title: Problème d’installation du Service Pack d’AEM Forms JEE 6.5.15.0 dans l’environnement JBoss® Linux®
description: Le Service Pack d’AEM Forms JEE 6.5.15.0 n’est pas installé correctement dans l’environnement JBoss® Linux®. Aucune modification de correctif n’est appliquée au serveur d’applications. Ajoutez le fichier RUP_BOM.xml au répertoire XML.
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms,AEM Forms on JEE
role: User, Developer
exl-id: ba3a5c1e-19db-49cf-ac64-513a6077f3e9
source-git-commit: c3e9029236734e22f5d266ac26b923eafbe0a459
workflow-type: tm+mt
source-wordcount: '196'
ht-degree: 34%

---

# Problème d’installation du pack de services AEM Forms 6.5.15.0 JEE dans l’environnement JBoss® {#aem-forms-installation-issue-environment}

## Problème {#issue}

Le Service Pack d’AEM Forms JEE 6.5.15.0 n’est pas installé correctement dans l’environnement JBoss® Linux®. Dans le fichier `PatchInstallerProcessing[1-9*].log`, l’entrée du journal, `[AEM_Forms_JEE_DIR]/patch/AEMForms-6.5.0-0057/xml/RUP_BOM.xml not found! Assuming this component is not in the installation. Skipping Processing`, est consignée. Cette entrée indique l’échec de l’installation du pack de services 6.5.15.0 d’AEM Forms JEE.

## Application {#applies-to}

Cette solution s’applique aux éléments suivants :
* Environnement JBoss® Linux®

>[!NOTE]
>
> Assurez-vous que l’AEM Forms JEE 6.5.15.0 Service Pack est installé au moins une fois sur le serveur d’applications avant d’exécuter les étapes d’[ajout du fichier RUP_BOM.xml au répertoire XML](#solution-solution).

## Solution {#solution}

Pour résoudre le problème d’installation du pack de services 6.5.15.0 AEM Forms JEE, ajoutez le fichier `RUP_BOM.xml` au répertoire XML :
1. Accédez au dossier dans lequel vous avez extrait le correctif `AEMForms-6.5.0-0057_jboss_linux.tar.gz`.
1. Accédez à l’emplacement `/CDROM_Installers/Linux/Disk1/InstData` et localisez le fichier `Resource1.zip`.
1. Copiez le fichier `Resource1.zip` à un autre emplacement en dehors du dossier extrait et décompressez le fichier `Resource1.zip`.
1. Accédez à `/C_/builds/dev_releng/branches/rrt/aem6.5.0_rollup/tier1/install/patch/fileset_dir/xml` et copiez le fichier.`RUP_BOM.xml`.
1. Collez le fichier RUP_BOM.xml dans `[aem_forms_jee_installation_dir]/patch/AEMForms-6.5.0-0057/xml`.
1. Réinstallez le [pack de services 6.5.15.0 AEM Forms JEE](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases.html?lang=fr).
