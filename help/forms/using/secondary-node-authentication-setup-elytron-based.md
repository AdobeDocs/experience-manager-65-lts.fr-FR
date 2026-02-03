---
title: Configuration de l’authentification de nœud Secondaire (basée sur Elytron)
description: JBoss EAP 8 utilise Elytron pour permettre une communication et un enregistrement sécurisés des nœuds secondaires avec le contrôleur de domaine principal.
solution: Experience Manager
feature: Deploying
role: User,Admin,Developer
source-git-commit: 259cb81eb9652405dc7270535cbf9deb996ad2ac
workflow-type: tm+mt
source-wordcount: '471'
ht-degree: 5%

---


# Configuration de l’authentification de nœud Secondaire (basée sur Elytron)

## Configurer L’Authentification De Nœud Secondaire À L’Aide D’Elytron

JBoss EAP 8 utilise **Elytron** pour authentifier la communication entre **nœuds principaux et secondaires** dans un déploiement en cluster. Cette configuration garantit l’enregistrement et la communication sécurisés des nœuds secondaires avec le contrôleur de domaine principal.

Deux options de configuration sont disponibles en fonction des exigences en matière d’environnement et de sécurité.

## Conditions préalables

* Un utilisateur **gestion nommé`secondary`** doit être créé sur le **nœud principal**.
* Effectuez cette configuration **uniquement sur le(s) nœud(s) secondaire(s)**.
* Répétez la configuration pour **chaque nœud secondaire** dans le cluster.
* **JBoss doit être complètement arrêté** sur les nœuds principaux et secondaires.
* Toutes les opérations de la banque d’informations d’identification doivent être effectuées en **mode hors ligne**.

Pour arrêter JBoss en cours d’exécution :

* **Windows**

  ```
  <JBOSS_HOME>\bin\jboss-cli.bat --connect command=:shutdown
  ```

* **Linux/UNIX**

  ```
  <JBOSS_HOME>/bin/jboss-cli.sh --connect command=:shutdown
  ```

## Choisir une option de configuration

* **Option 1 : Configuration Rapide À L’Aide Du Magasin D’Informations D’Identification Par Défaut**
Recommandé pour les environnements inférieurs et les tests.

* **Option 2 : configuration personnalisée de la boutique d’informations d’identification**
Recommandé pour les environnements de production et sécurisés.

## Option 1 : Configuration Rapide À L’Aide Du Magasin D’Informations D’Identification Par Défaut

**Idéal pour** scénarios de développement, de test et de configuration rapide.

### Vue d’ensemble

* Un fichier de magasin d’informations d’identification par défaut (`cs_secondary_hc.p12`) est préconfiguré.
* Le mot de passe de la banque d’informations d’identification par défaut est déjà défini dans `domain.conf`.
* Seul l’alias du mot de passe d’authentification doit être ajouté.

### Étapes de configuration

#### Étape 1 : vérification du magasin d’informations d’identification par défaut

Vérifiez que le fichier de magasin d’informations d’identification par défaut existe :

* **Windows**

  ```
  <JBOSS_HOME>\domain\configuration\cs_secondary_hc.p12
  ```

* **Linux**

  ```
  <JBOSS_HOME>/domain/configuration/cs_secondary_hc.p12
  ```

Si le fichier n’existe pas, utilisez **Option 2**.

#### Étape 2 : Ajouter Un Alias De Mot De Passe D’Authentification

Exécutez la commande suivante à partir de `<JBOSS_HOME>/bin` :

* **Windows**

  ```
  elytron-tool.bat credential-store --location "../domain/configuration/cs_secondary_hc.p12" --password "password" --type KeyStoreCredentialStore --properties "keyStoreType=PKCS12" --add "secondary_hc_auth" --secret "ActualSecondaryUserPassword"
  ```

* **Linux**

  ```
  ./elytron-tool.sh credential-store --location "../domain/configuration/cs_secondary_hc.p12" --password "password" --type KeyStoreCredentialStore --properties "keyStoreType=PKCS12" --add "secondary_hc_auth" --secret "ActualSecondaryUserPassword"
  ```

> La valeur du secret doit correspondre au mot de passe utilisé lors de la création de l’utilisateur `secondary` sur le nœud principal.

