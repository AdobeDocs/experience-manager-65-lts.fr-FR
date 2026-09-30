---
title: Définir les polices à incorporer
description: Découvrez comment spécifier les polices à incorporer dans un formulaire adaptatif. Vous pouvez spécifier les polices qui sont incorporées ou ne le sont jamais dans des formulaires générés par le service Forms.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_output
products: SG_EXPERIENCEMANAGER/6.5/FORMS
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
hide: true
removedfrom6.5.2025: 'yes'
exl-id: 374f9425-b596-4481-8fd0-6df07c521a19
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
source-wordcount: '283'
ht-degree: 100%
---
# Définir les polices à incorporer{#specify-fonts-to-embed}

>[!NOTE]
> 
> Vérifiez que l’utilisateur ou l’utilisatrice dispose de droits d’administration pour accéder à la console d’administration.

Vous pouvez spécifier les polices qui sont toujours ou jamais incorporées avec les formulaires utilisés par le service Output. L’incorporation de polices augmente la taille de fichier des formulaires. Incorporez les polices inhabituelles dont les utilisateurs et les utilisatrices disposent rarement sur leurs systèmes mais n’incorporez pas les polices courantes qui sont généralement installées.

>[!NOTE]
>
>Si vous avez spécifié un fichier XCI personnalisé pour Output, l’option d’incorporation de polices dans le fichier XCI remplace ces paramètres. (Voir [Définir les emplacements de fichiers pour Output](/help/forms/using/admin-help/specify-file-locations-output.md#specify-file-locations-for-output)).

1. Dans Administration Console, cliquez sur Services > Output.
1. Sous Paramètres d’incorporation des polices, dans le champ Toujours incorporer les polices, saisissez les noms des polices à incorporer aux formulaires (en les séparant par des virgules). Les polices que vous spécifiez ne sont incorporées dans le formulaire généré que si elles sont utilisées dans le formulaire. Ce paramètre est ignoré si l’option d’incorporation des polices a été activée dans le fichier XCI transmis au service. Dans ce cas, toutes les polices utilisées dans le PDF sont toujours incorporées.
1. Dans le champ Ne jamais incorporer les polices, saisissez les noms des polices à ne pas incorporer avec les formulaires (en les séparant par des virgules). Les polices que vous spécifiez ne sont pas incorporées dans le PDF, même si elles sont utilisées dans le PDF généré. Ce paramètre est ignoré si l’option d’incorporation des polices a été désactivée dans le fichier XCI transmis au service. Dans ce cas, aucune des polices utilisées dans le PDF n’est incorporée.
1. Cliquez sur Enregistrer.
