---
title: Portail Formulaires | Gestion des données utilisateur
description: Découvrez la gestion des données utilisateur telles que l’accès, la suppression et le stockage de données sur le portail AEM Forms.
contentOwner: vishgupt
topic-tags: grdp
products: SG_EXPERIENCEMANAGER/6.5/FORMS
role: Admin,User
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
exl-id: f9eb6e61-5669-4cb7-a528-f1c09e455a60
source-git-commit: c3e9029236734e22f5d266ac26b923eafbe0a459
workflow-type: tm+mt
source-wordcount: '867'
ht-degree: 100%

---

# Portail Formulaires | Gestion des données utilisateur {#forms-portal-handling-user-data}

Le portail [!DNL AEM Forms] fournit des composants que vous pouvez utiliser pour répertorier les formulaires adaptatifs, les formulaires HTML5 et d’autres ressources Forms sur la page [!DNL AEM Sites]. Vous pouvez également le configurer pour qu’il affiche les formulaires adaptatifs sous forme de brouillons et envoyés ainsi que les formulaires HTML5 d’un utilisateur connecté. Pour plus d’informations sur le portail Formulaires et ses fonctionnalités, reportez-vous à la [Présentation de la publication de formulaires sur un portail](/help/forms/using/introduction-publishing-forms.md).

Lorsqu’une personne connectée enregistre un formulaire adaptatif en tant que brouillon ou l’envoie, il s’affiche dans les onglets Brouillons et envois sur le portail Formulaires. Les données des formulaires sous forme de brouillons ou envoyés sont stockées dans le magasin de données configuré pour le déploiement AEM. Les brouillons et les envois des utilisateurs et utilisatrices anonymes ne sont pas affichés sur la page du portail Formulaires, cependant les données sont stockées dans le magasin de données configuré. Consultez [Configuration des services de stockage pour les brouillons et les envois](/help/forms/using/configuring-draft-submission-storage.md).

## Données utilisateur et magasins de données {#user-data-and-data-stores}

Le portail Formulaires stocke les données des formulaires sous forme de brouillons de formulaires et de formulaires envoyés dans les cas suivants :

* L’action d’envoi configurée dans le formulaire adaptatif est **Action d’envoi du portail Formulaires**.
* Pour envoyer d’autres actions qu’une **Action d’envoi du portail Formulaires**, l’option **[!UICONTROL Stockage des données dans le portail Formulaires]** est activée dans les propriétés **[!UICONTROL Envoi]** du conteneur de formulaire adaptatif.

Pour chaque brouillon de formulaire et formulaire envoyé pour des utilisateurs et utilisatrices connectés et anonymes, le portail Formulaires stocke les données suivantes :

* Métadonnées de formulaire telles que le nom du formulaire, le chemin d’accès au formulaire, l’ID de brouillon ou d’envoi, le chemin d’accès aux pièces jointes et l’ID des données utilisateur
* Pièce jointe au formulaire en tant qu’octets de données
* Données de formulaire sous forme d’octets de données

Selon la persistance du magasin de données configuré, les données de formulaires sous forme de brouillons et envoyés sont stockées aux emplacements suivants.

<table>
 <tbody>
  <tr>
   <td><p><strong>Type de persistance</strong></p> </td>
   <td><p><strong>Stockage de données</strong></p> </td>
   <td><p><strong>Emplacement</strong></p> </td>
  </tr>
  <tr>
   <td><p>Valeur par défaut</p> </td>
   <td><p>Référentiel AEM d’instances de création et de publication</p> </td>
   <td><p><code>/content/forms/fp/</code></p> </td>
  </tr>
  <tr>
   <td><p>Distant</p> </td>
   <td><p>Référentiel AEM des instances de création et distantes</p> </td>
   <td><p><code>/content/forms/fp/</code></p> </td>
  </tr>
  <tr>
   <td><p>Base de données</p> </td>
   <td><p>Référentiel AEM d’instance de création et de tables de base de données</p> </td>
   <td>Tables de base de données <code>data</code>, <code>metadata</code> et <code>additionalmetadata</code></td>
  </tr>
 </tbody>
</table>

## Accès et suppression des données utilisateur {#access-and-delete-user-data}

Vous pouvez accéder aux données de formulaires envoyés et sous forme de brouillons pour des utilisateurs et utilisatrices connectés et anonymes dans les magasins de données configurés et, si nécessaire, les supprimer.

### Instances AEM {#aem-instances}

Toutes les données des formulaires envoyés et sous forme de brouillons enregistrées dans des instances AEM (d’auteur, de publication ou distante) pour les utilisateurs connectés et anonymes sont stockées dans le nœud `/content/forms/fp/` du référentiel AEM applicable. Chaque fois qu’un utilisateur ou une utilisatrice connectée ou anonyme enregistre un formulaire en tant que brouillon ou l’envoie, un `draft ID` ou un `submission ID`, un `user data ID`, et un `ID` aléatoire pour chaque pièce jointe (le cas échéant) sont générés. Il est associé au brouillon ou à l’envoi correspondant.

