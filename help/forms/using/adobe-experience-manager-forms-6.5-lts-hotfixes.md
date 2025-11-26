---
title: Correctifs Adobe Experience Manager Forms 6.5 LTS SP1
description: Fournit des informations sur la manière de télécharger et d’installer un correctif pour AEM Forms 6.5 LTS.
exl-id: 37287332-3c8d-4ddc-a77e-3c5ee332898b
solution: Experience Manager
feature: Release Information
role: User,Admin,Architect,Developer
source-git-commit: bb270a983d9d3f7d116a179886daf763e7e2341e
workflow-type: tm+mt
source-wordcount: '251'
ht-degree: 45%

---


# Correctifs LTS Adobe Experience Manager Forms 6.5{#aem-form-hotfix}

Cet article répertorie les correctifs critiques implémentés pour résoudre les problèmes connus, améliorer la stabilité du système et améliorer les performances globales d’AEM Forms 6.5 LTS.

>[!NOTE]
>
> Les correctifs sont conçus pour être cumulatifs, c’est-à-dire qu’ils englobent tous les correctifs précédents. Ainsi, lorsque vous appliquez le dernier correctif à une version, il résout non seulement le problème le plus récent, mais incorpore également tous les correctifs et améliorations antérieurs.

## Correctifs pour AEM Forms 6.5 LTS {#hotfix-for-aem-forms}

<table>
  <tbody>
  <tr>
    <td><strong>Date</strong></td>
    <td><strong>Lien de téléchargement des correctifs (lien de distribution logicielle AEM)</strong></td>
    <td><strong>Problèmes résolus</strong></td>
  </tr>
  <tr>
    <td>
      <strong>9 septembre 2025</strong><br>
    <td>
    <ul>
    <li>Windows- <a href="https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?pack[...]1-correctif-on-add-on/adobe-aemfd-win-pkg-6.1.176-RHF-002.zip">Correctif2 pour le pack de services 6.5 LTS d’AEM sous Windows</a></li>
    <li>Linux- <a href="https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?pack[...]correctif-sur-modulecomplémentaire/adobe-aemfd-linux-pkg-6.1.176-RHF-002.zip">Hotfix2 pour AEM Service Pack 6.5 LTS sous Linux</a></li>
     <li>OSX - <a href="https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?pack[...]1-hotfix-on-add-on/adobe-aemfd-osx-pkg-6.1.176-RHF-002.zip">correctif2 pour AEM Service Pack 6.5 LTS on OSX</a></li>
    <td>
    <ul>
    <li>Amélioration de la fiabilité de l’envoi des formulaires en résolvant un problème où les envois peuvent échouer lorsque la validation côté serveur (SSV) a été activée. Si vous rencontrez des problèmes, contactez [l’assistance Adobe Experience Manager Forms](https://business.adobe.com/in/support/main.html)
    </li>
    </ul>
    </td>    
  </tr>
    </ul>
    </td>    
  </tr>
  <tbody>
</table>

## Télécharger et installer un correctif OSGi {#download-install-hotfix}

Effectuez les étapes suivantes pour télécharger et installer le correctif :

1. Téléchargez le [correctif](#hotfix-for-adaptive-forms) à partir du lien Distribution logicielle.
1. Procédez à l’extraction du fichier d’archive Hotfix pour obtenir un package Experience Manager (.zip) et des fichiers de lot (.jar).
1. Chargez et installez le package (.zip) via le [gestionnaire de modules](https://experienceleague.adobe.com/fr/docs/experience-manager-65/content/sites/administering/contentmanagement/package-manager#accessing).
1. Ouvrez les lots Configuration Manager `https://server:host/system/console/bundles`, chargez et installez le lot (.jar). Le correctif est installé.
