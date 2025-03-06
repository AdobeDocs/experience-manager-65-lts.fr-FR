---
title: Configuration du balisage des ressources à l’aide du service de contenu dynamique
description: Découvrez comment configurer le balisage intelligent et le balisage intelligent amélioré dans  [!DNL Adobe Experience Manager] à l’aide du service de contenu dynamique.
role: Admin
feature: Tagging,Smart Tags
solution: Experience Manager, Experience Manager Assets
exl-id: be7c294c-149b-4825-8376-573f9e2987e2
source-git-commit: 995bad770ba026ee918233f4bf28e6ba3cf003a6
workflow-type: tm+mt
source-wordcount: '1895'
ht-degree: 98%

---

# Préparation de [!DNL Assets] pour le balisage intelligent {#configure-asset-tagging-using-the-smart-content-service}

Avant de commencer à baliser vos ressources à l’aide des services de contenu dynamique, intégrez [!DNL Experience Manager Assets] à l’Adobe Developer Console pour tirer parti du service dynamique d’[!DNL Adobe Sensei]. Une fois configuré, entraînez le service à l’aide de quelques images et d’une balise.
Avant d’utiliser le service de contenu dynamique, vérifiez les points suivants :

* [Intégration à la console Adobe Developer](#integrate-adobe-io).
* [Entraînement du service de contenu dynamique](#training-the-smart-content-service)
* Installez le dernier pack de services [[!DNL Experience Manager] ](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/aem-releases-updates.html?lang=fr).

>[!IMPORTANT]
>
>Voir [Préparation d’Assets pour le balisage intelligent](https://experienceleague.adobe.com/fr/docs/experience-manager-65/content/assets/administer/config-smart-tagging) pour la configuration des balises intelligentes dans AEM 6.5.

**Nouveaux utilisateurs et nouvelles utilisatrices**

Les services de contenu intelligent ne sont plus disponibles pour les nouveaux utilisateurs et les nouvelles utilisatrices On-Premise [!DNL Experience Manager Assets].

**Utilisateurs et utilisatrices existants**

Les utilisateurs et utilisatrices On-Premise existants, pour qui cette fonctionnalité est déjà activée, peuvent continuer à utiliser les services de contenu intelligent.

## Intégration à la console Adobe Developer {#integrate-adobe-io}

Lors de l’intégration à la console Adobe Developer, le serveur [!DNL Experience Manager] authentifie vos informations d’identification de service auprès de la passerelle de la console Adobe Developer avant de transférer votre demande au service de contenu dynamique. Pour l’intégration, vous avez besoin d’un compte Adobe ID disposant de droits d’administrateur pour l’organisation et d’une licence Smart Content Service achetée et activée pour votre organisation.

Pour configurer le service de contenu dynamique, procédez comme suit :

1. Créez une intégration dans l’[Adobe Developer Console](#create-adobe-io-integration).

1. Créez la [configuration du compte technique Adobe IMS](#create-ims-account-config) en utilisant la clé API et d’autres informations d’identification fournies par l’Adobe Developer Console.

1. [Configurez le service de contenu dynamique](#configure-smart-content-service).

1. [Testez la configuration](#validate-the-configuration).

### Créer l’intégration de l’Adobe Developer Console {#create-adobe-io-integration}

Pour utiliser les API de service de contenu dynamique, créez une intégration dans l’Adobe Developer Console afin d’obtenir la [!UICONTROL Clé API] (générée dans le champ [!UICONTROL ID CLIENT] de l’intégration dans l’Adobe Developer Console), l’[!UICONTROL ID D’ORGANISATION] et le [!UICONTROL SECRET CLIENT] pour les [!UICONTROL Paramètres du service de balisage intelligent des ressources] de la configuration cloud dans [!DNL Experience Manager].

1. Accédez à l’URL [https://developer.adobe.com](https://developer.adobe.com/) dans un navigateur. Sélectionnez le compte approprié et vérifiez que le rôle d’organisation associé est **administrateur ou administratrice** système.

1. Créez un projet portant le nom de votre choix. Cliquez sur **[!UICONTROL Add API]** (Ajouter une API).

1. Sur la page **[!UICONTROL Add API]**, sélectionnez **[!UICONTROL Experience Cloud]** puis **[!UICONTROL Smart Content]** (Contenu dynamique). Cliquez sur **[!UICONTROL Next]** (Suivant).

1. Sélectionnez **[!UICONTROL OAuth serveur à serveur]**. Cliquez sur **[!UICONTROL Suivant]**.
Pour plus de détails sur la façon d’effectuer cette configuration, consultez la documentation de la Developer Console, en fonction de vos besoins :

   * Vue d’ensemble :
      * [Authentification de serveur à serveur](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/)

   * Créer de nouvelles informations d’identification OAuth :
      * [Guide de mise en œuvre des informations d’identification OAuth de serveur à serveur](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/implementation/)

   * Migrer des informations d’identification JWT existantes vers des informations d’identification OAuth :
      * [Migrer des informations d’identification du compte de service (JWT) vers les informations d’identification OAuth de serveur à serveur](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/migration/)


1. Dans la page **[!UICONTROL Sélectionner les profils de produit]**, sélectionnez **[!UICONTROL Services de contenu dynamique]**. Cliquez sur **[!UICONTROL Enregistrer l’API configurée]**. 

   Une page affiche davantage d’informations sur la configuration. Laissez cette page ouverte pour copier et ajouter ces valeurs dans les [!UICONTROL Paramètres du service de balisage intelligent des ressources] de la configuration cloud dans [!DNL Experience Manager] pour configurer des balises intelligentes.

   ![Informations d’identification OAuth dans la Developer Console](assets/ims-configuration-developer-console.png)

### Créer la configuration du compte technique Adobe IMS {#create-ims-account-config}

Suivez les étapes ci-dessous pour créer la configuration du compte technique IMS :

1. Dans l’interface d’utilisation [!DNL Experience Manager], accédez à **[!UICONTROL Outils]** > **[!UICONTROL Sécurité]** > **[!UICONTROL Configurations d’Adobe IMS]**.

1. Cliquez sur **[!UICONTROL Créer]**.

1. Dans la boîte de dialogue Configuration du compte technique Adobe IMS, utilisez les valeurs suivantes :

   ![Fenêtre de configuration d’Adobe IMS](assets/adobe-ims-config.png)

   | Champ | Description |
   | -------- | ---------------------------- |
   | Solution cloud | Sélectionnez **[!UICONTROL Balises intelligentes]** dans le menu déroulant. |
   | Titre | Ajoutez le titre du compte IMS de configuration. |
   | Serveur d’autorisation | Ajouter `https://ims-na1.adobelogin.com` |
   | ID client | À fournir via l’[Adobe Developer Console](https://developer.adobe.com/console/). |
   | Secret client | À fournir via l’[Adobe Developer Console](https://developer.adobe.com/console/). |
   | Portée | À fournir via l’[Adobe Developer Console](https://developer.adobe.com/console/). |
   | ID d’organisation | À fournir via l’[Adobe Developer Console](https://developer.adobe.com/console/). |

1. Sélectionnez la configuration que vous avez créée et cliquez sur **[!UICONTROL Contrôle de l’intégrité]**.

1. Confirmez la boîte de dialogue du Contrôle de l’intégrité, puis cliquez sur Fermer une fois la configuration vérifiée comme saine.

### Créer une configuration {#configure-smart-content-service}

Pour configurer l’intégration, utilisez les valeurs d’[!UICONTROL ID DE COMPTE TECHNIQUE], d’[!UICONTROL ID D’ORGANISATION], de [!UICONTROL SECRET CLIENT] et d’[!UICONTROL ID CLIENT] à partir de l’intégration de la console Adobe Developer. La création d’une configuration cloud de balises intelligentes permet d’authentifier les demandes d’API provenant du déploiement [!DNL Experience Manager].

1. Dans [!DNL Experience Manager], accédez à **[!UICONTROL Outils]** > **[!UICONTROL Cloud Service]** > **[!UICONTROL Balise intelligente]** pour ouvrir les [!UICONTROL configurations de balise intelligente].

1. Cliquez sur **[!UICONTROL Créer]** pour créer une configuration. Autrement, cliquez sur **[!UICONTROL Propriétés]** pour mettre à jour la configuration existante.

1. Renseignez les champs suivants :

   ![Configuration des balises intelligentes](assets/smart-tags-config.png)

   | Champ | Description |
   | -------- | ---------------------------- |
   | Titre | Ajoutez le titre du compte IMS de configuration. |
   | Configuration Adobe IMS associée | Sélectionnez une configuration dans le menu déroulant. |
   | Service URL (URL du service) | `https://smartcontent.adobe.io/<region where your Experience Manager author instance is hosted>`. Par exemple, `https://smartcontent.adobe.io/apac`. Vous pouvez indiquer `na`, `emea`, ou `apac` comme les régions où votre instance d’auteur Experience Manager est hébergée. |

   >[!NOTE]
   >
   >Si le service géré Experience Manager est mis en service avant le 1er septembre 2022, utilisez l’URL de service suivante :
   >`https://mc.adobe.io/marketingcloud/smartcontent`

1. Cliquez sur **[!UICONTROL Enregistrer et fermer]**.

### Validation de la configuration {#validate-the-configuration}

Une fois la configuration terminée, vous pouvez utiliser un MBean JMX pour valider la configuration. Pour procéder à la validation, suivez ces étapes.

1. Accédez à votre serveur [!DNL Experience Manager] sur `https://[aem_server]:[port]`.

1. Accédez à **[!UICONTROL Outils]** > **[!UICONTROL Opérations]** > **[!UICONTROL Console Web]** pour ouvrir la console OSGi. Cliquez sur **[!UICONTROL Principal] > [!UICONTROL JMX]**.

<!--
1. Click `com.day.cq.dam.similaritysearch.internal.impl`. It opens **[!UICONTROL SimilaritySearch Miscellaneous Tasks]**.-->

1. Cliquez sur `com.day.cq.dam.similaritysearch.internal.impl (SCS)`.

   ![Fenêtre Mbean](assets/mbean.png)

1. Cliquez sur `validateConfigs()`. Dans la boîte de dialogue **[!UICONTROL Valider les configurations]**, cliquez sur **[!UICONTROL Invoquer]**.

Le résultat de la validation s’affiche dans la même boîte de dialogue.

### Activation du balisage intelligent dans le workflow [!UICONTROL Ressource de mise à jour de la gestion des ressources numériques] (Facultatif) {#enable-smart-tagging-in-the-update-asset-workflow-optional}

1. Dans [!DNL Experience Manager], accédez à **[!UICONTROL Outils]** > **[!UICONTROL Workflow]** > **[!UICONTROL Modèles]**.

1. Sur la page **[!UICONTROL Modèles de processus]**, sélectionnez le modèle de processus **[!UICONTROL Ressources de mise à jour de gestion des actifs numériques (DAM)]**.

1. Cliquez sur **[!UICONTROL Modifier]** dans la barre d’outils.

1. Développez le panneau latéral pour afficher les étapes. Faites glisser l’étape **[!UICONTROL Balisage intelligent de la ressource]** disponible dans la section Processus de DAM (gestion des actifs numériques) et placez-la après l’étape **[!UICONTROL Miniatures des processus]**.

   ![Ajout de l’étape Balisage intelligent de la ressource après l’étape Miniatures des processus dans le processus Ressources de mise à jour de gestion des actifs numériques (DAM)](assets/smart-tag-in-dam-update-asset-workflow.png)

1. Ouvrez les propriétés de l’étape pour modifier les détails. Dans **[!UICONTROL Paramètres avancés]**, vérifiez que l’option **[!UICONTROL Avance du gestionnaire]** est sélectionnée.

   ![Configuration du workflow de Ressource de mise à jour de la gestion des ressources numériques et ajout de l’étape de balisage intelligent](assets/smart-tag-step-properties-workflow1.png)

1. Dans l’onglet **[!UICONTROL Arguments]**, sélectionnez **[!UICONTROL Ignorer les erreurs]** si vous souhaitez que le workflow se termine même si l’étape de balisage automatique échoue.

   De plus, pour baliser les ressources lors de leur chargement, et ce, que le balisage intelligent soit activé ou non dans les dossiers, cochez la case **[!UICONTROL Ignorer l’indicateur de balise intelligente]**.

   ![Configuration du workflow de ressource de mise à jour de la gestion des ressources numériques pour ajouter l’étape de balisage intelligent et sélectionner l’avance du gestionnaire](assets/smart-tag-step-properties-workflow2.png)

1. Cliquez sur Terminé ![Icône Terminé](assets/do-not-localize/check-ok-done-icon.png) pour fermer l’étape du processus.

1. Cliquez sur **[!UICONTROL Synchroniser]** pour enregistrer le workflow.

## Entraînement du service de contenu dynamique {#training-the-smart-content-service}

Pour que le service de contenu dynamique reconnaisse votre taxonomie métier, exécutez-la sur une série de ressources qui incluent déjà des balises correspondant à votre entreprise. Pour baliser efficacement vos images de marque, le service de contenu dynamique requiert que les images d’entraînement respectent certaines instructions. Après l’entraînement, le service peut appliquer la même taxonomie à un ensemble de ressources similaire.

Vous pouvez entraîner le service plusieurs fois afin d’améliorer sa capacité à appliquer des balises pertinentes. Après chaque cycle d’entraînement, exécutez un workflow de balisage et vérifiez si vos ressources sont correctement balisées.

Vous pouvez entraîner le service de contenu intelligent périodiquement ou selon les besoins.

>[!NOTE]
>
>Le workflow d’entraînement s’exécute sur les dossiers uniquement.

### Instructions d’entraînement {#guidelines-for-training}

Pour un résultat optimal, les images de votre corpus d’entraînement respectent les instructions suivantes :

**Quantité et taille :** minimum 30 images par balise. Minimum 500 pixels sur le côté le plus long.

**Cohérence** : les images utilisées pour une balise spécifique sont visuellement similaires.

Par exemple, il est déconseillé d’incorporer une balise `my-party` pour toutes ces images (en situation d’entraînement), car elles ne sont pas similaires visuellement.

![Images d’illustration donnant un exemple d’instructions d’entraînement](/help/assets/assets/do-not-localize/coherence.png)

**Couverture** : les images d’entraînement doivent être suffisamment variées. L’idée est de fournir quelques exemples raisonnablement différents pour apprendre à Experience Manager à se concentrer sur les bons éléments. Si vous appliquez la même balise sur des images visuellement différentes, incluez au moins cinq exemples de chaque type.

Par exemple, pour la balise *mannequin-pose-tête-baissée*, incluez davantage d’images d’entraînement similaires à l’image mise en évidence ci-dessous pour que le service reconnaisse les images similaires avec plus de précision lors du balisage.

![Images d’illustration donnant un exemple d’instructions d’entraînement](/help/assets/assets/do-not-localize/coverage_1.png)

**Distraction/obstruction** : l’entraînement du service donne de meilleurs résultats sur les images qui ont moins de distractions (telles que des arrière-plans importants ou des objets/personnes sans lien avec le sujet principal).

Par exemple, pour la balise *chaussure-décontractée*, la seconde image n’est pas un bon candidat pour l’entraînement.

![Images d’illustration donnant un exemple d’instructions d’entraînement](/help/assets/assets/do-not-localize/distraction.png)

**Complétude :** si une image est admissible pour plusieurs balises, ajoutez toutes les balises applicables avant d’inclure l’image à des fins de formation. Par exemple, pour les balises telles que `raincoat` et `model-side-view`, ajoutez les deux balises sur la ressource éligible avant de l’inclure pour la formation.

![Images d’illustration donnant un exemple d’instructions d’entraînement](/help/assets/assets/do-not-localize/completeness.png)

>[!NOTE]
>
>La capacité du service de contenu dynamique à s’entraîner à partir de vos balises et à les appliquer à d’autres images dépend de la qualité des images que vous utilisez pour l’entraînement. Pour obtenir des résultats optimaux, Adobe recommande d’utiliser des images visuellement similaires afin d’entraîner le service pour chaque balise.

### Entraînement périodique {#periodic-training}

Vous pouvez activer le service de contenu dynamique afin qu’il s’entraîne périodiquement sur les ressources et les balises associées au sein d’un dossier. Ouvrez la page de [!UICONTROL Propriétés] de votre dossier de ressources, sélectionnez **[!UICONTROL Activer les balises intelligentes]** sous l’onglet **[!UICONTROL Détails]** et enregistrez les modifications.

![enable_smart_tags](assets/enable_smart_tags.png)

Lorsque cette option est sélectionnée pour un dossier, [!DNL Experience Manager] exécute automatiquement un workflow d’entraînement afin d’entraîner le service de contenu dynamique sur les ressources du dossier et leurs balises. Par défaut, le workflow d’entraînement s’exécute toutes les semaines à 00 h 30 le samedi.

### Entraînement à la demande {#on-demand-training}

Vous pouvez entraîner le service de contenu dynamique lorsque cela s’avère nécessaire à partir de la console de workflow.

1. Dans l’interface d’[!DNL Experience Manager], accédez à **[!UICONTROL Outils]** > **[!UICONTROL Workflow]** > **[!UICONTROL Modèles]**.
1. Dans la page **[!UICONTROL Modèles de workflow]**, sélectionnez le workflow **[!UICONTROL Entraînement des balises intelligentes]**, puis cliquez sur **[!UICONTROL Démarrer le workflow]** dans la barre d’outils.
1. Dans la boîte de dialogue **[!UICONTROL Exécuter le workflow]**, localisez le dossier de payload qui comprend les ressources balisées pour entraîner le service.
1. Indiquez le titre du workflow et ajoutez un commentaire. Cliquez ensuite sur **[!UICONTROL Exécuter]**. Les ressources et les balises sont soumises à l’entraînement.

   ![workflow_dialog](assets/workflow_dialog.png)

>[!NOTE]
>
>Une fois que les ressources figurant dans un dossier sont traitées pour l’entraînement, seules les ressources modifiées sont traitées au cours des cycles d’entraînement suivants.

### Affichage des rapports de formation {#viewing-training-reports}

Pour vérifier que le service de contenu dynamique est entraîné sur vos balises dans la série de ressources d’entraînement, examinez le rapport de workflow d’entraînement dans la console Rapports.

1. Dans l’interface [!DNL Experience Manager], accédez à **[!UICONTROL Outils]** > **[!UICONTROL Ressources]** > **[!UICONTROL Rapports]**.
1. Dans la page **[!UICONTROL Rapports de ressources]**, cliquez sur **[!UICONTROL Créer]**.
1. Sélectionnez le rapport **[!UICONTROL Entraînement des balises intelligentes]**, puis cliquez sur **[!UICONTROL Suivant]** dans la barre d’outils.
1. Indiquez un titre et une description pour le rapport. Sous **[!UICONTROL Planifier le rapport]**, laissez l’option **[!UICONTROL Maintenant]** sélectionnée. Si vous souhaitez planifier le rapport pour une date ultérieure, sélectionnez **[!UICONTROL Plus tard]** et spécifiez une date et une heure. Ensuite, cliquez sur **[!UICONTROL Créer]** dans la barre d’outils.
1. Dans la page **[!UICONTROL Rapports de ressources]**, sélectionnez le rapport que vous avez généré. Pour afficher le rapport, cliquez sur **[!UICONTROL Afficher]** dans la barre d’outils.
1. Passez en revue les détails du rapport.

   Le rapport affiche le statut d’identification des balises que vous avez entraînées. La couleur verte de la colonne **[!UICONTROL État de l’entraînement]** indique que le service de contenu dynamique est entraîné pour la balise. La couleur jaune indique que le service n’est pas complètement entraîné pour une balise particulière. Dans ce cas, ajoutez d’autres images avec la balise particulière et exécutez le workflow d’entraînement pour l’entraînement complet du service sur la balise.

   Si vous ne voyez pas vos balises dans ce rapport, lancez à nouveau le workflow d’entraînement pour ces balises.

1. Pour télécharger le rapport, sélectionnez-le dans la liste, puis cliquez sur **[!UICONTROL Télécharger]** dans la barre d’outils. Le rapport est téléchargé sous la forme d’une feuille de calcul Microsoft Excel.

## Limites {#limitations}

* Le balisage intelligent amélioré est basé sur des modèles d’apprentissage d’images et de leurs balises. Ces modèles ne sont pas toujours parfaits pour identifier les balises. La version actuelle du service de contenu dynamique présente les limites suivantes :

   * Impossibilité d’identifier des différences subtiles dans les images. Par exemple, des chemises coupe droite ou ajustée.
   * Impossibilité d’identifier des balises basées sur des motifs ou des éléments minuscules d’une image. Par exemple, des logos sur des t-shirts.
   * Le balisage est pris en charge dans les paramètres régionaux gérés par [!DNL Experience Manager].

* Pour rechercher des ressources à l’aide de balises intelligentes (standard ou améliorées), utilisez la recherche de texte intégral d’[!DNL Assets]. Il n’y a aucun prédicat de recherche distinct pour les balises intelligentes.

>[!MORELIKETHIS]
>
>* [Vue d’ensemble et entraînement des balises intelligentes](enhanced-smart-tags.md)
>* [Dépanner les balises intelligentes pour les informations d’identification OAuth](config-oauth.md)
>* [Tutoriel vidéo sur les balises intelligentes](https://experienceleague.adobe.com/docs/experience-manager-learn/assets/metadata/image-smart-tags.html?lang=fr)
