---
title: Contrôle des opérations de gestion des utilisateurs et utilisatrices dans Adobe Experience Manager
description: Découvrez comment contrôler les opérations de gestion des utilisateurs et utilisatrices dans Adobe Experience Manager.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: Security
content-type: reference
docset: aem65
feature: Operations
solution: Experience Manager, Experience Manager Sites
role: Admin
exl-id: cd93bdfb-e8f1-45e8-b2a1-de70aba42581
source-git-commit: c3e9029236734e22f5d266ac26b923eafbe0a459
workflow-type: tm+mt
source-wordcount: '295'
ht-degree: 100%

---

# Contrôle des opérations de gestion des utilisateurs et utilisatrices dans Adobe Experience Manager (AEM) {#how-to-audit-user-management-operations-in-aem}

## Présentation {#introduction}

AEM a introduit la possibilité de consigner les modifications d’autorisation afin que vous puissiez les contrôler ultérieurement.

Cette amélioration permet de contrôler la création, la lecture, la mise à jour et la suppression des autorisations et des affectations collectives des utilisateurs et utilisatrices. Plus précisément, il enregistre les événements suivants :

* Création d’un nouvel utilisateur ou d’une nouvelle utilisatrice
* Ajout d’un nouvel utilisateur ou d’une nouvelle utilisatrice à un groupe
* Modifications des autorisations d’une personne existante ou d’un groupe existant

Par défaut, les entrées sont écrites dans le fichier `error.log`. Pour faciliter la surveillance, il est recommandé de les rediriger vers un fichier journal distinct. Vous trouverez plus d’informations sur la façon de procéder dans le paragraphe ci-dessous.

## Rediriger la sortie vers un fichier journal distinct {#redirecting-the-output-to-a-separate-log-file}

Pour rediriger la sortie de la journalisation vers un fichier journal distinct, vous devez créer une configuration **Enregistreur de journalisation Apach Sling**. Dans l’exemple ci-dessous, nous utilisons `useraudit.log` comme nom de fichier distinct.

1. Accédez à la console Web en vous rendant sur *https://serveraddress:serverport/system/console/configMgr*.
1. Recherchez la **Configuration de l’enregistreur de journalisation Apache Sling**. Ensuite, appuyez sur le « + » à droite de l’entrée pour créer une configuration d’usine.
1. Créez la configuration suivante :

   * **Niveau de journalisation :** informations
   * **Fichier journal :** logs/useraudit.log
   * **Modèle de message :** conservez la valeur par défaut
   * **Enregistreur :** com.adobe.granite.security.user.internal.audit, com.adobe.granite.security.user.internal.servlets.AuthorizableServlet

   Pour afficher les deux enregistreurs dans le champ **Enregistreur**, vous devez saisir le nom du premier enregistreur, puis créer un autre champ en cliquant sur le bouton « + » et en entrant le nom du second enregistreur.

## Exemple de sortie {#example-output}

S’ils sont configurés correctement, les paramètres doivent se présenter comme suit :

