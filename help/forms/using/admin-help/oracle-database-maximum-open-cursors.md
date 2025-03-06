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
exl-id: 98663f16-6c05-4485-9bf2-a2de9d1975c8
source-git-commit: c3e9029236734e22f5d266ac26b923eafbe0a459
workflow-type: tm+mt
source-wordcount: '82'
ht-degree: 100%

---

# Nombre maximal de curseurs ouverts dans une base de données Oracle {#oracle-database-maximum-open-cursors-threshold}

Pour configurer une valeur maximale pour les curseurs ouverts dans Oracle, vous devrez peut-être ajuster cette valeur à un nombre approprié pour votre application. Il apparaît qu’avec une charge de taille moyenne, le nombre moyen de curseurs ouverts était de 2700. Il est recommandé de commencer par une limite supérieure fixée à 3000. Pour plus d’informations, rendez-vous sur [https://www.orafaq.com/node/758](https://www.orafaq.com/node/758).
