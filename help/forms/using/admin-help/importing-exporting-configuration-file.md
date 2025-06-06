---
title: Import et export du fichier de configuration
description: Découvrez comment importer et exporter le fichier de configuration pour modifier les préférences du serveur ou configurer une autre instance de produit AEM Forms.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_user_management
products: SG_EXPERIENCEMANAGER/6.5/FORMS
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
hide: true
hidefromtoc: true
exl-id: 92fdcee3-2007-4bbc-be4b-426d65b8dbc1
source-git-commit: bc91f56d447d1f2c26c160f5c414fd0e6054f84c
workflow-type: tm+mt
source-wordcount: '264'
ht-degree: 100%

---

# Import et export du fichier de configuration {#importing-and-exporting-the-configuration-file}

>[!NOTE]
> 
> Vérifiez que l’utilisateur ou l’utilisatrice dispose de droits d’administration pour accéder à la console d’administration.

La page Configuration manuelle permet de télécharger une copie des paramètres de configuration au format XML. Les paramètres de ce fichier contrôlent toutes les préférences du serveur. Vous pouvez ensuite modifier le fichier et le charger à nouveau sur le serveur. Vous pouvez également utiliser ce fichier pour configurer une autre instance de produit AEM Forms.

Pour éviter tout risque de sécurité, la valeur du mot de passe de liaison du serveur d’annuaire n’est pas incluse dans un fichier de configuration exporté. Mettez à jour le mot de passe dans le fichier XML avant d’importer le fichier dans un nouveau système.

>[!NOTE]
>
>L’importation du fichier de configuration reconfigure AEM Forms en fonction des informations contenues dans le fichier. Seule une personnes chargée de l’administration système ou qui donne des conseils en services professionnels et qui connaît bien le produit AEM Forms et le code XML peut envisager de modifier le fichier de configuration. Il peut être nécessaire de modifier le fichier de configuration, par exemple, pour reconfigurer un paramètre corrompu.

**Exportation des informations de configuration**

1. Dans la console d’administration, cliquez sur Paramètres > User Management > Configuration > Importer et exporter des fichiers de configuration.
1. Cliquez sur Exporter. Si vous utilisez Microsoft Internet Explorer, vous devez spécifier l’emplacement d’enregistrement du fichier. Si vous utilisez Firefox, le fichier est enregistré sur votre bureau.

**Importation des informations de configuration**

1. Dans la console d’administration, cliquez sur Paramètres > User Management > Configuration > Importer et exporter des fichiers de configuration.
1. Cliquez sur Parcourir pour trouver le fichier de configuration, sur Importer, puis sur OK.