#### Étape 3 : vérification de la configuration domain.conf

Vérifiez que l’entrée suivante existe déjà (aucune modification requise) :

* **Windows**

  ```
  set "JAVA_OPTS=%JAVA_OPTS% -DSec_Auth_PASS=password"
  ```

* **Linux**

  ```
  JAVA_OPTS="$JAVA_OPTS -DSec_Auth_PASS=password"
  ```

#### Étape 4 : démarrer les nœuds

1. Démarrez le **nœud principal** et attendez qu’il soit entièrement initialisé.
2. Démarrez le **nœud secondaire**.

### Vérification

Vérifiez les journaux :

* **Nœud De Principal**

  ```
  <JBOSS_HOME>/domain/log/host-controller.log
  ```

  ```
  Registered remote secondary host "secondary"
  ```

* **Nœud Secondaire**

  ```
  Connected to primary host controller
  ```

## Option 2 : Configuration De La Boutique D’Informations D’Identification Personnalisées (Production)

**Idéal pour :** environnements de production nécessitant une sécurité renforcée.

### Étapes de configuration

#### Étape 1 : Supprimer Le Magasin D’Informations D’Identification Par Défaut (Le Cas Échéant)

Si le magasin d’informations d’identification par défaut existe, renommez-le :

* **Windows**

  ```
  rename cs_secondary_hc.p12 cs_secondary_hc.p12.bak
  ```

* **Linux**

  ```
  mv cs_secondary_hc.p12 cs_secondary_hc.p12.bak
  ```

#### Étape 2 : Créer un magasin d’informations d’identification personnalisé

Depuis le `<JBOSS_HOME>/bin` :

* **Windows**

  ```
  elytron-tool.bat credential-store --create --location "../domain/configuration/cs_secondary_hc.p12" --password "YourCustomPassword" --type KeyStoreCredentialStore --properties "keyStoreType=PKCS12"
  ```

* **Linux**

  ```
  ./elytron-tool.sh credential-store --create --location "../domain/configuration/cs_secondary_hc.p12" --password "YourCustomPassword" --type KeyStoreCredentialStore --properties "keyStoreType=PKCS12"
  ```

#### Étape 3 : Ajouter Un Alias De Mot De Passe D’Authentification

* **Windows**

  ```
  elytron-tool.bat credential-store --location "../domain/configuration/cs_secondary_hc.p12" --password "YourCustomPassword" --type KeyStoreCredentialStore --properties "keyStoreType=PKCS12" --add "secondary_hc_auth" --secret "ActualSecondaryUserPassword"
  ```

* **Linux**

  ```
  ./elytron-tool.sh credential-store --location "../domain/configuration/cs_secondary_hc.p12" --password "YourCustomPassword" --type KeyStoreCredentialStore --properties "keyStoreType=PKCS12" --add "secondary_hc_auth" --secret "ActualSecondaryUserPassword"
  ```

#### Étape 4 : mettre à jour domain.conf

Mettez à jour la référence du mot de passe de la banque d’informations d’identification :

* **Windows**

  ```
  set "JAVA_OPTS=%JAVA_OPTS% -DSec_Auth_PASS=YourCustomPassword"
  ```

* **Linux**

  ```
  JAVA_OPTS="$JAVA_OPTS -DSec_Auth_PASS=YourCustomPassword"
  ```

#### Étape 5 : vérification de la configuration XML

Assurez-vous `host-secondary.xml` contient le magasin d’informations d’identification et les entrées du client d’authentification configurés.
Aucune modification n’est requise si la configuration par défaut est présente.


#### Étape 6 : démarrer les nœuds

1. Démarrez le **nœud principal** et attendez qu’il soit complètement démarré.
2. Démarrez le **nœud secondaire**.

### Vérification

Confirmez la réussite de l’enregistrement en utilisant les journaux de contrôleur hôte sur les deux nœuds.

## Résumé

* L’**option 1** fournit une configuration rapide à l’aide d’un magasin d’informations d’identification préconfiguré.
* L’**option 2** renforce la sécurité en utilisant un mot de passe de magasin d’informations d’identification personnalisé.
* La configuration doit être effectuée **sur des nœuds secondaires uniquement**.
* La configuration du nœud de Principal est réutilisée automatiquement dans le domaine.

