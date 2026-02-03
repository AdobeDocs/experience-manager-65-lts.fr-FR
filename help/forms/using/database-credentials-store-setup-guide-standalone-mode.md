---
title: Guide De Configuration Du Magasin D’Informations D’Identification De Base De Données (Mode Autonome)
description: Recherchez la configuration du magasin d’informations d’identification de base de données pour AEM Forms JEE sur JBoss/Red Hat EAP en mode autonome.
solution: Experience Manager
feature: Deploying
role: User,Admin,Developer
source-git-commit: 259cb81eb9652405dc7270535cbf9deb996ad2ac
workflow-type: tm+mt
source-wordcount: '763'
ht-degree: 2%

---


# Guide De Configuration Du Magasin D’Informations D’Identification De Base De Données (Mode Autonome)

## Vue d’ensemble

Ce guide couvre la **configuration de la banque d’informations d’identification de base de données** pour AEM Forms JEE sur JBoss/Red Hat EAP en **mode autonome**. Cela est nécessaire lors d’une installation manuelle.

**Ce guide couvre les sujets suivants**

- Création du magasin d’informations d’identification de la base de données (`cred-store.p12`)
- Ajout sécurisé d’alias de mot de passe de base de données
- Configuration de JBoss pour utiliser la banque d’informations d’identification

**CRITIQUE :** ces scripts fonctionnent en **MODE HORS LIGNE UNIQUEMENT**. JBoss doit être arrêté avant d’exécuter ces scripts. Les scripts utilisent `embed-server` mode qui nécessite l’arrêt du serveur.

**Remarque :** il ne s’agit **pas** d’un guide d’installation autonome complet. Ce document suppose que :

- JBoss est déjà installé
- Les fichiers de configuration autonomes (`lc_oracle.xml`, `lc_mysql.xml` ou `lc_mssql.xml`) sont déjà configurés
- La base de données est configurée et accessible

Si vous avez besoin d&#39;instructions complètes pour l&#39;installation autonome, reportez-vous au guide d&#39;installation principal.

## Conditions préalables

Avant d’exécuter ces scripts, vérifiez les points suivants :

1. **JBoss DOIT être arrêté**
   - Ces scripts fonctionnent **MODE HORS LIGNE UNIQUEMENT**
   - Les scripts utilisent des `embed-server` qui nécessitent l’arrêt du serveur
   - Si JBoss est en cours d’exécution, les scripts échouent
   - Vérifiez si JBoss est en cours d’exécution :
      - Windows : rechercher `java.exe` processus dans le Gestionnaire des tâches
      - Linux : `ps aux | grep jboss` ou `ps aux | grep java`
   - Arrêtez JBoss en cours d’exécution :
      - Appuyez sur `Ctrl+C` dans le terminal où JBoss est en cours d’exécution.
      - Ou arrêtez le processus manuellement

2. **Le mot de passe de la base de données est prêt**

3. **Vous avez choisi un mot de passe sécurisé pour la banque d’informations d’identification**

4. **Vous savez quel fichier de configuration de base de données vous utilisez :**
   - `lc_oracle.xml` (pour la base de données Oracle)
   - `lc_mysql.xml` (pour la base de données MySQL)
   - `lc_mssql.xml` (pour la base de données SQL Server de Microsoft)

## Étapes de configuration

### Étape 1 : Créer Un Magasin D’Informations D’Identification De Base De Données

Utilisez les scripts fournis pour créer le magasin d’informations d’identification de base de données et ajouter tous les alias de mot de passe requis.

#### Sous Windows :

**Emplacement du script :** `create-elytron-cred-standalone.bat`

`batch cd path\to\script\location create-elytron-cred-standalone.bat`

**Le script vous invitera à saisir :**
1. **Chemin JBOSS_HOME** (par exemple, `C:\Adobe\Adobe_Experience_Manager_Forms\jboss`)
2. **Nom du fichier de configuration** (par exemple, `lc_oracle.xml`, `lc_mysql.xml` ou `lc_mssql.xml`)
3. **Mot de passe de la banque d’informations d’identification** (cela protège le fichier de stockage des clés ; mémorisez ce mot de passe)
4. **Mot de passe de la base de données** (votre mot de passe de base de données réel)

**Fonction du script :**

