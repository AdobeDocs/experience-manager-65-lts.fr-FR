---
title: AEM Forms bloque les requêtes HTTP valides
description: Les contrôles de validation XSS d’AEM Forms peuvent bloquer les requêtes HTTP valides des clients et clientes qui utilisent des composants personnalisés. Découvrez comment identifier le problème et relâcher temporairement les contrôles de validation.
solution: Experience Manager, Experience Manager Forms
feature: Security
role: Admin,Developer
exl-id: 10a02e57-7ff8-42d8-b31e-f714c0dd8338
source-git-commit: 4df5a9888532afd86562678a76c35841ac5634b8
workflow-type: tm+mt
source-wordcount: '276'
ht-degree: 6%
---
# AEM Forms bloque les requêtes HTTP valides {#aem-forms-blocks-valid-http-requests}

## Problème {#issue}

AEM Forms comprend des contrôles de sécurité pour empêcher les attaques XSS (cross-site scripting). Ces vérifications peuvent bloquer certaines requêtes HTTP valides pour les clients et clientes qui utilisent des composants personnalisés dans AEM Forms. Lorsqu’une requête est bloquée, le message suivant apparaît dans les journaux du serveur :

```text
Got Exception while Validating XSS: HTTP parameter name: params[browserLocale]: Invalid input. Please conform to regex ^[a-zA-Z0-9_]{1,32}$ with a maximum length of 2000: org.owasp.esapi.errors.ValidationException: HTTP parameter name: params[browserLocale]: Invalid input. Please conform to regex ^[a-zA-Z0-9_]{1,32}$ with a maximum length of 2000.
```

>[!NOTE]
>
>Pour une requête POST, la valeur par défaut du paramètre est **1048576**. Pour une requête GET, la valeur par défaut du paramètre est **2000**. Pour modifier la valeur du paramètre d’une requête POST, transmettez l’argument `com.adobe.idp.dsc.provider.rest.httpParamMaxSize` au démarrage du serveur.

## Cause {#cause}

L’expression régulière de validation XSS est plus stricte que le format de la valeur de paramètre envoyée par le composant personnalisé. Par conséquent, AEM Forms rejette la requête.

## Résolution {#resolution}

>[!CAUTION]
>
>La suppression des contrôles de sécurité rend le système vulnérable aux attaques XSS (cross-site scripting). Supprimez les contrôles de sécurité uniquement en tant que solution temporaire.

Pour supprimer temporairement les contrôles de sécurité et autoriser toutes les requêtes HTTP :

1. Arrêtez le serveur AEM Forms.

1. Créez une sauvegarde du fichier `[AEM-Forms-Installation-Directory]/configurationManager/export/adobe-livecycle-<application_server_name>.ear`.

1. Extrayez le fichier `esapi-helper-2.x.x.jar` du fichier `adobe-livecycle-<server_name>.ear`. L’emplacement du fichier `esapi-helper-2.x.x.jar` est différent pour chaque serveur d’applications :

   | Serveur d’applications | Emplacement du fichier esapi-helper-2.x.x.jar |
   | --- | --- |
   | JBoss | `adobe-livecycle-jboss.ear/lib` |
   | Oracle WebLogic | `adobe-livecycle-weblogic.ear/APP-INF/lib` |
   | IBM WebSphere | `adobe-livecycle-websphere.ear/` |

1. Ouvrez les fichiers `[extracted esapi-helper-2.x.x.jar]/esapi/validation.properties` et `[extracted esapi-helper-2.x.x.jar]/esapi/ESAPI.properties` pour les modifier.

1. Définissez la valeur des propriétés suivantes sur `^[\\s\\S]*$`. Par exemple, `Validator.HTTPParameterName=^[\\s\\S]*$`. Enregistrez et fermez les fichiers.

   * `Validator.HTTPQueryString`
   * `Validator.PMCallParameterName`
   * `Validator.PMCallParameterValue`
   * `Validator.HTTPParameterName`
   * `Validator.HTTPParameterValue`
   * `Validator.xssSafeString`

1. Regroupez les `esapi-helper-2.x.x.jar` mises à jour dans `adobe-livecycle-<application_server_name>.ear`. Déployez le `adobe-livecycle-<application_server_name>.ear` mis à jour sur le serveur d’applications.

1. Démarrez le serveur AEM Forms.

## Référence {#references}

* [Réduction des vulnérabilités SSRF (Server Side Request Forgery) pour AEM Forms on JEE 6.5 LTS SP2](/help/forms/troubleshooting/mitigating-server-side-request-forgery-vulnerabilities-for-aem-forms-on-jee-65-lts-sp2.md)
