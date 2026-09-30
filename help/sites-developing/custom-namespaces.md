---
title: Espaces de noms personnalisés
description: Découvrez comment définir et déployer des espaces de noms personnalisés vers AEM 6.5 LTS.
solution: Experience Manager, Experience Manager Sites
feature: Developing,JCR
role: Developer
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
  - id: c45915cf-e157-4af7-a80d-97b905bcb3a5
    internal-label: Experience Manager Sites
feature_v2:
  - id: c5d917df-d8bd-5e97-a117-6dde1e9f7103
    internal-label: Developing
  - id: f2d27a5f-0d67-4d85-8a24-86a8d8a3574b
    internal-label: Developer tools
subfeature_v2:
  - id: cd14456d-a492-4b5c-8a82-1fbd4460dbd2
    internal-label: Java Content Repository
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 2e690827bfa8f3d8227860de4efb802758ae0095
workflow-type: tm+mt
source-wordcount: '224'
ht-degree: 66%
---

# Espaces de noms personnalisés{#custom-namespaces}

Découvrez comment définir et déployer des [espaces de noms](https://developer.adobe.com/experience-manager/reference-materials/spec/jcr/1.0/4.5_Namespaces.html) personnalisés vers AEM 6.5 LTS.

Les espaces de noms personnalisés sont la partie facultative d’une propriété JCR précédant un `:`. AEM utilise plusieurs espaces de noms, tels que :

+ `jcr` pour les propriétés du système JCR.
+ `cq` pour les propriétés AEM (anciennement appelées Adobe CQ).
+ `dam` pour les propriétés AEM spécifiques aux ressources DAM.
+ `dc` pour les propriétés Dublin Core.

... et beaucoup d’autres.

Les espaces de noms peuvent être utilisés pour indiquer la portée et l’intention d’une propriété. La création d’un espace de noms personnalisés, souvent le nom de votre société, permet d’identifier clairement les nœuds ou les propriétés spécifiques à votre mise en œuvre AEM et de conserver des données spécifiques à votre entreprise.

Les espaces de noms personnalisés sont gérés dans les scripts [Sling Repository Initialization (repoinit)](https://sling.apache.org/documentation/bundles/repository-initialization.html) et déployés en tant que configurations OSGi dans le package de configuration de votre projet (par exemple, `ui.config`).

## Ressources {#resources}

+ [Documentation sur l’initialisation du référentiel Sling (repoinit)](https://sling.apache.org/documentation/bundles/repository-initialization.html#repoinit-parser-test-scenarios)

## Code {#code}

Le code suivant est utilisé pour configurer un espace de noms `wknd`.

### Configuration OSGi de l’initialisateur de référentiel

`/ui.config/src/main/content/jcr_root/apps/wknd-examples/osgiconfig/config/org.apache.sling.jcr.repoinit.RepositoryInitializer~wknd-examples-namespaces.cfg.json`

```json
{
    "scripts": [
        "register namespace (wknd) https://site.wknd/1.0"
    ]
}
```

Cela permet d’utiliser dans AEM des propriétés personnalisées utilisant l’espace de noms `wknd`, comme indiqué par le premier paramètre après l’instruction `register namespace` . Pour des définitions de script plus avancées, consultez les exemples de la [documentation sur l’initialisation du référentiel Sling (repoinit)](https://sling.apache.org/documentation/bundles/repository-initialization.html#repoinit-parser-test-scenarios).
