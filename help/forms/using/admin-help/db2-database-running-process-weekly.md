---
title: 'DB2&rég; base de données : exécution d’un processus hebdomadaire'
description: Découvrez comment vous pouvez améliorer la performance de votre base de données AEM Forms DB2®.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/maintaining_the_aem_forms_database
products: SG_EXPERIENCEMANAGER/6.5/FORMS
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
hide: true
hidefromtoc: true
exl-id: e8cf9e73-345c-4dea-8361-b678c1a3cd1b
source-git-commit: bc91f56d447d1f2c26c160f5c414fd0e6054f84c
workflow-type: tm+mt
source-wordcount: '148'
ht-degree: 95%

---

# Base de données DB2® : exécution d’un processus hebdomadaire{#db-database-running-a-process-weekly}

Si votre base de données DB2® AEM Forms commence à s’exécuter lentement, l’exécution hebdomadaire du processus suivant peut améliorer ses performances :

1. Démarrez DB2® Control Center :

   (Windows) Sélectionnez Démarrer > Programmes > IBM® DB2® > Outils d’administration générale > Centre de contrôle.

   (Linux® et UNIX®) Ouvrez une invite de commande et saisissez la commande `db2jcc`.

1. Dans l’arborescence d’objets du centre de contrôle DB2®, cliquez sur Toutes les bases de données.
1. Cliquez sur la base de données que vous avez créée pour AEM Forms, puis sur le dossier Tableaux.
1. Sélectionnez tous les tableaux de base de données dans le volet de contenu, cliquez dessus avec le bouton droit et sélectionnez Statistiques d’exécution.
1. Accédez à Statistics > Index Statistics.
1. Sélectionnez Collect Statistics For All Indexes, puis Collect Statistics For Indexes With Extended Detailed Statistics et cliquez sur OK.

Un message s’affiche une fois le processus terminé. Fermez le message.
