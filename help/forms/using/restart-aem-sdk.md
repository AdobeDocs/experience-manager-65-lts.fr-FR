---
title: Redémarrage du SDK AEM
description: Bonnes pratiques pour redémarrer le SDK AEM
role: Admin, Developer, User
feature: Adaptive Forms,AEM Forms on JEE,AEM Forms on OSGi
solution: Experience Manager, Experience Manager Forms
hide: true
hidefromtoc: true
exl-id: 68935045-89b1-4219-b111-88a4600200df
source-git-commit: bc91f56d447d1f2c26c160f5c414fd0e6054f84c
workflow-type: tm+mt
source-wordcount: '92'
ht-degree: 100%

---

# Redémarrage du SDK AEM

Si vous redémarrez le SDK AEM en arrêtant les processus Java™, cela peut entraîner des incohérences dans l’environnement de développement AEM et une erreur se produit comme suit :

`javax.jcr.RepositoryException: Applying repoinit operation failed despite retry; set loglevel to DEBUG to see all exceptions. Last exception message was: Failed to set ACL (javax.jcr.ValueFormatException: Invalid type: 0) AclLine ALLOW {principals=[forms-xfa-writers], privileges=[jcr:modifyProperties]} restrictions=[rep:glob=[*/jcr:content/*], rep:itemNames=[xfaForm], fd:condition=[xfaForm, 1]]`

![Restart-aem-sdk-error](/help/forms/using/assets/restart-sdk-error.png)

## Solution

Pour redémarrer le SDK AEM, accédez à la fenêtre de commande active et appuyez sur la commande `Ctrl + C` pour le redémarrer.

Il est recommandé d’utiliser la commande « Ctrl+C » pour redémarrer le SDK. Le redémarrage du SDK AEM à l’aide de méthodes alternatives, par exemple l’arrêt des processus Java™, peut entraîner des incohérences dans l’environnement de développement AEM.
