---
title: Résolution des problèmes liés à la réplication
description: Cet article fournit des informations sur la manière de résoudre les problèmes de réplication.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: configuring
docset: aem65
feature: Configuring
solution: Experience Manager, Experience Manager Sites
role: Admin
exl-id: 015def31-c7de-42b3-8218-1284afcb6921
source-git-commit: 408f6aaedd2cc0315f6e66b83f045ca2716db61d
workflow-type: tm+mt
source-wordcount: '927'
ht-degree: 96%

---

# Résolution des problèmes liés à la réplication{#troubleshooting-replication}

Cette page fournit des informations sur la manière de résoudre les problèmes de réplication.

## Problème {#problem}

La réplication (réplication non inverse) échoue pour une raison quelconque.

## Résolution {#resolution}

Il existe plusieurs raisons pour lesquelles la réplication échoue. Cet article explique l’approche que vous pouvez adopter lors de l’analyse de ces problèmes.

**Les réplications sont-elles déclenchées en cliquant sur le bouton d’activation ? Dans le cas CONTRAIRE, procédez comme suit :**

1. Accédez à /crx/de/index.jsp et connectez-vous en tant qu’administrateur.
1. Vérifiez si un nœud /bin/replicate ou /bin/replicate.json existe. Si le nœud existe, supprimez-le et enregistrez.

**Les réplications sont-elles mises en file d’attente dans les files d’attente de l’agent de réplication ?**

Vérifiez si c’est le cas en vous rendant sur /etc/replication/agents.author.html, puis cliquez sur les agents de réplication pour vérifier les éléments ci-après.

**Si une ou plusieurs files d’attente sont bloquées :**

1. Le statut de la file d’attente est-t-il **blocked** ? Le cas échéant, l’instance de publication n’est-elle pas en cours d’éxécution ou a-t-elle cessé de répondre ? Vérifiez l’instance de publication pour déterminer ce qui ne va pas. En d’autres termes, consultez les journaux et vérifiez s’il existe une erreur OutOfMemory ou un autre problème. S’il s’agit uniquement d’un problème de lenteur, prenez des images mémoire de threads et analysez-les.
1. Le statut de la file d’attente est-t-il **Queue is active - # pending** ? Fondamentalement, la tâche de réplication peut être bloquée dans une lecture de socket en attente de réponse de l’instance de publication ou de Dispatcher. Cela peut signifier que l’instance de publication ou de Dispatcher est en charge élevée ou bloquée dans un verrou. Dans ce cas, prenez les images mémoire de threads des instances de création et de publication.

   * Ouvrez les images mémoire de threads de l’instance de création dans un analyseur d’image mémoire de threads, vérifiez s’il indique que la tâche d’événement Sling de l’agent de réplication est bloquée dans un socketRead.
   * Ouvrez les images mémoire de threads de l’instance de publication dans un analyseur d’images mémoire de threads, analysez ce qui peut empêcher l’instance de publication de répondre. Vous devez voir un thread dont le nom comporte : POST /bin/receive. Il s’agit du thread recevant la réplication de l’instance de création.

**Si toutes les files d’attente de l’agent sont bloquées**

1. Il est possible qu’un certain élément du contenu ne puisse pas être sérialisé sous /var/replication/data à cause de la corruption du référentiel ou d’un autre problème. Vérifiez les journaux /error.log pour détecter une erreur correspondante. Pour supprimer un élément de réplication défectueux, procédez comme suit :

   1. Accédez à https://&lt;hôte>:&lt;port>/crx/de et connectez-vous en tant qu’utilisateur administrateur.
   1. Cliquez sur « Outils » dans le menu supérieur.
   1. Cliquez sur le bouton de loupe.
   1. Sélectionnez « XPath » comme type.
   1. Dans la boîte de dialogue « Requête », saisissez cette requête : /jcr:root/var/eventing/jobs//element(, slingevent:Job) order by @slingevent:created&#42;
   1. Cliquez sur « Rechercher ».
   1. Dans les résultats, les éléments principaux sont les dernières tâches d’événement Sling. Cliquez sur chacune d’elles et recherchez les réplications bloquées qui correspondent à ce qui apparaît en haut de la file d’attente.

**Créer un replication.log**

