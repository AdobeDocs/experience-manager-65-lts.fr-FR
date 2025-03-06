---
title: Échec de la sauvegarde de la base de données lors de la mise à niveau vers 6.5.12.0 pour MySQL.
description: Lorsqu’un utilisateur effectue une mise à niveau vers Experience Manager 6.5.12.0 et clique sur « Mettre à niveau MySQL », le gestionnaire de configuration ne parvient pas à sauvegarder la base de données Experience Manager Forms précédente.
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms,AEM Forms on JEE
role: User, Developer
exl-id: afc09a9f-58ef-4292-a2f2-b62d3246c006
source-git-commit: c3e9029236734e22f5d266ac26b923eafbe0a459
workflow-type: tm+mt
source-wordcount: '101'
ht-degree: 39%

---

# Échec de la sauvegarde de la base de données lors de la mise à niveau vers la version 6.5.12.0 pour MySQL. {#issue}

Lorsque l’utilisateur effectue une mise à niveau vers Experience Manager 6.5.12.0 et clique sur « Mettre à niveau MySQL », le gestionnaire de configuration ne parvient pas à sauvegarder la base de données Experience Manager Forms précédente, le message d’erreur suivant apparaît :

`Failed to backup the previous Adobe Experience Manager Forms Database`


## Application {#applies-to}

* Experience Manager 6.5 Forms

## Solution {#solution}

Pour résoudre le problème, augmentez la taille max_packet_size de la base de données à 100 Mo ou selon les besoins dans le fichier my.ini situé à l’emplacement {AEM_HOME}/mysql.
