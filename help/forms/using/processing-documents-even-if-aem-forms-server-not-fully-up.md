---
title: Le serveur AEM Forms commence à traiter les documents avant même que tous les services ne soient opérationnels et en cours d’exécution.
description: Le serveur AEM Forms commence à traiter les documents avant même que tous les services ne soient opérationnels et en cours d’exécution sur le serveur JEE et le serveur OSGi.
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
hide: true
hidefromtoc: true
exl-id: 22dd8daa-b8c6-4e7d-bca3-3958a79fb4b5
source-git-commit: bc91f56d447d1f2c26c160f5c414fd0e6054f84c
workflow-type: tm+mt
source-wordcount: '111'
ht-degree: 99%

---

# Le serveur AEM Forms commence à traiter les documents avant même que tous les services ne soient opérationnels et en cours d’exécution.{#aem-forms-server-start-processing-documents-even-if-it-is-not-fully-up}

## Problème {#issue}

<!--When user restarts AEM Forms server, the current calling processes or services still continue such as rendering PDF documents and more. It causes the restart of the AEM Forms server to not startup correctly.-->

Avant que le serveur AEM Forms ne soit pleinement opérationnel et que toutes les applications ne soient opérationnelles et en cours d’exécution, le serveur AEM Forms commence à traiter les documents.


## Application {#applies-to}

La solution s’applique au serveur AEM Forms on JEE et au serveur AEM Forms on OSGi.

## Solution {#solution}

Pour résoudre le problème, ajoutez un argument `Dcom.adobe.livecycle.dsc.deferServiceStart=true` au [fichier de commandes](https://experienceleague.adobe.com/docs/experience-manager-65-lts/deploying/deploying/command-line-start-and-stop.html#windows-platform-start-bat-script-example) au démarrage du serveur.
