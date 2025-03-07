---
title: Mise à niveau vers AEM 6.5 Forms LTS on OSGi
description: Vous pouvez effectuer une mise à niveau directe d’AEM 6.5.22.0 Forms vers AEM 6.5 Forms LTS.
content-type: reference
role: Admin, User
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms, AEM Forms on OSGi, AEM Forms Upgrade
exl-id: 9233d4b7-441c-4cbd-86f8-2c52b99c3330
source-git-commit: dd45dfe953a111ccbbc71e8e25a8a2577037587a
workflow-type: tm+mt
source-wordcount: '837'
ht-degree: 81%

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
   1. Ouvrez [Package Manager](/help/sites-administering/package-manager.md) et cliquez sur **[!UICONTROL Télécharger le package]** pour télécharger le package.
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
