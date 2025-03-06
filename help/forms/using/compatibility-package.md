---
title: Package de compatibilité
description: L’installation du package de compatibilité sur le LTS AEM Forms 6.5 vous permet d’utiliser les ressources de Correspondence Management d’AEM Forms 6.5 et versions antérieures, ainsi que les modèles et pages de formulaires adaptatifs obsolètes
role: Admin,User
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
exl-id: 3a529a82-e2fd-423c-96c1-a5accc87775e
source-git-commit: 2e0cbe62754866d31de69547f9af1f2f63930f2c
workflow-type: tm+mt
source-wordcount: '364'
ht-degree: 54%

---

# Package de compatibilité{#compatibility-package}

## Présentation {#overview}

La communication interactive est l’approche par défaut et recommandée pour créer des communications client dans AEM Forms 6.5 LTS. Pour continuer à utiliser les lettres dans AEM Forms 6.5 LTS, vous devez installer le dernier [package de compatibilité AEMFD](https://experienceleague.adobe.com/fr/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases).

Le package de compatibilité AEMFD vous permet également d’[utiliser les ressources AEM Forms 6.5.22.0, 6.4, 6.3 et 6.2 suivantes sur AEM Forms 6.5 LTS](../../forms/using/compatibility-package.md#add-support-for-aem-forms-and-assets-in-aem-forms)

* Fragments de document
* Lettres
* Dictionnaires de données
* Modèles et pages obsolètes de formulaires adaptatifs

Pour plus d’informations, consultez la section [Ressources devenues compatibles avec AEM Forms 6.5 après l’installation du package de compatibilité](../../forms/using/compatibility-package.md#assetsmadecompatible).

## Ajoutez la prise en charge des ressources AEM Forms 6.5, 6.4, 6.3 et 6.2 dans AEM Forms 6.5 LTS {#add-support-for-aem-forms-and-assets-in-aem-forms-6.5.lts}

Après avoir effectué une mise à niveau, exécutez les opérations suivantes pour installer le package de compatibilité AEMFD et rendre vos actifs compatibles avec la version 6.5 :

Assurez-vous que le [package de compatibilité AEM](https://experienceleague.adobe.com/fr/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases) est préinstallé.

1. Installez la dernière version d’AEM 6.5 LTS [package de compatibilité](https://experienceleague.adobe.com/fr/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases).

   Pour plus d’informations sur le chargement et l’installation du package, consultez [Utilisation de packages](/help/sites-administering/package-manager.md).

1. Une fois les journaux stabilisés, redémarrez le serveur.
1. Utilisez l’utilitaire de migration pour rendre vos ressources compatibles avec 6.5 LTS.

   >[!NOTE]
   >
   > Il est recommandé d’utiliser la commande `Ctrl + C` pour redémarrer le SDK. Le redémarrage du SDK AEM à l’aide de méthodes alternatives, par exemple l’arrêt des processus Java, peut entraîner des incohérences dans l’environnement de développement AEM.

   Pour plus d’informations, consultez la section [Utilitaire de migration](../../forms/using/migration-utility.md).

## Compatibilité d’Assets avec AEM Forms 6.5 LTS via l’installation du package de compatibilité {#assetsmadecompatible}

En installant le package de compatibilité , vous pouvez rendre les ressources et modèles suivants compatibles avec AEM Forms 6.5 LTS :

* Actifs de Correspondence Management d’AEM 6.4 et versions antérieures:

   * [Lettres](../../forms/using/create-letter.md)
   * [Dictionnaires de données](/help/forms/using/data-dictionary.md)
   * Fragments de document

* Modèles obsolètes de formulaires adaptatifs :

   * /libs/fd/af/templates/blankTemplate2
   * /libs/fd/af/templates/simpleEnrollmentTemplate
   * /libs/fd/af/templates/simpleEnrollmentTemplate2
   * /libs/fd/af/templates/surveyTemplate
   * /libs/fd/af/templates/surveyTemplate2
   * /libs/fd/af/templates/tabbedEnrollmentTemplate
   * /libs/fd/af/templates/tabbedEnrollmentTemplate2
   * /libs/fd/afaddon/templates/advancedEnrollmentTemplate
   * /libs/fd/afaddon/templates/advancedEnrollmentTemplate2

* Pages obsolètes de formulaires adaptatifs :

   * /libs/fd/af/components/page/survey
   * /libs/fd/af/components/page/tabbedenrollment
   * /libs/fd/afaddon/components/page/advancedenrollment
