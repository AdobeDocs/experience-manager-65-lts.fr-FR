---
title: Configuration de SSL pour JBoss Application Server (AEM 6.5 LTS JEE)
description: Découvrez comment configurer SSL pour le serveur d’applications JBoss.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_ssl
products: SG_EXPERIENCEMANAGER/6.5/FORMS
solution: Experience Manager, Experience Manager Forms
feature: Document Security
role: User, Developer
hide: true
hidefromtoc: true
source-git-commit: 86d6d0f7b6fe1c36349f29e45a3eee31b04e5e80
workflow-type: tm+mt
source-wordcount: '782'
ht-degree: 1%

---


# Configuration de SSL pour JBoss Application Server (AEM 6.5 LTS JEE)

## Vue d’ensemble

Pour configurer SSL sur le serveur d’applications JBoss pour Adobe Experience Manager (AEM) 6.5 LTS s’exécutant sur Java EE, vous devez activer la communication HTTPS sécurisée. L’activation de SSL chiffre les données échangées entre les clients et le serveur, ce qui en fait une exigence de sécurité essentielle pour tout déploiement d’AEM Forms en production.

Le processus comprend deux étapes principales :

- **Obtention d’informations d’identification SSL** soit en générant un certificat autosigné, soit en en demandant un à une autorité de certification (CA).
- **Activation de SSL sur JBoss** — Utilisation du sous-système Elytron via les commandes de l’interface de ligne de commande JBoss.

Dans ce guide, les valeurs d’espace réservé suivantes sont utilisées :

- `[appserver root]` : le répertoire racine du serveur d’applications JBoss exécutant AEM Forms.
- `[type]` : nom de dossier qui varie en fonction du type d&#39;installation effectué.
- `[JAVA_HOME]` : le répertoire dans lequel le JDK est installé.

## Partie 1 : création d’informations d’identification SSL (auto-signé)

Si vous ne disposez pas d’un certificat d’une autorité de certification, vous pouvez générer des informations d’identification SSL auto-signées à l’aide de l’utilitaire Java `keytool`. Convient aux environnements de développement ou de test.

### Étape 1 — Générer le KeyStore

Accédez à `[JAVA_HOME]/bin` dans une invite de commande et exécutez la commande suivante, en remplaçant les valeurs par celles appropriées à votre environnement. Le nom d’hôte doit être le nom de domaine complet (FQDN) de votre serveur d’applications :

```bash
keytool -genkey -dname "CN=Host Name, OU=Group Name, O=Company Name, L=City Name, S=State, C=Country Code" \
  -alias "AEMForms Cert" -keyalg RSA \
  -keypass key_password -keystore keystorename.keystore
```

A l’invite, saisissez le `keystore_password`. Notez que le mot de passe du fichier de stockage des clés et de la clé doit être identique.

### Étape 2 — Copiez le KeyStore dans le répertoire de configuration

Copiez le fichier de stockage des clés généré dans le dossier de configuration approprié à votre type d’installation :

```bash
# Windows Single Server
copy keystorename.keystore [appserver root]\standalone\configuration

# Windows Server Cluster
copy keystorename.keystore [appserver root]\domain\configuration

# Linux Single Server
cp keystorename.keystore [appserver root]/standalone/configuration

# Linux Server Cluster
cp keystorename.keystore [appserver root]/domain/configuration
```

### Étape 3 — Exporter le fichier de certificat

Exportez le certificat du fichier de stockage des clés à l’aide de l’une des commandes suivantes :

```bash
# Single Server
keytool -export -alias "AEMForms Cert" -file AEMForms_cert.cer \
  -keystore [appserver root]/standalone/configuration/keystorename.keystore

# Server Cluster
keytool -export -alias "AEMForms Cert" -file AEMForms_cert.cer \
  -keystore [appserver root]/domain/configuration/keystorename.keystore
```

Saisissez le `keystore_password` lorsque vous y êtes invité.

### Étape 4 — Copier et vérifier le certificat

Copiez `AEMForms_cert.cer` dans le répertoire de configuration, puis vérifiez son contenu :

```bash
# Copy (Linux Single Server example)
cp AEMForms_cert.cer [appserver root]/standalone/configuration

# Verify certificate contents (Single Server)
keytool -printcert -v -file [appserver root]/standalone/configuration/AEMForms_cert.cer

# Verify certificate contents (Server Cluster)
keytool -printcert -v -file [appserver root]/domain/configuration/AEMForms_cert.cer
```

### Étape 5 — Importer le certificat dans le Truststore Java

Avant l’importation, assurez-vous que le fichier `cacerts` est accessible en écriture :

```bash
# Windows: Right-click cacerts → Properties → deselect Read-only

# Linux:
chmod 777 [JAVA_HOME]/jre/lib/security/cacerts
```

Importez ensuite le certificat :

```bash
keytool -import -alias "AEMForms Cert" -file AEMForms_cert.cer \
  -keystore [JAVA_HOME]/jre/lib/security/cacerts
```

Lorsque vous êtes invité à saisir le mot de passe, saisissez `changeit` (le mot de passe par défaut du TrustStore Java ; vérifiez auprès de votre administrateur si celui-ci a été modifié). Quand vous avez demandé **Approuver ce certificat ? [non]**, tapez `yes`. Un message de confirmation doit s’afficher : *« Le certificat a été ajouté au KeyStore. »*

