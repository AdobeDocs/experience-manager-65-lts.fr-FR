---
title: Définition des polices à incorporer
description: Découvrez comment spécifier les polices à incorporer dans un formulaire adaptatif. Vous pouvez spécifier les polices qui sont incorporées ou ne le sont jamais dans des formulaires générés par le service Forms.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_forms
products: SG_EXPERIENCEMANAGER/6.5/FORMS
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
hide: true
hidefromtoc: true
exl-id: c73dced8-7242-465c-85bc-9315a9a08605
source-git-commit: bc91f56d447d1f2c26c160f5c414fd0e6054f84c
workflow-type: tm+mt
source-wordcount: '282'
ht-degree: 100%

---

# Définition des polices à incorporer {#specifying-fonts-to-embed}

>[!NOTE]
> 
> Vérifiez que l’utilisateur ou l’utilisatrice dispose de droits d’administration pour accéder à la console d’administration.

Vous pouvez spécifier les polices qui sont toujours incorporées ou qui ne le sont jamais dans les formulaires générés par le service Forms. L’incorporation de polices augmente la taille de fichier des formulaires. Incorporez des polices inhabituelles que les utilisateurs et utilisatrices ont rarement sur leurs systèmes. N’incorporez pas les polices courantes généralement installées.

>[!NOTE]
>
>Si vous avez spécifié un fichier XCI personnalisé pour Forms, l’option d’incorporation de polices dans le fichier XCI remplace ces paramètres. (Voir [Configurer des emplacements pour Forms](/help/forms/using/admin-help/configuring-locations-forms.md#configuring-locations-for-forms).)

1. Dans la console d’administration, cliquez sur **[!UICONTROL Services > Forms]**.
1. Sous **[!UICONTROL Paramètres d’incorporation des polices]**, dans le champ **[!UICONTROL Toujours incorporer les polices]**, saisissez les noms des polices à incorporer aux formulaires (en les séparant par des virgules). Les polices que vous spécifiez ne sont incorporées dans le formulaire généré que si elles sont utilisées dans le formulaire. Ce paramètre est ignoré si l’option d’incorporation des polices a été activée dans le fichier XCI transmis au service, car dans ce cas, toutes les polices utilisées dans le PDF sont toujours incorporées.
1. Dans le champ **[!UICONTROL Ne jamais incorporer les polices]**, saisissez les noms des polices à ne pas incorporer avec les formulaires (en les séparant par des virgules). Les polices que vous spécifiez ne sont pas incorporées dans le PDF, même si elles sont utilisées dans le PDF généré. Ce paramètre est ignoré si l’option d’incorporation des polices a été désactivée dans le fichier XCI transmis au service, car dans ce cas, aucune des polices utilisées dans le PDF n’est incorporée.
1. Cliquez sur **[!UICONTROL Enregistrer]**.
