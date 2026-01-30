---
title: Migration de contenu LTS d’AEM 6.5 vers AEM 6.5 à l’aide de la mise à niveau Oak
description: Découvrez comment migrer du contenu d’AEM 6.5 vers AEM 6.5 LTS à l’aide de l’outil de mise à niveau Oak
feature: Upgrading
solution: Experience Manager, Experience Manager Sites
role: Admin
exl-id: 8c4ffb0e-b4dc-4a81-ac43-723754cbc0de
source-git-commit: a85b54d5a7c3b00f95f439941a390dcfee883187
workflow-type: tm+mt
source-wordcount: '558'
ht-degree: 0%

---

# Migration de contenu LTS d’AEM 6.5 vers AEM 6.5 à l’aide de la mise à niveau Oak {#aem-65-to-aem-65lts-content-migration-using-oak-upgrade}

Ce document explique comment mettre à niveau Adobe Experience Manager de **6.5** vers **6.5 LTS**, en mettant l’accent sur la migration du référentiel de contenu. Elle traite de l’utilisation de l’outil de mise à niveau d’Oak pour transférer du contenu entre les référentiels avec précision et contrôle.

## Prérequis {#prerequisites}

Avant de commencer la migration, assurez-vous que les conditions suivantes sont remplies :

1. Compatibilité Java : AEM 6.5 LTS doit être installé et configuré pour fonctionner avec Java™ 17. Une fois la configuration effectuée, démarrez l’instance AEM et vérifiez que tous les lots sont actifs et en cours d’exécution sans problème
1. Ressources système : assurez-vous que l’espace disque et la mémoire disponibles sont suffisants pour gérer les deux référentiels pendant le processus de migration
1. Outil de mise à niveau d’Oak : téléchargez le fichier jar `oak-upgrade` à partir du [référentiel Maven officiel](https://mvnrepository.com/artifact/org.apache.jackrabbit/oak-upgrade). Assurez-vous que la version correspond à la version principale d’Oak utilisée dans AEM 6.5 LTS. L’outil de mise à niveau d’Oak s’exécute sur Oracle® Java™ 11 ou version ultérieure

## Processus de migration {#step-by-step-migration-process}

### Arrêt d’AEM 6.5 et d’AEM 6.5 LTS {#stopping-aem65-and-aem65lts}

Avant de lancer la migration, arrêtez vos instances LTS AEM 6.5 et AEM 6.5. Cela permet de s’assurer que le référentiel est dans un état stable et qu’aucune écriture supplémentaire ne se produit pendant la migration.

### Sauvegarde de l’instance AEM 6.5 {#backing-up-the-aem65-instance}

Effectuez une sauvegarde complète de votre instance AEM 6.5 si ce n’est pas déjà fait.

### Utilisation de l’outil de mise à niveau d’Oak pour la migration de contenu {#using-the-oak-upgrade-tool-for-content-migration}

L&#39;outil Oak-Upgrade est exécuté à partir de la ligne de commande, comme dans l&#39;exemple suivant :

```
java -jar oak-upgrade-*.jar [options] /path/to/source/repository /path/to/destination/repository 
```

Vous trouverez ci-dessous les commandes et options essentielles :

**Principales options**

* `--include-paths` : spécifiez les sous-arborescences à inclure dans la migration. Voir cet exemple pour l’utilisation de la commande :

  ```
  java -jar oak-upgrade-*.jar --include-paths=/content/site /old/repository /new/repository
  ```

* `--exclude-paths` : exclure des chemins spécifiques de la migration. Soyez prudent lorsque vous utilisez cette option : si le chemin d’accès existe sur le système cible, il est supprimé. Voir cet exemple pour l’utilisation de la commande :

  ```
  java -jar oak-upgrade-*.jar --exclude-paths=/content/old_site /old/repository /new/repository 
  ```

* `--copy-binaries` : par défaut, Oak-upgrade migre uniquement les références vers des fichiers binaires, en laissant les fichiers réels dans le magasin d’objets blob/de données d’origine. Par conséquent, le nouveau référentiel repose toujours sur le magasin source pour les fichiers binaires. Pour migrer les fichiers binaires avec le contenu du référentiel, utilisez le paramètre `--copy-binaries` pour copier toutes les données binaires dans le nouveau magasin, comme illustré ci-dessous :

  ```
  java -jar oak-upgrade-*.jar \
  --copy-binaries \
  --src-datastore=/old/repository/datastore \
  --datastore=/new/repository/datastore \
  /old/repository \
  /new/repository 
  ```

### Migration des points de contrôle {#migratiing-checkpoints}

Lors de la migration d’un ancien référentiel SegmentMK (version antérieure à Oak 1.6) vers un nouveau SegmentMK (version d’Oak supérieure ou égale à 1.6), les points de contrôle sont également migrés. Ce processus évite la réindexation lorsque l’Oak est exécutée pour la première fois sur le nouveau référentiel. Toutefois, les points de contrôle ne sont pas migrés dans les cas suivants :

1. Les chemins d’inclusion, d’exclusion ou de fusion personnalisés sont spécifiés ou
1. Le système copie les fichiers binaires par référence. Aucun magasin de données source n’est spécifié et deux points de contrôle différents contiennent un fichier binaire différent sous le même chemin d’accès.

Dans le deuxième cas, Oak-upgrade émet l&#39;avertissement et les ruptures suivants :

```
Checkpoints are not copied, because no external datastore has been specified. This results in the full repository reindexing on the first start. Use --skip-checkpoints to force the migration or see https://jackrabbit.apache.org/oak/docs/migration.html#Checkpoints_migration for more info. 
```

Le moyen le plus simple de résoudre ce problème consiste à spécifier le magasin de données source dans les options de ligne de commande (par exemple, `--src-datastore` ou `--src-s3datastore`).

L’avertissement peut également être ignoré, mais dans ce cas, le référentiel est entièrement réindexé au premier démarrage. Le processus peut être long, en particulier pour les instances volumineuses. Le référentiel n’est pas utilisable tant que le processus de réindexation n’est pas terminé. Utilisez l’option `--skip-checkpoints` pour supprimer l’avertissement.

Vous pouvez également réindexer hors ligne le référentiel avant de démarrer AEM à l’aide de la [réindexation hors ligne](/help/sites-deploying/offline-reindexing.md) pour éviter une réindexation complète au premier démarrage.

Pour plus d’informations sur l’outil de mise à niveau d’Oak et son utilisation avancée, consultez la [documentation officielle](https://jackrabbit.apache.org/oak/docs/migration.html).