>[!NOTE]
>
> Si vous vous connectez à AEM Forms via SSL à partir de Workbench, vous devez également installer le certificat sur l’ordinateur Workbench.

## Partie 2 : activer SSL sur JBoss à l’aide du sous-système Elytron

Une fois les informations d’identification SSL en place, vous pouvez désormais activer HTTPS sur JBoss à l’aide de son sous-système de sécurité Elytron via l’interface de ligne de commande JBoss. Assurez-vous que votre fichier de stockage de clés se trouve dans le répertoire de configuration approprié avant de continuer.

>[!NOTE]
>
> Sous Windows, chaque commande de l’interface de ligne de commande doit être saisie sur une seule ligne, sans saut de ligne. Remplacez `keystorename.keystore` par votre nom de fichier réel et `changeit` par votre fichier de stockage des clés/mot de passe des clés.

### Étape 6a — Créer un Key-Store Elytron

```bash
/subsystem=elytron/key-store=aemKeyStore:add(
  path="keystorename.keystore",
  relative-to=jboss.server.config.dir,
  type="JKS",
  credential-reference={clear-text="changeit"})
```

Remplacez `JKS` par `PKCS12` si votre fichier de stockage des clés utilise ce format.

### Étape 6b — Créer le Key-Manager Elytron

```bash
/subsystem=elytron/key-manager=aemKeyManager:add(
  key-store=aemKeyStore,
  credential-reference={clear-text="changeit"})
```

Si votre KeyStore contient plusieurs entrées de certificat, spécifiez explicitement l’alias :

```bash
/subsystem=elytron/key-manager=aemKeyManager:add(
  key-store=aemKeyStore,
  alias="AEMForms Cert",
  credential-reference={clear-text="changeit"})
```

### Étape 6c — Mettre à jour le contexte SSL du serveur

```bash
/subsystem=elytron/server-ssl-context=applicationSSC:write-attribute(
  name=key-manager,
  value=aemKeyManager)
```

### Étape 6d — Configuration du listener HTTPS Undertow

Connectez le contexte SSL à Undertown (le serveur web JBoss) pour activer le listener HTTPS :

```bash
/subsystem=undertow/server=default-server/https-listener=https:add(
  socket-binding=https,
  ssl-context=applicationSSC)
```

## Partie 3 : redémarrage du serveur d’applications

Une fois la configuration Elytron terminée, redémarrez JBoss pour appliquer les modifications.

### Installations Clé En Main (Services Windows)

- Ouvrez **Panneau de Contrôle > Outils D’Administration > Services**.
- Sélectionnez **JBoss pour Adobe Experience Manager forms**.
- Sélectionnez **Action > Arrêter** et attendez que le service s’arrête.
- Sélectionnez **Action > Démarrer**.

### Installations de JBoss préconfigurées ou manuelles

À partir d’une invite de commande, accédez à `[appserver root]/bin` :

```bash
# Stop the server
Windows: shutdown.bat -S
Linux:   ./shutdown.sh -S

# Wait until JBoss fully shuts down, then start the server
Windows: run.bat -c <profile>
Linux:   ./run.sh -c <profile>
```

## Partie 4 : Demander des informations d’identification à une autorité de certification

Pour les environnements de production, vous devez utiliser un certificat émis par une autorité de certification approuvée. Le processus implique la génération d’une paire de clés, la création d’une demande de signature de certificat (CSR), puis l’importation du certificat signé par l’autorité de certification.

### Générer le KeyStore et créer une demande de signature de certificat

Accédez à `[JAVA_HOME]/bin` et générez le fichier de stockage des clés :

```bash
keytool -genkey -dname "CN=Host Name, OU=Group Name, O=Company Name, L=City Name, S=State, C=Country Code" \
  -alias "AEMForms Cert" -keyalg RSA \
  -keypass key_password -keystore keystorename.keystore
```

Ensuite, générez la CSR à envoyer à votre autorité de certification :

```bash
keytool -certreq -alias "AEMForms Cert" \
  -keystore keystorename.keystore \
  -file AEMFormscertRequest.csr
```

Envoyez le fichier `.csr` à votre autorité de certification. Une fois que vous avez reçu le certificat signé, procédez comme suit.

### Importer le certificat signé par l’autorité de certification

Importez d’abord le certificat racine de l’autorité de certification :

```bash
keytool -import -trustcacerts -file rootcert.pem \
  -keystore keystorename.keystore -alias root
```

Si le navigateur n’a pas encore approuvé le certificat racine, importez-le également à cet endroit. Importez ensuite le certificat signé par l’autorité de certification :

```bash
keytool -import -trustcacerts -file CACertificateName.crt \
  -keystore keystorename.keystore
```

>[!NOTE]
>
> Le certificat signé par l’autorité de certification importé remplacera tout certificat public autosigné existant s’il est présent dans le fichier de stockage des clés.

Une fois le certificat d’autorité de certification importé, suivez les **étapes 6a à 6d** de la partie 2 (configuration Elytron), redémarrez le serveur (partie 3) et vérifiez l’accès SSL.

## Vérifier l’accès SSL

Après avoir redémarré le serveur, vérifiez que SSL fonctionne correctement en accédant à la console d’administration AEM Forms via HTTPS. Le port SSL par défaut pour JBoss est `8443` :

```
https://[host name]:8443/adminui
```

Si la console d’administration se charge correctement via HTTPS, SSL a été configuré correctement. Utilisez le port `8443` pour toutes les connexions SSL suivantes à AEM Forms.
