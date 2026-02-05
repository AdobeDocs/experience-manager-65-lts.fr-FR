---
title: Configuration de la banque d’informations d’identification de base de données (basée sur Elytron)
description: JBoss EAP 8 prend en charge les magasins d’informations d’identification Elytron pour la gestion sécurisée des mots de passe de base de données dans AEM Forms pour la configuration du mode domaine.
solution: Experience Manager
feature: Deploying
role: User,Admin,Developer
source-git-commit: f093f39fb535209297940cff13a99c7631812152
workflow-type: tm+mt
source-wordcount: '379'
ht-degree: 2%

---


# Configuration de la banque d’informations d’identification de base de données (basée sur Elytron)

## Configuration Du Magasin D’Informations D’Identification De Base De Données À L’Aide D’Elytron

JBoss EAP 8 utilise **Elytron credential stores** pour gérer en toute sécurité les mots de passe de base de données pour les déploiements AEM Forms. Adobe fournit des **scripts automatisés** pour simplifier la création et la configuration de la banque d’informations d’identification basée sur Elytron en mode domaine.


Cette configuration doit être effectuée **avant de démarrer le contrôleur de domaine JBoss**.

### Conditions préalables

* Le serveur **JBoss doit être complètement arrêté** avant d’exécuter le script de création de la banque d’informations d’identification.
* La création de la banque d’informations d’identification doit être effectuée en **mode hors ligne uniquement**.

Pour arrêter JBoss en cours d’exécution :

* **Windows**

  ```
  <JBOSS_HOME>\bin\jboss-cli.bat --connect command=:shutdown
  ```

* **Linux/UNIX**

  ```
  <JBOSS_HOME>/bin/jboss-cli.sh --connect command=:shutdown
  ```

### Scripts de téléchargement

Téléchargez le script approprié en fonction de votre système d’exploitation :

| Nom du script | Système d’exploitation |
| -------------------------------- | ---------------- |
| `create-elytron-cred-domain.bat` | Windows |
| `create-elytron-cred-domain.sh` | Linux/UNIX |

Pour Linux, rendez le script exécutable :

```
chmod +x create-elytron-cred-domain.sh
```

### Étapes de configuration

#### Étape 1 : télécharger et placer le script

Téléchargez le script approprié et placez-le dans le répertoire suivant :

```
<JBOSS_HOME>/bin
```

#### Étape 2 : exécuter le script

* **Windows**

  ```
  cd <JBOSS_HOME>\bin
  create-elytron-cred-domain.bat
  ```

* **Linux/UNIX**

  ```
  cd <JBOSS_HOME>/bin
  ./create-elytron-cred-domain.sh
  ```

#### Étape 3 : fournir les informations requises

Lors de l’exécution, le script demande les entrées suivantes :

1. **Chemin JBOSS_HOME**
Saisissez le chemin d’accès complet au répertoire d’installation de JBoss.

2. **Nom du fichier de configuration de la base de données**
Saisissez l’une des valeurs suivantes en fonction de votre base de données :

   * `domain_oracle.xml`
   * `domain_mysql.xml`
   * `domain_mssql.xml`

3. **Mot de passe de la banque d’informations d’identification**
Saisissez un mot de passe sécurisé pour protéger la banque d’informations d’identification.

   > Ce mot de passe est masqué lors de la saisie et doit être mémorisé pour les étapes ultérieures.

4. **Mot de passe de la base de données**
Entrez le mot de passe réel de connexion à la base de données.

#### Étape 4 : exécution et validation de script

Le script effectue automatiquement les actions suivantes :

* Crée des `cred-store.p12` dans :

  ```
  <JBOSS_HOME>/domain/configuration/
  ```

* Crée les alias d’informations d’identification suivants :

   * `EncryptDBPassword`
   * `EncryptDBPassword_IDP_DS`
   * `EncryptDBPassword_EDC_DS`
   * `EncryptDBPassword_AEM_DS`
* Vérifie que tous les alias ont bien été ajoutés

Une exécution réussie confirme la création de la banque d’informations d’identification et la vérification de l’alias.

#### Étape 5 : configurer les options JVM

Mettez à jour la configuration de démarrage du domaine JBoss pour fournir le mot de passe de la boutique d’informations d’identification.

* **Linux**
Modifier :

  ```
  <JBOSS_HOME>/bin/domain.conf
  ```

  Ajouter :

  ```
  JAVA_OPTS="$JAVA_OPTS -DCS_PASS=YourCredStorePassword"
  ```

* **Windows**
Modifier :

  ```
  <JBOSS_HOME>/bin/domain.conf.bat
  ```

  Ajouter :

  ```
  set "JAVA_OPTS=%JAVA_OPTS% -DCS_PASS=YourCredStorePassword"
  ```

Remplacez `YourCredStorePassword` par le mot de passe saisi lors de la création de la boutique d’informations d’identification.

Les fichiers de configuration de domaine référencent cette valeur à l’aide de la variable `${CS_PASS}` .


#### Étape 6 : vérification de la configuration du domaine

Ouvrez le fichier de configuration du domaine de la base de données :

```
<JBOSS_HOME>/domain/configuration/<domain_*.xml>
```

Vérifiez que les sources de données font référence au magasin d’informations d’identification Elytron :

```xml
<security>
    <user-name>your_database_username</user-name>
    <credential-reference store="db-creds" alias="EncryptDBPassword_IDP_DS"/>
</security>
```

Chaque source de données utilise un alias spécifique :

* **IDP_DS:** `EncryptDBPassword_IDP_DS`
* **EDC_DS:** `EncryptDBPassword_EDC_DS`
* **AEM_DS:** `EncryptDBPassword_AEM_DS`
* **DefaultDS / ExampleDS:** `EncryptDBPassword`

Tous les alias font référence au même mot de passe de base de données stocké dans la banque d’informations d’identification.

>[!NOTE]
>
>* Configurez le magasin d’informations d’identification uniquement sur le nœud principal.
>* Les nœuds Secondaires utilisent automatiquement la configuration de domaine synchronisée à partir du nœud principal.