- Crée un magasin d’informations d’identification à l’adresse : `JBOSS_HOME\standalone\configuration\cred-store.p12`
- Modifie temporairement le fichier de configuration pour activer la création de la banque d’informations d’identification
- Ajoute les alias suivants avec le mot de passe de votre base :
   - `EncryptDBPassword`
   - `EncryptDBPassword_IDP_DS`
   - `EncryptDBPassword_EDC_DS`
   - `EncryptDBPassword_AEM_DS`
- Restaure le fichier de configuration à son état d’origine
- Vérifie que tous les alias ont été ajoutés avec succès.

#### Sous Linux :

**Emplacement du script :** `create-elytron-cred-standalone.sh`

`bash cd /path/to/script/location chmod +x create-elytron-cred-standalone.sh./create-elytron-cred-standalone.sh`

**Le script vous invitera à saisir :**

1. **Chemin JBOSS_HOME** (par exemple, `/opt/Adobe/Adobe_Experience_Manager_Forms/jboss`)
2. **Nom du fichier de configuration** (par exemple, `lc_oracle.xml`, `lc_mysql.xml` ou `lc_mssql.xml`)
3. **Mot de passe de la banque d’informations d’identification** (cela protège le fichier de stockage des clés ; mémorisez ce mot de passe)
4. **Mot de passe de la base de données** (votre mot de passe de base de données réel)

**Fonction du script :**

- Crée un magasin d’informations d’identification à l’adresse : `JBOSS_HOME/standalone/configuration/cred-store.p12`
- Modifie temporairement le fichier de configuration pour activer la création de la banque d’informations d’identification
- Ajoute les alias suivants avec le mot de passe de votre base :
   - `EncryptDBPassword`
   - `EncryptDBPassword_IDP_DS`
   - `EncryptDBPassword_EDC_DS`
   - `EncryptDBPassword_AEM_DS`
- Restaure le fichier de configuration à son état d’origine
- Vérifie que tous les alias ont été ajoutés avec succès.

**Sortie attendue :**

```
=== JBoss Elytron Credential Store Setup ===
Enter JBOSS_HOME path (e.g. /opt/jboss): /opt/Adobe/Adobe_Experience_Manager_Forms/jboss
Enter configuration file name (e.g. lc_oracle.xml): lc_oracle.xml
Enter credential store password: ********
Confirm credential store password: ********
Enter database password: ********
Creating credential store using JBoss CLI...
Adding aliases to credential store...
Verifying credential store aliases...

All 4 aliases verified successfully!
- EncryptDBPassword
- EncryptDBPassword_IDP_DS
- EncryptDBPassword_EDC_DS
- EncryptDBPassword_AEM_DS

Credential store setup completed successfully!
```

### Étape 2 : Mettre à jour le fichier de configuration autonome

Après avoir exécuté le script, vous devez configurer JBoss pour lire le mot de passe de la banque d’informations d’identification au démarrage.

#### Sous Windows :

**Emplacement du fichier :** `<JBOSS_HOME>\bin\standalone.conf.bat`

Exemple : `C:\Adobe\Adobe_Experience_Manager_Forms\jboss\bin\standalone.conf.bat`

Ajoutez ou mettez à jour la ligne suivante :

```batch
set "JAVA_OPTS=%JAVA_OPTS% -DCS_PASS=YourActualPassword123"
```

Remplacez `YourActualPassword123` par le **mot de passe de la banque d’informations d’identification** que vous avez utilisé à l’étape 1.

#### Sous Linux :

**Emplacement du fichier :** `<JBOSS_HOME>/bin/standalone.conf`

Exemple : `/opt/Adobe/Adobe_Experience_Manager_Forms/jboss/bin/standalone.conf`

Ajoutez ou mettez à jour la ligne suivante :

```bash
JAVA_OPTS="$JAVA_OPTS -DCS_PASS=YourActualPassword123"
```

Remplacez `YourActualPassword123` par le **mot de passe de la banque d’informations d’identification** que vous avez utilisé à l’étape 1.

### Étape 3 : démarrer JBoss

Une fois la configuration de la banque d’informations d’identification terminée, démarrez JBoss avec le fichier de configuration approprié.

