---
title: Mise à niveau d’AEM 6.5 LTS sur JBoss EAP 8 (Windows)
description: Ce guide fournit des instructions détaillées pour mettre à niveau une installation LTS Adobe Experience Manager (AEM) 6.5 existante de JBoss EAP 7.4 vers JBoss EAP 8 sous Windows, à l’aide du JDK 21.
source-git-commit: 835530039678bc16a6de87b8d580be91a2026f94
workflow-type: tm+mt
source-wordcount: '1374'
ht-degree: 4%

---

# Mise à niveau d’AEM 6.5 LTS sur JBoss EAP 8 (Windows)

## Vue d’ensemble

Ce guide fournit des instructions détaillées pour mettre à niveau une installation LTS Adobe Experience Manager (AEM) 6.5 existante de JBoss EAP 7.4 vers JBoss EAP 8 sous Windows, à l’aide du JDK 21.

**Chemin de mise à niveau :** JBoss EAP 7.4 (JDK 11) → JBoss EAP 8 (JDK 21)

## Remarques importantes

>[!NOTE]
>
>Il s’agit d’une procédure de mise à niveau critique. Commencez toujours par effectuer cette mise à niveau dans un environnement hors production et conservez des sauvegardes complètes.
>
> **&#x200B; CONDITIONS PRÉALABLES : &#x200B;** une sauvegarde complète du système et un plan de restauration documenté sont obligatoires avant de continuer.

## Conditions requises avant la mise à niveau

### Configuration requise

| Composant | Condition requise |
|-----------|-------------|
| Système d’exploitation | Windows Server 2016 ou version ultérieure (64 bits) |
| Environnement Source | JBoss EAP 7.4 avec AEM 6.5 LTS |
| Environnement cible | JBoss EAP 8.x |
| Java Development Kit | JDK 21 (Oracle ou OpenJDK) |
| Version d’AEM | Pack de services AEM 6.5 (recommandé le plus récent) |
| Espace disque | 50 Go d’espace libre minimum pour le processus de mise à niveau |

### Téléchargements requis

Avant de commencer la mise à niveau, vérifiez les points suivants :

