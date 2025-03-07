---
title: Bases de la gestion des certificats et des informations d’identification
description: Découvrez les notions de base de la gestion des certificats et des informations d’identification.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/managing_certificates_and_credentials
products: SG_EXPERIENCEMANAGER/6.5/FORMS
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
hide: true
hidefromtoc: true
exl-id: 8aeacdb7-68a7-476f-a725-f9ad7406cc9c
source-git-commit: bc91f56d447d1f2c26c160f5c414fd0e6054f84c
workflow-type: tm+mt
source-wordcount: '301'
ht-degree: 94%

---

# Bases de la gestion des certificats et des informations d’identification {#basics-of-managing-certificates-and-credentials}

Les *informations d’identification* contiennent les informations de clé privée dont vous avez besoin pour signer ou identifier des documents. Un *certificat* correspond aux informations de clé publique que vous configurez pour l’approbation. AEM Forms utilise des certificats et des informations d’identification à plusieurs fins :

* Les extensions d’Acrobat Reader DC utilisent des informations d’identification pour activer les droits Adobe Reader des documents PDF. (Voir [Configuration des informations d’identification à utiliser avec les extensions Acrobat Reader DC](/help/forms/using/admin-help/configuring-credentials-acrobat-reader-dc.md#configuring-credentials-for-use-with-acrobat-reader-dc-extensions).)
* Vous pouvez configurer Rights Management pour afficher les informations d’identification à utiliser dans Acrobat uniquement auprès d’émetteurs approuvés. (Voir [Configurer les paramètres d’affichage de Rights Management](/help/forms/using/admin-help/configuring-client-server-options.md#configure-document-security-display-settings).) Le nom commun (NC) doit être présent dans le certificat.
* Le service Signature accède aux certificats et aux informations d’identification. Pour plus de détails sur le service Signature, voir [Référence des services](https://www.adobe.com/go/learn_aemforms_services_65_fr).

**Génération d’une paire de clés**

AEM Forms utilise son Trust Store pour stocker et gérer les certificats, les informations d’identification et les listes de révocation de certificats (CRL). De plus, vous pouvez utiliser un périphérique HSM (Hardware Security Module) indépendant pour stocker les clés privées.

AEM Forms ne propose aucune option pour générer une paire de clés. Cependant, vous pouvez la générer à l’aide d’outils, tels que Java keytool, et l’importer dans le Trust Store d’AEM Forms. Pour plus d’informations sur Java keytool, consultez les articles suivants :

[https://docs.oracle.com/javase/tutorial/security/toolsign/step3.html](https://docs.oracle.com/javase/tutorial/security/toolsign/step3.html)

[https://docs.oracle.com/cd/E19798-01/821-1841/gjrgy/index.html](https://docs.oracle.com/cd/E19798-01/821-1841/gjrgy/index.html)

[https://helpcenter.gsx.com/hc/en-us/articles/115015960428-How-to-Generate-a-Self-Signed-Certificate-and-Private-Key-using-OpenSSL](https://helpcenter.gsx.com/hc/fr-fr/articles/115015960428-How-to-Generate-a-Self-Signed-Certificate-and-Private-Key-using-OpenSSL)

Les types de signature suivants sont pris en charge et peuvent être importés dans AEM Forms :

* Signature XML
* XMLTimeStampToken
* Jeton d’horodatage RFC 3161
* PKCS#7
* PKCS#1
* Signatures DSA

**Gestion des clés perdues ou compromises**

Si vous pensez que votre clé est perdue ou a été compromise, prenez les mesures suivantes :

1. Informez l’autorité de certification afin qu’elle ajoute la clé compromise à la liste de révocation des certificats pour révoquer la clé.
1. Obtenez une nouvelle clé et ses certificats auprès de l’autorité de certification.
1. Signez à nouveau les documents signés avec la clé compromise à l’aide de la nouvelle clé.
