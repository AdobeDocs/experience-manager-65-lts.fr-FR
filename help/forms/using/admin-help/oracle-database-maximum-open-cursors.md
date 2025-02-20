---
title: Nombre maximal de curseurs ouverts dans une base de données Oracle
description: Découvrez comment configurer une valeur maximale pour les curseurs ouverts dans Oracle.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/maintaining_the_aem_forms_database
products: SG_EXPERIENCEMANAGER/6.5/FORMS
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
source-git-commit: 29391c8e3042a8a04c64165663a228bb4886afb5
workflow-type: tm+mt
source-wordcount: '82'
ht-degree: 100%

---

# Nombre maximal de curseurs ouverts dans une base de données Oracle {#oracle-database-maximum-open-cursors-threshold}

Pour configurer une valeur maximale pour les curseurs ouverts dans Oracle, vous devrez peut-être ajuster cette valeur à un nombre approprié pour votre application. Il apparaît qu’avec une charge de taille moyenne, le nombre moyen de curseurs ouverts était de 2700. Il est recommandé de commencer par une limite supérieure fixée à 3000. Pour plus d’informations, rendez-vous sur [https://www.orafaq.com/node/758](https://www.orafaq.com/node/758).
