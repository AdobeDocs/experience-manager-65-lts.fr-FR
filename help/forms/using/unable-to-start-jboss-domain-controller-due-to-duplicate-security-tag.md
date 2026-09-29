---
title: Impossible de démarrer le contrôleur de domaine JBoss
description: Dans les déploiements de clusters LTS AEM Forms 6.5.1 utilisant JBoss EAP 8, le fichier de configuration peut contenir des balises en double.
solution: Experience Manager
feature: Deploying
role: User,Admin,Developer
exl-id: f24e7245-7b43-4b1c-ba7a-162344ef545c
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 2e690827bfa8f3d8227860de4efb802758ae0095
workflow-type: tm+mt
source-wordcount: '152'
ht-degree: 1%
---
# Impossible de démarrer le contrôleur de domaine JBoss

## Problème

Dans **les déploiements de clusters AEM Forms 6.5.1 LTS** à l’aide de **JBoss EAP 8**, le fichier de configuration
`<JBOSS_HOME>/domain/configuration/domain_oracle.xml` (et variantes spécifiques à la base de données) peut contenir une **balise de `<security>` d&#39;ouverture dupliquée**.

Cela entraîne une **configuration XML non valide**, ce qui entraîne l’échec du démarrage du contrôleur de domaine **JBoss** et empêche l’initialisation réussie du cluster.

## Application

* **Produit :** AEM Forms 6.5.1 LTS
* **Type de déploiement :** cluster
* **Serveur d’applications :** JBoss EAP 8.x
* **Fichiers de configuration:**

  * `<JBOSS_HOME>/domain/configuration/domain_oracle.xml`
  * `<JBOSS_HOME>/domain/configuration/domain_mysql.xml`
  * `<JBOSS_HOME>/domain/configuration/domain_mssql.xml`

## Étapes de dépannage

1. Au démarrage du contrôleur de domaine, les erreurs suivantes peuvent être observées :

   * `WFLYCTL0198: Unexpected element 'security'`
   * `IJ010061: Unexpected element: security`

2. Ouvrez le fichier de configuration approprié :

   ```
   <JBOSS_HOME>/domain/configuration/domain_oracle.xml
   (or domain_mysql.xml / domain_mssql.xml)
   ```

3. Recherchez la balise d’ouverture de `<security>` en double.

   **Configuration incorrecte :**

   ```xml
   <security>
       <security>
           <user-name>adobe</user-name>
           <credential-reference store="db-creds" alias="EncryptDBPassword"/>
       </security>
   ```

4. Supprimez la balise `<security>` d’ouverture supplémentaire afin que la configuration soit corrigée comme illustré ci-dessous :

   **Configuration correcte :**

   ```xml
   <security>
       <user-name>adobe</user-name>
       <credential-reference store="db-creds" alias="EncryptDBPassword"/>
   </security>
   ```

5. Enregistrez le fichier et démarrez le contrôleur de domaine JBoss.

6. Assurez-vous que la même configuration validée est appliquée de manière cohérente sur tous les nœuds du cluster.
