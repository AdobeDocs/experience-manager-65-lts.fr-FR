---
title: Configurer SSL sous Windows Vista
description: Découvrez comment configurer SSL sous Windows Vista. Utilisez et exécutez Java Keytool pour générer le certificat SSL avec les clés RSA pour l’authentification.
solution: Experience Manager, Experience Manager Forms
feature: Document Security
role: User, Developer
hide: true
hidefromtoc: true
exl-id: ee73f6a1-712c-461f-95e8-85f8c5694293
source-git-commit: d0f29cb177e98315cd50c2d7e96c3605eec14885
workflow-type: tm+mt
source-wordcount: '173'
ht-degree: 100%

---

# Configurer SSL sous Windows Vista {#configuring-ssl-on-windows-vista}

Pour configurer SSL sous Windows Vista™, vous avez besoin d’un certificat SSL avec des clés RSA pour l’authentification. Vous pouvez utiliser l’outil Java Keytool pour créer ce certificat.

>[!NOTE]
>
>Windows Vista ne fonctionnera pas avec les clés DSA.

Vous pouvez exécuter Keytool à l’aide d’une seule commande qui inclut toutes les informations requises pour créer le certificat et le fichier de stockage de clés.

**Créer un certificat SSL**

1. Dans une invite de commande, naviguez jusqu’à *`[JAVA HOME]`*/bin et tapez la commande ci-dessous pour créer le certificat et le fichier de stockage des clés :

   `keytool -genkey -keyalg RSA -dname "CN=`*Nom d’hôte* `, OU=`*Nom du groupe* `, O=`*Nom de la société* `,L=`*Nom de la ville* `, S=`*État* `, C=`*Code pays* `" -alias`*« LC Cert »* `-keypass` `key`*_* *mot de passe* `-keystore`*keystorename* `.keystore`

   >[!NOTE]
   >
   >Remplacez *`[JAVA_HOME]`par le répertoire dans lequel le JDK est installé, puis remplacez le texte en italiques par les valeurs correspondant à l’environnement.*

1. Saisissez `changeit` comme mot de passe. Il s’agit du mot de passe par défaut d’une installation Java, mais l’administrateur système peut l’avoir modifié.
