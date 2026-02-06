---
title: Conditions préalables à l’intégration à Adobe Target
description: Découvrez les conditions préalables à l’intégration à Adobe Target.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: integration
content-type: reference
docset: aem65
solution: Experience Manager, Experience Manager Sites
feature: Integration
role: Admin
exl-id: e1771229-b2ce-406a-95a5-99b11fafbe34
source-git-commit: 24bd1f57da3f9ce613ee28276d1ae9465b6dfba6
workflow-type: tm+mt
source-wordcount: '511'
ht-degree: 63%

---

# Conditions préalables à l’intégration à Adobe Target{#prerequisites-for-integrating-with-adobe-target}

Dans le cadre de l’[intégration d’AEM et Adobe Target](/help/sites-administering/target.md), vous devez vous inscrire à Adobe Target, configurer l’agent de réplication et sécuriser les paramètres d’activité sur le nœud de publication.

## S’inscrire auprès d’Adobe Target {#registering-with-adobe-target}

Pour intégrer AEM à Adobe Target, vous devez disposer d’un compte Adobe Target valide. Ce compte doit disposer au minimum des permissions de niveau **approbateur**. Lorsque vous vous inscrivez à Adobe Target, vous recevez un code client. Vous avez besoin du code client et de votre nom d’utilisateur et mot de passe Adobe Target pour connecter AEM à Adobe Target.

Le code client identifie le compte client Adobe Target lors de l’appel du serveur Adobe Target.

>[!NOTE]
>
>L’équipe Target doit permettre à votre compte d’utiliser l’intégration.
>
>Si ce n’est pas encore le cas, contactez l’[Assistance clientèle Adobe](https://experienceleague.adobe.com/en/docs/target/using/cmp-resources-and-contact-information).

## Activation de l’agent de réplication Target {#enabling-the-target-replication-agent}

L’[agent de réplication](/help/sites-deploying/replication.md) Test&amp;Target doit être activé sur l’instance de création. Notez que cet agent de réplication n’est pas activé par défaut si vous utilisez le mode d’exécution [nosamplecontent](/help/sites-deploying/configure-runmodes.md#using-samplecontent-and-nosamplecontent) pour installer AEM. Pour plus d’informations sur la sécurisation de votre environnement de production, voir [Liste de contrôle de sécurité](/help/sites-administering/security-checklist.md).

1. Sur la page d’accueil AEM, cliquez sur **Outils** > **Déploiement** > **Réplication**.
1. Cliquez sur **Agents sur l’instance de création**.
1. Cliquez sur l’agent de réplication **Test et cible**, puis cliquez sur **Modifier**.
1. Sélectionnez l’option Activé, puis cliquez sur **OK**.

   >[!NOTE]
   >
   >Lorsque vous configurez l’agent de réplication Test&amp;Target, sous l’onglet **Transport**, l’URI est défini par défaut sur `tnt:///`. Ne remplacez pas cet URI par `https://admin.testandtarget.omniture.com`.
   >
   >Si vous essayez de tester la connexion avec `tnt:///`, une erreur s’affiche, indiquant le comportement attendu. La raison en est que l’URI est destiné à un usage interne uniquement. Ne pas utiliser avec **Tester la connexion**.

## Sécurisez le nœud de paramètres d’activité {#securing-the-activity-settings-node}

Sécurisez le nœud de paramètres d’activité **cq:ActivitySettings** sur l’instance de publication afin qu’il ne soit pas accessible aux utilisateurs normaux. Le nœud de paramètres d’activité doit être accessible uniquement au service gérant la synchronisation de l’activité avec Adobe Target.

Le nœud **cq:ActivitySettings** est disponible dans CRXDE Lite sous `/content/campaigns/*nameofbrand*`* *sous le nœud `jcr:content` des activités . Par exemple, `/content/campaign/we-retail/master/myactivity/jcr:content/cq:ActivitySettings`. Ce nœud est créé après que vous ciblez un composant.

Le nœud **cq:ActivitySettings** sous le `jcr:content` de l’activité est protégé par les listes de contrôle d’accès suivantes :

* Refuser tout pour tout le monde.
* Autoriser les `jcr:read,rep:write` pour les `target-activity-authors` (l’auteur est un membre de ce groupe prêt à l’emploi).
* Autoriser les `jcr:read,rep:write` pour les `targetservice`.

Ces paramètres permettent de garantir que les utilisateurs ordinaires n’ont pas accès aux propriétés de nœud. Utilisez les mêmes ACL sur les instances de création et de publication. Consultez la section [Administration et sécurité des utilisateurs](/help/sites-administering/security.md) pour plus d’informations.

## Configuration de l’externaliseur de liens d’AEM {#configuring-the-aem-link-externalizer}

Lors de la modification d’une activité dans Adobe Target, l’URL pointe sur **localhost**, à moins que vous ne modifiiez l’URL sur le nœud de création AEM. Vous pouvez configurer l’externaliseur de liens d’AEM si vous souhaitez que le contenu exporté pointe vers un domaine *publier*.

>[!NOTE]
>
>Consultez également la section [Ajout de la configuration cloud](/help/sites-administering/experience-fragments-target.md#add-the-cloud-configuration).

Pour configurer l’externaliseur d’AEM :

>[!NOTE]
>
>Pour plus d’informations, voir [Externalisation des URL](/help/sites-developing/externalizer.md).

1. Accédez à la console web OSGi : **https://&lt;server>:&lt;port>/system/console/configMgr.**
1. Recherchez **Externalisateur de lien Day CQ** et saisissez le domaine du nœud de création.

   ![Day CQ Link Externalizer](assets/aem-externalizer-01.png)
