---
title: Intégration de l’interface utilisateur de création de correspondance dans votre portail personnalisé
description: Intégrer l’IU de création de correspondance à votre portail personnalisé
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: correspondence-management
docset: aem65
feature: Correspondence Management
solution: Experience Manager, Experience Manager Forms
role: Admin, User, Developer
exl-id: 496b125b-b091-4843-ba9f-2479dbeba07b
source-git-commit: c3e9029236734e22f5d266ac26b923eafbe0a459
workflow-type: tm+mt
source-wordcount: '413'
ht-degree: 100%

---

# Intégration de l’interface utilisateur de création de correspondance dans votre portail personnalisé{#integrating-create-correspondence-ui-with-your-custom-portal}

## Présentation {#overview}

Cet article décrit comment intégrer la solution de création de correspondance à votre environnement.

## Appel basé sur une URL {#url-based-invocation}

Pour appeler l’application de création de correspondance à partir d’un portail personnalisé, vous pouvez préparer l’URL avec les paramètres de requête suivants :

* l’identifiant du modèle de lettre (à l’aide du paramètre cmLetterId).

* l’URL des données XML extraites à partir de la source de données sélectionnée (à l’aide du paramètre cmDataUrl).

Par exemple, le portail personnalisé prépare l’URL sous la forme\
`https://'[server]:[port]'/[contextPath]/aem/forms/createcorrespondence.html?random=[timestamp]&cmLetterId=[letter identifier]&cmDataUrl=[data URL]`, qui pourrait être le href dʼun lien sur le portail.

>[!NOTE]
>
>Un appel de ce type n’est pas sécurisé, car les paramètres nécessaires sont transmis en tant que requête GET, en étant exposés (clairement visibles) dans l’URL.

>[!NOTE]
>
>Avant d’appeler l’application de création de correspondance, enregistrez et chargez les données pour appeler l’IU de création de correspondance à l’URL de données donnée. Vous pouvez le faire à partir du portail personnalisé ou par un autre processus principal.

## Appel en ligne basé sur les données {#inline-data-based-invocation}

Un autre moyen (plus sûr) d’appeler l’application de création de correspondance consiste à accéder à l’URL https://&#39;[serveur]:[port]&#39;/[contextPath]/aem/forms/createcorrespondence.html, en transmettant les paramètres et données permettant d’appeler l’application de création de correspondance dans le cadre d’une requête POST (sans que l’utilisateur final ne les voie). Cela signifie également que vous pouvez désormais transmettre les données XML pour l’application de création de correspondance en ligne (dans le cadre de la même requête, à l’aide du paramètre cmData), ce qui n’était pas possible/idéal dans l’approche précédente.

### Paramètres de spécification de lettre {#parameters-for-specifying-letter}

| **Nom** | **Type** | **Description** |
|---|---|---|
| cmLetterInstanceId | Chaîne | Identifiant de l’instance de lettre. |
| cmLetterId | Chaîne | Le nom du modèle de lettre. |

L’ordre des paramètres dans le tableau indique leur priorité d’utilisation pour le chargement de la lettre.

### Paramètres de spécification de la source de données XML {#parameters-for-specifying-the-xml-data-source}

<table>
 <tbody>
  <tr>
   <td><strong>Nom</strong></td> 
   <td><strong>Type</strong></td> 
   <td><strong>Description</strong></td> 
  </tr>
  <tr>
   <td>cmDataUrl<br /> </td> 
   <td>URL</td> 
   <td>Données XML provenant d’un fichier source utilisant des protocoles de base tels que cq, ftp, http ou file.<br /> </td> 
  </tr>
  <tr>
   <td>cmLetterInstanceId</td> 
   <td>Chaîne</td> 
   <td>Utilisation des données XML disponibles dans l’instance de lettre.</td> 
  </tr>
  <tr>
   <td>cmUseTestData</td> 
   <td>Booléen</td> 
   <td>Pour réutiliser les données de test associées au dictionnaire de données.</td> 
  </tr>
 </tbody>
</table>

L’ordre des paramètres dans le tableau indique leur priorité d’utilisation pour le chargement des données XML.

### Autres paramètres {#other-parameters}

<table>
 <tbody>
  <tr>
   <td><strong>Nom</strong></td> 
   <td><strong>Type</strong></td> 
   <td><strong>Description</strong></td> 
  </tr>
  <tr>
   <td>cmPreview<br /> </td> 
   <td>Booléen</td> 
   <td>True pour ouvrir la lettre en mode aperçu<br /> </td> 
  </tr>
  <tr>
   <td>Aléatoire</td> 
   <td>Date et heure</td> 
   <td>Pour résoudre les problèmes de mise en cache du navigateur.</td> 
  </tr>
 </tbody>
</table>

Si vous utilisez le protocole http ou cq pour le paramètre cmDataURL, l’URL correspondante doit pouvoir être accessible de manière anonyme.
