---
title: Présentation de la configuration SSL
description: Découvrez comment améliorer la sécurité de la communication lors de la configuration de SSL.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_ssl
products: SG_EXPERIENCEMANAGER/6.5/FORMS
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
hide: true
hidefromtoc: true
exl-id: 2e81b9b9-321d-4423-9748-6385956b1d90
source-git-commit: bc91f56d447d1f2c26c160f5c414fd0e6054f84c
workflow-type: tm+mt
source-wordcount: '211'
ht-degree: 100%

---

# Présentation de la configuration SSL {#overview-of-configuring-ssl}

Vous pouvez créer des informations d’identification et configurer SSL (Secure Socket Layer) sur le serveur d’applications afin de mieux sécuriser la communication avec votre serveur d’applications.

En tant que solution de sécurité, Rights Management requiert la configuration de SSL. Lorsque vous configurez des certificats SSL, veillez à n’utiliser que des clés RSA. Les certificats SSL avec clés DSA ne sont pas pris en charge.

Les informations fournies s’appliquent aux procédures d’installation clé en main, automatique et manuelle. Elles décrivent une méthode parmi d’autres, permettant de configurer SSL. Mais vous pouvez également utiliser d’autres méthodes plus appropriées à votre réseau ou à votre organisation.

>[!NOTE]
>
>Il est conseillé de terminer la procédure d’installation, de configuration et de déploiement des modules d’AEM Forms et de vérifier qu’ils s’exécutent correctement, avant de configurer SSL sur le serveur d’applications.

>[!NOTE]
>
>Lorsque vous créez des certificats de sécurité et des informations d’identification SSL, utilisez les mêmes droits d’accès utilisateur que ceux du serveur d’applications. Si ce dernier utilise d’autres droits d’accès, le rendu du formulaire au format PDFForm peut ne pas être correct lorsque ContentRootURI pointe vers une adresse https.

Si vous disposez d’un serveur LDAP compatible SSL, configurez la gestion des utilisateurs et utilisatrices pour l’utiliser. (Voir [Configuration de la gestion des utilisateurs et utilisatrices pour un serveur LDAP compatible SSL](/help/forms/using/admin-help/configure-user-management-ssl-enabled.md#configure-user-management-for-an-ssl-enabled-ldap-server).)
