---
title: Réduction des vulnérabilités SSRF (Server Side Request Forgery) pour AEM Forms on JEE 6.5 LTS SP2
description: Procédure de réduction des vulnérabilités SSRF (Server Side Request Forgery) sur les déploiements du pack de services 2 LTS d’AEM Forms on JEE 6.5 exécutés sur JBoss.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: Security
solution: Experience Manager, Experience Manager Forms
feature: Security
role: Admin
exl-id: 7c4a9e12-3b8f-4d6a-9f1e-2a5c8d7e6b04
source-git-commit: 314aafaec6b45d7ea929f32d47e73da293800d4b
workflow-type: tm+mt
source-wordcount: '335'
ht-degree: 28%

---

# Réduction des vulnérabilités SSRF (Server Side Request Forgery)

## Référence rapide {#quick-reference}

| Niveau D&#39;Impact | Versions affectées | Action recommandée |
| --- | --- | --- |
| Critique | Service Pack 2 d’AEM Forms on JEE 6.5 LTS (6.5 LTS SP2) | Installez manuellement le [correctif](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/hotfix/adobe-edcserver-jboss.ear) |
| Non affecté | AEM Forms sur OSGi, Workbench, Cloud Service | Aucune action n’est requise. |

**Vulnérabilités corrigées :**

* SSRF (Server Side Request Forgery) (CWE-918)

## Vue d’ensemble {#overview}

### Éléments affectés {#whats-affected}

| Vulnérabilité | Impact | Composants affectés |
| --- | --- | --- |
| SSRF (Server Side Request Forgery) (CWE-918) | Les attaquant(e)s peuvent inciter le serveur à envoyer des requêtes involontaires à des ressources internes ou externes | AEM Forms on JEE 6.5 LTS SP2 |

### Éléments non affectés {#whats-not-affected}

* Experience Manager Forms Workbench (toutes les versions)
* Experience Manager Forms sur OSGi (toutes les versions)
* Experience Manager Forms as a Cloud Service

## Options de résolution {#resolution-options}

### Avant de commencer {#before-you-start}

Avant d’apporter des modifications, effectuez une sauvegarde du fichier EAR que vous êtes sur le point de remplacer :

* Localisez `adobe-edcserver-jboss.ear` dans votre répertoire de déploiement :

  ```text
  [AEM installation directory]/deploy/adobe-edcserver-jboss.ear
  ```

* Copiez le fichier vers un emplacement de sauvegarde sécurisé en dehors du répertoire de déploiement.
* Vérifiez que la sauvegarde est terminée et accessible avant de procéder aux mises à jour.

Cette précaution vous permet d’effectuer une restauration à l’état d’origine en cas de problème lors du processus de mise à jour.

### Installation manuelle du correctif pour AEM Forms sur JEE 6.5 LTS SP2 (JBoss)

1. Téléchargez `adobe-edcserver-jboss.ear` à partir du portail de distribution de logiciels [Adobe](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/hotfix/adobe-edcserver-jboss.ear).

1. Recherchez `adobe-edcserver-jboss.ear` dans votre répertoire de déploiement et remplacez-le par le fichier téléchargé :

   ```text
   [AEM installation directory]/deploy/adobe-edcserver-jboss.ear
   ```

1. Lancez le gestionnaire de configuration d’AEM Forms pour redéployer le fichier EAR mis à jour et appliquer le correctif.

1. Redémarrez le serveur d’applications et confirmez la réussite du déploiement à partir des journaux du serveur.

## Référence {#references}

* [Bonnes pratiques de sécurité d’Adobe Experience Manager Forms](/help/forms/using/hardening-securing-aem-forms-environment.md)
