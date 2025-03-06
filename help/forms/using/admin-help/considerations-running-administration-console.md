---
title: Remarques concernant l’exécution de la console d’administration
description: Ce document répertorie quelques points à prendre en compte lors de l’exécution de la console d’administration.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/maintaining_the_application_server
products: SG_EXPERIENCEMANAGER/6.5/FORMS
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
exl-id: bdd884c4-ae12-4827-8251-01033cbc0185
source-git-commit: c3e9029236734e22f5d266ac26b923eafbe0a459
workflow-type: tm+mt
source-wordcount: '147'
ht-degree: 100%

---

# Remarques concernant l’exécution de la console d’administration {#considerations-when-running-administrationconsole}

>[!NOTE]
> 
> Vérifiez que l’utilisateur ou l’utilisatrice dispose de droits d’administration pour accéder à la console d’administration.

Il existe plusieurs éléments à prendre en compte lors de l’exécution de la console d’administration :

* Si vous accédez à la console d’administration en utilisant l’URL `https://[hostname]:'port'/adminui`, le nom d’hôte spécifié ne peut pas contenir de caractères de soulignement. Dans le cas contraire, les liens vers certaines zones d’Administration Console risquent de ne pas fonctionner correctement.
* Si vous exécutez une console d’administration dans l’Explorateur de fichiers sur un système d’exploitation japonais, il se peut que vous rencontriez les problèmes suivants :

   * Un clic sur un lien vous renvoie à la page de connexion au lieu du lien prévu.
   * Un clic sur un lien entraîne l’affichage d’une erreur d’autorisation.

  La bonne pratique consiste à exécuter la console d’administration depuis un autre navigateur, tel que Mozilla Firefox, pour éviter que des liens n’échouent.

* N’utilisez pas de barres obliques inverses (\) lorsque vous exécutez des recherches dans la console d’administration.
