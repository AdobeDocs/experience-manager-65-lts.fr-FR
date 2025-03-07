---
title: Configuration des délais d’expiration à utiliser avec Extensions d’Acrobat Reader DC
description: Découvrez comment définir des délais d’expiration à utiliser avec les extensions Acrobat Reader DC.
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
hide: true
hidefromtoc: true
exl-id: c2f96686-15e3-4d92-acfe-f971c5849de4
source-git-commit: bc91f56d447d1f2c26c160f5c414fd0e6054f84c
workflow-type: tm+mt
source-wordcount: '189'
ht-degree: 100%

---

# Configuration des délais d’expiration à utiliser avec Extensions d’Acrobat Reader DC  {#setting-timeout-values-for-use-with-acrobat-reader-dc-extensions}

>[!NOTE]
> 
> Vérifiez que l’utilisateur ou l’utilisatrice dispose de droits d’administration pour accéder à la console d’administration.

Lorsque vous travaillez sur de nombreux fichiers PDF dans Extensions Acrobat Reader DC, configurez comme suit les valeurs de délai d’expiration suivantes pour éviter l’expiration et l’échec des travaux :

**Délai avant suppression du document**

Cette valeur peut être définie dans la console d’administration. Cliquez sur Paramètres > Paramètres de Core System > Configurations, puis indiquez une valeur dans le champ Délai par défaut avant suppression du document.

**Délai de gestion des utilisateurs dans AEM Forms :** cette valeur peut être définie en modifiant le fichier config.xml. Dans la console d’administration, cliquez sur Paramètres > User Management > Configuration > Importer et exporter des fichiers de configuration, puis sur Exporter. Ouvrez le fichier config.xml exporté, puis modifiez les lignes ci-après de la façon suivante :

&lt;entry key=&quot;assertionValidityInMinutes&quot; value=&quot;600&quot;/>

&lt;entry key=&quot;SessionTimeout&quot; value=&quot;600&quot;/>

Enregistrez le fichier config.xml, puis réimportez-le dans la console d’administration.

**Délai d’expiration de session du serveur d’applications :** cette valeur peut être définie sur le serveur d’applications. Pour plus d’informations, consultez la documentation de votre serveur d’applications.
