---
title: Éditeur universel
description: Découvrez la flexibilité de l’éditeur universel et comment il peut vous aider à alimenter vos expériences découplées à l’aide d’AEM 6.5 LTS.
feature: Developing
role: Developer
exl-id: 495df631-5bdd-456b-b115-ec8561f33488
source-git-commit: 24bd1f57da3f9ce613ee28276d1ae9465b6dfba6
workflow-type: tm+mt
source-wordcount: '1166'
ht-degree: 43%

---

# À propos de l’éditeur universel {#universal-editor}

Découvrez la flexibilité de l’éditeur universel et comment il peut vous aider à alimenter vos expériences découplées à l’aide d’AEM 6.5 LTS.

## Vue d’ensemble {#overview}

L’éditeur universel est un éditeur visuel polyvalent qui fait partie d’Adobe Experience Manager Sites. Il permet aux auteurs d’effectuer une modification ce que vous voyez est ce que vous obtenez (WYSIWYG) de n’importe quelle expérience découplée.

* Les auteurs bénéficient de la flexibilité de l’éditeur universel. Il prend en charge la même modification visuelle cohérente pour toutes les formes de contenu découplé AEM.
* Les développeurs et les développeuses bénéficient de la polyvalence de l’éditeur universel, car il prend également en charge le véritable découplage de l’implémentation. Il permet aux développeurs d’utiliser pratiquement n’importe quel framework ou architecture de leur choix, sans imposer de contraintes de SDK ou de technologie.

Consultez la [documentation d’AEM as a Cloud Service sur l’éditeur universel](https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-service/content/implementing/developing/universal-editor/introduction) pour plus d’informations.

## Architecture {#architecture}

L’éditeur universel est un service qui fonctionne en tandem avec AEM pour créer du contenu découplé.

* L’éditeur universel est hébergé sur `https://experience.adobe.com/#/aem/editor/canvas` et peut modifier les pages rendues par AEM 6.5 LTS.
* L’éditeur universel lit la page AEM via Dispatcher à partir de l’instance de création AEM.
* Le service de l’éditeur universel, qui s’exécute sur le même hôte que Dispatcher, écrit les modifications dans l’instance de création AEM.

![Flux de création à l’aide de l’éditeur universel](assets/author-flow.png)

## Conditions requises {#requirements}

Les éléments suivants prennent en charge l’éditeur universel :

* AEM 6.5 LTS GA
   * L’hébergement On-Premise et Adobe Managed Services (AMS) sont pris en charge.