#### Accès aux données utilisateur {#access-user-data}

Lorsqu’une personne connectée enregistre un formulaire en tant que brouillon ou l’envoie, un nœud enfant est créé avec son ID d’utilisateur ou d’utilisatrice. Par exemple, les données de brouillons et d’envois de Sarah Rose dont l’ID utilisateur est `srose` sont stockées dans le nœud `/content/forms/fp/srose/` du référentiel AEM. Dans le nœud de l’ID utilisateur, les données sont organisées dans une structure hiérarchique.

Le tableau ci-dessous explique comment les données de tous les brouillons de `srose` sont stockées dans le référentiel AEM.

>[!NOTE]
>
>Une structure exacte telle que `drafts` est répliquée pour les formulaires envoyés par `srose` sous le nœud `/content/forms/fp/srose/submit/`.
>
>Tous les brouillons et envois des utilisateurs `anonymous` sont stockés sous le nœud `/content/forms/fp/anonymous/`, qui range les brouillons et les envois de tous les utilisateurs anonymes sous les nœuds `draft` et `submit`.

| Nœud | Description |
|---|---|
| `/content/forms/fp/srose/drafts` | Données de nœud de conteneur pour tous les brouillons de l’utilisateur |
| `/content/forms/fp/srose/drafts/attachments/` | Range toutes les pièces jointes de l’utilisateur en fonction de l’ID du brouillon |
| `/content/forms/fp/srose/drafts/attachments/<ID>` | Contient la pièce jointe de l’ID sélectionné au format binaire |
| `/content/forms/fp/srose/drafts/metadata/` | Range les métadonnées de formulaire de l’utilisateur en fonction de l’ID du brouillon |
| `/content/forms/fp/srose/drafts/metadata/<draft ID>` | Contient les métadonnées de formulaire de l’ID de brouillon sélectionné |
| `/content/forms/fp/srose/drafts/data/` | Range les données de formulaire de l’utilisateur en fonction de l’ID de données utilisateur |
| `/content/forms/fp/srose/drafts/data/<user data ID>` | Contient des données de formulaire pour l’ID de données utilisateur sélectionné au format binaire |

#### Suppression de données utilisateur {#delete-user-data}

Pour supprimer définitivement des données utilisateur des brouillons et des envois dans les systèmes AEM pour un utilisateur connecté, vous devez supprimer le nœud `user ID` pour un utilisateur spécifique à partir du nœud d’auteur. Supprimez manuellement les données de toutes les instances AEM applicables.

Les données de brouillon et d’envoi de tous les utilisateurs anonymes sont stockées dans les nœuds communs `drafts` et `submit` sous `/content/forms/fp/anonymous`. Il n’existe aucune méthode permettant de rechercher les données relatives à un utilisateur anonyme spécifique, sauf si certaines informations d’identification sont connues. Dans ce cas, vous pouvez rechercher les informations qui identifient l’utilisateur ou l’utilisatrice anonyme dans le référentiel AEM et supprimer manuellement le nœud qui les contient dans toutes les instances AEM applicables afin de supprimer les données du système AEM. Toutefois, pour supprimer les données de brouillons et d’envois de tous les utilisateurs anonymes, vous pouvez supprimer le nœud `anonymous`.

### Base de données {#database}

Lorsqu’AEM est configuré pour stocker des données dans une base de données, les données de brouillon et d’envoi du Portail Formulaires sont stockées dans les tables de base de données suivantes pour les utilisateurs et utilisatrices connectés et anonymes :

* data
* metadata
* additionalmetadata

#### Accès aux données utilisateur {#access-user-data-1}

Pour accéder aux données de brouillons et d’envois d’un utilisateur ou d’une utilisatrice connectée et anonyme dans les tables de base de données, exécutez la commande de base de données suivante. Dans la requête, remplacez `logged-in user` par l’ID de l’utilisateur des données auxquelles vous souhaitez accéder ou par `anonymous` pour les utilisateurs anonymes.

```sql
select * from metadata, data, additionalmetadatatable where metadata.owner = 'logged-in user' and metadata.id = additionalmetadatatable.id and metadata.userdataID = data.id
```

#### Suppression de données utilisateur {#delete-user-data-1}

Pour supprimer les données de brouillons et d’envois d’un utilisateur ou d&#39;une utilisatrice connectée des tables de base de données, exécutez la commande de base de données suivante. Dans la requête, remplacez `logged-in user` par l’ID de l’utilisateur des données que vous souhaitez supprimer ou par `anonymous` pour les utilisateurs anonymes. Pour supprimer les données d’un utilisateur ou d’une utilisatrice anonyme spécifique dans la base de données, vous devez le ou la trouver à l’aide d’informations d’identification et le ou la supprimer des tables de base de données contenant ces informations.

```sql
DELETE FROM metadata, data, additionalmetadatatable USING metadata INNER JOIN data ON metadata.userdataID = data.id INNER JOIN additionalmetadatatable ON metadata.id = additionalmetadatatable.id WHERE metadata.owner = 'logged-in user'
```
