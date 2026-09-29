---
title: Démarrer et arrêter des services
description: Découvrez comment démarrer et arrêter des services associés aux modules AEM Forms et au serveur d’applications et à la base de données.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/managing_services
products: SG_EXPERIENCEMANAGER/6.5/FORMS
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
hide: true
removedfrom6.5.2025: 'yes'
exl-id: a4ff69d2-a429-49b9-ba48-9dd56ccdf23e
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
  - id: e8f6de9b-cf88-4405-8d10-15efa08c230e
    internal-label: Experience Manager Forms
feature_v2:
  - id: e72c079d-d036-46d5-b43d-29b276a174c2
    internal-label: Authoring and publishing content
subfeature_v2:
  - id: a26f372d-6d7c-452b-81df-594dd4365ae1
    internal-label: Adaptive Forms
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 2e690827bfa8f3d8227860de4efb802758ae0095
workflow-type: tm+mt
source-wordcount: '311'
ht-degree: 100%
---
# Démarrer et arrêter des services {#starting-and-stopping-services}

>[!NOTE]
> 
> Vérifiez que l’utilisateur ou l’utilisatrice dispose de droits d’administration pour accéder à la console d’administration.

Il existe deux types de services faisant partie d’AEM Forms :

* Services qui contrôlent le serveur d’applications et la base de données AEM Forms.
* Services qui contrôlent les modules AEM Forms.

## Démarrer ou arrêter des services associés aux modules AEM Forms {#start-or-stop-the-services-associated-with-aem-forms-modules}

Les modules AEM Forms (par exemple, Forms, Rights Management et Output) fonctionnent comme des services. Vous devrez parfois arrêter ou démarrer les services de ces modules AEM Forms. Par exemple, vous devez arrêter puis redémarrer un service AEM Forms après avoir procédé à une modification sur un paramètre de ce service.

>[!NOTE]
>
> Il est recommandé d’utiliser la commande « Ctrl+C » pour redémarrer le SDK. Le redémarrage du SDK AEM à l’aide de méthodes alternatives, par exemple l’arrêt des processus Java, peut entraîner des incohérences dans l’environnement de développement AEM.

1. Dans Console d’administration, cliquez sur **Services** > **Applications et services** > **Gestion des services**.
1. Dans la page Gestion des services, cochez la case en regard du service à arrêter ou à démarrer et cliquez sur Arrêter ou Démarrer.

## Démarrer ou arrêter des services pour le serveur d’applications et la base de données {#start-or-stop-services-for-the-application-server-and-database}

Une implémentation complète d’AEM Forms comprend des services de serveur d’applications et de base de données :

* *`[application server]`* pour AEM Forms
* *`[database]`* pour AEM Forms

Sous Windows, ces services sont accessibles dans **Outils d’administration** > **Panneau de services**. Par exemple, si vous avez installé AEM Forms sur JBoss à l’aide de la méthode clé en main, les services suivants sont disponibles :

* JBoss pour Adobe Experience Manager Forms
* MySQL pour Adobe Experience Manager Forms

Pour démarrer ou arrêter un service, sélectionnez-le dans la liste, puis cliquez sur le bouton approprié dans le panneau.

Sous UNIX® ou Linux, saisissez le texte suivant à partir d’une ligne de commande, dans laquelle *`[service name]`* correspond au nom du service à vérifier :

```java
     ps -A | grep [service name]
```
