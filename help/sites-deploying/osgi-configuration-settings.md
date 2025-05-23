---
title: Paramètres de configuration OSGi
description: Cet article décrit les paramètres de configuration OSGi (répertoriés en fonction de l’offre groupée) pertinents pour la mise en œuvre du projet. La liste sert de ligne directrice et n’est pas exhaustive.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: configuring
content-type: reference
docset: aem65
feature: Configuring
solution: Experience Manager, Experience Manager Sites
role: Admin
exl-id: d3356f5f-f80f-4ce0-b4e2-3ee927208ab1
source-git-commit: 408f6aaedd2cc0315f6e66b83f045ca2716db61d
workflow-type: tm+mt
source-wordcount: '3247'
ht-degree: 98%

---

# Paramètres de configuration OSGi{#osgi-configuration-settings}

L’[OSGi](https://www.osgi.org/) est un élément fondamental de la pile technologique d’AEM. Il est utilisé pour contrôler les lots composites d’AEM et leur configuration.

OSGi « *fournit les primitives normalisées qui permettent de créer des applications à partir de petits composants réutilisables et collaboratifs. Ces composants peuvent être créés dans une application et déployés* ».

Cette fonctionnalité permet une gestion conviviale des offres groupées, car elles peuvent être arrêtées, installées et démarrées individuellement. Les interdépendances sont gérées automatiquement. Chaque composant OSGi (voir [Spécifications OSGi](https://docs.osgi.org/specification/)) se trouve dans l’un des lots. Avec AEM, il existe plusieurs méthodes pour gérer les paramètres de configuration de ces offres groupées ; voir [Configurer OSGi](/help/sites-deploying/configuring-osgi.md) pour plus de détails et les pratiques recommandées.

Les paramètres de configuration OSGi suivants (répertoriés en fonction de l’offre groupée) sont pertinents pour la mise en œuvre du projet. Les paramètres répertoriés ne doivent pas tous être ajustés, certains sont mentionnés pour vous aider à comprendre comment fonctionne AEM.

>[!CAUTION]
>
>La liste est destinée à servir de ligne directrice et n’est pas exhaustive. Toutes les offres groupées ne sont pas répertoriées, pas plus que tous les paramètres de certaines des offres groupées qui le sont.
>
>La configuration nécessaire varie d’un projet à l’autre.
>
>Voir la console Web pour connaître les valeurs utilisées et des informations détaillées sur les paramètres.

>[!NOTE]
>
>D’autres lots peuvent être nécessaires pour des zones spécifiques de fonctionnalité dans AEM. Dans ce cas, les informations de configuration figurent sur la page liée à la fonctionnalité en question.

Le **Listener d’événement de réplication AEM** configure les éléments suivants :

* Les **Modes d’exécution**, dans lesquels les événements de réplication sont distribués aux écouteurs. Par exemple, s’il est défini comme auteur, c’est le système qui « initie » la réplication.

* Ajouter le mode d’exécution **publier** si le code du projet traite les événements de réplication (réplication inverse) dans un environnement de publication. Par exemple, lorsque le Dispatcher est utilisé pour vider le contenu de l’environnement de publication ou lorsque la réplication standard vers d’autres instances de publication se produit.

Le **Listener de modification du référentiel AEM** configure les éléments suivants :

* Les **Chemins**, les emplacements à écouter pour maintenir les événements de référentiel prêts à être distribuer.

Le **Référentiel client CRX Sling** configure l’accès au référentiel de contenu sous-jacent.

* Le **Mot de passe administrateur** doit être modifié après installation afin de garantir la [sécurité](/help/sites-administering/security-checklist.md) de votre instance.
* Aucune autre modification n’est nécessaire et vous devez procéder avec précaution pour toute modification car elles peuvent affecter l’accès au référentiel.

La **Console de gestion OSGi Apache Felix** configure :

* Les **plug-ins**, les éléments de navigation principaux (plug-ins de la console) qui doivent être disponibles dans la **console de gestion Web d’Apache Felix** en tant qu’éléments de menu de premier niveau. Désactivez tous les éléments dont vous n’avez pas besoin, car chacun d’entre eux requiert de l’espace et des ressources.

>[!CAUTION]
>
>Veillez à configurer les éléments suivants :
>
>**Nom d’utilisateur** et **Mot de passe**, les informations d’identification pour accéder à la console de gestion web Apache Felix.
>Le mot de passe doit être modifié après l’installation initiale pour garantir [la sécurité](/help/sites-administering/security-checklist.md) de votre instance.

>[!NOTE]
>
>Cette configuration doit être effectuée par le biais de la console Felix, car elle est nécessaire au démarrage (avant que le référentiel ne soit disponible).

L’**Enregistreur de données de demandes personnalisables Apache Sling** configure :

* le **Nom de l’enregistreur** et le **Format de journal** pour configurer l’emplacement et le format de la demande et de la journalisation des accès (valeur par défaut : `request.log`). Ce fichier journal est essentiel pour analyser la performance ou déboguer les fonctionnalités liées à la chaîne web. Il est associé à l’[enregistreur de demandes Apache Sling](#apacheslingrequestlogger).

Voir [Journalisation AEM](/help/sites-deploying/configure-logging.md) et [Journalisation Sling](https://sling.apache.org/documentation/development/logging.html).

Le **Pool de threads Apache Sling** configure les éléments suivants :

* La **Taille minimale du pool** et la **Taille max. du pool**, les taille du pool utilisées pour contenir les threads d’événement.

* La **Taille de la file d’attente**, taille maximale de la file d’attente de thread si le pool est épuisé.
La valeur recommandée est la suivante : `-1` car elle définit la file d’attente sur Illimité. Si une limite est définie, des pertes peuvent survenir lorsqu’elle est dépassée.

* La modification de ces paramètres peut améliorer les performances dans des scénarios comportant un grand nombre d’événements ; par exemple, une utilisation importante de la gestion des DAM ou des workflows AEM.
* Les valeurs spécifiques à votre scénario doivent être établies à l’aide de tests.
* Ces paramètres peuvent avoir une incidence sur les performances de votre instance. Par conséquent, ne les modifiez pas sans raison et sans précautions.

Le **Servlet GET Apache Sling** configure certains aspects du rendu :

* L’**Index automatique** pour activer ou désactiver le rendu du répertoire pour la navigation.
* **Activez** (ou désactivez) les rendus par défaut, tels qu’**HTML**, **texte brut**, **JSON** ou **XML**.
Ne désactivez pas JSON.

>[!NOTE]
>
>Ce paramètre est automatiquement configuré pour les instances d’exploitation si vous exécutez AEM en [mode Prêt pour l’exploitation](/help/sites-administering/production-ready.md).

Le **Gestionnaire de script Java Apache Sling** configure les paramètres de compilation des fichiers .java en tant que scripts (servlets).

Certains paramètres peuvent affecter les performances. Désactivez ces paramètres si possible, en particulier pour une instance d’exploitation.

* La **machine virtuelle source** et la **machine virtuelle cible** définissent la version du JDK utilisée comme mode d’exécution JVM.

* pour les instances de production :

   * Désactivez l’option **Générer les informations de débogage**.

**Programme d’installation de JCR Apache Sling** Ces paramètres n’ont pas besoin d’être configurés, mais peuvent être utiles pour savoir quand développer ou déboguer. Par exemple, les dossiers d’installation peuvent être utiles pour archiver ou extraire, ou créer un package.

* **regexp du nom des dossiers d’installation** et **Profondeur de hiérarchie maximale des dossiers d’installation** : indiquez où et dans quelle profondeur les dossiers de référentiel sont recherchés pour les ressources à installer. Lorsqu’un caractère générique est utilisé (comme dans .&#42;/install), toutes les correspondances appropriées seront recherchées, par exemple, `/libs/sling/install` et `/libs/cq/core/install`.

* **Chemin de recherche** : la liste des chemins d’accès recherchés par jcrinstall pour l’installation des ressources, ainsi qu’un nombre indiquant le facteur de pondération pour ce chemin.

**Configuration de la file d’attente Apache Sling** configurez les paramètres qui gèrent la planification des tâches :

* **Intervalle de reprise**, **Nombre maximal de reprises**, **Nombre maximal de tâches en parallèle** entre autres.

* La modification de ces paramètres peut améliorer les performances dans des scénarios comportant un grand nombre de tâches ; par exemple, une utilisation intensive de la gestion des ressources numériques et des workflows AEM.
* Les valeurs spécifiques à votre scénario doivent être établies à l’aide de tests.
* Ne modifiez pas ces paramètres sans raison, mais uniquement après mûre réflexion.

Le **Gestionnaire de script JSP Apache Sling** configure les paramètres relatifs aux performances pour le gestionnaire de script JSP. Pour améliorer les performances, désactivez-en le plus possible.

En particulier pour les instances d’exploitation :

* Désactivez l’option **Générer les informations de débogage**.
* désactivez **Conserver le code Java™ généré**
* Désactivez l’option **Contenu mappé**.
* désactivez **Afficher les fragments source**

>[!NOTE]
>
>Ce paramètre est automatiquement configuré pour les instances d’exploitation si vous exécutez AEM en [mode Prêt pour l’exploitation](/help/sites-administering/production-ready.md).

La **Configuration de journalisation Apache Sling** configure les éléments suivants :

* Le **Niveau de journal** et le **fichier journal**, pour définir l’emplacement et le niveau de journal de la configuration de journalisation centrale (error.log). Le niveau peut être défini sur `DEBUG`, `INFO`, `WARN`, `ERROR`, et `FATAL`.

* Le **nombre de fichiers journaux** et le **seuil du fichier journal** pour définir la taille et la rotation de version du fichier journal.

* Le **modèle de message** définit le format des messages du journal.

Voir [Journalisation AEM](/help/sites-deploying/configure-logging.md#global-logging) et [Journalisation Sling](https://sling.apache.org/documentation/development/logging.html).

La **Configuration de l’enregistreur de journaux Apache Sling (configuration d’usine)** configure :

* Le **Niveau de journal**, le **Fichier journal** et le **Format de message** pour définir les détails du fichier journal et des messages.

* L’**Enregistreur** pour définir la catégorie ; par exemple, uniquement le journal pour com.day.cq.

* En utilisant la **Configurations d’usine**, un certain nombre de configurations supplémentaires peuvent être ajoutées pour répondre aux différents niveaux de journal et catégories nécessaires.
* Ces configurations sont utiles lors du développement. Par exemple, pour consigner des messages TRACE pour un service spécifique dans un fichier journal spécifique.
* De telles configurations s’avèrent utiles dans un environnement de production. Par exemple, pour que les messages relatifs à un service spécifique soient consignés dans un fichier journal individuel afin de faciliter la surveillance.

Voir [Journalisation AEM](/help/sites-deploying/configure-logging.md) et [Journalisation Sling](https://sling.apache.org/documentation/development/logging.html).

La **Configuration de rédacteur de journalisation Apache Sling (configuration d’usine)** configure les éléments suivants :

* Le **Fichier journal** pour définir l’existence d’un fichier journal
* Le **nombre de fichiers journaux** pour définir la rotation des versions

* Le rédacteur peut être utilisé par une **configuration de journalisation de journaux Apache Sling**.

* Ces configurations sont utiles lors du développement. Par exemple, pour consigner des messages TRACE pour un service spécifique dans un fichier journal spécifique.
* De telles configurations s’avèrent utiles dans un environnement de production. Par exemple, pour que les messages relatifs à un service spécifique soient consignés dans un fichier journal individuel afin de faciliter la surveillance.

Voir [Journalisation AEM](/help/sites-deploying/configure-logging.md) et [Journalisation Sling](https://sling.apache.org/documentation/development/logging.html).

Le **Servlet principal Apache Sling** configure :

* le **Nombre d’appels par demande** et la **Profondeur de récursion** pour protéger votre système contre la récursivité infinie et les appels excessifs de script.

Le **Service de type MIME Apache Sling Commons** configure les éléments suivants :

* **Types MIME** : pour ajouter les types requis par votre projet dans le système. Cela permet d’effectuer une requête `GET` sur un fichier pour définir l’en-tête du type de contenu approprié pour lier le type de fichier et l’application.

**Filtre de référent Apache Sling** : pour résoudre les problèmes de sécurité connus avec Cross-Site Request Forgery (CSRF) dans CRX WebDAV et Apache Sling, vous devez configurer le filtre de référent.

Le service de filtrage des référents est un service OSGi qui vous permet de configurer :

* les méthodes HTTP à filtrer ;
* si un en-tête de référent vide est permis ;
* et une liste des serveurs autorisés, en plus de l’hôte de serveur.

Reportez-vous à la section [Liste de contrôle de sécurité - Problèmes de falsification des demandes cross-site](/help/sites-administering/security-checklist.md#protect-against-cross-site-request-forgery) pour plus de détails.

>[!NOTE]
>
>Le filtre de référent Apache Sling dépend de l’installation d’un package de correctif rapide.

L’**Enregistreur de requêtes Apache Sling** configure les éléments suivants :

* Divers paramètres pour définir comment les requêtes sont consignées
* **Activer le journal de requête** : pour activer ou désactiver le journal de requête.

* **Activer le journal d’accès** : pour activer ou désactiver le journal d’accès.

Associé à la [journalisation de données de requêtes personnalisables Apache Sling](#apacheslingcustomizablerequestdatalogger).

Voir [Journalisation AEM](/help/sites-deploying/configure-logging.md) et [Journalisation Sling](https://sling.apache.org/documentation/development/logging.html).

La **Resource Resolver Factory d’Apache Sling** configure les aspects centraux de la résolution des ressources Sling :

* **Chemins de recherche de ressources** : ajoutez des chemins spécifiques au projet (sans supprimer `/libs` ou `/apps`).

* Les **URL virtuelles** pour définir vos mappages aux URL de redirection.

* **Mappages d’URL** pour définir les alias. Par exemple, renommez `/content` en `/`.

* L’**Emplacement du mappage**, la configuration du mappeur extériorisée dans `/etc/map`

* Utilisez votre installation locale (par exemple, utilisez `https://localhost:4502/system/console/jcrresolver`) pour déterminer quel résolveur de ressources est actif.

Voir : [https://cwiki.apache.org/confluence/display/SLING/Flexible+Resource+Resolution](https://cwiki.apache.org/confluence/display/SLING/Flexible+Resource+Resolution).

>[!CAUTION]
>
>Configurez ces options dans le référentiel.
>
>Sinon, les modifications apportées aux **Mappages d’URL** à l’aide de la console Felix peuvent être écrasées par AEM au prochain démarrage.

Le **Gestionnaire d’erreur et résolveur de script et le servlet Apache Sling** Le servlet Sling et le résolveur de script ont plusieurs tâches :

1. Ils sont utilisés comme `ServletResolver` pour sélectionner le servlet ou le script à appeler pour traiter la demande.

1. Ils servent de `SlingScriptResolver`.

1. Ils assurent la gestion des erreurs en implémentant l’interface `ErrorHandler` à l’aide du même algorithme pour sélectionner les servlets et les scripts assurant la gestion des erreurs, comme ceux utilisés pour résoudre les servlets et scripts assurant le traitement des demandes.

Plusieurs paramètres peuvent être définis, notamment :

* Les **chemins d’exécution** : ils répertorient les chemins d’accès à rechercher pour les scripts exécutables. En configurant des chemins spécifiques, vous pouvez limiter les scripts à exécuter. Si vous ne configurez aucun chemin, le chemin par défaut est utilisé (`/` = root). Cela permet d’exécuter de tous les scripts.
Si la valeur configurée du chemin se termine par une barre oblique, la recherche concerne l’arborescence entière. En l’absence de barre oblique, le script n’est exécuté que s’il s’agit d’une correspondance exacte.

* **Extensions par défaut** : la liste des extensions adoptant le comportement par défaut. Le dernier segment de chemin du type de ressource peut être utilisé comme nom du script.

**Configuration du proxy de composants HTTP Apache** : il s’agit de la configuration de proxy pour tout le code utilisant le client HTTP Apache, utilisée lorsque du code HTTP est créé. Par exemple, lors de la réplication.

Lors de la création d’une configuration, ne modifiez pas la configuration d’usine. Créez plutôt une configuration d’usine pour ce composant à l’aide du gestionnaire de configuration disponible à l’adresse suivante : **https://localhost:4502/system/console/configMgr/**. La configuration du proxy est disponible à l’adresse **org.apache.http.proxyconfigurator.**

**Gestionnaire de bibliothèques HTML Adobe Granite** : configurez-le pour contrôler la gestion des bibliothèques clientes (css ou js), par exemple, la manière dont la structure sous-jacente est vue.

* Pour les instances de production :

   * Activez **Minifier** (pour supprimer les caractères CRLF et les espaces blancs).
   * Activez **Gzip** (pour permettre l’extraction et l’accès aux fichiers avec une seule requête).
   * Désactivez **Déboguer**
   * Désactivez **Minutage**

* Pour le développement JS (en particulier lors du débogage) :

   * désactivez **Minifier** ;
   * activez **Déboguer** pour séparer les fichiers à des fins de débogage et les utiliser avec un bug de déclenchement ;
   * activez **Minutage** si le minutage vous intéresse ;
   * activez **Déboguer** pour afficher les messages du journal de la console JS.

>[!CAUTION]
>
>Lorsque vous changez le paramètre sur **Minifier** ou **Gzip**, vous devez également supprimer le contenu du cache clientlibs. Consultez l’[article de la base de connaissances](https://experienceleague.adobe.com/docs/experience-cloud-kcs/kbarticles/KA-16543.html?lang=fr) pour plus de détails.

>[!NOTE]
>
>Ce paramètre est automatiquement configuré pour les instances d’exploitation si vous exécutez AEM en [mode Prêt pour l’exploitation](/help/sites-administering/production-ready.md).

**Gestionnaire d’authentification d’en-tête HTTP Adobe Granite** paramètres à l’échelle du système pour la méthode d’authentification de base de la requête HTTP.

Lors de l’utilisation de [groupes d’utilisateurs fermés](/help/sites-administering/cug.md), vous pouvez configurer, entre autres, les éléments suivants :

* **Domaine HTTP**
* La **page de connexion par défaut**

Le **Service de vérificateur de lien Day CQ** vérifie et, si nécessaire, configure les éléments suivants :

* La **période du planificateur** pour définir l’intervalle selon lequel les liens externes doivent être automatiquement vérifiés

* Vérifiez l’**Intervalle de tolérance des liens invalides** pour la période au-delà de laquelle un lien externe infructueux est considéré comme invalide.
* Les **Modèles de remplacement de la vérification de lien**, pour définir les chemins à exclure de la vérification des liens.

La **Tâche du vérificateur de lien Day CQ** configure les paramètres d’une seule tâche de vérification de lien (une tâche qui vérifie un lien externe) :

* Vérifiez les intervalles définis dans les options **Intervalle de test de lien valide** et **Intervalle de test d’un lien invalide**.

* Les différents paramètres liés aux proxys pour l’accès Internet et les NTLM nécessaires pour les accès externes lors de la vérification d’un lien.

Le **Service de messagerie Day CQ** Configurez le nom d’hôte et les informations d’accès au serveur de messagerie. Voir la section Configuration du service de messagerie.

La **Newsletter MCM Day CQ** Configurez les différents paramètres utilisés avec la newsletter.

Le **Mappage racine Day CQ** configure :

* Le **chemin cible** pour définir où une requête « `/` » sera redirigée.

Il existe deux interfaces utilisateur disponibles dans AEM :

* L’IU tactile est l’IU standard.
* L’IU classique obsolète est toujours pleinement opérationnelle.

En utilisant le mappage racine d’AEM, vous pouvez configurer l’IU que vous souhaitez utiliser en tant que valeur par défaut pour votre instance :

* Pour utiliser l’IU optimisée pour les écrans tactiles en tant qu’IU par défaut, le **chemin cible** doit pointer vers :

  ```shell
     /projects.html
  ```

* Pour utiliser l’IU classique en tant qu’IU par défaut, le **chemin cible** doit pointer vers :

  ```shell
     /welcome.html
  ```

>[!NOTE]
>
>Pour une installation standard, l’IU optimisée pour les écrans tactiles est l’UI par défaut.

**Gestionnaire d’authentification SSO Adobe Granite** - Configurez les détails de l’authentification unique (SSO). Ces informations sont souvent nécessaires dans les configurations de création d’entreprise, souvent avec LDAP.

Différentes propriétés de configuration sont disponibles :

* **Chemin**
Chemin pour lequel ce gestionnaire d’authentification est actif. Si ce paramètre n’est pas renseigné, le gestionnaire d’authentification est désactivé. Par exemple, si vous utilisez le chemin /, le gestionnaire d’authentification est utilisé pour l’ensemble du référentiel.

* **Classement de service**
La valeur de classement du service OSGi Framework est utilisée pour indiquer l’ordre d’appel de ce service. Cette valeur est une valeur `int` où les valeurs supérieures désignent une plus grande priorité.
La valeur par défaut est `0`.

* **Noms des en-têtes**
Les noms des en-têtes qui peuvent contenir un identifiant utilisateur.

* **Noms de cookies**
Les noms de cookies pouvant contenir un identifiant utilisateur.

* **Noms de paramètres**
Les noms de paramètres de requête pouvant fournir l’identifiant utilisateur.

* **La carte utilisateur**
Pour les utilisateurs sélectionnés, le nom d’utilisateur extrait de la requête HTTP peut être remplacé par un nom différent dans l’objet des informations d’authentification. Le mappage est défini ici. Si le nom d’utilisateur `admin` apparaît d’un côté ou de l’autre de la carte, le mappage est ignoré. Le caractère « = » doit être placé dans une séquence d’échappement avec un « \ » au début.

* **Format**
Indique le format dans lequel l’identifiant utilisateur est fourni. Utilisez :

   * `Basic` si l’identifiant utilisateur est codé au format d’authentification HTTP de base ;
   * `AsIs` si l’identifiant utilisateur est fourni en texte brut ou si une valeur appliquée d’expression régulière doit être utilisée telle quelle.

**Filtre de débogage de la gestion de contenu web Day CQ**
Utile lors du développement car il permet d’utiliser des suffixes comme ?debug=layout lors de l’accès à une page. Par exemple, https://localhost:4502/cf#/content/geometrixx/en/support.html?debug=layout fournit des informations de mise en page qui peuvent intéresser le développeur ou la développeuse.

* Pour garantir les performances et la sécurité, désactivez-le sur les instances d’exploitation.

Le **Filtre de gestion de contenu web Day CQ** configure les éléments suivants :

* Le **mode de gestion de contenu web** permet de définir le mode par défaut.
* Sur une instance de création, ce mode pourrait être `edit`, `disable,preview`, ou `analytics`.
Les autres modes sont accessibles depuis le sidekick. Vous pouvez également utiliser le suffixe `?wcmmode=disabled` pour simuler un environnement d’exploitation.

* Sur une instance de publication, ce mode doit être défini sur `disabled` afin de vous assurer qu’aucun autre mode n’est accessible.

>[!NOTE]
>
>Ce paramètre est automatiquement configuré pour les instances d’exploitation si vous exécutez AEM en [mode Prêt pour l’exploitation](/help/sites-administering/production-ready.md).

Le **Vérificateur de lien de gestion de contenu web Day CQ** configure les éléments suivants :

* La **liste des configurations de réécriture** pour spécifier une liste d’emplacements pour les configurations de vérificateur de lien basé sur le contenu. Les configurations peuvent être basées sur le mode d’exécution. Ce fait est important pour faire la distinction entre les environnements de création et de publication, car les paramètres du vérificateur de liens peuvent différer.

La **Fabrique du gestionnaire de pages de gestion de contenu web Day CQ** configure :

* la **Vérification de l’activation de la sous-arborescence de page** pour qu’un utilisateur (sans autorisation de réplication) supprime ou déplace des pages (même si les pages ne sont pas activées).

Le **Processeur de page de gestion de contenu web Day CQ** configure :

* les **chemins d’accès**, une liste d’emplacements où le système détecte des modifications de page avant de déclencher `jcr:Event`.

L’**outil de suivi des impressions de page Adobe**, pour une instance de création, configure :

* **sling.auth.requirements** : définissez la valeur de cette propriété sur `-/libs/wcm/stats/tracker`.

>[!CAUTION]
>
>Cette configuration autorise les requêtes anonymes au service de suivi.

>[!NOTE]
>
>Consultez la section [Impressions de page](/help/sites-deploying/configuring.md#enabling-page-impressions) pour plus d’informations.

Les **Statistiques de page de la gestion de contenu web Day CQ**, pour une instance de publication, configure les éléments suivants :

* L’**URL pour envoyer des données** pour configurer l’URL utilisée pour suivre les statistiques de page (essentiel si la demande d’un outil de suivi passe par le Dispatcher) ; par exemple, l’URL par défaut est `https://localhost:4502/libs/wcm/stats/tracker`.

* Le **Script de suivi activé** pour activer (`true`) ou désactiver (`false`) l’intégration du script de suivi sur les pages. La valeur par défaut est `false`.

>[!NOTE]
>
>Consultez la section [Impressions de page](/help/sites-deploying/configuring.md#enabling-page-impressions) pour plus d’informations.

Le **Gestionnaire de versions de la gestion de contenu web Day CQ** contrôlez si et comment les versions sont gérées dans votre système :

* **Créer une version lors de l’activation**, activé dans une installation standard
* **Activer la purge**

* **Purger les chemins d’accès**, les chemins d’accès qui seront recherchés suite à une action de recherche.
* **Chemins de version implicites**, les chemins d’accès pour lesquels la création de version implicite est active

* **Âge de version maximal**, l’âge maximale (en jours) d’une version

* **Nombre maximal de versions**, le nombre maximal de versions à conserver

Consultez la section [Purge des version](/help/sites-deploying/version-purging.md) pour plus d’informations.

Le **Service de notification par e-mail des workflows Day CQ** configure les paramètres d’e-mail pour les notifications envoyées par un workflow.

**Usine d’analyseur d’HTML Adobe AEM Rewriter**

Contrôle l’analyseur de HTML pour le module de réécriture CQ.

* **Balises supplémentaires à traiter** - Vous pouvez ajouter ou supprimer des balises HTML à traiter par l’analyseur. Par défaut, les balises suivantes sont traitées : A, IMG, AREA, FORM, BASE, LINK, SCRIPT, BODY, HEAD.
* **Conserver les majuscules** : par défaut, l’analyseur HTML convertit les attributs contenant une majuscule (par exemple `eBay`) en minuscules (par exemple, `ebay`). Vous pouvez désactiver ce paramètre pour conserver les attributs de casse mixte. Ce paramètre est utile lors de l’utilisation de structures front-end telles qu’Angular 2.

Le **Pool de connexions JDBC Day Commons** configure l’accès à une base de données externe utilisée comme source de contenu.

Comme c’est une configuration d’usine, plusieurs instances peuvent être configurées.

**Module de réécriture CDN** : la communication entre AEM et le réseau CDN doit être assurée pour que les ressources et fichiers binaires soient diffusés à la personne utilisatrice finale de manière sécurisée. Ce processus implique les deux tâches suivantes :

* Accédez à la ressource à partir d’AEM par le biais du réseau CDN la première fois (ou après son expiration dans le cache).
* Accédez à la ressource mise en cache dans le réseau CDN en toute sécurité. Une fois la ressource mise en cache dans le réseau CDN, la requête n’est pas envoyée à AEM, et tous les utilisateurs et utilisatrices ayant accès à cette ressource doivent être servis à partir du réseau CDN.

AEM fournit un module de réécriture permettant de réécrire les URL de ressources internes en URL CDN externes. Il réécrit les liens à transmettre au réseau CDN, y compris une signature JWS et un délai d’expiration pour permettre un accès sécurisé à la ressource. Cette fonctionnalité doit être utilisée sur les instances de création.

Le flux global est le suivant :

1. L’utilisateur ou l’utilisatrice s’authentifie avec AEM et demande une page contenant des ressources.
1. La page demandée contient une ressource similaire à `/content/dam/geometrixx-media/articles/paladin_trailer.jpg/jcr:content/renditions/cq5dam.thumbnail.319.319.png`.
1. Le module de réécriture transforme le lien en URL CDN contenant une signature JWS :
   `CDN_domain/content/dam/geometrixx-media/articles/paladin_trailer.jpg/_jcr_content/renditions/cq5dam.thumbnail.319.319.png?cdn_sign=JWS_SIGNATURE`

1. Le navigateur de l’utilisateur, puis transfère la demande de ressource au serveur CDN.
1. Le CDN doit être configuré pour charger la demande à AEM avec le paramètre `cdn_sign`.
1. Un gestionnaire d’authentification valide le paramètre `cdn_sign`, puis renvoie la ressource au CDN, qui est ensuite renvoyée à l’utilisateur.

Le flux entre le navigateur de l’utilisateur, le CDN et AEM peut être visualisée comme suit.

![chlimage_1-8](assets/chlimage_1-8.png)

>[!NOTE]
>
>Cette fonctionnalité est actuellement disponible uniquement pour les instances de création AEM.

**CDNConfigServiceImpl** Fournit des configurations CDN.

La fonction de réécriture CDN peut être activée en indiquant le **nom de domaine de distribution CDN** dans la configuration pour com.adobe.cq.cd n.rewriter.impl.CDNConfigServiceImpl.

Le service contient également d’autres options de configuration comme activer/désactiver la réécriture du CDN, les préfixes de chemin pour lesquels la réécriture CDN est exécutée, les valeurs TTL et le protocole (HTTP ou HTTPS).

**CDN Rewriter** Un module de réécriture pour réécrire les URL des images internes en URL CDN

La valeur **Attributs de balise** dans com.adobe.cq.cdn.rewriter.impl.CDNRewriter peut être définie de sorte que seuls les liens d’une sélection d’images soient réécrits.
