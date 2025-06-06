---
title: Obtention d’informations sur la page au format JSON
description: Pour obtenir les informations sur la page, envoyez une requête au servlet PageInfo afin d’obtenir les métadonnées de page au format JSON.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: components
content-type: reference
solution: Experience Manager, Experience Manager Sites
feature: Developing
role: Developer
exl-id: 6c54197f-86da-41bd-93e6-ee78ece91013
source-git-commit: a869ffbc6015fd230285838d260434d9c0ffbcb0
workflow-type: tm+mt
source-wordcount: '931'
ht-degree: 99%

---

# Obtention d’informations sur la page au format JSON{#obtaining-page-information-in-json-format}

Pour obtenir les informations sur la page, envoyez une requête au servlet PageInfo afin d’obtenir les métadonnées de page au format JSON.

Le servlet PageInfo renvoie des informations sur les ressources dans le référentiel. Le servlet est lié à l’URL `https://<server>:<port>/libs/wcm/core/content/pageinfo.json` et utilise le paramètre `path` pour identifier la ressource. L’exemple d’URL suivant renvoie des informations sur le nœud `/content/we-retail/us/en` :

```shell
http://localhost:4502/libs/wcm/core/content/pageinfo.json?path=/content/we-retail/us/en
```

>[!NOTE]
>
>Si vous avez besoin d’informations sur la page au format JSON pour fournir la diffusion de contenu aux canaux qui ne sont pas des pages web AEM traditionnelles, par exemple :
>
>* des applications sur une seule page ;
>* des applications mobiles natives ;
>* D’autres canaux et points de contact externes à AEM.
>
>Consultez le document [Exportateur JSON pour Content Services](/help/sites-developing/json-exporter.md).

## Fournisseurs d’informations sur la page {#page-information-providers}

Les composants de page peuvent être associés à un ou plusieurs services `com.day.cq.wcm.api.PageInfoProvider` qui génèrent des métadonnées de page. Le servlet PageInfo appelle chaque service PageInfoProvider et agrège les métadonnées :

1. Le client HTTP envoie une requête au servlet PageInfo, qui inclut l’URL de la page.
1. Le servlet PageInfo détecte le composant qui effectue le rendu de la page.
1. Le servlet PageInfo appelle chaque PageInfoProvider associé au composant.
1. Le servlet agrège les métadonnées que chaque PageInfoProvider renvoie et ajoute les métadonnées à la réponse HTTP dans un objet JSON.

![chlimage_1-2](assets/chlimage_1-2a.png)

>[!NOTE]
>
>Comme pour PageInfoProviders, utilisez ListInfoProviders pour mettre à jour les listes d’informations au format JSON. (Voir [Personnalisation de la console d’administration des sites web](/help/sites-developing/customizing-siteadmin.md).)

## Fournisseurs d’informations de page par défaut {#default-page-information-providers}

Le composant `/libs/foundation/components/page` est associé aux services PageInfoProvider suivants :

* **Fournisseur de statut de page par défaut :** informations sur le statut de la page, telles que son verrouillage, si la page est la payload d’un workflow actif et les workflows disponibles pour la page.
* **Fournisseur d’informations sur la relation en direct :** informations concernant la gestion multisite (MSM), par exemple si la page fait partie d’un plan directeur et s’il s’agit d’une Live Copy.
* **Servlet de langue du contenu** : langue de la page en cours et informations sur chacune des langues dans lesquelles la page est disponible.
* **Fournisseur de statut du workflow** : informations de statut sur le workflow en cours dont la page fait partie du payload.
* **Fournisseur d’informations sur le package de workflow** : fournit des informations sur chaque package de workflow stocké dans le référentiel et indique si chaque package contient la ressource actuelle.
* **Fournisseur d’informations sur l’émulateur :** informations sur les émulateurs d’appareil mobile disponibles pour cette ressource. Si le composant de page n’effectue pas le rendu des pages mobiles, aucun émulateur n’est disponible.
* **Fournisseur d’informations sur les annotations :** informations sur les annotations figurant sur la page.

Par exemple, le servlet PageInfo renvoie la réponse JSON suivante pour le nœud `/content/we-retail/us/en` :

