---
title: Installation d’un serveur d’applications
description: Découvrez comment installer Adobe Experience Manager avec un serveur d’applications.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: deploying
solution: Experience Manager, Experience Manager Sites
feature: Deploying
role: Admin
exl-id: 09d54b52-485a-453c-a2d0-535adead9e6c
source-git-commit: b9b5492b1bf5f717dec6a48ffbe808bf75cbce6a
workflow-type: tm+mt
source-wordcount: '843'
ht-degree: 42%

---

# Installation d’un serveur d’applications{#application-server-install}

>[!NOTE]
>
>`JAR` et `WAR` sont les types de fichiers dans lesquels Adobe Experience Manager (AEM) est publié. Ces formats font l’objet d’une assurance qualité afin d’offrir les niveaux de prise en charge qu’Adobe s’est engagé à fournir.
>

Cette section vous explique comment installer Adobe Experience Manager (AEM) avec un serveur d’applications. Consultez la section [Plateformes prises en charge](/help/sites-deploying/technical-requirements.md#servlet-engines-application-servers) pour en savoir plus sur les niveaux de prise en charge relatifs aux différents serveurs d’applications.

La procédure d’installation est décrite pour les serveurs d’applications suivants :

* [WebSphere](#websphere)
* [Tomcat 10.0.x/10.1.x](#tomcat)

Pour plus d’informations sur l’installation d’applications Web, sur les configurations serveur et sur le démarrage et l’arrêt du serveur, consultez la documentation du serveur d’applications approprié.

<!-- >[!NOTE]
>
>If you are using Dynamic Media in a WAR deployment, see [Dynamic Media documentation](/help/assets/config-dynamic.md#enabling-dynamic-media). -->

## Description générale {#general-description}

### Comportement par défaut lors de l’installation d’AEM sur un serveur d’applications {#default-behaviour-when-installing-aem-in-an-application-server}

AEM est fourni sous la forme d’un fichier WAR à déployer.

Lors du déploiement, les événements suivants se produisent par défaut :

* Le mode d’exécution est `author`
* L’instance (référentiel, environnement Felix OSGI, lots, etc.) est installée dans est `${user.dir}/crx-quickstart`, où `${user.dir}` est le répertoire de travail actuel. Ce chemin d’accès à crx-quickstart est appelé `sling.home`

* La racine de contexte est le nom du fichier war. Par exemple, `aem-65-lts`.

#### Configuration {#configuration}

Vous pouvez modifier le comportement par défaut de la manière suivante :

* Mode d’exécution : configurez le paramètre `sling.run.modes` dans le fichier `WEB-INF/web.xml` du fichier war AEM avant le déploiement.

* sling.home : configurez le paramètre `sling.home` dans le fichier `WEB-INF/web.xml` du fichier war AEM avant le déploiement

* Racine de contexte : renommez le fichier war AEM.

#### Installation de l’instance de publication {#publish-installation}

Pour déployer une instance de publication, vous devez définir le mode d’exécution sur « publication » :

* Décompressez le `WEB-INF/web.xml` à partir du fichier war AEM.
* Modifier `sling.run.modes` paramètre en publication
* Recompressez `web.xml` fichier dans le fichier war AEM
* Déployez le fichier war AEM.

#### Vérification de l’installation {#installation-check}

Pour vérifier si tout est installé, vous pouvez :

* parcourir le fichier `error.log` jusqu’à la fin pour vous assurer que tout le contenu est installé ;
* vérifier que tous les ensembles sont installés sous `/system/console`.

#### Deux instances sur le même serveur d’applications {#two-instances-on-the-same-application-server}

À des fins de démonstration, il peut être approprié d’installer les instances de création et de publication dans un seul serveur d’applications. Pour ce faire, vous devez :

1. Modifiez `sling.home` variable et `sling.run.modes` variables de l’instance de publication
1. Décompressez le fichier `WEB-INF/web.xml` à partir du fichier war AEM.
1. Définissez le paramètre `sling.home` sur un autre chemin (les chemins absolus et relatifs sont possibles)
1. Remplacez `sling.run.modes` par `publish` pour l’instance de publication
1. Recompressez le fichier `web.xml`
1. Renommez les fichiers WAR afin qu’ils portent des noms différents. Par exemple, renommez l’un en `aemauthor.war` et l’autre en `aempublish.war`
1. Utilisez des paramètres de mémoire plus élevés. Par exemple, les instances AEM par défaut utilisent `-Xmx3072m`.
1. Déployer les deux applications web
1. Après le déploiement, arrêtez les deux applications web.
1. Dans les instances de création et de publication, assurez-vous que dans le fichier `sling.properties`, la `felix.service.urlhandlers` de propriété est définie sur `false`. (Par défaut, il est défini sur `true`).
1. Redémarrez les deux applications web.

## Procédures d’installation des serveurs d’applications {#application-servers-installation-procedures}

### WebSphere® 24.0.0.7 {#websphere}

Avant le déploiement, veuillez lire la [ Description générale ](#general-description) ci-dessus.

**Préparation du serveur**

* Laissez les en-têtes d’authentification de base tels quels :

   * Pour permettre à AEM d’authentifier un utilisateur, désactivez la sécurité administrative globale du serveur WebSphere®. Pour ce faire, accédez à **Sécurité > Sécurité globale** et décochez la case **Activer la sécurité administrative**, enregistrez et redémarrez le serveur.

* Set `"JAVA_OPTS= -Xmx2048m"`
* Si vous souhaitez installer AEM à l’aide de la racine de contexte = /, vous devez modifier la racine de contexte de l’application web par défaut existante.

**Déploiement de l’application web AEM**

* Télécharger le fichier war d’AEM
* Effectuez vos configurations dans le fichier `web.xml` si nécessaire. Pour plus d’informations, voir [Description générale](#general-description) ci-dessus.

   * Décompresser le fichier `WEB-INF/web.xml`
   * Remplacez le paramètre `sling.run.modes` par `publish`
   * Supprimez les commentaires du paramètre de `sling.home` initial et définissez ce chemin selon vos besoins
   * Recompressez le fichier `web.xml`.

* Déployer le fichier war AEM

   * Choisissez une racine de contexte. Si vous souhaitez définir les modes d’exécution Sling, vous devez sélectionner les étapes détaillées de l’assistant de déploiement, puis le spécifier à l’étape 6 de l’assistant.

* Démarrer l’application web AEM

#### Tomcat 10.0.x/10.1.x {#tomcat}

Avant de procéder à un déploiement, lisez la [Description générale](#general-description) ci-dessus.

* **Préparation du serveur Tomcat**

   * Augmentez les paramètres mémoire de la machine virtuelle :

      * Dans `bin/catalina.bat` (soit `catalina.sh` sous UNIX®), ajoutez le paramètre suivant :

        ```
        set "JAVA_OPTS= -Xmx2048m`
        ```

   * Tomcat n’active pas l’accès administrateur ou responsable lors de l’installation. Vous devez donc modifier manuellement le fichier `tomcat-users.xml` pour autoriser l’accès pour ces comptes :

      * Modifiez le fichier `tomcat-users.xml` afin d’inclure l’accès pour l’administrateur et le gestionnaire. La configuration doit être semblable à l’exemple suivant :

        ```xml
        <?xml version='1.0' encoding='utf-8'?>
        <tomcat-users>
        role rolename="manager"/>
        role rolename="tomcat"/>
        <role rolename="admin"/>
        <role rolename="role1"/>
        <role rolename="manager-gui"/>
        <user username="both" password="tomcat" roles="tomcat,role1"/>
        <user username="tomcat" password="tomcat" roles="tomcat"/>
        <user username="admin" password="admin" roles="admin,manager-gui"/>
        <user username="role1" password="tomcat" roles="role1"/>
        </tomcat-users>
        ```

   * Si vous souhaitez déployer AEM avec la racine de contexte « / », vous devez modifier la racine de contexte de l’application web ROOT existante :

      * Arrêtez et annulez le déploiement de l’application web ROOT.
      * Renommez le dossier `ROOT.war` dans le dossier webapps de Tomcat.
      * Redémarrer l’application web.

   * Si vous installez l’application web AEM à l’aide de la fonction manager-gui, vous devez augmenter la taille maximale d’un fichier chargé, car la taille par défaut autorise uniquement le chargement de 50 Mo. Pour ce faire, ouvrez le `web.xml` de l’application Web du gestionnaire :

     `webapps/manager/WEB-INF/web.xml`

     et augmenter les `max-file-size` et les `max-request-size` à au moins 500MB. Consultez le `multipart-config` suivant dans un exemple `web.xml` fichier ci-dessous :

     ```xml
     <multipart-config>
     <!-- 500MB max -->
     <max-file-size>524288000</max-file-size>
     <max-request-size>524288000</max-request-size>
     <file-size-threshold>0</file-size-threshold>
     </multipart-config>
     ```

* **Déployer l’application web AEM**

   * Téléchargez le fichier war d’AEM.
   * Effectuez vos configurations dans le fichier `web.xml` si nécessaire.

      * Décompresser le fichier `WEB-INF/web.xml`
      * Remplacez le paramètre `sling.run.modes` par `publish`
      * Supprimez les commentaires du paramètre de `sling.home` initial et définissez ce chemin d’accès selon vos besoins
      * Recompressez le fichier `web.xml`.

   * Renommez le fichier war AEM en `ROOT.war` si vous souhaitez le déployer en tant qu’application web racine. Renommez-le en `aemauthor.war` si vous souhaitez l’`aemauthor` en tant que racine contextuelle.
   * Copiez-le dans le dossier webapps de Tomcat.
   * Patientez jusqu’à ce qu’AEM soit installé.
