---
title: Configurer le message du jour
description: Le message du jour vous permet de définir un message à afficher sur la page de bienvenue de l’interface utilisateur de Workspace.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_workspace
products: SG_EXPERIENCEMANAGER/6.5/FORMS
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
hide: true
removedfrom6.5.2025: 'yes'
exl-id: 9581155d-5346-4346-b483-ecb0c51b53e3
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
source-wordcount: '186'
ht-degree: 100%
---
# Configurer le message du jour {#setting-the-message-of-the-day}

>[!NOTE]
> 
> Vérifiez que l’utilisateur ou l’utilisatrice dispose de droits d’administration pour accéder à la console d’administration.

Vous pouvez définir un message à afficher sur la page de bienvenue de l’interface utilisateur de Workspace.

Si nécessaire, vous pouvez utiliser les balises HTML prises en charge par Adobe Flash® Player pour formater l’apparence du texte :

* &lt;a> Balise d’ancrage
* &lt;b> Balise gras
* &lt;br> Balise de saut
* &lt;font> Balise de police
* &lt;img> Balise d’image
* &lt;i> Balise italique
* &lt;li> Balise d’élément de liste
* &lt;p> Balise de paragraphe
* &lt;span> Balise d’étendue
* &lt;textformat> Balise de format de texte
* &lt;u> Balise de soulignement

Pour plus d’informations sur les balises prises en charge, voir la définition de la propriété `htmlText` de la classe TextField dans le document [Flex Language Reference](https://flex.apache.org/).

## Définir le message du jour {#set-the-message-of-the-day}

1. Dans la console d’administration, cliquez sur Services > Workspace > Message du jour.
1. Dans la zone Message du jour, indiquez le texte à afficher sur l’écran de bienvenue.
1. Cliquez sur Enregistrer.

>[!NOTE]
>
>Flex Workspace est obsolète pour la version d’AEM Forms.
