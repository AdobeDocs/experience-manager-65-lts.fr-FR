---
title: Mise à niveau vers AEM 6.5 Forms LTS on OSGi
description: Vous pouvez effectuer une mise à niveau directe d’AEM 6.5.22.0 Forms vers AEM 6.5 Forms LTS.
content-type: reference
role: Admin, User
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms, AEM Forms on OSGi, AEM Forms Upgrade
exl-id: 9233d4b7-441c-4cbd-86f8-2c52b99c3330
source-git-commit: b7aa877f9e782b0568adc7baa440dc630c690454
workflow-type: tm+mt
source-wordcount: '1527'
ht-degree: 47%

---

# Mise à niveau vers AEM 6.5 Forms LTS on OSGi {#upgrade-to-aem-forms-osgi}

Pour [mettre à niveau d’AEM 6.5 vers AEM 6.5 LTS](/help/sites-deploying/upgrade.md), effectuez la mise à niveau vers AEM 6.5.22.0 Forms ou une version ultérieure. Une mise à niveau directe d’AEM 6.5.22.0 vers AEM 6.5 Forms LTS est prise en charge.

Si vous utilisez AEM 6.0 Forms, AEM 6.1 Forms, AEM 6.2 Forms, AEM 6.3 Forms, AEM 6.4 Forms ou AEM 6.5 Forms, aucune mise à niveau directe vers AEM 6.5 Forms LTS n’est disponible. Pour obtenir des chemins de mise à niveau détaillés, consultez la documentation [Chemins de mise à niveau](/help/forms/using/upgrade.md).

Après la mise à niveau vers le pack de services AEM Forms 6.5.22.0, procédez comme suit pour effectuer la mise à niveau vers AEM 6.5 LTS Forms :