Il est parfois utile de définir tous les journaux de réplication pour qu’ils soient ajoutés dans un fichier journal distinct au niveau DEBUG. Pour ce faire :

1. Accédez à https://host:port/system/console/configMgr et connectez-vous en tant qu’administrateur.
1. Recherchez la configuration de l’enregistreur de journalisation Apache Sling et créez une instance en cliquant sur le bouton **+** à droite de la configuration d’usine. Cela crée un nouvel enregistreur de journal.
1. Définissez la configuration comme suit :

   * Niveau de connexion : DÉBOGUER
   * Fichier journal : logs/replication.log
   * Enregistreur : com.day.cq.replication

1. Si vous pensez que le problème est lié de quelque manière que ce soit à sling eventing/jobs, vous pouvez également ajouter ce package Java™ sous categories:org.apache.sling.event.

## Suspension de la file d’attente de l’agent de réplication  {#pausing-replication-agent-queue}

Parfois, il peut être judicieux de suspendre la file d’attente de réplication afin de réduire la charge sur le système de création, sans la désactiver. Actuellement, cela n’est possible qu’en configurant temporairement un port non valide. À partir de la version 5.4, vous pouvez voir un bouton de pause dans la file d’attente de l’agent de réplication, qui présente certaines limites.

1. L’état n’est pas conservé, ce qui signifie que, si vous redémarrez un serveur ou que le lot de réplication est recyclé, il revient à l’état en cours d’exécution.
1. La pause est inactive pendant une période plus courte (1 heure après l’absence totale d’activité avec réplication par d’autres threads) et non pendant une période plus longue. Parce qu’il existe une fonctionnalité dans sling qui permet d’éviter les threads inactifs. Vérifiez essentiellement si un thread de file d’attente de tâches a été inutilisé pendant une plus longue période, dans ce cas, cela déclenche les cycles de nettoyage. En raison du cycle de nettoyage, le thread est arrêté et le paramètre en pause est donc perdu. Comme les tâches sont conservées, il lance un nouveau thread pour traiter la file d’attente qui ne contient pas les détails de la configuration suspendue. En raison de cette file d’attente, l’état devient un état d’exécution.

## Les autorisations de page ne sont pas répliquées lors de l’activation de l’utilisateur ou l’utilisatrice. {#page-permissions-are-not-replicated-on-user-activation}

Les autorisations de page ne sont pas répliquées car elles sont stockées sous les nœuds auxquels l’accès est accordé, pas avec l’utilisateur.

En règle générale, les autorisations de page ne doivent pas être répliquées de l’instance de création vers l’instance de publication et ne le sont pas par défaut. En effet, les droits d’accès doivent être différents dans ces deux environnements. Par conséquent, Adobe recommande de configurer les listes de contrôle d’accès sur l’instance de publication, indépendamment de l’instance de création.

## File d’attente de réplication bloquée lors de la réplication des informations d’espace de noms, de l’instance de création vers l’instance de publication {#replication-queue-blocked-when-replicating-namespace-information-from-author-to-publish}

Dans certains cas, la file d’attente de réplication est bloquée lors de la tentative de réplication des informations sur les espaces de noms, de l’instance de création vers l’instance de publication. Ce problème se produit car l’utilisateur de la réplication ne dispose pas du privilège `jcr:namespaceManagement`. Pour éviter ce problème, vérifiez les points suivants :

* L’utilisateur de la réplication (tel que configuré sous l’onglet [Transfert](/help/sites-deploying/replication.md#replication-agents-configuration-parameters) > Utilisateur) existe également sur l’instance de publication.
* L’utilisateur dispose des privilèges de lecture et d’écriture sur le chemin où le contenu est installé.
* L’utilisateur possède le privilège `jcr:namespaceManagement` au niveau du référentiel. Vous pouvez accorder le privilège comme suit :

1. Connectez-vous à CRX/DE (`https://localhost:4502/crx/de/index.jsp`) en tant qu’administrateur ou administratrice.
1. Cliquez sur l’onglet **Contrôle d’accès**.
1. Sélectionnez **Référentiel**.
1. Cliquez sur **Ajouter une entrée** (icône plus).
1. Entrez le nom de l’utilisateur ou de l’utilisatrice.
1. Sélectionnez `jcr:namespaceManagement` dans la liste des privilèges.
1. Cliquez sur **OK**.
