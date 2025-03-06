---
title: Configurer les paramètres de verrouillage des comptes
description: Utilisez l’option Activer le verrouillage de compte pour verrouiller des comptes utilisateur après un nombre spécifié d’échecs d’authentification consécutifs.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/setting_up_and_managing_domains
products: SG_EXPERIENCEMANAGER/6.5/FORMS
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
exl-id: e78860dc-9375-465c-b1fa-2a4827ca8dce
source-git-commit: c3e9029236734e22f5d266ac26b923eafbe0a459
workflow-type: tm+mt
source-wordcount: '208'
ht-degree: 100%

---

# Configurer les paramètres de verrouillage des comptes {#configure-account-locking-settings}


>[!NOTE]
> 
> Vérifiez que l’utilisateur ou l’utilisatrice dispose de droits d’administration pour accéder à la console d’administration.

Lorsque vous ajoutez un domaine, spécifiez s’il convient d’activer le verrouillage des comptes. Si l’option Activer le verrouillage de compte est activée, les comptes d’utilisateurs sont verrouillés après un certain nombre d’échecs d’authentification consécutifs. Après une durée définie, l’utilisateur ou l’utilisatrice peut à nouveau tenter de s’authentifier. Cette fonctionnalité évite que les utilisateurs et les utilisatrices ne tentent plusieurs combinaisons d’informations d’identification pour accéder au système.

Utilisez les paramètres de la page Gestion des domaines pour spécifier le nombre maximum d’échecs d’authentification et la durée de verrouillage des comptes. Ces paramètres s’appliquent à tous les domaines dans lesquels le verrouillage des comptes est activé.

1. Dans la console dʼadministration, cliquez sur **[!UICONTROL Paramètres > Gestion des utilisateurs > Gestion des domaines]**.
1. Dans la zone Échecs d’authentification consécutifs maximum, saisissez le nombre de tentatives consécutives de connexion d’un utilisateur ou d’une utilisatrice avant que son compte ne soit verrouillé. La valeur par défaut est 20.
1. Dans la zone Déverrouiller le compte après (minutes), indiquez la durée de verrouillage du compte utilisateur en minutes. À l’issue de ce délai, l’utilisateur ou l’utilisatrice peut tenter de se reconnecter. La valeur par défaut est 30.
1. Cliquez sur **[!UICONTROL Enregistrer]**.