**Remarque :** pour connaître les commandes et procédures de démarrage exactes permettant de démarrer JBoss en mode autonome, reportez-vous au **guide d’installation principal**. Les commandes de démarrage peuvent varier en fonction de votre configuration et de votre type de base de données (`lc_oracle.xml`, `lc_mysql.xml` ou `lc_mssql.xml`).

## Vérification

### Vérifier les journaux du serveur

**Emplacement du journal :**

- Windows : `<JBOSS_HOME>\standalone\log\server.log`
- Linux : `<JBOSS_HOME>/standalone/log/server.log`

**Rechercher des messages de démarrage réussis :**

```
INFO  [org.jboss.as.server] WFLYSRV0025: JBoss EAP started
INFO  [org.jboss.as.connector.deployers.jdbc] Bound data source [java:/AdobeDataSource]
```

**Aucune erreur liée à :**

- Chargement du magasin d’informations d’identification
- Connexion à la base de données
- Alias manquants

## Résolution des problèmes

### Problème 1 : Magasin D’Informations D’Identification Introuvable

**Message d’erreur :**

```
ERROR Unable to load credential store
```

**Solution :**

1. Vérifiez que le fichier de magasin d’informations d’identification existe :
   - Windows : `dir <JBOSS_HOME>\standalone\configuration\cred-store.p12`
   - Linux : `ls -l <JBOSS_HOME>/standalone/configuration/cred-store.p12`
2. En cas d’absence, réexécutez le script de création de la boutique d’informations d’identification (étape 1)

### Problème 2 : mot de passe incorrect de la banque d’informations d’identification

**Message d’erreur :**

```
ERROR Unable to load credential store - Invalid password
```

**Solution :**
Vérifiez que le mot de passe dans `standalone.conf.bat` / `standalone.conf` (étape 2) correspond au mot de passe utilisé lors de la création de la banque d’informations d’identification (étape 1).

**À Corriger:**
Modifiez le `standalone.conf.bat` / `standalone.conf` et mettez à jour le mot de passe :

```
set "JAVA_OPTS=%JAVA_OPTS% -DCS_PASS=CorrectPassword"
```

### Problème 3 : Échec De La Connexion À La Base De Données

**Message d’erreur :**

```
ERROR Failed to obtain connection
```

**Solution :**

1. Vérifiez que le mot de passe de la base de données utilisé dans la banque d’informations d’identification est correct
2. Vérifiez que la configuration de la source de données référence l’alias correct
3. Vérifier la connectivité réseau au serveur de base de données

**Pour Recréer Le Magasin D’Informations D’Identification, Procédez Comme Suit :**

1. Arrêter JBoss
2. Supprimez le magasin d’informations d’identification existant :
   - Windows : `del <JBOSS_HOME>\standalone\configuration\cred-store.p12`
   - Linux : `rm <JBOSS_HOME>/standalone/configuration/cred-store.p12`
3. Réexécutez le script de création de la banque d’informations d’identification avec le mot de passe correct de la base de données

### Problème 4 : Le Script Échoue Lors De L’Exécution

**Message d’erreur :**

```
ERROR: jboss-cli.bat is not found
```

**Solution :**
Vérifiez que le chemin d’accès JBOSS_HOME est correct et pointe vers le répertoire d’installation de JBoss.

**Message d’erreur :**

```
ERROR: Configuration file not found
```

**Solution :**

1. Vérifiez que le nom du fichier de configuration est correct
2. Vérifiez que le fichier existe dans `JBOSS_HOME\standalone\configuration\` répertoire
3. Vérifiez que vous utilisez le fichier de configuration spécifique à la base de données approprié

## Référence rapide

### Banque D’Informations D’Identification De Base De Données (Mode Autonome)

**Objectif : Stocker** mots de passe de base de données en toute sécurité

**Script:**

- Windows : `create-elytron-cred-standalone.bat`
- Linux : `create-elytron-cred-standalone.sh`

**Crée:**

- Fichier : `standalone/configuration/cred-store.p12`
- Alias : `EncryptDBPassword`, `EncryptDBPassword_IDP_DS`, `EncryptDBPassword_EDC_DS`, `EncryptDBPassword_AEM_DS`

**Configuration :**

- Variable : `-DCS_PASS=password`
- Fichier : `standalone.conf.bat` (Windows) ou `standalone.conf` (Linux)