```
{
   "status":{
      "path":"/content/we-retail/us/en",
      "isLocked":false,
      "lockOwner":"",
      "canUnlock":false,
      "lastModified":1467202845038,
      "lastModifiedBy":"admin",
      "timeUntilValid":0,
      "onTime":0,
      "offTime":0,
      "replication":{
         "numQueued":0
      },
      "isDesignable":true,
      "isDeveloper":true
   },
   "isPage":true,
   "pageResourceType":"weretail/components/structure/page",
   "enableFragmentIdentifier":false,
   "workflow":{
      "isRunning":false
   },
   "workflows":{
      "wcm":{
         "models":[
            {
               "wid":"/etc/workflow/models/dam/adddamsize/jcr:content/model",
               "label":"Add Asset Size",
               "label_xss":"Add Asset Size"
            },
            {
               "wid":"/etc/workflow/models/ac-newsletter-workflow-simple/jcr:content/model",
               "label":"Approve for Adobe Campaign",
               "label_xss":"Approve for Adobe Campaign"
            },
            {
               "wid":"/etc/workflow/models/dam/dam-autotag-assets/jcr:content/model",
               "label":"DAM Smart Tag Assets",
               "label_xss":"DAM Smart Tag Assets"
            },
            {
               "wid":"/etc/workflow/models/dam/update_asset/jcr:content/model",
               "label":"DAM Update Asset",
               "label_xss":"DAM Update Asset"
            },
            {
               "wid":"/etc/workflow/models/cloudservices/DTM_bundle_download/jcr:content/model",
               "label":"Default DTM Bundle Download",
               "label_xss":"Default DTM Bundle Download"
            },
            {
               "wid":"/etc/workflow/models/dam/dam_download_asset/jcr:content/model",
               "label":"Download Asset",
               "label_xss":"Download Asset"
            },
            {
               "wid":"/etc/workflow/models/dam/dynamic-media-video-thumbnail-replacement/jcr:content/model",
               "label":"Dynamic Media Video Thumbnail Replacement",
               "label_xss":"Dynamic Media Video Thumbnail Replacement"
            },
            {
               "wid":"/etc/workflow/models/dam/dynamic-media-video-user-uploaded-thumbnail/jcr:content/model",
               "label":"Dynamic Media Video User Uploaded Thumbnail Process",
               "label_xss":"Dynamic Media Video User Uploaded Thumbnail Process"
            },
            {
               "wid":"/etc/workflow/models/projects/approval_workflow/jcr:content/model",
               "label":"Project Approval Workflow",
               "label_xss":"Project Approval Workflow"
            },
            {
               "wid":"/etc/workflow/models/publish_example/jcr:content/model",
               "label":"Publish Example",
               "label_xss":"Publish Example"
            },
            {
               "wid":"/etc/workflow/models/publish_to_campaign/jcr:content/model",
               "label":"Publish to Adobe Campaign",
               "label_xss":"Publish to Adobe Campaign"
            },
            {
               "wid":"/etc/workflow/models/s7dam/request_to_publish_to_youtube/jcr:content/model",
               "label":"Publish to YouTube",
               "label_xss":"Publish to YouTube"
            },
            {
               "wid":"/etc/workflow/models/projects/request_copy/jcr:content/model",
               "label":"Request Copy",
               "label_xss":"Request Copy"
            },
            {
               "wid":"/etc/workflow/models/request_for_activation/jcr:content/model",
               "label":"Request for Activation",
               "label_xss":"Request for Activation"
            },
            {
               "wid":"/etc/workflow/models/request_for_deactivation/jcr:content/model",
               "label":"Request for Deactivation",
               "label_xss":"Request for Deactivation"
            },
            {
               "wid":"/etc/workflow/models/request_for_deletion/jcr:content/model",
               "label":"Request for Deletion",
               "label_xss":"Request for Deletion"
            },
            {
               "wid":"/etc/workflow/models/request_to_complete_move_operation/jcr:content/model",
               "label":"Request to complete Move operation",
               "label_xss":"Request to complete Move operation"
            },
            {
               "wid":"/etc/workflow/models/screens-update-asset/jcr:content/model",
               "label":"Screens Update Asset",
               "label_xss":"Screens Update Asset"
            },
            {
               "wid":"/etc/workflow/models/s7dam/request_to_remove_from_youtube/jcr:content/model",
               "label":"Unpublish from YouTube",
               "label_xss":"Unpublish from YouTube"
            },
            {
               "wid":"/etc/workflow/models/wcm-translation/create_language_copy/jcr:content/model",
               "label":"WCM: Create Language Copy",
               "label_xss":"WCM: Create Language Copy"
            },
            {
               "wid":"/etc/workflow/models/wcm-translation/prepare_translation_project/jcr:content/model",
               "label":"WCM: Prepare Translation Project",
               "label_xss":"WCM: Prepare Translation Project"
            },
            {
               "wid":"/etc/workflow/models/wcm-translation/translate-i18n-dictionary/jcr:content/model",
               "label":"WCM: Prepare and Translate I18n-Dictionary",
               "label_xss":"WCM: Prepare and Translate I18n-Dictionary"
            },
            {
               "wid":"/etc/workflow/models/wcm-translation/sync_translation_job/jcr:content/model",
               "label":"WCM: Sync Translation Job",
               "label_xss":"WCM: Sync Translation Job"
            },
            {
               "wid":"/etc/workflow/models/wcm-translation/update_language_copy/jcr:content/model",
               "label":"WCM: Update Language Copy",
               "label_xss":"WCM: Update Language Copy"
            }
         ]
      },
      "translation":{
         "models":[
            {
               "wid":"/etc/workflow/models/dam/adddamsize/jcr:content/model",
               "label":"Add Asset Size",
               "label_xss":"Add Asset Size"
            },
            {
               "wid":"/etc/workflow/models/ac-newsletter-workflow-simple/jcr:content/model",
               "label":"Approve for Adobe Campaign",
               "label_xss":"Approve for Adobe Campaign"
            },
            {
               "wid":"/etc/workflow/models/dam/dam-autotag-assets/jcr:content/model",
               "label":"DAM Smart Tag Assets",
               "label_xss":"DAM Smart Tag Assets"
            },
            {
               "wid":"/etc/workflow/models/cloudservices/DTM_bundle_download/jcr:content/model",
               "label":"Default DTM Bundle Download",
               "label_xss":"Default DTM Bundle Download"
            },
            {
               "wid":"/etc/workflow/models/dam/dam_download_asset/jcr:content/model",
               "label":"Download Asset",
               "label_xss":"Download Asset"
            },
            {
               "wid":"/etc/workflow/models/dam/dynamic-media-video-thumbnail-replacement/jcr:content/model",
               "label":"Dynamic Media Video Thumbnail Replacement",
               "label_xss":"Dynamic Media Video Thumbnail Replacement"
            },
            {
               "wid":"/etc/workflow/models/dam/dynamic-media-video-user-uploaded-thumbnail/jcr:content/model",
               "label":"Dynamic Media Video User Uploaded Thumbnail Process",
               "label_xss":"Dynamic Media Video User Uploaded Thumbnail Process"
            },
            {
               "wid":"/etc/workflow/models/projects/approval_workflow/jcr:content/model",
               "label":"Project Approval Workflow",
               "label_xss":"Project Approval Workflow"
            },
            {
               "wid":"/etc/workflow/models/publish_to_campaign/jcr:content/model",
               "label":"Publish to Adobe Campaign",
               "label_xss":"Publish to Adobe Campaign"
            },
            {
               "wid":"/etc/workflow/models/s7dam/request_to_publish_to_youtube/jcr:content/model",
               "label":"Publish to YouTube",
               "label_xss":"Publish to YouTube"
            },
            {
               "wid":"/etc/workflow/models/projects/request_copy/jcr:content/model",
               "label":"Request Copy",
               "label_xss":"Request Copy"
            },
            {
               "wid":"/etc/workflow/models/request_for_deletion/jcr:content/model",
               "label":"Request for Deletion",
               "label_xss":"Request for Deletion"
            },
            {
               "wid":"/etc/workflow/models/request_to_complete_move_operation/jcr:content/model",
               "label":"Request to complete Move operation",
               "label_xss":"Request to complete Move operation"
            },
            {
               "wid":"/etc/workflow/models/screens-update-asset/jcr:content/model",
               "label":"Screens Update Asset",
               "label_xss":"Screens Update Asset"
            },
            {
               "wid":"/etc/workflow/models/translation/jcr:content/model",
               "label":"Translation Prepare",
               "label_xss":"Translation Prepare"
            },
            {
               "wid":"/etc/workflow/models/s7dam/request_to_remove_from_youtube/jcr:content/model",
               "label":"Unpublish from YouTube",
               "label_xss":"Unpublish from YouTube"
            }
         ]
      }
   },
   "translation":{

   },
   "design":{
      "path":"/conf/we-retail/settings/wcm/templates/hero-page/policies",
      "lastModified":0
   },
   "componentsRef":"/libs/wcm/core/content/components.1497341312569.json",
   "editableTemplate":"/conf/we-retail/settings/wcm/templates/hero-page",
   "msm":{
      "msm:isLiveCopy":true,
      "msm:isInBlueprint":false,
      "msm:isSource":false
   },
   "launches":{
      "isLaunch":false,
      "isInLaunch":false
   },
   "language":"en",
   "languages":{
      "rows":[
         {
            "path":"/content/we-retail/us/en",
            "exists":true,
            "hasContent":true,
            "lastModified":0,
            "iso":"en",
            "country":"gb",
            "language":"English"
         },
         {
            "path":"/content/we-retail/us/es",
            "exists":true,
            "hasContent":true,
            "lastModified":0,
            "iso":"es",
            "country":"es",
            "language":"Spanish"
         }
      ]
   },
   "workflowInfo":{
      "isRunning":false
   },
   "workflowPackageInfo":{
      "workflowPackages":[

      ],
      "selectedWorkflowPackages":[

      ],
      "runningSelectedWorkflowPackages":[

      ]
   },
   "emulators":{
      "groups":{
         "responsive":{
            "title":"Responsive Devices",
            "description":"The devices in this group are able to display a website built using responsive design patterns.",
            "path":"/etc/mobile/groups/responsive",
            "galaxy5":{
               "text":"Galaxy S5",
               "action":"start",
               "path":"/libs/wcm/mobile/components/emulators/galaxy5",
               "canRotate":true,
               "hasTouchScrolling":true,
               "contentCssPath":"/etc/mobile/groups/responsive/static.css",
               "width":1080,
               "height":1920,
               "device-pixel-ratio":3
            },
            "ipad":{
               "text":"iPad",
               "action":"start",
               "path":"/libs/wcm/mobile/components/emulators/ios/ipad",
               "canRotate":true,
               "hasTouchScrolling":true,
               "contentCssPath":"/etc/mobile/groups/responsive/static.css",
               "width":768,
               "height":1024,
               "device-pixel-ratio":1
            },
            "iphone5":{
               "text":"iPhone 5",
               "action":"start",
               "path":"/libs/wcm/mobile/components/emulators/ios/iphone5",
               "canRotate":true,
               "hasTouchScrolling":true,
               "contentCssPath":"/etc/mobile/groups/responsive/static.css",
               "width":640,
               "height":1136,
               "device-pixel-ratio":2
            },
            "iphone6":{
               "text":"iPhone 6",
               "action":"start",
               "path":"/libs/wcm/mobile/components/emulators/ios/iphone6",
               "canRotate":true,
               "hasTouchScrolling":true,
               "contentCssPath":"/etc/mobile/groups/responsive/static.css",
               "width":750,
               "height":1334,
               "device-pixel-ratio":2
            },
            "iphone4":{
               "text":"iPhone 4",
               "action":"start",
               "path":"/libs/wcm/mobile/components/emulators/ios/iphone4",
               "canRotate":true,
               "hasTouchScrolling":true,
               "contentCssPath":"/etc/mobile/groups/responsive/static.css",
               "width":640,
               "height":960,
               "device-pixel-ratio":2
            },
            "iphone6plus":{
               "text":"iPhone 6 Plus",
               "action":"start",
               "path":"/libs/wcm/mobile/components/emulators/ios/iphone6plus",
               "canRotate":true,
               "hasTouchScrolling":true,
               "contentCssPath":"/etc/mobile/groups/responsive/static.css",
               "width":1080,
               "height":1920,
               "device-pixel-ratio":2.6
            },
            "nexuss":{
               "text":"Nexus S",
               "action":"start",
               "path":"/libs/wcm/mobile/components/emulators/nexuss",
               "canRotate":true,
               "hasTouchScrolling":true,
               "contentCssPath":"/etc/mobile/groups/responsive/static.css",
               "width":320,
               "height":533,
               "device-pixel-ratio":1
            }
         }
      }
   },
   "annotations":[

   ],
   "permissions":{
      "modify":true,
      "replicate":true,
      "read":true,
      "create":true,
      "delete":true,
      "acl_read":true,
      "acl_edit":true
   },
   "isTargetable":"true",
   "responsive":{
      "breakpoints":{
         "phone":{
            "width":650,
            "title":"Smaller Screen"
         },
         "tablet":{
            "width":1200,
            "title":"Tablet"
         }
      }
   }
}
```

