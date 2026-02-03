---
title: Propriétés de configuration de Correspondence Management
description: Cette rubrique explique comment modifier le compositeur de ressources avec des configurations spécifiques à une solution.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: correspondence-management
feature: Correspondence Management
solution: Experience Manager, Experience Manager Forms
role: Admin, User, Developer
exl-id: 23be6248-1013-488e-91e6-ac1f6fb7da50
source-git-commit: c714e51f0c0368988ce552969747ab5fce5c186f
workflow-type: tm+mt
source-wordcount: '807'
ht-degree: 48%

---

# Propriétés de configuration de Correspondence Management {#correspondence-management-configuration-properties}

Pour configurer ces propriétés, ouvrez l’URL suivante dans un navigateur : `https://<server>:<port>/<contextPath>/system/console/configMgr` et sélectionnez **Configurations de Correspondence Management**.

Correspondence Management possède les propriétés de configuration suivantes :

<table>
 <tbody>
  <tr>
   <th><p><strong>Propriété</strong></p> </th>
   <th><p><strong>Description</strong></p> </th>
   <th><p><strong>Valeur par défaut</strong></p> </th>
   <th><p><strong>Valeurs acceptables</strong></p> </th>
  </tr>
  <tr>
   <td><p>Indentation</p> </td>
   <td>Mise en retrait sur les modules<p> </p> </td>
   <td><p>12,7 mm</p> </td>
   <td><p>N’importe quel nombre</p> </td>
  </tr>
  <tr>
   <td>Largeur minimale (nombres)</td>
   <td>Largeur minimale à appliquer au champ de puces/nombres, lors de l’utilisation de listes numérotées à l’exception des nombres romains.</td>
   <td>8,0 mm</td>
   <td>N’importe quel nombre</td>
  </tr>
  <tr>
   <td><p>Largeur minimale (chiffres romains)</p> </td>
   <td><p>Largeur minimale à appliquer au champ de puce/nombre, lors de l’utilisation de nombres romains.</p> </td>
   <td><p>12,7 mm</p> </td>
   <td><p>N’importe quel nombre</p> </td>
  </tr>
  <tr>
   <td>Type de rendu</td>
   <td>Type de rendu utilisé par l’application pour afficher l’aperçu de la lettre. </td>
   <td>Rendu HTML</td>
   <td>Rendu HTMLou rendu PDF.</td>
  </tr>
  <tr>
   <td><p>Activation de la surbrillance du PDF dans CCR</p> </td>
   <td><p>Active la mise en surbrillance sur PDF dans l’application.</p> </td>
   <td><p>true</p> </td>
   <td><p>true/false</p> </td>
  </tr>
  <tr>
   <td><p>Type de surbrillance de la cible</p> </td>
   <td><p>Type de surbrillance de la cible dans l’application.</p> </td>
   <td><p>border</p> </td>
   <td><p>bord/remplissage/aucun</p> </td>
  </tr>
  <tr>
   <td><p>Couleur de surbrillance de la cible</p> </td>
   <td><p>Couleur de surbrillance cible dans l’application.</p> </td>
   <td><p>90;155;245</p> </td>
   <td><p>N’importe quelle couleur RVB au format R;V;B</p> </td>
  </tr>
  <tr>
   <td><p>Type de surbrillance du contenu</p> </td>
   <td><p>Type de surbrillance du contenu dans l’application.</p> </td>
   <td><p>Remplissage</p> </td>
   <td><p>bord/remplissage/aucun</p> </td>
  </tr>
  <tr>
   <td><p>Couleur de surbrillance du contenu</p> </td>
   <td><p>Couleur de surbrillance du contenu dans l’application.</p> </td>
   <td><p>210;225;245</p> </td>
   <td><p>N’importe quelle couleur RVB au format R;V;B</p> </td>
  </tr>
  <tr>
   <td><p>Type de surbrillance du champ</p> </td>
   <td><p>Type de surbrillance du champ dans l’application.</p> </td>
   <td><p>Remplissage</p> </td>
   <td><p>bord/remplissage/aucun</p> </td>
  </tr>
  <tr>
   <td><p>Couleur de surbrillance du champ</p> </td>
   <td><p>Couleur de surbrillance du champ dans l’application.</p> </td>
   <td><p>210;225;245</p> </td>
   <td><p>N’importe quelle couleur RVB au format R;V;B</p> </td>
  </tr>
  <tr>
   <td><p>Délai d’expiration de l’application</p> </td>
   <td><p>Expiration de l'application en secondes.</p> </td>
   <td><p>1200</p> </td>
   <td><p>N’importe quel nombre</p> </td>
  </tr>
  <tr>
   <td><p>Nom de paramètre du document PDF</p> </td>
   <td><p>Nom du paramètre pour le document PDF en post-traitement.</p> </td>
   <td><p>inPDFDoc</p> </td>
   <td><p>N’importe quel nom de variable de chaîne</p> </td>
  </tr>
  <tr>
   <td><p>Nom de paramètre de données XML</p> </td>
   <td><p>Nom du paramètre du document XML (données) en post-traitement.</p> </td>
   <td><p>inXMLDoc</p> </td>
   <td><p>N’importe quel nom de variable de chaîne</p> </td>
  </tr>
  <tr>
   <td><p>Nom de paramètre du document XDP</p> </td>
   <td><p>Nom du paramètre du document XDP envoyé au post-traitement.</p> </td>
   <td><p>inXDPDoc</p> </td>
   <td><p>N’importe quel nom de variable de chaîne</p> </td>
  </tr>
  <tr>
   <td><p>Nom de paramètre de l’URL de redirection</p> </td>
   <td><p>Nom du paramètre pour l’URL de redirection envoyée à partir du post-traitement. Cette valeur peut être n’importe quel nom de variable de chaîne.</p> </td>
   <td><p>redirectURL</p> </td>
   <td><p>N’importe quel nom de variable de chaîne</p> </td>
  </tr>
  <tr>
   <td><p>Type d’envoi de PDF</p> </td>
   <td><p>Type d’envoi PDF (type de PDF généré lors de l’envoi à partir de l’application).</p> </td>
   <td><p>nonInteractive</p> </td>
   <td><p>interactif/non interactif</p> </td>
  </tr>
  <tr>
   <td><p>Optimisation de l’instance du dictionnaire de données</p> </td>
   <td><p>Permet un transfert optimisé de l’instance de dictionnaire de données vers le serveur et le client.</p> </td>
   <td><p>true</p> </td>
   <td><p>true/false</p> </td>
  </tr>
  <tr>
   <td><p>Auto Correct Inconsistencies </p> </td>
   <td><p>Lorsqu’elle est activée, elle gère automatiquement les incohérences possibles dans les affectations de lettre.</p> </td>
   <td><p>true</p> </td>
   <td><p>true/false</p> </td>
  </tr>
  <tr>
   <td><p>Utilisation des formats de données configurés</p> </td>
   <td><p>Contrôle si les formats de modification de données et le format d'affichage de données configurés doivent être utilisés.</p> </td>
   <td><p>true</p> </td>
   <td><p>true/false</p> </td>
  </tr>
  <tr>
   <td><p>Formats d’affichage des données</p> </td>
   <td><p>Indique un format d’affichage spécifique aux paramètres régionaux pour les données.</p> </td>
   <td><p>locale=en_US; dateFormat=dd-MM-yyyy; numberDecimalSeparator=.; numberGroupSeparator= ; numberUseGroupSeparator=truelocale=de_DE; dateFormat=dd-MM-yyyy; numberDecimalSeparator= ; numberGroupSeparator=.; numberUseGroupSeparator=truelocale=fr_FR; dateFormat=dd-MM-yyyy; numberDecimalSeparator=,; numberGroupSeparator= ; numberUseGroupSeparator=truelocale=ja_JP; dateFormat=dd-MM-yyyy; numberDecimalSeparator=.; numberGroupSeparator=,; numberUseGroupSeparator=true</p> </td>
   <td><p>--</p> </td>
  </tr>
  <tr>
   <td><p>Format de modification des données</p> </td>
   <td><p>Format de modification des données. Utilisé lors de l’écriture de données sous forme de chaîne ou de l’analyse de données de chaîne.</p> </td>
   <td><p>locale=en_US; dateFormat=dd-MM-yyyy; numberDecimalSeparator=.; numberGroupSeparator=,; numberUseGroupSeparator=true</p> </td>
   <td>--<p> </p> </td>
  </tr>
  <tr>
   <td><p>Gestion des instances de lettre lors de la publication</p> </td>
   <td><p>Activer/désactiver la fonctionnalité de lettre (applicable uniquement au serveur de publication).</p> </td>
   <td><p>false</p> </td>
   <td><p>true/false</p> </td>
  </tr>
  <tr>
   <td><p>Activation de l’audit</p> </td>
   <td><p>Activer/désactiver la fonctionnalité d’audit. Lorsque la valeur est false, les journaux d’audit de toutes les actions sont désactivés.</p> </td>
   <td><p>false</p> </td>
   <td><p>true/false</p> </td>
  </tr>
  <tr>
   <td><p>Activation de l’audit de lecture</p> </td>
   <td><p>Activer/désactiver la fonctionnalité d’audit pour les lectures de ressources.</p> </td>
   <td><p>false</p> </td>
   <td><p>true/false</p> </td>
  </tr>
  <tr>
   <td><p>Activation de l’audit de création</p> </td>
   <td><p>Activer/désactiver la fonctionnalité d’audit pour la création de ressources.</p> </td>
   <td><p>false</p> </td>
   <td><p>true/false</p> </td>
  </tr>
  <tr>
   <td><p>Activation de l’audit de mise à jour</p> </td>
   <td><p>Activer/désactiver la fonctionnalité d’audit pour la mise à jour des ressources.</p> </td>
   <td><p>false</p> </td>
   <td><p>true/false</p> </td>
  </tr>
  <tr>
   <td><p>Activation de l’audit de rétablissement</p> </td>
   <td><p>Activer/désactiver la fonctionnalité d’audit pour la restauration de ressources.</p> </td>
   <td><p>false</p> </td>
   <td><p>true/false</p> </td>
  </tr>
  <tr>
   <td><p>Activation de l’audit de publication</p> </td>
   <td><p>Activation/désactivation de la fonctionnalité d’audit pour la publication de ressources</p> </td>
   <td><p>false</p> </td>
   <td><p>true/false</p> </td>
  </tr>
  <tr>
   <td><p>Activation de l’audit d’enregistrement en tant que brouillon</p> </td>
   <td><p>Activer/désactiver la fonctionnalité d’audit pour enregistrer les brouillons de lettre.</p> </td>
   <td><p>false</p> </td>
   <td><p>true/false</p> </td>
  </tr>
  <tr>
   <td><p>Activation de l’audit d’envoi</p> </td>
   <td><p>Activer/désactiver la fonctionnalité d’audit pour l’envoi de lettre.</p> </td>
   <td><p>false</p> </td>
   <td><p>true/false</p> </td>
  </tr>
  <tr>
   <td><p>Activation de l’audit d’e-mail</p> </td>
   <td><p>Activer/désactiver la fonctionnalité d’audit pour les lettres envoyées par e-mail.</p> </td>
   <td><p>false</p> </td>
   <td><p>true/false</p> </td>
  </tr>
  <tr>
   <td><p>Activation de l’audit d’impression</p> </td>
   <td><p>Activer/désactiver la fonctionnalité d’audit pour l’impression des lettres.</p> </td>
   <td><p>false</p> </td>
   <td><p>true/false</p> </td>
  </tr>
  <tr>
   <td><p>Activation de l’audit de diffusion personnalisée</p> </td>
   <td><p>Activer/désactiver la fonctionnalité d’audit pour la diffusion personnalisée des lettres.</p> </td>
   <td><p>false</p> </td>
   <td><p>true/false</p> </td>
  </tr>
  <tr>
   <td><p>Nom du paramètre de documents joints</p> </td>
   <td><p>Nom du paramètre pour les documents de pièce jointe envoyés au post-traitement.</p> </td>
   <td><p>inAttachmentDocs</p> </td>
   <td><p>N’importe quel nom de variable de chaîne</p> </td>
  </tr>
  <tr>
   <td><p>Racine de l’utilisateur CM</p> </td>
   <td><p>URL du dossier contenant toutes les ressources utilisateur de Correspondence Management.</p> </td>
   <td><p>--</p> </td>
   <td><p>Emplacement de dossier valide</p> </td>
  </tr>
  <tr>
   <td><p>Taille du cache de lettres</p> </td>
   <td><p>Indiquez le Nombre maximal de lettres à conserver dans le cache.</p> <p>La modification de cette valeur entraîne le nettoyage <code>in-memory</code> cache.</p> </td>
   <td><p>100</p> </td>
   <td><p>N’importe quelle valeur numérique</p> </td>
  </tr>
  <tr>
   <td><p>Activation du cache de lettres</p> </td>
   <td><p>Activer/désactiver le cache de lettre.</p> <p>La modification de cette valeur entraîne le nettoyage <code>in-memory </code> cache.</p> </td>
   <td><p>true</p> </td>
   <td><p>true/false</p> </td>
  </tr>
  <tr>
   <td><p>Commande des éléments de données</p> </td>
   <td><p>Conserve l’ordre des éléments de données dans l’interface en fonction de leur séquence dans la lettre.</p> </td>
   <td><p>true</p> </td>
   <td><p>true/false</p> </td>
  </tr>
  <tr>
   <td><p>Prise en charge du rechargement</p> </td>
   <td><p>Activer/désactiver la prise en charge du rechargement dans les lettres rendues côté serveur.</p> <p>La désactivation améliore les performances de rendu des lettres.</p> </td>
   <td><p>false</p> </td>
   <td><p>true/false</p> <p> </p> </td>
  </tr>
  <tr>
   <td>Dossier temp </td>
   <td>Emplacement du dossier temporaire.</td>
   <td>acm.tpmFolder</td>
   <td> </td>
  </tr>
  <tr>
   <td>Enregistrement à distance</td>
   <td>Enregistre les instances de lettre sur l’auteur ou l’autrice de traitement spécifique.</td>
   <td> </td>
   <td> </td>
  </tr>
  <tr>
   <td>Options de compatibilité</td>
   <td>Options de compatibilité du format configname : configvalue séparées par une virgule.</td>
   <td>acm.compatibilityOptions</td>
   <td> </td>
  </tr>
  <tr>
   <td><p>Debug Directory </p> <p> </p> </td>
   <td>Recherche du dossier du système de fichiers pour le débogage. Si le répertoire ne <code>exists</code> pas, aucun fichier de vidage de débogage n’est généré.</td>
   <td>acm.debugDirectory</td>
   <td> </td>
  </tr>
 </tbody>
</table>
