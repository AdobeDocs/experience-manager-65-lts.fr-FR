---
title: Correctifs LTS Adobe Experience Manager Forms 6.5
description: Fournit des informations sur la manière de télécharger et d’installer un correctif pour AEM Forms 6.5 LTS. Pour AEM 6.5 (non-LTS), consultez l’article sur les correctifs Forms d’AEM 6.5 .
solution: Experience Manager
feature: Release Information
role: User,Admin,Developer
exl-id: e485100f-3e16-4fd4-a8ce-af771d765dd1
source-git-commit: 989d83cfc56f7a7d4e2aea5a7ac1ca444d505859
workflow-type: tm+mt
source-wordcount: '1137'
ht-degree: 11%
---
# Correctifs LTS Adobe Experience Manager Forms 6.5{#aem-form-hotfix}

Cet article répertorie les correctifs critiques implémentés pour résoudre les problèmes connus, améliorer la stabilité du système et améliorer les performances globales d’AEM Forms 6.5 LTS.


Cet article s’applique à AEM Forms 6.5 LTS. Pour les déploiements d’AEM 6.5 (non-LTS), consultez [Correctifs Adobe Experience Manager Forms](https://experienceleague.adobe.com/fr/docs/experience-manager-65/content/release-notes/aem-forms-hotfix).

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
      <strong>21 septembre 2026</strong><br>
      <em>S’applique à :</em> les déploiements JEE du Service Pack 2 d’AEM Forms 6.5 LTS (JBoss, WebLogic, WebSphere)<br>
    </td>
    <td>
    <p><strong>Pour installer ce correctif, procédez comme suit :</strong></p>
    <p><strong>Étape 1 : installation du correctif</strong></p>
    <ul>
    <strong>JBoss:</strong>
    <li>Windows : <a href="https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/hotfix/aem-6-5-lts-sp2-hotfix/jboss/adobe-aem-forms-jee-hotfix-6.5.LTS.2-win-jboss.zip">correctif pour AEM Forms 6.5 LTS SP2 sous Windows pour le serveur JBoss JEE</a></li>
    <li>Linux : <a href="https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/hotfix/aem-6-5-lts-sp2-hotfix/jboss/adobe-aem-forms-jee-hotfix-6.5.LTS.2-linux-jboss.tar.gz">correctif pour AEM Forms 6.5 LTS SP2 sous Linux pour le serveur JBoss JEE</a></li>
    <strong>WebLogic:</strong>
    <li>Windows : <a href="https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/hotfix/aem-6-5-lts-sp2-hotfix/weblogic/adobe-aem-forms-jee-hotfix-6.5.LTS.2-win-weblogic.zip">correctif pour AEM Forms 6.5 LTS SP2 sous Windows pour le serveur Weblogic JEE</a></li>
    <li>Linux : <a href="https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/hotfix/aem-6-5-lts-sp2-hotfix/weblogic/adobe-aem-forms-jee-hotfix-6.5.LTS.2-linux-weblogic.tar.gz">correctif pour AEM Forms 6.5 LTS SP2 sous Linux pour le serveur Weblogic JEE</a></li>
    <strong>WebSphere:</strong>
    <li>Windows : <a href="https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/hotfix/aem-6-5-lts-sp2-hotfix/websphere/adobe-aem-forms-jee-hotfix-6.5.LTS.2-win-websphere.zip">correctif pour AEM Forms 6.5 LTS SP2 sous Windows pour le serveur WebSphere JEE</a></li>
    <li>Linux : <a href="https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/hotfix/aem-6-5-lts-sp2-hotfix/websphere/adobe-aem-forms-jee-hotfix-6.5.LTS.2-linux-websphere.tar.gz">correctif pour AEM Forms 6.5 LTS SP2 sous Linux pour le serveur WebSphere JEE</a></li>
    </ul>
    <p>Installez le correctif en suivant la procédure d’installation standard d’AEM Forms sur JEE. <!-- TODO: link to the 6.5 LTS JEE patch installation instructions once available --></p>
    <p><strong>Étape 2 : installer le lot de correctifs de vulnérabilité</strong></p>
    <ul>
    <li><a href="https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/hotfix/aem-6-5-lts-sp2-hotfix/SP2LTSBundles_VULN-36670.zip">Lot de correctifs de vulnérabilité pour AEM Forms 6.5 LTS SP2</a></li>
    </ul>
    <ol>
    <li>Ouvrez la console OSGi sur <code>http://&lt;host&gt;:&lt;port&gt;/lc/system/console/bundles</code>.</li>
    <li>Cliquez sur <strong> Installer/Mettre à jour </strong>.</li>
    <li>Cochez les cases <strong>Démarrer le bundle</strong> et <strong>Actualiser les packages</strong>.</li>
    <li>Cliquez sur <strong>Choisir un fichier</strong>, puis chargez le lot téléchargé.</li>
    <li>Patientez jusqu’à ce que le journal se dépose et que le lot s’affiche comme <strong>Actif</strong>.</li>
    </ol>
    <p><strong>Étape 3 : mettre à jour le programme d’installation d’AEM Forms Workbench</strong></p>
    <p>Vous devez effectuer une mise à jour vers le dernier programme d’installation d’AEM Forms Workbench. Téléchargez-le à partir du <a href="https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/fd/workbench/6-5-0-20260902-1-45/Workbench_DVD.zip">programme d’installation d’AEM Forms Workbench</a>.</p>
    <p><strong>Étape 4 : mettre à jour les fichiers de bibliothèque cliente (développeurs)</strong></p>
    <p>Ce correctif comprend une mise à jour majeure de la <code>adobe-livecycle-client.jar</code> de bibliothèque cliente SDK (voir <a href="/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files">Inclure des fichiers de bibliothèque Java AEM Forms</a>). Si votre projet utilise ce fichier JAR, mettez à jour <code>adobe-livecycle-client.jar</code> dans le chemin d’accès aux classes de votre projet après avoir installé le correctif. La dernière version est disponible à l’adresse <code>&lt;AEM_Forms_Installation_dir&gt;\sdk\client-libs\common\adobe-livecycle-client.jar</code>.</p>
    <p>Le correctif est cumulatif. Vous pouvez donc l’appliquer au pack de services 2 LTS d’AEM Forms 6.5 ou à un pack de services antérieur sans installer le pack de services 2 au préalable.</p>
    </td>
    <td>
    <ul>
    <li><b>FORMS-26818</b> Après la mise à jour d’Apache Shiro vers la version 2.1.0, AEM Forms sur JEE ne parvient pas à amorcer avec un <code>NoClassDefFoundError</code> pour le gestionnaire de sécurité Shiro. Ce correctif restaure le démarrage réussi.</li>
    <li><b>FORMS-26819</b> Échec d’AEM Forms on JEE avec une erreur « aucune classe trouvée » pour <code>org.owasp.esapi.reference.JavaLogFactory</code>. Ce correctif résout la classe manquante.</li>
    <li><b>FORMS-26584, FORMS-26589</b> Après la mise à niveau vers AEM Forms 6.5 LTS, les points d’entrée TaskManager sont supprimés. Ce correctif restaure les points d’entrée TaskManager.</li>
    <li><b>FORMS-26569</b> Sur JEE, l’étape Configuration Manager MergeEars échoue avec une erreur de déclaration DOCTYPE (<code>ALC-LCM-010-200</code>) en raison du créateur XML sécurisé. Ce correctif permet de terminer l’étape MergeEars .</li>
    <li><b>Les journaux au niveau de l'application FORMS-25063</b> sont manquants sur les déploiements d'IBM WebSphere Liberty. Ce correctif restaure la journalisation au niveau de l’application.</li>
    <li><b>FORMS-24892</b> Sur JBoss, l’e-mail échoue avec « IMAPProvider not a subtype ». Ce correctif restaure la fonctionnalité de messagerie sur JBoss.</li>
    <li><b>FORMS-24692</b> Sur WebSphere Liberty Profile (WLP), l’e-mail échoue avec « Impossible de convertir le socket en TLS ». Ce correctif restaure les e-mails via TLS sur WLP.</li>
    <li><b>FORMS-26688</b> Met à jour la bibliothèque Gibson vers la version 6.0.29665850.</li>
    <li><b>Amélioration de la validation de l’assertion SAML des rétroportages FORMS-25222</b>.</li>
    <li><b>FORMS-26733, FORMS-26734</b> Mise à jour d’Apache Log4j vers la version 2.25.5.</li>
    <li>Ce correctif comprend également des correctifs de sécurité.</li>
    </ul>
    <p><strong>Build:</strong> AEMForms-6.6.0-0008</p>
    </td>
  </tr>
  <tr>
    <td>
      <strong>9 septembre 2025</strong><br>
    <td>
    <ul>
    <li>Windows- <a href="https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?pack[...]1-correctif-on-add-on/adobe-aemfd-win-pkg-6.1.176-RHF-002.zip">Correctif2 pour le pack de services 6.5 LTS d’AEM sous Windows</a></li>
    <li>Linux- <a href="https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?pack[...]correctif-sur-modulecomplémentaire/adobe-aemfd-linux-pkg-6.1.176-RHF-002.zip">Hotfix2 pour AEM Service Pack 6.5 LTS sous Linux</a></li>
     <li>MacOS - <a href="https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?pack[...]1-hotfix-on-add-on/adobe-aemfd-osx-pkg-6.1.176-RHF-002.zip">correctif2 pour AEM Service Pack 6.5 LTS sur MacOS</a></li>
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
1. Procédez à l’extraction du fichier d’archive Hotfix pour obtenir un package Experience Manager (.zip) et des fichiers de bundle (.jar).
1. Chargez et installez le package (.zip) via le [gestionnaire de modules](https://experienceleague.adobe.com/fr/docs/experience-manager-65/content/sites/administering/contentmanagement/package-manager#accessing).
1. Ouvrez les bundles Configuration Manager `https://server:host/system/console/bundles`, chargez et installez le bundle (.jar). Le correctif est installé.