## Filtrage des informations sur le package de workflow {#filtering-workflow-package-information}

Configurez le service Fournisseur d’informations sur le package de workflow de la gestion de contenu web Day CQ pour qu’il renvoie des informations sur les packages de workflow qui vous intéressent. Par défaut, le service Fournisseur d’informations sur le package de workflow renvoie des informations sur chaque package de workflow du référentiel. L’itération sur un sous-ensemble de packages de workflow utilise moins de ressources du serveur.

>[!NOTE]
>
>L’onglet Workflow du Sidekick utilise le servlet PageInfo pour obtenir une liste des packages de workflow. Dans la liste, vous pouvez sélectionner le package auquel ajouter la page active. Les filtres que vous créez affectent cette liste.
>

L’ID du service est `com.day.cq.wcm.workflow.impl.WorkflowPackageInfoProvider`. Pour créer un filtre, indiquez une valeur pour une propriété `workflowpackageinfoprovider.filter`.

Les valeurs de propriété comportent le caractère + ou - , suivi du chemin d’accès au package :

* Le chemin d’accès est le chemin du nœud racine du package de workflow. Le chemin d’accès utilise la syntaxe FileVault.
* Pour inclure un package, utilisez le préfixe +.
* Pour exclure un package, utilisez le préfixe -.

