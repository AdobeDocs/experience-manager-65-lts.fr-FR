---
title: Éléments de stockage dans AEM 6.5 LTS
description: Découvrez les implémentations de stockage de nœud disponibles dans AEM 6.5 LTS et comment gérer le référentiel.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: platform
content-type: reference
legacypath: /content/docs/en/aem/6-0/deploy/upgrade/microkernels-in-aem-6-0
solution: Experience Manager, Experience Manager Sites
feature: Deploying
role: Admin
exl-id: e51842b5-fa91-42d2-a490-5a7e867dada7
source-git-commit: 0e60c406a9cf1e5fd13ddc09fd85d2a2f8a410f6
workflow-type: tm+mt
source-wordcount: '712'
ht-degree: 75%

---

# Éléments de stockage dans AEM 6.5 LTS{#storage-elements-in-aem}

Cet article traite des sujets suivants :

* [Présentation du stockage dans AEM 6.5 LTS](/help/sites-deploying/storage-elements-in-aem-6.md#overview-of-storage-in-aem)
* [Maintenance du référentiel](/help/sites-deploying/storage-elements-in-aem-6.md#maintaining-the-repository)

## Présentation du stockage dans AEM 6.5 LTS {#overview-of-storage-in-aem}

Les innovations au niveau du référentiel constituent l’une des modifications les plus importantes du LTS d’AEM 6.5.

Actuellement, il existe deux implémentations de stockage de nœud disponibles dans AEM 6.5 LTS : le stockage Tar et le stockage MongoDB.

### Stockage Tar {#tar-storage}

#### Exécution d’une toute nouvelle instance AEM installée avec un stockage tar {#running-a-freshly-installed-aem-instance-with-tar-storage}

Par défaut, le LTS d’AEM 6.5 utilise le stockage Tar pour stocker les nœuds et les fichiers binaires à l’aide des options de configuration par défaut. Vous pouvez configurer manuellement ses paramètres de stockage en procédant comme suit :

1. Téléchargez le fichier jar de démarrage rapide LTS d’AEM 6.5 et placez-le dans un nouveau dossier.
1. Décompressez AEM comme suit :

   `java -jar <aem-65-lts>.jar -unpack`

1. Créez un dossier nommé `crx-quickstart\install` dans le répertoire d’installation.

1. Créez un fichier nommé `org.apache.jackrabbit.oak.segment.SegmentNodeStoreService.config` dans le dossier nouvellement créé.

1. Modifiez le fichier et définissez les options de configuration. Les options suivantes sont disponibles pour le magasin de nœuds de segment, qui est la base de l’implémentation du stockage Tar d’AEM :

   * `repository.home` : chemin d’accès à la page d’accueil du référentiel dans laquelle sont stockées diverses données du référentiel. Par défaut, les fichiers de segment doivent être stockés dans le répertoire crx-quickstart/segmentstore.
   * `tarmk.size` : taille maximale d’un segment en Mo. La valeur par défaut est 256 Mo.

1. Démarrez AEM.

### Stockage Mongo {#mongo-storage}

>[!NOTE]
>
>La version minimale prise en charge de Mongo est Mongo 6.

#### Exécution d’une instance AEM nouvellement installée avec le stockage Mongo {#running-a-freshly-installed-aem-instance-with-mongo-storage}

Le LTS AEM 6.5 peut être configuré pour s’exécuter avec le stockage MongoDB en suivant la procédure ci-dessous :

1. Téléchargez le fichier jar de démarrage rapide LTS d’AEM 6.5 et placez-le dans un nouveau dossier.
1. Décompressez AEM en exécutant la commande suivante :

   `java -jar <aem-65-lts>.jar -unpack`

1. Assurez-vous que MongoDB est installé et qu’une instance de `mongod` est en cours d’exécution. Pour plus d’informations, reportez-vous à la section [Configuration de MongoDB](https://docs.mongodb.org/manual/installation/).
1. Créez un dossier nommé `crx-quickstart\install` dans le répertoire d’installation.
1. Configurez le magasin de nœuds en créant un fichier de configuration avec le nom de la configuration que vous souhaitez utiliser dans le répertoire `crx-quickstart\install`.

   Le magasin de nœuds de document (qui sert de base à l’implémentation du stockage MongoDB d’AEM) utilise un fichier nommé `org.apache.jackrabbit.oak.plugins.document.DocumentNodeStoreService.config`.

1. Modifiez le fichier et définissez vos options de configuration. Les options suivantes sont disponibles :

   * `mongouri` : [MongoURI](https://docs.mongodb.org/manual/reference/connection-string/) requis pour se connecter à la base de données Mongo. La valeur par défaut est de `mongodb://localhost:27017`.
   * `db` : nom de la base de données Mongo. Par défaut, les nouvelles installations LTS d’AEM 6.5 utilisent **aem-author** comme nom de la base de données.
   * `cache` : taille du cache en Mo. Cette taille de cache est répartie entre les différents caches utilisés dans DocumentNodeStore. La valeur par défaut est 256.
   * `changesSize` : taille en Mo de la collection limitée utilisée dans Mongo pour la mise en cache de la sortie diff. La valeur par défaut est 256.
   * `customBlobStore` : valeur booléenne indiquant qu’un magasin de données personnalisé est utilisé. La valeur par défaut est false.

1. Créez un fichier de configuration avec le PID du magasin de données que vous souhaitez utiliser et modifiez le fichier pour définir les options de configuration. Pour plus d’informations, consultez [Configuration des magasins de nœuds et des entrepôts de données](/help/sites-deploying/data-store-config.md).

1. Démarrez le jar LTS AEM 6.5 avec un serveur principal de stockage MongoDB en exécutant :

   ```shell
   java -jar <aem-65-lts>.jar -r crx3,crx3mongo
   ```

   Où le mode d’exécution principal est **`-r`**, l’exemple commence avec la prise en charge de MongoDB.

#### Désactiver THP (Transparent Huge Pages) {#disabling-transparent-huge-pages}

Red Hat® Linux® utilise un algorithme de gestion de la mémoire appelé Transparent Huge Pages (THP). Tandis qu’AEM effectue des lectures et des écritures affinées, THP est optimisé pour des opérations plus volumineuses. Pour cette raison, il est recommandé de désactiver THP sur les stockages Tar et Mongo. Pour désactiver l’algorithme, procédez comme suit :

1. Ouvrez le fichier `/etc/grub.conf` dans l’éditeur de texte de votre choix.
1. Ajoutez la ligne suivante au fichier **grub.conf** :

   ```
   transparent_hugepage=never
   ```

1. Enfin, vérifiez si le paramètre a été appliqué en exécutant :

   ```
   cat /sys/kernel/mm/redhat_transparent_hugepage/enabled
   ```

   Si THP est désactivé, la sortie de la commande ci-dessus doit être :

   ```
   always madvise [never]
   ```

>[!NOTE]
>
>Reportez-vous aux ressources suivantes :
>
>* Pour plus d’informations à propos de Transparent Huge Pages sur Red Hat® Linux®, consultez l’article suivant du portail clientèle Red Hat® : [Comment utiliser, surveiller et désactiver les paramètres Transparent Huge Pages dans Red Hat Enterprise Linux 6, 7 et 8 ?](https://access.redhat.com/solutions/46111)
>* Pour obtenir des conseils sur l’optimisation sous Linux®, voir [Optimisation des performances](/help/sites-deploying/configuring-performance.md).
>

## Maintenance du référentiel {#maintaining-the-repository}

Chaque mise à jour du référentiel crée une révision du contenu. Par conséquent, avec chaque mise à jour, la taille du référentiel augmente. Pour éviter une croissance incontrôlée du référentiel, les anciennes révisions doivent être nettoyées pour libérer des ressources de disque. Cette fonctionnalité de maintenance est appelée Nettoyage des révisions. Le mécanisme de nettoyage des révisions permet de récupérer de l’espace disque en supprimant les données obsolètes du référentiel. Pour de plus amples informations sur le nettoyage des révisions, consultez la [page sur le nettoyage des révisions](/help/sites-deploying/revision-cleanup.md).
