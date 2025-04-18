---
title: Élaborer un plan de tests
description: Les cas de test individuels sont amalgamés dans votre plan de test.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: testing
content-type: reference
docset: aem65
solution: Experience Manager, Experience Manager Sites
feature: Developing
role: Developer
exl-id: b2dfc8fb-7bc4-4b5e-8c8f-1463fdc18e50
source-git-commit: c3e9029236734e22f5d266ac26b923eafbe0a459
workflow-type: tm+mt
source-wordcount: '193'
ht-degree: 100%

---

# Élaborer un plan de tests{#compiling-your-test-plan}

Les cas de test individuels sont ensuite amalgamés dans votre plan de test, qui définit également :

**Priorités**

Certains tests auront plus d’importance que d’autres. Il est donc conseillé d’indiquer leur priorité.

Par exemple, certains tests peuvent affecter une décision Go/No-Go et doivent donc être confirmés à chaque version intermédiaire testée.

**Itérations**

Si votre projet utilise une forme d’itération de développement (impliquant la mise à disposition de plusieurs versions), une indication des résultats pour chaque itération peut se révéler utile ou nécessaire. Cela peut être utilisé pour indiquer les éléments suivants :

* Les tests qui seront couverts dans telle ou telle itération.
* Les résultats vus pour les tests répétés dans diverses itérations.
* Que les tests de priorité et les tests sur les fonctionnalités de base sont répétés à intervalles réguliers.

**Testeur**

À un moment donné, vous pouvez affecter soit l’équipe de test appropriée, soit une personne spécifique au test (en fonction des disponibilités et/ou de l’expérience).

**Résumé ou vue d’ensemble**

Afin de créer des rapports, vous souhaitez fournir une vue d’ensemble des résultats de test :

* Pourcentage de tests déjà couverts.
* Pourcentage de réussite/échec.
* Chiffres spécifiques relatifs aux tests de priorité.
