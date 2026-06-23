---
title: Réduction des vulnérabilités VULN-36128 et VULN-36120 pour AEM Forms on JEE 6.5 LTS SP2
description: Étapes de réduction pour les déploiements VULN-36128 et VULN-36120 sur AEM Forms on JEE 6.5 LTS Service Pack 2 s’exécutant sur JBoss.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: Security
solution: Experience Manager, Experience Manager Forms
feature: Security
role: Admin
exl-id: 7c4a9e12-3b8f-4d6a-9f1e-2a5c8d7e6b04
source-git-commit: 1b876f20cbc3a00a02a4449f0d353fb858695235
workflow-type: tm+mt
source-wordcount: '303'
ht-degree: 14%

---

# Réduction des vulnérabilités VULN-36128 et VULN-36120 pour AEM Forms on JEE 6.5 LTS SP2

## Référence rapide {#quick-reference}

| Niveau D&#39;Impact | Versions affectées | Action recommandée |
| --- | --- | --- |
| Critique | Service Pack 2 d’AEM Forms on JEE 6.5 LTS (6.5 LTS SP2) | Installez manuellement le [correctif](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/hotfix/adobe-edcserver-jboss.ear) |
| Non affecté | AEM Forms sur OSGi, Workbench, Cloud Service | Aucune action n’est requise. |

**Vulnérabilités corrigées :**

* **VULN-36128** : vulnérabilité d’exécution de code à distance permettant à des attaquant·e·s distant non autorisés d’exécuter du code arbitraire.
* **VULN-36120** : vulnérabilité de validation d’entrée incorrecte qui pourrait autoriser un accès non autorisé à des informations sensibles.

## Étapes de réduction {#mitigation-steps}

### Avant de commencer {#before-you-start}

Avant d’apporter des modifications, sauvegardez le fichier EAR que vous êtes sur le point de remplacer :

* Localisez `adobe-edcserver-jboss.ear` dans votre répertoire de déploiement :

  ```text
  [AEM installation directory]/deploy/adobe-edcserver-jboss.ear
  ```

* Copiez le fichier vers un emplacement de sauvegarde sécurisé en dehors du répertoire de déploiement.
* Vérifiez que la sauvegarde est terminée et accessible avant de procéder aux mises à jour.

Cette précaution vous permet de restaurer l’état d’origine en cas de problème lors du processus de mise à jour.

### Installation manuelle du correctif pour AEM Forms sur JEE 6.5 LTS SP2 (JBoss) {#manual-hotfix-installation-aem-forms-jee-65-lts-sp2-jboss}

1. Téléchargez `adobe-edcserver-jboss.ear` à partir du portail de distribution de logiciels [Adobe](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/hotfix/adobe-edcserver-jboss.ear).

1. Recherchez `adobe-edcserver-jboss.ear` dans votre répertoire de déploiement et remplacez-le par le fichier téléchargé :

   ```text
   [AEM installation directory]/deploy/adobe-edcserver-jboss.ear
   ```

1. Lancez le gestionnaire de configuration d’AEM Forms pour redéployer le fichier EAR mis à jour et appliquer entièrement le correctif.

1. Redémarrez le serveur d’applications et confirmez la réussite du déploiement à partir des journaux du serveur.

## Références {#references}

* [Bonnes pratiques de sécurité d’Adobe Experience Manager Forms](/help/forms/using/hardening-securing-aem-forms-environment.md)