Le service applique le résultat cumulé de tous les filtres. Par exemple, les valeurs de filtre suivantes excluent tous les packages de workflow, à l’exception de ceux du dossier Editions :

```
-/etc/workflow/packages(/.*)?
+/etc/workflow/packages/Editions(/.&ast;)?
```

>[!NOTE]
>
>Dans AEM, il existe plusieurs méthodes pour gérer les paramètres de configuration pour ces services. Pour plus d’informations, voir [Configurer OSGi](/help/sites-deploying/configuring-osgi.md).

Par exemple, pour configurer le service à l’aide de CRXDE Lite :

1. Ouvrez CRXDE Lite ([http://localhost:4502/crx/de](http://localhost:4502/crx/de)).
1. Dans le dossier de configuration de votre application, créez un nœud :

   * Nom : `com.day.cq.wcm.workflow.impl.WorkflowPackageInfoProvider`
   * Type : `sling:OsgiConfig`

1. Sélectionnez le nœud et ajoutez une propriété :

   * Nom : `workflowpackageinfoprovider.filter`
   * Type : `String[]`
   * Valeur : chemin d’accès au package de workflow au bon format.

1. Cliquez sur Enregistrer tout.

Pour configurer le service dans la source de votre projet :

1. Recherchez ou créez le dossier de configuration de votre application AEM dans la source de votre projet.

   Par exemple, si vous avez utilisé l’archétype multimodule du module externe Content Package Maven pour créer votre projet, le chemin du dossier est `<projectroot>/content/src/ for example, content/src/main/content/jcr_root/apps/<appname>/config`.
1. Dans le dossier de configuration, créez un fichier texte nommé com.day.cq.wcm.workflow.impl.WorkflowPackageInfoProvider.xml.
1. Copiez le texte suivant dans le fichier :

   ```
   <?xml version="1.0" encoding="UTF-8"?>
    <jcr:root xmlns:sling="https://sling.apache.org/jcr/sling/1.0"
    xmlns:jcr="https://www.jcp.org/jcr/1.0"
    jcr:primaryType="sling:OsgiConfig"
    workflowpackageinfoprovider.filter="[]"/>
   ```

1. À l’intérieur des crochets (`[]`) qui entourent la propriété `workflowpackageinfoprovider.filter`, entrez une liste de valeurs de filtre séparées par des virgules, semblable à l’exemple suivant :

   `workflowpackageinfoprovider.filter="[-/etc/workflow/packages(/.*)?,+/etc/workflow/packages/Editions(/.*)?]"/>`

1. Enregistrez le fichier.

## Créer un fournisseur d’informations sur la page {#creating-a-page-information-provider}

Créez un service Fournisseur d’informations sur la page personnalisé pour ajouter des métadonnées de page que votre application peut facilement obtenir.

1. Mettez en œuvre l’interface `com.day.cq.wcm.api.PageInfoProvider`.
1. Regroupez et déployez la classe en tant que service OSGi.
1. Créez un composant de page dans votre application. Utilisez `foundation/components/page` comme valeur de la propriété `sling:resourceSuperType`.

1. Ajoutez un nœud sous le nœud de composant nommé `cq:infoProviders`.
1. Sous le nœud `cq:infoProviders`, ajoutez un nœud pour votre service PageInfoProvider. Vous pouvez spécifier n’importe quel nom pour le nœud.
1. Ajoutez la propriété suivante à votre nœud PageInfoProvider :

   * Nom : className
   * Type : chaîne
   * Valeur : PID de votre service PageInfoProvider.

Dans le cas des ressources qui utilisent votre composant de page d’application comme `sling:resourceType`, le servlet PageInfo renvoie les métadonnées PageInfoProvider personnalisées en plus des métadonnées PageInfoProvider par défaut.

### Exemple de mise en œuvre de PageInfoProvider {#example-pageinfoprovider-implementation}

La classe Java suivante implémente [PageInfoProvider](https://developer.adobe.com/experience-manager/reference-materials/6-5-lts/javadoc/index.html) et renvoie l’URL publiée de la ressource de page active.

```java
package com.adobe.example;

import org.apache.felix.scr.annotations.Component;
import org.apache.felix.scr.annotations.Properties;
import org.apache.felix.scr.annotations.Property;
import org.apache.felix.scr.annotations.ReferenceCardinality;
import org.apache.felix.scr.annotations.Service;
import org.apache.felix.scr.annotations.Reference;

import org.apache.sling.api.SlingHttpServletRequest;
import org.apache.sling.api.resource.Resource;
import org.apache.sling.api.resource.ResourceResolver;

import org.apache.sling.commons.json.JSONException;
import org.apache.sling.commons.json.JSONObject;

import com.day.cq.wcm.api.Page;
import com.day.cq.wcm.api.PageInfoProvider;

@Component(metatype = false)
@Properties({
 @Property(name="service.description", value="Returns the public URL of a resource.")
})
@Service
public class PageUrlInfoProvider implements PageInfoProvider {

 @Reference(cardinality = ReferenceCardinality.OPTIONAL_UNARY)
 private com.day.cq.commons.Externalizer externalizer;

 private String fetchExternalUrl(ResourceResolver rr, String path) {
  return externalizer.publishLink(rr, path);
 }

 public void updatePageInfo(SlingHttpServletRequest request, JSONObject info, Resource resource)
   throws JSONException {

  Page page = resource.adaptTo(Page.class);
  JSONObject urlinfo = new JSONObject();
  urlinfo.put("publishURL", fetchExternalUrl(null,page.getPath()));
  info.put("URLs",urlinfo);
 }
}
```

L’exemple suivant, dans CRXDE Lite, montre le composant de page configuré pour utiliser le service PageUrlInfoProvider :

![chlimage_1-3](assets/chlimage_1-3a.png)

Le service PageUrlInfoProvider renvoie les données suivantes pour le nœud `/content/we-retail/us/en` :

```xml
"URLs": {
    "publishURL": "http://localhost:4503/content/we-retail/us/en"
}
```
