---
title: Fichiers journaux
description: Les événements, comme les erreurs d’exécution ou de démarrage, sont enregistrés dans les fichiers journaux du serveur d’applications, que vous pouvez ouvrir à l’aide d’un éditeur de texte.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/maintaining_aem_forms
products: SG_EXPERIENCEMANAGER/6.5/FORMS
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
exl-id: ff4dce07-725e-4750-9e95-4261b50580bd
source-git-commit: c3e9029236734e22f5d266ac26b923eafbe0a459
workflow-type: tm+mt
source-wordcount: '115'
ht-degree: 100%

---

# Fichiers journaux {#log-files}

Les événements tels que les erreurs d’exécution ou de démarrage sont enregistrés dans les fichiers journaux du serveur d’applications. Si vous rencontrez des problèmes lors du déploiement sur le serveur d’applications, vous pouvez utiliser les fichiers journaux pour vous aider à identifier le problème. Vous pouvez ouvrir les fichiers journaux à l’aide de n’importe quel éditeur de texte.

(JBoss) Les fichiers journaux suivants se trouvent dans le répertoire `[appserver root]/server/'server'/log` :

* boot.log
* server.log.*[aaaa-mm-jj]*
* server.log

(WebLogic) Les fichiers journaux du domaine sont dans le répertoire `[appserverdomain]` et ceux du serveur se trouvent dans le répertoire `[appserverdomain]/servers/[appserver name]/logs` :

* `access.log`
* `[appserver name].log`
* `[appserver name].out.[incremental number]`

(WebSphere) Les fichiers journaux suivants se trouvent dans le répertoire `[appserver root]/profiles/default/logs/[appserver name]` :

* SystemErr.log
* SystemOut.log
* StartServer.log