1. **Distribution de JBoss EAP 8.0**\
   Télécharger depuis : [&#128279;](https://developers.redhat.com/products/eap/download)

2. **Programme d’installation du JDK 21**\
   Télécharger Oracle JDK 21 ou OpenJDK 21 pour Windows (64 bits)

3. **Fichier WAR AEM 6.5 LTS**\
   Procurez-vous le dernier pack de services WAR d’AEM 6.5 auprès de la distribution logicielle d’Adobe.

## Étape 1 : créer une sauvegarde complète

>[!IMPORTANT]
>
> Effectuez des sauvegardes complètes avant de continuer.

### Liste de contrôle de sauvegarde

- [ ] Sauvegarde complète du répertoire d’installation de JBoss EAP 7.4 existant
- [ Sauvegarde ] du dossier `crx-repository`
- [ Sauvegarde ] du dossier `crx-quickstart`
- [ ] Exportation de toutes les configurations personnalisées
- [ Sauvegarde de la base de données ] (si vous utilisez une base de données externe)
- [ ] documenter l’état et les configurations actuels du système

### Créer une sauvegarde

```cmd
# Example backup location
C:\AEM-Backups\Pre-Upgrade-<date>

# Copy entire JBoss 7.4 directory
xcopy "C:\jboss-eap-7.4" "C:\AEM-Backups\Pre-Upgrade-<date>\jboss-eap-7.4" /E /I /H
```

**Recommandé :** stockez les sauvegardes sur un lecteur ou un emplacement réseau distinct.

## Étape 2 : installer JBoss EAP 8

### Extraire JBoss EAP 8

1. Extrayez la distribution ZIP EAP 8 JBoss dans votre répertoire d’installation cible :

   ```
   C:\jboss-eap-8.0
   ```

2. Notez que ce chemin d’accès au répertoire est `<JBOSS_HOME>` à utiliser dans ce guide.

### Répliquer la structure du répertoire

Assurez-vous que la nouvelle installation de JBoss EAP 8 présente la même structure de répertoires personnalisée que la configuration précédente de JBoss EAP 7.4, en particulier :

- Répertoires de déploiement personnalisés
- Dossiers de configuration externes
- Emplacements des fichiers journaux
- Tout module ou bibliothèque personnalisé

## Étape 3 : Migrer les données du référentiel

### Copier le référentiel CRX

1. Accédez à votre installation JBoss EAP 7.4 existante :

   ```
   <OLD_JBOSS_HOME>\bin\crx-repository
   ```

2. Copiez l’intégralité du dossier `crx-repository` vers la nouvelle installation de JBoss EAP 8 :

   ```cmd
   xcopy "C:\jboss-eap-7.4\bin\crx-repository" "C:\jboss-eap-8.0\bin\crx-repository" /E /I /H
   ```

**Important :** ce dossier contient votre référentiel de contenu et doit être entièrement transféré.

### Vérifier la copie du référentiel

Après avoir copié, vérifiez que la taille et la structure du référentiel correspondent à la source :

```cmd
dir "C:\jboss-eap-8.0\bin\crx-repository" /s
```

## Étape 4 : Arrêter L’Instance AEM

Avant d’apporter des modifications, assurez-vous qu’AEM est complètement arrêté.

### Arrêter via les services Windows

1. Ouvrez **Services** (Exécution : `services.msc`).
2. Localisation de votre service AEM/JBoss
3. Cliquez avec le bouton droit et sélectionnez **Arrêter**
4. Attendez que le service s’arrête complètement

### Arrêter via la ligne de commande

Si AEM a été démarré manuellement :

1. Accédez à la fenêtre de la console JBoss .
2. Presse `Ctrl+C`
3. Attendre la fin de l’arrêt correct

### Vérifier l&#39;arrêt

Assurez-vous que le processus Java n’est plus en cours d’exécution :

```cmd
tasklist | findstr java
```

## Étape 5 : Nettoyer les fichiers AEM hérités

Supprimez les fichiers obsolètes du répertoire `crx-quickstart` pour garantir une mise à niveau correcte.

>[!CAUTION]
>
> Supprimez uniquement les fichiers et dossiers spécifiques répertoriés ci-dessous. Ne supprimez aucun autre fichier de configuration, code personnalisé ou donnée de référentiel.

### 5.1 Supprimer le dossier de démarrage du Launchpad

**Location:**

```
<JBOSS_HOME>\bin\crx-repository\crx-quickstart\launchpad\startup
```

**Action:**

```cmd
rd /s /q "C:\jboss-eap-8.0\bin\crx-repository\crx-quickstart\launchpad\startup"
```

**Objectif :** ce dossier contient d’anciens lots OSGi qui seront régénérés lors de la mise à niveau.

### 5.2 Suppression du fichier JAR de base

**Location:**

```
<JBOSS_HOME>\bin\crx-repository\crx-quickstart\launchpad\org.apache.sling.launchpad.base.jar
```

**Action:**

```cmd
del "C:\jboss-eap-8.0\bin\crx-repository\crx-quickstart\launchpad\org.apache.sling.launchpad.base.jar"
```

**Objectif :** ce fichier JAR sera remplacé par la version du nouveau fichier WAR.

### 5.3 Supprimer le fichier de commande Bootstrap

**Location:**

```
<JBOSS_HOME>\bin\crx-repository\crx-quickstart\launchpad\felix\bundle0\BootstrapCommandFile_*.txt
```

**Action:**

```cmd
del "C:\jboss-eap-8.0\bin\crx-repository\crx-quickstart\launchpad\felix\bundle0\BootstrapCommandFile_*.txt"
```

**Objectif :** les commandes Bootstrap seront régénérées pour le nouvel environnement.

### 5.4 Suppression du fichier sling.options

**Location:**

```
<JBOSS_HOME>\bin\crx-repository\crx-quickstart\launchpad\felix\sling.options.file
```

**Action:**

```cmd
del "C:\jboss-eap-8.0\bin\crx-repository\crx-quickstart\launchpad\felix\sling.options.file"
```

### 5.5 Suppression du fichier sling_bootstrap.txt

**Location:**

```
<JBOSS_HOME>\bin\crx-repository\crx-quickstart\launchpad\sling_bootstrap.txt
```

**Action:**

```cmd
del "C:\jboss-eap-8.0\bin\crx-repository\crx-quickstart\launchpad\sling_bootstrap.txt"
```

### 5.6 Sauvegarder et supprimer le fichier sling.properties

Ce fichier contient des configurations spécifiques à un environnement qui devront peut-être être fusionnées ultérieurement.

**Location:**

```
<JBOSS_HOME>\bin\crx-repository\crx-quickstart\conf\sling.properties
```

**Action:**

1. **Créer une sauvegarde :**

   ```cmd
   copy "C:\jboss-eap-8.0\bin\crx-repository\crx-quickstart\conf\sling.properties" "C:\AEM-Backups\sling.properties.backup"
   ```

2. **Supprimer l’original :**

   ```cmd
   del "C:\jboss-eap-8.0\bin\crx-repository\crx-quickstart\conf\sling.properties"
   ```

**Objectif :** une nouvelle `sling.properties` sera générée. Passez en revue votre sauvegarde pour restaurer toute configuration personnalisée après la mise à niveau.

## Étape 6 : installation et configuration du JDK 21

### Installation du JDK 21

1. Exécutez le programme d’installation du JDK 21 pour Windows.
2. Installez à un emplacement standard (par exemple, `C:\Program Files\Java\jdk-21`).
3. Terminer l’assistant d’installation

### Configurer les variables d’environnement

#### Définir JAVA_HOME

1. Ouvrez **Propriétés du système** → **Avancé** → **Variables d’environnement**
2. Sous **Variables système**, cliquez sur **Nouveau**
3. Définissez :
   - Nom de la variable : `JAVA_HOME`
   - Valeur de la variable : `C:\Program Files\Java\jdk-21`
4. Cliquez sur **OK**

#### Mettre à jour la variable PATH

1. Dans **Variables système**, sélectionnez `Path` et cliquez sur **Modifier**
2. Ajouter une nouvelle entrée :

   ```
   %JAVA_HOME%\bin
   ```

3. Déplacez cette entrée en haut de la liste pour vous assurer que JDK 21 est prioritaire
4. Cliquez sur **OK** dans toutes les boîtes de dialogue

### Vérifier l’installation Java

1. Ouvrez une **nouvelle** invite de commande (pour charger les variables d’environnement mises à jour).
2. Vérifier la version Java :

   ```cmd
   java -version
   ```

   Sortie attendue :

   ```
   java version "21.0.x"
   Java(TM) SE Runtime Environment (build 21.0.x+...)
   Java HotSpot(TM) 64-Bit Server VM (build 21.0.x+..., mixed mode, sharing)
   ```

3. Vérifiez JAVA_HOME :

   ```cmd
   echo %JAVA_HOME%
   ```

## Étape 7 : configurer les paramètres JVM

Avant de déployer AEM, configurez les paramètres de mémoire JVM appropriés pour l’utilisation en production.

### Modifier le fichier standalone.conf.bat

1. Accédez à :

   ```
   <JBOSS_HOME>\bin
   ```

2. Ouvrez `standalone.conf.bat` dans un éditeur de texte (en tant qu’administrateur).

3. Recherchez ou ajoutez la configuration `JAVA_OPTS` :

   ```batch
   rem # AEM Production JVM Settings
   set "JAVA_OPTS=-Xms4096m -Xmx4096m -XX:MaxMetaspaceSize=768m"
   set "JAVA_OPTS=%JAVA_OPTS% -Djava.net.preferIPv4Stack=true"
   set "JAVA_OPTS=%JAVA_OPTS% -Dfile.encoding=UTF-8"
   set "JAVA_OPTS=%JAVA_OPTS% -server"
   ```

4. Enregistrer et fermer le fichier

**Paramètres recommandés :**

| Paramètre | Valeur recommandée | Description |
|-----------|-------------------|-------------|
| `-Xms` | 4 096 m - 8 192 m | Taille initiale du tas |
| `-Xmx` | 4 096 m - 8 192 m | Taille maximale du tas |
| `-XX:MaxMetaspaceSize` | 768 m - 1 024 m | Limite d’espace des métadonnées |

**Remarque :** ajustez les valeurs en fonction de la mémoire disponible et de la charge de travail requise pour votre serveur.

## Étape 8 : Déployer AEM 6.5 LTS WAR

### Préparer le fichier WAR

Assurez-vous que votre fichier WAR AEM est correctement configuré conformément au guide de déploiement :

- `jboss-deployment-structure.xml` est présent
- `web.xml` comprend des paramètres multipart-config
- WAR est recompressé si des modifications ont été apportées

### Déployer sur JBoss

1. Copiez le fichier WAR LTS d’AEM 6.5 dans le répertoire des déploiements :

   ```cmd
   copy "C:\AEM-Downloads\cq-quickstart-6.5.xx.war" "C:\jboss-eap-8.0\standalone\deployments\cq-quickstart.war"
   ```

**Important :** assurez-vous que le nom du fichier WAR correspond au chemin de contexte de l’URL souhaité.

## Étape 9 : démarrer JBoss EAP 8 avec AEM

### Démarrer le serveur

1. Ouvrez **Invite de commandes** en tant qu’**administrateur**.

2. Accédez au répertoire bin JBoss :

   ```cmd
   cd C:\jboss-eap-8.0\bin
   ```

3. Démarrez JBoss EAP 8 :

   ```cmd
   standalone.bat -b 0.0.0.0 -bmanagement 0.0.0.0
   ```

### Surveiller le démarrage initial

Regardez la sortie de la console pour :

1. **Déploiement WAR :**

   ```
   Deployed "cq-quickstart.war" (runtime-name : "cq-quickstart.war")
   ```

2. **Messages D’Initialisation AEM :**

   ```
   Apache Sling Application Launcher
   Sling Home: crx-repository/crx-quickstart
   ```

3. **Mise à niveau du référentiel (le cas échéant) :**

   ```
   Performing repository migration...
   ```

**Heure de démarrage prévue :** 5 à 15 minutes selon la taille du référentiel et les ressources système.

## Étape 10 : vérification de la réussite de la mise à niveau

### Vérifier le démarrage d’AEM

Surveillez la console JBoss pour obtenir le message de démarrage final :

```
**** AEM started successfully ****
```

### Accès à l’interface d’AEM

1. Ouvrir un navigateur web
2. Accédez à :

   ```
   http://localhost:8080/cq-quickstart
   ```

3. Connectez-vous avec les informations d’identification d’administrateur :
   - Nom d’utilisateur : `admin`.
   - Mot de passe : `admin` (ou votre mot de passe personnalisé)

### Vérification des informations système

1. Accédez à **Outils** → **Opérations** → **Console Web**

   ```
   http://localhost:8080/cq-quickstart/system/console
   ```

2. Cliquez sur **Informations système**

3. Vérifier :

   - **Version JVM :** doit afficher Java 21.
   - **Version de JBoss :** doit afficher EAP 8.x.
   - **Version d’AEM :** doit afficher 6.5.xx

### Vérifier l’intégrité du système

Accédez à **Outils** → **Opérations** → **Diagnostic** pour exécuter les contrôles d’intégrité :

- Statut du lot : tous les lots doivent être « actifs »
- Résolution de la ressource : doit afficher l’état sain
- Performances des requêtes : vérifiez s’il y a une dégradation

## Tâches après la mise à niveau

### Restaurer des configurations personnalisées

1. Vérifier le fichier `sling.properties` sauvegardé
2. Restaurez les modes d’exécution ou les configurations personnalisés dans le nouveau fichier :

   ```
   <JBOSS_HOME>\bin\crx-repository\crx-quickstart\conf\sling.properties
   ```

3. Redémarrez AEM si les configurations ont été modifiées.

### Mettre à jour les agents de réplication

1. Accédez à **Outils** → **Déploiement** → **Réplication** → **Agents sur l’auteur**
2. Examen et test de tous les agents de réplication
3. Mettez à jour toutes les références codées en dur vers les anciens chemins d’accès au serveur

### Tester la fonctionnalité essentielle

- [ ] Création et publication de contenu
- [ Chargement et traitement des ressources ]
- [ ] l’exécution du workflow
- [ ] l’authentification de l’utilisateur
- [ Points d’entrée de l’intégration ]
- [ ] Composants et modèles personnalisés

### Optimisation des performances

1. Vérifiez et effacez tous les caches temporaires
2. Surveillance des performances du système lors de l’utilisation initiale
3. Ajustez les paramètres JVM si nécessaire en fonction des modèles d’utilisation réels.

## Résolution des problèmes

### Problèmes courants

| Problème | Cause possible | Solution |
|-------|---------------|----------|
| Échec du démarrage d’AEM | Version Java incorrecte | Vérifier que `JAVA_HOME` pointe vers le JDK 21 |
| Erreurs de corruption du référentiel | Copie de référentiel incomplète | Restaurer à partir du référentiel de sauvegarde et de recopie |
| ErreurMémoire insuffisante | Mémoire de tas insuffisante | Augmentation des `-Xmx` dans les `standalone.conf.bat` |
| Lots dont l’état est défini sur « Installé » | Dépendances manquantes | Vérifier les dépendances de bundle dans la console web |
| Port 8080 déjà utilisé | Un autre service utilisant le port | Arrêt du service en conflit ou modification du port JBoss |

### Emplacements des fichiers journaux

- **Journal du serveur JBoss :**\
  `<JBOSS_HOME>\standalone\log\server.log`

- **Journal Des Erreurs AEM :**\
  `<JBOSS_HOME>\bin\crx-repository\crx-quickstart\logs\error.log`

- **Journal Des Accès AEM :**\
  `<JBOSS_HOME>\bin\crx-repository\crx-quickstart\logs\access.log`

### Procédure de restauration

Si la mise à niveau échoue et ne peut pas être résolue :

1. Arrêter JBoss EAP 8
2. Restaurez la sauvegarde complète de JBoss EAP 7.4
3. Restaurer le dossier `crx-repository`
4. Vérifiez que `JAVA_HOME` pointe vers le JDK 11 (en cas de restauration).
5. Démarrer l’environnement précédent

## Bonnes pratiques

### Avant le déploiement en production

- [ ] Tester le processus de mise à niveau complet dans un environnement de développement
- [ Test ] dans un environnement d’évaluation avec des données de type production
- [ ] documenter toutes les configurations et intégrations personnalisées
- [ ] Créer un plan de restauration détaillé
- [ ] Planifier la mise à niveau pendant la période de maintenance
- [ ] Informer toutes les parties prenantes du temps d’arrêt prévu

### Après la mise à niveau réussie

- [ Journaux système de ] Monitor pendant 48 à 72 heures
- [ ] Effectuer des tests de chargement pour identifier les problèmes de performances
- [ ] Mettre à jour la documentation du système
- [ ] Former l&#39;équipe sur toutes les différences de JBoss EAP 8
- [ ] Archiver toute la documentation de mise à niveau et les sauvegardes

## Documentation connexe

- [Guide de migration de JBoss EAP 8](https://access.redhat.com/documentation/en-us/red_hat_jboss_enterprise_application_platform/8.0/html/migration_guide/)
- Guide de mise à niveau vers Adobe Experience Manager 6.5 [&#128279;](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/upgrading/upgrade.html?lang=fr)
- [Installation des packs de services &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-65/release-notes/service-pack/sp-release-notes.html?lang=fr)

## Informations sur le document

| Champ | Valeur |
|-------|-------|
| Version du document | 1.0 |
| Date de la dernière mise à jour | Février 2026 |
| Version d’AEM | 6.5 LTS |
| Plateforme Source | JBoss EAP 7.4/JDK 11 |
| Plateforme cible | JBoss EAP 8.x / JDK 21 |
| Système d’exploitation | Windows Server |

**Mentions légales :** Adobe, Adobe Experience Manager et AEM sont des marques déposées d’Adobe Inc. JBoss et Red Hat sont des marques déposées de Red Hat, Inc.
