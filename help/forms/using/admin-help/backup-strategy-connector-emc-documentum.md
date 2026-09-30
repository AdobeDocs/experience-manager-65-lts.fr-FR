---
title: Stratégie de sauvegarde pour les utilisateurs de Connector for EMC Documentum&reg
description: Découvrez comment créer une stratégie de sauvegarde pour les utilisateurs de Connector for EMC Documentum&reg ;.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/aem_forms_backup_and_recovery
products: SG_EXPERIENCEMANAGER/6.5/FORMS
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
exl-id: 019e1a9b-c26c-429f-8153-fceeb85f7096
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
  - id: e8f6de9b-cf88-4405-8d10-15efa08c230e
    internal-label: Experience Manager Forms
feature_v2:
  - id: e72c079d-d036-46d5-b43d-29b276a174c2
    internal-label: Authoring and publishing content
subfeature_v2:
  - id: a26f372d-6d7c-452b-81df-594dd4365ae1
    internal-label: Adaptive Forms
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 2e690827bfa8f3d8227860de4efb802758ae0095
workflow-type: tm+mt
source-wordcount: '155'
ht-degree: 85%
---
# Stratégie de sauvegarde pour les utilisateurs et utilisatrices du connecteur pour EMC Documentum® {#backup-strategy-for-connector-for-emc-documentum-users}

Si le connecteur pour EMC Documentum® est installé, outre les instructions de ce chapitre, votre stratégie de sauvegarde et de récupération doit inclure la sauvegarde (ou la récupération) de l’ordinateur sur lequel le système ECM est installé. (Voir la documentation d’ECM Documentum®).

Sauvegardez votre environnement AEM Forms à l’aide du référentiel ECM et en procédant comme suit :

* Sauvegardez AEM Forms en suivant les instructions décrites dans ce document.
* Sauvegardez votre système ECM Documentum® en suivant les instructions fournies dans [Sauvegarde d’EMC Documentum® Content Server](/help/forms/using/admin-help/backing-recovering-emc-documentum-repository.md#back-up-the-emc-documentum-content-server).

Restaurez l’environnement AEM Forms à l’aide du référentiel ECM et en procédant comme suit :

* Restaurez votre système ECM en suivant les instructions fournies dans [Restauration d’EMC Documentum® Content Server](/help/forms/using/admin-help/backing-recovering-emc-documentum-repository.md#restore-the-emc-documentum-content-server).
* Restaurez AEM Forms en suivant les instructions décrites dans ce document.
