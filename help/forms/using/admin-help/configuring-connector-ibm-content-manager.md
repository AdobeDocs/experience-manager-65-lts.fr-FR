---
title: Configurer Connector for IBM Content Manager
description: Configurez Connector for IBM® Content Manager pour permettre la communication entre AEM Forms et IBM® Content Manager.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/connecting_to_a_content_management_system
products: SG_EXPERIENCEMANAGER/6.5/FORMS
solution: Experience Manager, Experience Manager Forms
role: User, Developer
feature: Adaptive Forms
hide: true
hidefromtoc: true
exl-id: 106f01a2-39fb-474b-8c58-5ab08666b918
source-git-commit: bc91f56d447d1f2c26c160f5c414fd0e6054f84c
workflow-type: tm+mt
source-wordcount: '285'
ht-degree: 100%

---

# Configurer Connector for IBM® Content Manager{#configuring-connector-for-ibm-content-manager}

>[!NOTE]
> 
> Vérifiez que l’utilisateur ou l’utilisatrice dispose de droits d’administration pour accéder à la console d’administration.

Connector for IBM® Content Manager permet la communication entre AEM Forms et IBM® Content Manager. Pour plus d’informations, voir Connectors for ECM, dans le [Guide de référence des services](https://help.adobe.com/fr_FR/livecycle/11.0/Services/index.html).

## Configurer la connexion IBM® Content Manager {#configure-the-ibm-content-manager-connection}

1. Dans la console d’administration, cliquez sur Services > Connector for IBM® Content Manager.
1. Dans le champ Nom du magasin de données, saisissez le nom du magasin de données IBM® Content Manager auquel vous connecter. Si la base de données est locale, saisissez son nom. S’il s’agit d’une base de données distante, indiquez son nom d’alias.
1. Dans la zone Nom d’utilisateur, saisissez l’ID de la personne qui se connectera au magasin de données IBM® Content Manager.
1. Dans le champ Mot de passe, saisissez le mot de passe de la personne.
1. (Facultatif) Dans le champ Chaîne de connexion de l’alias, saisissez des arguments de connexion supplémentaires. Ce champ n’est généralement pas complété. Pour plus d’informations, consultez votre documentation IBM®.
1. Cliquez sur Enregistrer.

## Validation des paramètres d’un service {#validation-of-service-settings}

Si vous saisissez un nom d’utilisateur ou un alias de magasin de données incorrect, vous obtenez les résultats suivants selon que le service Content Repository Connector for IBM Content Manager est en cours d’exécution ou non :

* Si le service est arrêté, aucune erreur n’apparaît lorsque vous enregistrez les informations de configuration du service. Cependant, lors du prochain démarrage du service, une exception est générée et le service ne démarre pas.
* Si le service est démarré, ce dernier tente de valider immédiatement les informations d’identification lorsque vous enregistrez les informations de configuration du service. Dans ce cas, une erreur se produit et les informations de configuration ne sont pas enregistrées.