1. Installation du package complémentaire AEM Forms. Suivez les étapes ci-dessous :

   1. Ouvrez la [Distribution de logiciels](https://experience.adobe.com/downloads). Vous avez besoin d’un Adobe ID pour vous connecter à la Distribution de logiciels.
   1. Sélectionnez **[!UICONTROL Adobe Experience Manager]** situé dans le menu d’en-tête.
   1. Dans la section **[!UICONTROL Filtres]** :
      1. Sélectionnez **[!UICONTROL Forms]** dans la liste déroulante **[!UICONTROL Solution]**.
      1. Sélectionnez la version et le type du package. Vous pouvez également utiliser l’option **[!UICONTROL Rechercher des téléchargements]** pour filtrer les résultats.
   1. Sélectionnez le nom de package applicable à votre système d’exploitation, sélectionnez **[!UICONTROL Accepter les conditions du CLUF]**, puis sélectionnez **[!UICONTROL Télécharger]**.
   1. Ouvrez le [gestionnaire de modules](/help/sites-administering/package-manager.md) et cliquez sur **[!UICONTROL Charger le package]** pour charger le package.
   1. Sélectionnez le package et cliquez sur **[!UICONTROL Installer]**.

      Vous pouvez également télécharger le package via le lien direct répertorié dans l’article [Versions d’AEM Forms](https://experienceleague.adobe.com/fr/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases).

      Une fois le package installé, vous êtes invité à redémarrer l’instance AEM. **N’arrêtez pas le serveur immédiatement.** Avant d’arrêter le serveur AEM Forms, attendez que les messages ServiceEvent REGISTERED et ServiceEvent UNREGISTERED cessent d’apparaître dans le fichier &lt;crx-repository>/error.log et que le journal soit stable. Notez également que quelques packages peuvent rester à l’état installé. Vous pouvez ignorer sans risque l’état de ces packages.


      **Redémarrez l’instance AEM avec les paramètres de ligne de commande JVM supplémentaires suivants** :
      `--add-opens java.base/java.util=ALL-UNNAMED --add-exports=java.xml/com.sun.org.apache.xml.internal.serialize=ALL-UNNAMED`

      Si le serveur est démarré via un script ou un service, mettez-le à jour en conséquence afin d’inclure les éléments ci-dessus, de sorte qu’ils soient également efficaces après les redémarrages suivants.

      >[!NOTE]
      >
      > Il est recommandé d’utiliser la commande « Ctrl+C » pour redémarrer le SDK. Le redémarrage du SDK AEM à l’aide de méthodes alternatives, par exemple l’arrêt des processus Java, peut entraîner des incohérences dans l’environnement de développement AEM.

1. Exécutez les activités postérieures à l’installation.

   * **Exécuter l’utilitaire de migration**

     L’utilitaire de migration rend les formulaires adaptatifs et les actions de gestion de la correspondance des versions antérieures compatibles avec les formulaires AEM 6.5. Vous pouvez télécharger l’utilitaire à partir de la Distribution de logiciels AEM. Pour des informations détaillées sur la configuration et l’utilisation de l’utilitaire de migration, voir [l’utilitaire de migration](../../forms/using/migration-utility.md).

     Si vous utilisez [Exemple pour l’intégration du composant brouillons et envois](https://helpx.adobe.com/fr/experience-manager/6-3/forms/using/integrate-draft-submission-database.html) avec la base de données et que vous mettez à niveau à partir d’une version précédente, exécutez les requêtes SQL suivantes après avoir effectué la mise à niveau :

     ```sql
     UPDATE metadata m, additionalmetadatatable am
     SET m.dataType = am.value
     WHERE m.id = am.id
     AND am.key = 'dataType'
     ```

     ```sql
     DELETE from additionalmetadatatable
     WHERE `key` = 'dataType'
     ```

   * **(Si vous effectuez une mise à niveau à partir d’AEM 6.2 Forms ou de versions précédentes uniquement) Reconfigurer Adobe Sign**

     Si Adobe Sign était configuré dans la version précédente d’AEM Forms, reconfigurez Adobe Sign à partir des services cloud d’AEM. Pour plus de détails, consultez la section [Intégrer Adobe Sign à AEM Forms](../../forms/using/adobe-sign-integration-adaptive-forms.md).

   * **Prise en charge de jQuery**

     Dans AEM 6.5 Forms, la version de jQuery est mise à jour vers la version 3.2.1 et la version de l’interface utilisateur de jQuery est mise à jour vers la version 1.12.1. AEM Form utilise JQuery en mode **noConflict**. Ainsi, si vous utilisez une autre version de jQuery, aucun problème ne s’affiche lors de l’exécution d’une mise à niveau. Cependant, lorsque vous effectuez une mise à niveau vers AEM 6.5 Forms :

      * Assurez-vous que vos composants personnalisés, le cas échéant, sont compatibles avec les versions jQuery prises en charge.
      * Supprimez les API non prises en charge des composants personnalisés. Voir [guide de mise à niveau](https://jquery.com/upgrade-guide/3.0/) pour la liste des API supprimées. Par exemple, la prise en charge des API load(), .unload() et .error() est supprimée. Utilisez la méthode .on() à la place des API mentionnées ci-dessus. Par exemple, remplacez $(&quot;img&quot;).load(fn) par $(&quot;img&quot;).on(&quot;load&quot;, fn).

   * **(Si vous effectuez une mise à niveau à partir d’AEM 6.2 Forms ou de versions précédentes uniquement) Reconfigurez l’analyse et les rapports**

     Dans AEM Forms 6.4, la variable de trafic pour la source et l’événement de succès de l’impression ne sont pas disponibles. Ainsi, lorsque vous effectuez une mise à niveau à partir d’AEM 6.2 Forms ou de versions précédentes, AEM Forms cesse d’envoyer des données au serveur Adobe Analytics et les rapports d’analyse pour les formulaires adaptatifs ne sont pas disponibles. AEM 6.4 Forms introduit également une variable de trafic pour la version de l’analyse des formulaires et un événement de succès pour le temps passé sur un champ. Dès lors, vous devez reconfigurer les analyses et les rapports de votre environnement AEM Forms. Pour obtenir des instructions détaillées, consultez la section [Configurer les analyses et les rapports](../../forms/using/configure-analytics-forms-documents.md).

1. Vérifiez que le serveur a été mis à niveau avec succès, que toutes les données ont également été migrées avec succès, et qu’il peut fonctionner normalement.

   * **Vérifiez l’état des bundles :** assurez-vous que tous les bundles sont actifs.
   * **Vérifier la réplication et la réplication inverse :** publiez, remplissez et envoyez quelques formulaires migrés. Vérifiez également les données envoyées.
   * **Vérifier l’accès aux interfaces utilisateur d’administration et de développement :** connectez-vous à l’instance AEM à partir d’un compte d’administration et vérifiez que vous avez accès aux URL suivantes :

      * `https://'[server]:[port]'/crx/packmgr`
      * `https://'[server]:[port]'/crx/de`
      * `https://'[server]:[port]'/aem/forms.html/content/dam/formsanddocuments`

   >[!NOTE]
   >
   >Dans AEM 6.4 Forms, la structure du référentiel crx a changé. Après la mise à niveau d’AEM 6.3 Forms vers AEM 6.5 Forms, utilisez les chemins d’accès modifiés pour la personnalisation que vous créez à nouveau. Pour la liste complète des chemins modifiés, voir [Restructuration du référentiel des formulaires dans AEM](https://experienceleague.adobe.com/en/docs/experience-manager-65/content/implementing/deploying/restructuring/forms-repository-restructuring-in-aem-6-5).


## Déploiement d’AEM sur JBoss EAP 8 (Windows)

### Vue d’ensemble

Ce guide fournit des instructions détaillées sur le déploiement de Adobe Experience Manager (AEM) en tant que fichier WAR OSGi autonome sur JBoss Enterprise Application Platform (EAP) 8 dans un environnement Windows à l’aide du JDK 21.

### Configuration requise

Avant de commencer le processus de déploiement, assurez-vous que votre environnement répond aux exigences suivantes :

| Composant | Condition requise |
|-----------|-------------|
| Système d’exploitation | Windows Server 2016 ou version ultérieure (64 bits) |
| Java Development Kit | JDK 21 (Oracle ou OpenJDK) |
| Serveur d’applications | JBoss EAP 8.x |
| Distribution AEM | Fichier WAR d’AEM (obtenu d’Adobe) |

>[!NOTE]
>
> Vérifiez que la variable d’environnement `JAVA_HOME` pointe vers votre répertoire d’installation du JDK 21.

### Étape 1 : installer JBoss EAP 8

#### Télécharger JBoss EAP

1. Accédez au portail de développement Red Hat :\
   [https://developers.redhat.com/products/eap/download](https://developers.redhat.com/products/eap/download)

2. Téléchargez la distribution JBoss EAP 8 ZIP pour Windows.

#### Extraire JBoss EAP

1. Extrayez le fichier ZIP téléchargé dans votre répertoire d’installation préféré.

2. Notez que ce chemin d’accès au répertoire est `<JBOSS_HOME>` à utiliser dans ce guide.

   **Exemple :**\
   ```C:\jboss-eap-8.0```

### Étape 2 : préparation du fichier WAR AEM

#### Obtenir AEM WAR

Procurez-vous le fichier WAR d’AEM auprès de la distribution logicielle Adobe ou de votre représentant Adobe.

#### Renommer le fichier WAR

Renommez le fichier WAR pour refléter le chemin d’accès contextuel de l’URL souhaité :

```
cq-quickstart.war
```

>[!IMPORTANT]
>
> Le nom de fichier WAR détermine le contexte de l’URL de l’application. Par exemple, `cq-quickstart.war` sera accessible à l’adresse `/cq-quickstart`.


### Étape 3 : configurer AEM WAR

Toutes les modifications de configuration doivent être effectuées **avant** le déploiement sur JBoss.

#### Créer un répertoire de travail

1. Créez un répertoire de travail temporaire :

   ```
   C:\aem\war-config
   ```

2. Copiez `cq-quickstart.war` dans ce répertoire.

#### Extraire le contenu WAR

1. Ouvrez **invite de commandes** et accédez à votre répertoire de travail :

   ```cmd
   cd C:\aem\war-config
   ```

2. Extrayez le fichier WAR :

   ```cmd
   jar -xvf cq-quickstart.war
   ```

   Vous créez ainsi une structure de répertoires avec des fichiers d’application `WEB-INF` et autres.

### Étape 4 : Configurer le descripteur de déploiement JBoss

#### Créer un fichier de structure de déploiement

1. Accédez au répertoire `WEB-INF` dans le fichier WAR extrait :

   ```cmd
   cd WEB-INF
   ```

2. Créez un fichier nommé `jboss-deployment-structure.xml`.

3. Ajoutez le contenu XML suivant :

   ```xml
   <?xml version="1.0" encoding="UTF-8"?>
   <jboss-deployment-structure xmlns="urn:jboss:deployment-structure:1.2">
       <deployment>
           <dependencies>
               <module name="jdk.unsupported" />
           </dependencies>
       </deployment>
   </jboss-deployment-structure>
   ```

4. Enregistrez et fermez le fichier.

**Objectif :** cette configuration permet d’accéder aux modules internes du JDK requis par AEM.

### Étape 5 : Configurer les paramètres de chargement multipartie

>[!NOTE]
>
> L’étape 5 s’applique uniquement à **AEM Forms**. Si vous configurez **AEM uniquement** vous pouvez ignorer cette étape.


#### Modifier le fichier web.xml

1. Ouvrez `WEB-INF\web.xml` dans un éditeur de texte.

2. Recherchez la section `<servlet>` contenant la configuration du mode d’exécution :

   ```xml
   <!-- Set the runmode per default to author -->
   <init-param>
       <param-name>sling.run.modes</param-name>
       <param-value>author</param-value>
   </init-param>
   <load-on-startup>100</load-on-startup>
   </servlet>
   ```

3. Remplacez la balise `</servlet>` de fermeture et la ligne précédente par :

   ```xml
   <init-param>
       <param-name>sling.run.modes</param-name>
       <param-value>author</param-value>
   </init-param>
   <multipart-config>
       <max-file-size>1048576000</max-file-size>
       <max-request-size>1048576000</max-request-size>
       <file-size-threshold>0</file-size-threshold>
   </multipart-config>
   <load-on-startup>100</load-on-startup>
   </servlet>
   ```

4. Enregistrez et fermez `web.xml`.

**Objectif :** ces paramètres permettent les chargements de fichiers volumineux (jusqu’à 1 Go) pour AEM Forms et la gestion des ressources numériques.

### Étape 6 : Recompressez le fichier WAR

Une fois toutes les modifications de configuration effectuées, recompressez le fichier WAR.

1. Revenez au répertoire de travail contenant le contenu extrait :

   ```cmd
   cd C:\aem\war-config
   ```

2. Créez le nouveau fichier WAR :

   ```cmd
   jar -cvf cq-quickstart.war *
   ```

>[!IMPORTANT]
>
> Effectuez cette étape une seule fois, une fois toutes les configurations terminées.

### Étape 7 : déployer et démarrer AEM

#### Déployer WAR sur JBoss

1. Copiez le `cq-quickstart.war` recompilé dans le répertoire des déploiements de JBoss :

   ```
   <JBOSS_HOME>\standalone\deployments
   ```

   **Exemple :**
   ```C:\jboss-eap-8.0\standalone\deployments```

#### Configuration des paramètres JVM (facultatifs, mais recommandés)

Avant de démarrer JBoss, configurez les paramètres de mémoire JVM :

1. Ouvrez `<JBOSS_HOME>\bin\standalone.conf.bat` dans un éditeur de texte.

1. Modifiez ou ajoutez la ligne suivante pour définir la mémoire de segment :

   ```batch
   set "JAVA_OPTS=-Xms4096m -Xmx4096m -XX:MaxMetaspaceSize=512m"
   ```

>[!NOTE]
>
> Ajustez les valeurs de mémoire en fonction de la capacité de votre serveur et des exigences d’AEM.

1. Enregistrez et fermez le fichier.

#### Démarrer JBoss EAP

1. Ouvrez **Invite de commandes** en tant qu’**administrateur**.

1. Accédez au répertoire bin de JBoss :

   ```cmd
   cd <JBOSS_HOME>\bin
   ```

   **Exemple :**
   ```cmd cd C:\jboss-eap-8.0\bin```

1. Démarrez le serveur JBoss :

   ```cmd
   standalone.bat -b 0.0.0.0 -bmanagement 0.0.0.0
   ```

   **Paramètres:**
   * `-b 0.0.0.0` : lie le serveur à toutes les interfaces réseau
   * `-bmanagement 0.0.0.0` : lie l&#39;interface de gestion à toutes les interfaces réseau

#### Surveiller le déploiement

Regardez la sortie de la console pour les messages de déploiement. La réussite du déploiement est indiquée par :

```
Deployed "cq-quickstart.war" (runtime-name : "cq-quickstart.war")
```

### Étape 8 : Accéder à AEM

Une fois le déploiement terminé et AEM entièrement démarré :

**URL d’auteur AEM :**
```http://<server-ip>:8080/cq-quickstart```

**Informations d’identification par défaut :**

* Nom d’utilisateur : `admin`.
* Mot de passe : `admin`.

**Important :** modifiez le mot de passe par défaut immédiatement après la première connexion.

### Résolution des problèmes

#### Problèmes courants

| Problème | Solution |
|-------|----------|
| Échec du déploiement avec l’exception ClassNotFoundException | Vérifiez que `jboss-deployment-structure.xml` est correctement configuré. |
| Erreur de mémoire insuffisante au démarrage | Augmenter la mémoire de tas dans `standalone.conf.bat` |
| AEM ne démarre pas après le déploiement | Vérification des journaux JBoss dans `<JBOSS_HOME>\standalone\log\server.log` |
| Impossible d’accéder à AEM dans le navigateur | Vérifiez que les paramètres du pare-feu autorisent le port 8080 |

#### Fichiers journaux

* **Journal du serveur JBoss :** `<JBOSS_HOME>\standalone\log\server.log`
* **Journal des erreurs AEM :** disponible via la console web d’AEM après le démarrage à\
  `http://<server-ip>:8080/cq-quickstart/system/console`

### Configuration supplémentaire

#### Configuration des modes d’exécution

Pour modifier les modes d’exécution d’AEM (création/publication), modifiez le paramètre `sling.run.modes` dans `WEB-INF\web.xml` avant de recompiler le fichier WAR :

```xml
<init-param>
    <param-name>sling.run.modes</param-name>
    <param-value>publish</param-value>
</init-param>
```

#### Recommandations de production

Pour les environnements de production :

* Configuration des certificats SSL/TLS dans JBoss
* Configuration des agents de réplication AEM
* Configuration du Dispatcher pour l’équilibrage de charge
* Activer les sauvegardes automatisées
* Implémentation de la surveillance et des alertes

### Documentation connexe

* [Documentation de JBoss EAP 8](https://access.redhat.com/documentation/en-us/red_hat_jboss_enterprise_application_platform/8.0)
* [Documentation Adobe Experience Manager](https://experienceleague.adobe.com/docs/experience-manager-65.html?lang=fr)
* [Guide d’installation et de déploiement d’AEM](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/deploying/deploy.html?lang=fr)

### Informations sur le document

| Champ | Valeur |
|-------|-------|
| Date de la dernière mise à jour | Février 2026 |
| Version d’AEM | 6.5+ (LTS) |
| Version de JBoss | EAP 8.x |
| Version du JDK | 21 |
| Plateforme | Windows |