```xml
19.05.2017 15:15:08.933 *INFO* [0:0:0:0:0:0:0:1 [1495196108932] POST /libs/granite/security/post/authorizables.html HTTP/1.1] com.adobe.granite.security.user.internal.servlets.AuthorizableServlet Create Group 'group1' operation initiated by User 'admin' (administrator)
19.05.2017 15:15:08.934 *INFO* [0:0:0:0:0:0:0:1 [1495196108932] POST /libs/granite/security/post/authorizables.html HTTP/1.1] com.adobe.granite.security.user.internal.audit.AuditAuthorizableAction Group 'group1' was created

19.05.2017 15:16:25.698 *INFO* [0:0:0:0:0:0:0:1 [1495196185696] POST /libs/granite/security/post/authorizables.html HTTP/1.1] com.adobe.granite.security.user.internal.servlets.AuthorizableServlet Create User 'user1' operation initiated by User 'admin' (administrator)
19.05.2017 15:16:25.700 *INFO* [0:0:0:0:0:0:0:1 [1495196185696] POST /libs/granite/security/post/authorizables.html HTTP/1.1] com.adobe.granite.security.user.internal.audit.AuditAuthorizableAction User 'user1' was created

19.05.2017 15:16:25.728 *INFO* [0:0:0:0:0:0:0:1 [1495196185726] POST /home/groups/d/dGf7f7vGrZRLs6HS3AK-.rw.userprops.html HTTP/1.1] com.adobe.granite.security.user.internal.servlets.AuthorizableServlet Edit Membership for Group 'group1' operation initiated by User 'admin' (administrator)
19.05.2017 15:16:25.729 *INFO* [0:0:0:0:0:0:0:1 [1495196185726] POST /home/groups/d/dGf7f7vGrZRLs6HS3AK-.rw.userprops.html HTTP/1.1] com.adobe.granite.security.user.internal.audit.AuditGroupAction User 'user1' was added to the group 'group1'

19.05.2017 15:17:29.830 *INFO* [0:0:0:0:0:0:0:1 [1495196249828] POST /home/users/5/5dI6iK4HkZmrfTjcLBoI.rw.userprops.html HTTP/1.1] com.adobe.granite.security.user.internal.servlets.AuthorizableServlet Password Change for User 'user2' operation initiated by User 'admin' (administrator)
19.05.2017 15:17:29.832 *INFO* [0:0:0:0:0:0:0:1 [1495196249828] POST /home/users/5/5dI6iK4HkZmrfTjcLBoI.rw.userprops.html HTTP/1.1] com.adobe.granite.security.user.internal.audit.AuditAuthorizableAction Password for User 'user2' was changed

19.05.2017 15:17:54.906 *INFO* [0:0:0:0:0:0:0:1 [1495196274904] POST /home/users/5/5dI6iK4HkZmrfTjcLBoI.rw.html HTTP/1.1] com.adobe.granite.security.user.internal.servlets.AuthorizableServlet Delete User 'user2' operation initiated by User 'admin' (administrator)
19.05.2017 15:17:54.906 *INFO* [0:0:0:0:0:0:0:1 [1495196274904] POST /home/users/5/5dI6iK4HkZmrfTjcLBoI.rw.html HTTP/1.1] com.adobe.granite.security.user.internal.audit.AuditAuthorizableAction User 'user2' was removed

19.05.2017 15:19:11.050 *INFO* [0:0:0:0:0:0:0:1 [1495196351049] POST /libs/granite/security/post/authorizables.html HTTP/1.1] com.adobe.granite.security.user.internal.servlets.AuthorizableServlet Create User 'user3' operation initiated by User 'admin' (administrator)
19.05.2017 15:19:11.052 *INFO* [0:0:0:0:0:0:0:1 [1495196351049] POST /libs/granite/security/post/authorizables.html HTTP/1.1] com.adobe.granite.security.user.internal.audit.AuditAuthorizableAction User 'user3' was created
19.05.2017 15:19:36.899 *INFO* [0:0:0:0:0:0:0:1 [1495196376898] POST /home/groups/d/dGf7f7vGrZRLs6HS3AK-.rw.userprops.html HTTP/1.1] com.adobe.granite.security.user.internal.servlets.AuthorizableServlet Edit Membership for Group 'group1' operation initiated by User 'admin' (administrator)

19.05.2017 15:19:36.916 *INFO* [0:0:0:0:0:0:0:1 [1495196376915] POST /home/groups/d/dGf7f7vGrZRLs6HS3AK-.rw.userprops.html HTTP/1.1] com.adobe.granite.security.user.internal.servlets.AuthorizableServlet Edit Membership for Group 'group1' operation initiated by User 'admin' (administrator)
19.05.2017 15:19:36.917 *INFO* [0:0:0:0:0:0:0:1 [1495196376915] POST /home/groups/d/dGf7f7vGrZRLs6HS3AK-.rw.userprops.html HTTP/1.1] com.adobe.granite.security.user.internal.audit.AuditGroupAction User 'user1' was removed from the group 'group1'

19.05.2017 15:21:34.419 *INFO* [0:0:0:0:0:0:0:1 [1495196494417] POST /home/groups/d/dGf7f7vGrZRLs6HS3AK-.rw.html HTTP/1.1] com.adobe.granite.security.user.internal.servlets.AuthorizableServlet Delete Group 'group1' operation initiated by User 'admin' (administrator)
19.05.2017 15:21:34.419 *INFO* [0:0:0:0:0:0:0:1 [1495196494417] POST /home/groups/d/dGf7f7vGrZRLs6HS3AK-.rw.html HTTP/1.1] com.adobe.granite.security.user.internal.audit.AuditAuthorizableAction Group 'group1' was removed

19.05.2017 15:44:10.404 *INFO* [0:0:0:0:0:0:0:1 [1495197850401] POST /home/users/3/35XVpVtLRx4a5J9gKrVG.rw.userprops.html HTTP/1.1] com.adobe.granite.security.user.internal.servlets.AuthorizableServlet Password Change for User 'john' operation initiated by User 'john' (not administrator)
19.05.2017 15:44:10.405 *INFO* [0:0:0:0:0:0:0:1 [1495197850401] POST /home/users/3/35XVpVtLRx4a5J9gKrVG.rw.userprops.html HTTP/1.1] com.adobe.granite.security.user.internal.audit.AuditAuthorizableAction Password for User 'john' was changed
```

## Interface utilisateur classique {#classic-ui}

Dans l’interface utilisateur classique, les informations sur les opérations CRUD enregistrées dans le journal d’audit relatives à l’ajout et à la suppression d’utilisateurs et d’utilisatrices sont limitées à l’ID de la personne concernée et à la date à laquelle la modification s’est produite.

Par exemple :

```
10.05.2019 18:01:09.123 INFO [0:0:0:0:0:0:0:1 [1557491469096] POST /libs/cq/security/authorizables/POST HTTP/1.1] com.adobe.granite.security.user.internal.audit.AuditAuthorizableAction User 'test' was created
```