* [AEM 6.5](https://experienceleague.adobe.com/fr/docs/experience-manager-65/content/implementing/developing/headless/universal-editor/introduction)
   * L’hébergement On-Premise et AMS sont pris en charge.
* [AEM as a Cloud Service](https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-service/content/implementing/developing/universal-editor/introduction) (version `2023.8.13099` ou ultérieure)

Ce document se concentre sur la prise en charge LTS d’AEM 6.5 de l’éditeur universel. Pour utiliser l’éditeur universel avec AEM 6.5 LTS, vous avez besoin des éléments suivants :

* AEM 6.5 LTS GA
* Dispatcher configuré de manière appropriée

## Configuration {#setup}

Pour utiliser l’éditeur universel, procédez comme suit :

1. [Configurez les services sur votre instance de création AEM.](#configure-aem)
1. [Configurer un service d’éditeur universel local.](#set-up-ue)
1. [Ajustez votre Dispatcher pour autoriser le service d’éditeur universel.](#update-dispatcher)

Une fois que vous avez terminé la configuration, vous pouvez [paramétrer vos applications pour qu’elles utilisent l’éditeur universel.](#instrumentation)

### Configuration des services {#configure-aem}

L’éditeur universel repose sur un certain nombre de services qui doivent être configurés.

#### Définissez l’attribut SameSite pour le cookie `login-token`. {#samesite-attribute}

1. Ouvrez le gestionnaire de configuration.
   * `http://<host>:<port>/system/console/configMgr`
1. Recherchez le **Gestionnaire d’authentification de jeton Adobe Granite** dans la liste, puis cliquez sur **Modifier les valeurs de configuration**.
1. Dans la boîte de dialogue, remplacez la valeur de l’attribut **SameSite pour le cookie du jeton de connexion** (`token.samesite.cookie.attr`) par `Partitioned`.
1. Cliquez sur **Enregistrer**.

#### Supprimez l’option X-Frame des en-têtes `SAMEORIGIN`. {#sameorigin}

1. Ouvrez le gestionnaire de configuration.
   * `http://<host>:<port>/system/console/configMgr`
1. Recherchez le **Servlet principal Apache Sling** dans la liste, puis cliquez sur **Modifier les valeurs de configuration**.
1. Supprimez la valeur `X-Frame-Options=SAMEORIGIN` de l’attribut **En-têtes de réponse supplémentaires** (`sling.additional.response.headers`) s’il existe.
1. Cliquez sur **Enregistrer**.

#### Configuration du gestionnaire d’authentification des paramètres de requête Granite Adobe {#query-parameter}

1. Ouvrez le gestionnaire de configuration.
   * `http://<host>:<port>/system/console/configMgr`
1. Recherchez le **Gestionnaire d’authentification des paramètres de requête Adobe Granite** dans la liste, puis cliquez sur **Modifier les valeurs de configuration**.
1. Dans le champ **Chemin d’accès** (`path`), ajoutez `/` pour activer le gestionnaire.
   * Une valeur vide désactive le gestionnaire d’authentification.
1. Cliquez sur **Enregistrer**.

#### Définir les chemins d’accès au contenu ou les `sling:resourceTypes` ouverts dans l’éditeur universel {#paths}

1. Ouvrez le gestionnaire de configuration.
   * `http://<host>:<port>/system/console/configMgr`
1. Recherchez le **Service d’URL de l’éditeur universel** dans la liste, puis cliquez sur **Modifier les valeurs de configuration**.
1. Définissez pour quels chemins d’accès de contenu ou `sling:resourceTypes` l’éditeur universel doit s’ouvrir.
   * Dans le champ **Mappage d’ouverture de l’éditeur universel** indiquez les chemins d’accès pour lesquels l’éditeur universel doit être ouvert.
   * Dans le champ **Sling:resourceTypes qui doit être ouvert par l’éditeur universel**, saisissez une liste de ressources que l’éditeur universel ouvre directement.
1. Cliquez sur **Enregistrer**.
1. Vérifiez votre [configuration de l’externaliseur](/help/sites-developing/externalizer.md) et assurez-vous au minimum que les environnements local, de création et de publication sont définis comme dans l’exemple suivant :

   ```text
   "local $[env:AEM_EXTERNALIZER_LOCAL;default=http://localhost:4502]",
   "author $[env:AEM_EXTERNALIZER_AUTHOR;default=http://localhost:4502]",
   "publish $[env:AEM_EXTERNALIZER_PUBLISH;default=http://localhost:4503]"
   ```

Une fois ces étapes de configuration terminées, AEM ouvre l’éditeur universel pour les pages dans l’ordre suivant :

1. AEM vérifie les mappages sous `Universal Editor Opening Mapping` et si le contenu se trouve sous l’un des chemins définis à cet endroit, l’éditeur universel s’ouvre pour lui.

1. Pour le contenu situé en dehors des chemins définis dans `Universal Editor Opening Mapping`, AEM vérifie si le `resourceType` de contenu correspond à une entrée dans **Sling:resourceTypes qui doit être ouverte par l’éditeur universel**. S’il correspond, AEM ouvre le contenu dans l’éditeur universel à l’adresse `${author}${path}.html`.
1. Sinon, AEM ouvre l’éditeur de page.

Les variables suivantes sont disponibles pour définir vos mappages dans l’`Universal Editor Opening Mapping`.

* `path` : chemin d’accès du contenu de la ressource à ouvrir
* `localhost` : entrée du service Externalizer pour les `localhost` sans schéma, par exemple, `localhost:4502`
* `author` : entrée du service Externalizer pour l’auteur sans schéma, par exemple, `localhost:4502`
* `publish` : entrée du service Externalizer pour la publication sans schéma, par exemple, `localhost:4503`
* `preview` : entrée du service Externalizer pour la prévisualisation sans schéma, par exemple, `localhost:4504`
* `env` : `prod`, `stage`, `dev` en fonction des modes d’exécution Sling définis
* `token` : jeton de requête requis pour le `QueryTokenAuthenticationHandler`

Exemples de mappages :

* Ouvrez toutes les pages présentes dans `/content/foo` dans l’instance de création AEM :
   * `/content/foo:${author}${path}.html?login-token=${token}`
   * Résultats à l’ouverture de la `https://localhost:4502/content/foo/x.html?login-token=<token>`
* Ouvrez toutes les pages présentes dans `/content/bar` sur un serveur NextJS distant, en fournissant toutes les variables comme informations.
   * `/content/bar:nextjs.server${path}?env=${env}&author=https://${author}&publish=https://${publish}&login-token=${token}`
   * Résultats à l’ouverture de la `https://nextjs.server/content/bar/x?env=prod&author=https://localhost:4502&publish=https://localhost:4503&login-token=<token>`

### Configuration du service d’éditeur universel {#set-up-ue}

Une fois AEM mis à jour et configuré, vous pouvez configurer un service d’éditeur universel local pour votre propre développement et vos propres tests en local.

1. Installez Node.js 20 ou une version ultérieure.
1. Téléchargez et décompressez le dernier service d’éditeur universel à partir de [Distribution logicielle](https://experienceleague.adobe.com/fr/docs/experience-cloud/software-distribution/home).
1. Configurez le service d’éditeur universel au moyen de variables d’environnement ou d’un fichier `.env`.
   * [Consultez la documentation sur l’éditeur universel d’AEM as a Cloud Service pour plus d’informations.](https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-service/content/implementing/developing/universal-editor/local-dev#setting-up-service)
   * Notez que vous devrez peut-être utiliser l’option `UES_MAPPING` si une réécriture d’adresse IP interne est requise.
1. Exécuter `universal-editor-service.cjs`

### Mettre à jour Dispatcher {#update-dispatcher}

Avec AEM configuré et un service d’éditeur universel local en cours d’exécution, vous devez autoriser un proxy inverse pour le nouveau service [dans Dispatcher.](https://experienceleague.adobe.com/fr/docs/experience-manager-dispatcher/using/dispatcher)

1. Ajustez le fichier vhost de l’instance de création pour inclure un proxy inverse.

   ```html
   <IfModule mod_proxy.c>
    ProxyPass "/universal-editor" "http://localhost:8080"
    ProxyPassReverse "/universal-editor" "http://localhost:8080"
   </IfModule>
   ```

   >[!NOTE]
   >
   >Le port par défaut est 8080. Si vous avez modifié cette valeur à l’aide du paramètre `UES_PORT` dans [votre fichier `.env`,](https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-service/content/implementing/developing/universal-editor/local-dev#setting-up-service) vous devez paramétrer ici la valeur de port en conséquence.

1. Redémarrez Apache.

## Instrumenter votre application {#instrumentation}

Avec AEM mis à jour et un service d’éditeur universel local en cours d’exécution, vous pouvez commencer à modifier du contenu découplé à l’aide de l’éditeur universel.

Cependant, votre application doit être instrumentée pour tirer parti de l’éditeur universel. Cela implique d’inclure des balises méta pour indiquer à l’éditeur comment et où conserver le contenu. Les détails de ce paramétrage sont disponibles dans la [documentation sur l’éditeur universel d’AEM as a Cloud Service.](https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-service/content/implementing/developing/universal-editor/getting-started#instrument-page).

Notez que lorsque vous suivez la documentation pour l’éditeur universel avec AEM as a Cloud Service, les modifications ci-dessous s’appliquent lors de son utilisation avec AEM 6.5 LTS.

* Le protocole dans la balise meta doit être `aem65` au lieu de `aem`.

  ```html
  <meta name="urn:adobe:aue:system:aemconnection" content={`aem65:${getAuthorHost()}`}/>
  ```

* Le point d’entrée du service de l’éditeur universel doit être spécifié à l’aide d’une balise meta.

  ```html
  <meta name="urn:adobe:aue:config:service" content={`${getAuthorHost()}/universal-editor`}/>
  ```

* Dans la section `plugins` de la définition des composants, `aem65` doit être utilisé à la place de `aem`.

>[!TIP]
>
>Pour obtenir un guide de développement complet sur l’éditeur universel, consultez [Présentation de l’éditeur universel pour les développeurs AEM](https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-service/content/implementing/developing/universal-editor/developer-overview) dans la documentation d’AEM as a Cloud Service. Notez les modifications LTS d’AEM 6.5 décrites dans cette section.

## Différences entre AEM 6.5 LTS et AEM as a Cloud Service {#differences}

L’éditeur universel dans AEM 6.5 LTS fonctionne globalement de la même manière que dans AEM as a Cloud Service, y compris pour l’interface utilisateur et une grande partie de la configuration. Il existe toutefois des différences qu’il convient de noter.

* L’éditeur universel d’ 6.5 LTS prend uniquement en charge le cas d’utilisation découplé.
* La configuration de l’éditeur universel varie légèrement pour 6.5 LTS ([comme décrit](#setup) dans le document actuel).
* L’éditeur universel dans LTS 6.5 utilise un sélecteur de ressources et un sélecteur de fragments de contenu différents d’AEM as a Cloud Service.
