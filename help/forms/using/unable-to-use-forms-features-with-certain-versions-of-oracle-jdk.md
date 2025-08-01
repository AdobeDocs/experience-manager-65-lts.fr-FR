---
title: Impossible d’utiliser Experience Manager Forms avec certaines versions du JDK Oracle.
description: Impossible d’utiliser Experience Manager Forms avec certaines versions du JDK Oracle.
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
exl-id: 4aa45f02-ff89-4e40-a15d-e62c5879a87d
source-git-commit: cf2f70432ccf9ebc80847cf5ec6acfe630feb39f
workflow-type: tm+mt
source-wordcount: '160'
ht-degree: 100%

---

# Impossible d’utiliser Experience Manager Forms avec certaines versions du JDK Oracle. {#unable-to-use-forms-with-certain-versions-of-oracle-jdk}

Le problème s’applique aux versions suivantes :

* Experience Manager Forms 6.3
* Experience Manager Forms 6.4
* Formulaires avec Experience Manager 6.5

## Problème {#issue}

L’utilisateur ou l’utilisatrice rencontre l’exception suivante :
`Caused by: javax.xml.xpath.XPathExpressionException: javax.xml.transform.TransformerException: JAXP0801002: the compiler encountered an XPath expression containing '101' operators that exceeds the '100' limit set by 'FEATURE_SECURE_PROCESSING'.`

## Raison {#reason}

L’exception se produit lorsque vous exécutez Experience Manager Forms avec une version du JDK (Java Development Kit) Oracle supérieure ou égale aux versions suivantes :

* [JDK7u341](https://www.oracle.com/java/technologies/javase/7u341-relnotes.html)
* [JDK8u331](https://www.oracle.com/java/technologies/javase/8u331-relnotes.html)
* [JDK11u15](https://www.oracle.com/java/technologies/javase/11-0-15-relnotes.html)

La version ci-dessus et les versions ultérieures de Java incluent de nouvelles limites de traitement XML dans la JVM (Java Virtual Machine), ce qui entraîne l’échec de certaines opérations spécifiques à Forms.

## Solution {#workaround}

1. Arrêtez votre serveur Experience Manager Forms.
1. Configurez l’argument JVM suivant pour votre serveur d’applications :

   `-Djdk.xml.xpathExprGrpLimit=100`
   `-Djdk.xml.xpathExprOpLimit=10000`
   `-Djdk.xml.xpathTotalOpLimit=10000`

   Il définit la propriété système dans la JVM sur une valeur raisonnablement élevée afin que la limite par défaut ne soit pas atteinte.

1. Démarrez votre serveur Experience Manager Forms.
