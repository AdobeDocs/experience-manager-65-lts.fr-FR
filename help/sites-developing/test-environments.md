---
title: Quels environnements de test sont nécessaires ?
description: Plusieurs environnements doivent être pris en compte dans le cadre du test.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: testing
content-type: reference
solution: Experience Manager, Experience Manager Sites
feature: Developing
role: Developer
exl-id: f74fbf2b-62bb-4fac-9ecb-5ace90ba0275
source-git-commit: c3e9029236734e22f5d266ac26b923eafbe0a459
workflow-type: tm+mt
source-wordcount: '169'
ht-degree: 100%

---

# Quels environnements de test sont nécessaires ?{#which-test-environments-will-be-needed}

Pour définir les configurations à tester, tenez compte des points suivants :

**Développement** - Pour les tests unitaires, et pour certains tests d’intégration.

**Tests** - Pour la plupart des tests.

**En direct** - Pour les tests finaux de performance et de contrainte. Également pour les tests d’acceptation avec le client.

Déterminez les instances dont vous avez besoin et où (généralement au moins une de chacune pour tous les niveaux de test) :

**Auteur** - Cette instance permet aux auteurs de saisir le contenu et de le publier.

**Publication** - Cette instance affiche le site web sous sa forme publiée pour que les visiteurs puissent y accéder.

Testé avec Dispatcher.

Enfin, le matériel doit être pris en compte : tous les tests de performance doivent être effectués sur un système aussi proche que possible de la configuration de l’environnement actif final. Pour cette raison, il est également recommandé de diviser le lancement du projet en :

**Prélancement** - Disponibilité réduite ; ce qui laisse du temps pour les tests de performance, le réglage et l’optimisation dans des conditions réalistes au sein de l’environnement de production.

**Lancement complet** - Disponibilité complète.
