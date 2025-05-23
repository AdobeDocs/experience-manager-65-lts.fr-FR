---
title: Création de modèles de workflow
description: Vous créez un modèle de workflow pour définir les étapes exécutées lorsqu’un utilisateur ou une utilisatrice lance le workflow.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: extending-aem
content-type: reference
docset: aem65
solution: Experience Manager, Experience Manager Sites
feature: Developing
role: Developer
exl-id: 7822a108-f128-4ccf-bd9f-348f0c2688da
source-git-commit: c3e9029236734e22f5d266ac26b923eafbe0a459
workflow-type: tm+mt
source-wordcount: '2462'
ht-degree: 100%

---

# Création de modèles de workflow{#creating-workflow-models}

>[!CAUTION]
>
>Pour utiliser l’interface utilisateur classique, reportez-vous à la [documentation AEM 6.3](https://helpx.adobe.com/fr/experience-manager/6-3/help/sites-developing/workflows-models.html) à titre de référence.

Vous créez un [modèle de workflow](/help/sites-developing/workflows.md#model) pour définir les étapes exécutées lorsqu’un utilisateur lance le workflow. Vous pouvez également définir des propriétés de modèle pour déterminer, par exemple, si le workflow est transitoire ou s’il utilise plusieurs ressources.

Lorsqu’un utilisateur ou une utilisatrice démarre un workflow, une instance est lancée. Il s’agit du modèle d’exécution correspondant, créé lorsque vous [synchronisez](#sync-your-workflow-generate-a-runtime-model) vos modifications.

## Créer un workflow {#creating-a-new-workflow}

Lorsque vous créez un modèle de workflow pour la première fois, il contient :

* Les étapes **Début de flux** et **Fin de flux**.
Ces étapes représentent le début et la fin du workflow. Elles sont obligatoires et ne peuvent pas être modifiées ni supprimées.
* Un exemple d’étape **Participant**, dont le nom est **Étape 1**.
Cette étape est configurée pour affecter un élément de travail à l’initiateur de workflow. Vous pouvez modifier ou supprimer cette étape et y ajouter d’autres étapes suivant les besoins.

Pour créer un workflow avec l’éditeur, procédez comme suit :

1. Ouvrez la console **Modèles de workflow** via **Outils**, **Workflow**, **Modèles**, ou, par exemple : [https://localhost:4502/aem/workflow](https://localhost:4502/aem/workflow).
1. Sélectionnez **Créer**, puis **Créer un modèle**.
1. La boîte de dialogue **Ajouter un modèle de workflow** s’ouvre. Saisissez le **Titre** et le **Nom** (facultatif) avant de sélectionner **Terminé**.
1. Le nouveau modèle est répertorié dans la console **Modèles de workflow**.
1. Sélectionnez votre nouveau workflow, puis utilisez [**Modifier** pour l’ouvrir à des fins de configuration](#editinganexistingworkflow) :
   ![wf-01](assets/wf-01.png)

>[!NOTE]
>
>Si vous créez des modèles par programmation (à l’aide d’un package crx), vous pouvez également créer un sous-dossier à l’intérieur de ceux-ci :
>
>`/var/workflow/models`
>
>Par exemple, `/var/workflow/models/prototypes`
>
>Ce dossier peut ensuite être utilisé pour [gérer l’accès aux modèles de ce dossier](/help/sites-administering/workflows-managing.md#create-a-subfolder-in-var-workflow-models-and-apply-the-acl-to-that).

## Modifier un workflow {#editing-a-workflow}

Vous pouvez modifier n’importe quel modèle de workflow existant pour :

* [définir des étapes](#addingasteptoamodel-) et leurs [paramètres](#configuring-a-workflow-step) ;
* configurer les propriétés du workflow, notamment les [phases](#configuring-workflow-stages-that-show-workflow-progress), [si le workflow est transitoire](#creatingatransientworkflow-) et/ou s’il [utilise plusieurs ressources](#configuring-a-workflow-for-multi-resource-support) ;

La modification d’un [**workflow (prêt à l’emploi) par défaut et/ou hérité**](#editing-a-default-or-legacy-workflow-for-the-first-time) comporte une étape supplémentaire pour s’assurer qu’une [copie sécurisée](/help/sites-developing/workflows-best-practices.md#locations-workflow-models) est effectuée avant l’application de vos modifications.

Lorsque les mises à jour de votre workflow sont terminées, vous devez utiliser **Synchroniser** pour **Générer un modèle d’exécution**. Voir [Synchroniser votre workflow](#sync-your-workflow-generate-a-runtime-model) pour plus d’informations.

### Synchroniser votre workflow : générer un modèle d’exécution {#sync-your-workflow-generate-a-runtime-model}

**Synchroniser** (à droite dans la barre d’outils de l’éditeur) génère un [modèle d’exécution](/help/sites-developing/workflows.md#runtime-model). Le modèle d’exécution est le modèle réellement utilisé lorsqu’un utilisateur ou une utilisatrice démarre un workflow. Si vous ne **synchronisez** pas vos modifications, elles ne seront pas disponibles au moment de l’exécution.

Lorsque vous (ou toute autre personne) apportez des modifications au workflow, vous devez utiliser **Synchroniser** pour générer un modèle d’exécution, même lorsque des boîtes de dialogue individuelles (par exemple, pour les étapes) disposent de leurs propres options d’enregistrement.

Lorsque les modifications sont synchronisées avec le modèle d’exécution (enregistré), **Synchronisé** s’affiche à la place.

Certaines étapes comportent des champs obligatoires et/ou une validation intégrée. Lorsque ces conditions ne sont pas remplies, une erreur s’affiche quand vous tentez de **Synchroniser** le modèle. Par exemple, si aucun participant n’a été défini pour une étape **Participant** :

![wf-21](assets/wf-21.png)

### Modifier un workflow par défaut ou hérité pour la première fois {#editing-a-default-or-legacy-workflow-for-the-first-time}

Lorsque vous ouvrez un [Modèle par défaut et/ou hérité](/help/sites-developing/workflows.md#workflow-types) pour modification :

* le navigateur d’étapes n’est pas disponible (côté gauche) ;
* une action **Modifier** est disponible dans la barre d’outils (côté droit).
* Au départ, le modèle et ses propriétés sont présentés en mode lecture seule comme suit :
   * Les workflows par défaut sont situés dans `/libs`.
   * Les workflows hérités se trouvent dans `/etc`.
Sélectionner **Modifier** aura les effets suivants :
* une copie du workflow est réalisée dans `/conf` ;
* le navigateur d’étapes devient accessible ;
* vous pourrez effectuer des modifications.

>[!NOTE]
>
>Pour plus d’informations, consultez la section [Emplacements des modèles de workflow](/help/sites-developing/workflows-best-practices.md#locations-workflow-models).

![wf-22](assets/wf-22.png)

### Ajouter une étape à un modèle {#adding-a-step-to-a-model}

Ajoutez des étapes à votre modèle pour représenter l’activité à exécuter : chaque étape effectue une activité spécifique. Il est possible de sélectionner des composants d’étape dans une instance AEM standard.

Lorsque vous modifiez un modèle, les étapes disponibles s’affichent dans les différents groupes de l’**Explorateur d’étapes**. Par exemple :

![wf-10](assets/wf-10.png)

>[!NOTE]
>
>Pour plus d’informations sur les composants d’étape principaux installés avec AEM, consultez [Référence des étapes du workflow](/help/sites-developing/workflows-step-ref.md).

Pour ajouter des étapes à votre modèle de workflow :

1. Ouvrez un modèle de workflow existant pour le modifier. Sélectionnez le modèle souhaité dans la console **Modèle de workflow**, puis cliquez sur **Modifier**.
1. Ouvrez le l’explorateur d’étapes à l’aide de l’option **Activer/désactiver le panneau latéral**, à l’extrémité gauche de la barre d’outils supérieure. Vous pouvez effectuer les opérations suivantes :

   * Utiliser le **Filtre** pour trouver des étapes spécifiques.
   * Utilisez le sélecteur de la liste déroulante pour limiter la sélection à un groupe d’étapes spécifique.
   * Sélectionnez l’icône Afficher la description ![wf-stepinfo-icon](assets/wf-stepinfo-icon.png) pour afficher des informations plus détaillées sur l’étape appropriée.

   ![wf-02](assets/wf-02.png)

1. Faites glisser la ou les étapes appropriées vers l’emplacement requis dans le modèle.

   Par exemple, une **Étape du participant**.

   Une fois l’étape ajoutée au flux, vous pouvez [la configurer](#configuring-a-workflow-step).

   ![wf-03](assets/wf-03.png)

1. Ajoutez autant d’étapes ou d’autres mises à jour que nécessaire.

   Au moment de l’exécution, les étapes sont exécutées dans l’ordre dans lequel elles apparaissent dans le modèle. Après avoir ajouté des composants d’étape, vous pouvez les faire glisser vers un autre emplacement dans le modèle.

   Vous pouvez également copier, couper, coller, regrouper ou supprimer des étapes existantes, comme avec la fonction [éditeur de page](/help/sites-authoring/editing-content.md).

   Les étapes de division peuvent également être réduites/développées à l’aide de l’option de barre d’outils : ![wf-collapseexpand-toolbar-icon](assets/wf-collapseexpand-toolbar-icon.png).

1. Confirmez les modifications à l’aide de l’option **Synchronisation** (barre d’outils de l’éditeur) afin de générer le modèle d’exécution.

   Voir [Synchroniser votre workflow](#sync-your-workflow-generate-a-runtime-model) pour plus d’informations.

### Configurer une étape de workflow {#configuring-a-workflow-step}

Vous pouvez **configurer** et personnaliser le comportement d’une étape de workflow à l’aide de la boîte de dialogue **Propriétés de l’étape**.

1. Pour ouvrir la boîte de dialogue **Propriétés de l’étape** pour une étape :

   * Cliquez sur l’étape* *dans le modèle de workflow et sélectionnez ensuite **Configurer** dans la barre d’outils du composant.

   * Double-cliquez sur l’étape.

   >[!NOTE]
   >
   >Pour plus d’informations sur les composants d’étape principaux installés avec AEM, consultez [Référence des étapes du workflow](/help/sites-developing/workflows-step-ref.md).

1. Configurez les **Propriétés de l’étape** selon les besoins ; les propriétés disponibles dépendent du type d’étape. Plusieurs onglets peuvent également être disponibles. Par exemple, l’étape **Étape de participant** par défaut présent dans un nouveau workflow sous la forme `Step 1` :

   ![wf-11](assets/wf-11.png)

1. Appuyez sur la coche pour confirmer vos mises à jour.
1. Confirmez les modifications à l’aide de l’option **Synchronisation** (barre d’outils de l’éditeur) afin de générer le modèle d’exécution.

   Pour plus d’informations, voir [Synchroniser votre workflow](#sync-your-workflow-generate-a-runtime-model).

### Créer un workflow transitoire {#creating-a-transient-workflow}

Vous pouvez créer un modèle de workflow [Transitoire](/help/sites-developing/workflows.md#transient-workflows) lors de la création d’un modèle ou en modifiant un modèle existant :

1. Ouvrez le modèle de workflow pour le [modifier](#editinganexistingworkflow).
1. Sélectionnez **Propriétés du modèle de workflow** dans la barre d’outils.
1. Dans la boîte de dialogue, activez **Workflow transitoire** (ou désactivez cette option si nécessaire) :

   ![wf-07](assets/wf-07.png)

1. Confirmez la modification à l’aide de l’option **Enregistrer et fermer**, suivie de **Synchronisation** (barre d’outils de l’éditeur) pour générer le modèle d’exécution.

   Pour plus d’informations, voir [Synchroniser votre workflow](#sync-your-workflow-generate-a-runtime-model).

>[!NOTE]
>
>Lorsque vous exécutez un workflow en mode [transitoire](/help/sites-developing/workflows.md#transient-workflows), AEM ne stocke aucun historique de workflow. Par conséquent, la [Chronologie](/help/sites-authoring/basic-handling.md#timeline) n’affiche aucune information relative au workflow.

## Mise à disposition des modèles de workflow dans l’interface utilisateur tactile {#classic2touchui}

Si un modèle de workflow présent dans l’interface utilisateur classique est absent du menu contextuel de sélection dans le rail **[!UICONTROL Chronologie]** de l’interface utilisateur tactile, effectuez la configuration pour la rendre disponible. Les étapes suivantes illustrent l’utilisation du modèle de workflow appelé **[!UICONTROL Demande d’activation]**.

1. Vérifiez que le modèle n’est pas disponible dans l’interface utilisateur tactile. Accédez à une ressource à l’aide du chemin `/assets.html/content/dam`. Sélectionnez une ressource. Ouvrez **[!UICONTROL Chronologie]** dans le rail gauche. Cliquez sur **[!UICONTROL Démarrer le workflow]** et confirmez que le modèle **[!UICONTROL Demande d’activation]** n’est pas présent dans la liste contextuelle.

1. Accédez à **[!UICONTROL Outils > Général > Balisage]**. Sélectionnez **[!UICONTROL Workflow]**.

1. Sélectionnez **[!UICONTROL Créer > Créer une balise]**. Définissez le **[!UICONTROL titre]** comme `DAM` et le **[!UICONTROL nom]** comme `dam`. Sélectionnez **[!UICONTROL Envoyer]**.
   ![Créer une balise dans le modèle de workflow](assets/workflow_create_tag.png)

1. Accédez à **[!UICONTROL Outils > Workflows > Modèles]**. Sélectionnez **[!UICONTROL Demande d’activation]**, puis **[!UICONTROL Modifier]**.

1. Sélectionnez **[!UICONTROL Modifier]**, ouvrez le menu **[!UICONTROL Informations sur la page]** et, à partir de là, sélectionnez l’onglet **[!UICONTROL Ouvrir les propriétés]** et accédez à l’onglet **[!UICONTROL De base]** (s’il n’est pas déjà ouvert).

1. Ajoutez `Workflow : DAM` dans le champ **[!UICONTROL Balises]**. Confirmez la sélection en activant la case à cocher.

1. Confirmez l’ajout de la balise en sélectionnant **[!UICONTROL Enregistrer et fermer]**.
   ![Modifier les propriétés de page du modèle](assets/workflow_model_edit_activation1.png)

1. Terminez la procédure en sélectionnant **[!UICONTROL Synchronisation]**. Le workflow est désormais disponible dans l’interface utilisateur tactile.

### Configurer un workflow pour prendre en charge plusieurs ressources {#configuring-a-workflow-for-multi-resource-support}

Vous pouvez configurer un modèle de workflow pour [prendre en charge plusieurs ressources](/help/sites-developing/workflows.md#multi-resource-support) lors de la création d’un modèle ou en modifiant un modèle existant :

1. Ouvrez le modèle de workflow pour le [modifier](#editinganexistingworkflow).
1. Sélectionnez **Propriétés du modèle de workflow** dans la barre d’outils.

1. Dans la boîte de dialogue, activez **Prise en charge multi-ressource** (ou désactivez cette option si nécessaire) :

   ![wf-08](assets/wf-08.png)

1. Confirmez la modification à l’aide de l’option **Enregistrer et fermer**, suivie de **Synchronisation** (barre d’outils de l’éditeur) pour générer le modèle d’exécution.

   Voir [Synchroniser votre workflow](#sync-your-workflow-generate-a-runtime-model) pour plus d’informations.

### Configurer les étapes de workflow (qui affichent la progression du workflow) {#configuring-workflow-stages-that-show-workflow-progress}

[Les phases de workflow](/help/sites-developing/workflows.md#workflow-stages) permettent de visualiser la progression d’un workflow lors de la gestion des tâches.

>[!CAUTION]
>
>Si les phases du workflow sont définies dans **Propriétés de la page**, mais ne sont pas utilisées pour les étapes du workflow, la barre de progression n’affichera aucune progression (quelle que soit l’étape actuelle du workflow).

Les phases à mettre à disposition sont définies dans les modèles de workflow ; les modèles de workflow existants peuvent être mis à jour pour inclure des définitions de partie. Vous pouvez définir un nombre illimité de phases pour le modèle de workflow.

Pour définir les **Phases** pour votre workflow :

1. Ouvrez le modèle de workflow à modifier.
1. Sélectionnez **Propriétés du modèle de workflow** dans la barre d’outils. Ouvrez ensuite l’onglet **Phases**.
1. Ajoutez (et positionnez) les **Phases** souhaitées. Vous pouvez définir un nombre illimité de phases pour le modèle de workflow.

   Par exemple :

   ![wf-08-1](assets/wf-08-1.png)

1. Cliquez sur **Enregistrer et fermer** pour enregistrer les propriétés.
1. Attribuez une phase à chacune des étapes du modèle de workflow. Par exemple :

   ![wf-09](assets/wf-09.png)

   Une phase peut être affectée à plusieurs étapes. Par exemple :

   | **Étape** | **Phase** |
   |---|---|
   | Étape 1 | Création |
   | Étape 2 | Création |
   | Étape 3 | Révision |
   | Étape 4 | Approuver |
   | Étape 5 | Approuver |
   | Étape 6 | Terminer |

1. Confirmez les modifications à l’aide de l’option **Synchronisation** (barre d’outils de l’éditeur) afin de générer le modèle d’exécution.

   Pour plus d’informations, voir [Synchroniser votre workflow](#sync-your-workflow-generate-a-runtime-model).

## Exporter un modèle de workflow dans un package {#exporting-a-workflow-model-in-a-package}

Pour exporter un modèle de workflow dans un package, procédez comme suit :

1. Créez un package à l’aide du [Gestionnaire de modules](/help/sites-administering/package-manager.md#package-manager) :

   1. Accédez au Gestionnaire de modules via **Outils**, **Déploiement**, **Packages**.

   1. Cliquez sur **Créer un package**.
   1. Spécifiez le **Nom du module**, ainsi que tout autre détail selon les besoins.
   1. Cliquez sur **OK**.

1. Cliquez sur **Modifier** dans la barre d’outils de votre nouveau package. 

1. Ouvrez l’onglet **Filtres**.

1. Sélectionnez **Ajouter un filtre** et indiquez le chemin d’accès de la *conception* de votre modèle de workflow :

   `/conf/global/settings/workflow/models/<*your-model-name*>`

   Cliquez sur **Terminé**.

1. Sélectionnez **Ajouter un filtre** et indiquez le chemin d’accès de votre modèle de workflow *d’exécution* :

   `/var/workflow/models/<*your-model-name*>`

   Cliquez sur **Terminé**.

1. Ajoutez des filtres supplémentaires pour tous les scripts personnalisés utilisés par votre modèle.
1. Cliquez sur **Enregistrer** pour confirmer vos définitions de filtre.
1. Sélectionnez **Compilation** dans la barre d’outils de votre définition de package.
1. Sélectionnez **Télécharger** dans la barre d’outils du package.

## Utiliser des workflows pour traiter les envois de formulaire {#using-workflows-to-process-form-submissions}

Vous pouvez configurer un formulaire pour qu’il soit traité par le workflow sélectionné. Lorsque les utilisateurs ou les utilisatrices envoient le formulaire, une nouvelle instance de workflow est créée avec les données de l’envoi du formulaire servant de payload.

Pour configurer le workflow à utiliser avec votre formulaire :

1. Créez une page et ouvrez-la pour modification.
1. Ajoutez un composant **Formulaire** à la page.
1. **Configurez** le composant **Début du formulaire** qui s’est affiché dans la page.
1. Utilisez **Démarrer le workflow** pour sélectionner le workflow de votre choix parmi ceux qui sont disponibles :

   ![wf-12](assets/wf-12.png)

1. Confirmez la nouvelle configuration du formulaire en cochant la case.

## Tester les workflows {#testing-workflows}

Lors du test d’un workflow, il est recommandé d’utiliser divers types de payload, notamment des types différents de ceux pour lesquels il a été développé. Par exemple, si vous souhaitez que votre workflow traite les ressources, testez-le en définissant une Page comme payload et assurez-vous qu’il ne génère pas d’erreurs.

Par exemple, testez votre nouveau workflow comme suit :

1. [Démarrez votre modèle de workflow](/help/sites-administering/workflows-starting.md) à partir de la console.
1. Définissez le **payload** et confirmez-le.

1. Prenez les mesures nécessaires pour que le workflow avance.
1. Surveillez les fichiers journaux pendant l’exécution du workflow.

Vous pouvez également configurer AEM pour qu’il affiche des messages **DEBUG** dans les fichiers journaux. Pour plus d’informations, consultez la section [Journalisation](/help/sites-deploying/configure-logging.md). Une fois le développement terminé, redéfinissez le **Niveau de journal** sur **Infos**.

## Exemples {#examples}

### Exemple : création d’un workflow (simple) pour accepter ou refuser une demande de publication {#example-creating-a-simple-workflow-to-accept-or-reject-a-request-for-publication}

Pour illustrer certaines des possibilités de création d’un workflow, l’exemple suivant crée une variante du workflow `Publish Example`.

1. [Créez un modèle de workflow](#creating-a-new-workflow).

   Le nouveau workflow contiendra :

   * **Début de flux**
   * `Step 1`
   * **Fin de flux**

1. Supprimez `Step 1` (car ce type d’étape n’est pas correct pour cet exemple) :

   * Cliquez sur l’étape et sélectionnez ensuite **Supprimer** dans la barre d’outils du composant. Confirmez l’action.

1. Dans la sélection de **Workflow** du navigateur d’étapes, faites glisser une **Étape de participant** sur le workflow et positionnez-la entre **Début de flux** et **Fin de flux**.
1. Pour ouvrir la boîte de dialogue des propriétés, deux possibilités s’offrent à vous :

   * Cliquez sur l’étape de participant et sélectionnez ensuite **Configurer** dans la barre d’outils du composant.
   * Double-cliquez sur l’étape du participant ou de la participante.

1. Dans l’onglet **Commun**, saisissez `Validate Content` pour le **Titre** et la **Description**.
1. Ouvrez l’onglet **Utilisateur/Groupe** :

   * Activez **Avertir l’utilisateur ou l’utilisatrice par e-mail**.
   * Sélectionnez `Administrator` (`admin`) pour le champ **Utilisateur/Groupe**.

   >[!NOTE]
   >
   >Pour envoyer des e-mails, [les détails du service de messagerie et du compte utilisateur ou utilisatrice doivent être configurés](/help/sites-administering/notification.md).

1. Appuyez sur la coche pour confirmer les mises à jour.

   Vous revenez alors à l’aperçu du modèle de workflow. L’étape de participant y a été renommée `Validate Content`.

1. Faites glisser une **Division OU** sur le workflow et positionnez-la entre `Validate Content` et **Fin de flux**.
1. Ouvrez la **Division OU** pour la configuration.
1. Configurez les éléments suivants :

   * **Commun** : précisez le nom de la division.
   * **Branche 1** : sélectionnez **Itinéraire par défaut**.

   * **Branche 2** : vérifiez que **Itinéraire par défaut** n’est pas sélectionné.

1. Confirmez vos mises à jour de la **Division OU**.
1. Faites glisser une **Étape de participant ou participante** sur la branche de gauche, ouvrez les propriétés, spécifiez les valeurs suivantes, puis confirmez les modifications :

   * **Titre** : `Reject Publish Request`

   * **Utilisateur/Groupe** : par exemple, `projects-administrators`

   * **Avertir l’utilisateur par e-mail** : activez cette option pour que l’utilisateur soit averti par e-mail.

1. Faites glisser une **Étape du processus** sur la branche de droite, ouvrez les propriétés, spécifiez les valeurs suivantes, puis confirmez les modifications :

   * **Titre** : `Publish Page as Requested`

   * **Processus** : sélectionnez `Activate Page`. Ce processus publie la page sélectionnée sur les instances d’éditeur.

1. Cliquez sur **Synchronisation** (barre d’outils de l’éditeur) pour générer le modèle d’exécution.

   Voir [Synchroniser votre workflow](#sync-your-workflow-generate-a-runtime-model) pour plus d’informations.

   Votre nouveau modèle de workflow ressemblera à ceci :

   ![wf-13](assets/wf-13.png)

1. Appliquez ce workflow à votre page, de sorte que lorsque l’utilisateur définit l’étape **Valider le contenu** sur **Terminé**, il peut choisir s’il souhaite **Publier la page comme demandé** ou **Rejeter la demande de publication**.

   ![chlimage_1-72](assets/chlimage_1-72.png)

### Exemple : définition d’une règle pour une division OU à l’aide d’un script ECMA {#defineruleecmascript}

Les étapes **Division OU** vous permettent d’introduire des chemins de traitement conditionnel dans votre workflow.

Pour définir une règle OU, procédez comme suit :

1. Créez deux scripts et enregistrez-les dans le référentiel, par exemple sous :

   `/apps/myapp/workflow/scripts`

   >[!NOTE]
   >
   >Les scripts doivent comporter une [fonction `check()`](#function-check) qui renvoie une valeur booléenne.

1. Modifiez le workflow et ajoutez la **Division OU** au modèle.
1. Modifiez les propriétés de la **Branche 1** de la **Division OU** :

   * Définissez-la comme **Itinéraire par défaut** en configurant la **Valeur** sur `true`.

   * Dans **Règle**, définissez le chemin d’accès au script. Par exemple :
     `/apps/myapp/workflow/scripts/myscript1.ecma`

   >[!NOTE]
   >
   >Vous pouvez changer l’ordre des branches si nécessaire.

1. Modifiez les propriétés de la **Branche 2** de la **Division OU**.

   * En tant que **Règle**, définissez le chemin d’accès à l’autre script. Par exemple :
     `/apps/myapp/workflow/scripts/myscript2.ecma`

1. Définissez les propriétés des différentes étapes de chaque branche. Assurez-vous que la valeur **Utilisateur/Groupe** est définie.
1. Cliquez sur **Synchronisation** (barre d’outils de l’éditeur) pour conserver vos modifications dans le modèle d’exécution.

   Pour plus d’informations, voir [Synchroniser votre workflow](#sync-your-workflow-generate-a-runtime-model).

#### Fonction Check() {#function-check}

>[!NOTE]
>
>Voir [Utiliser ECMAScript](/help/sites-developing/workflows-customizing-extending.md#using-ecmascript).

L’exemple de script suivant renvoie la valeur `true` si le nœud est un `JCR_PATH` situé sous `/content/we-retail/us/en` :

```
function check() {
    if (workflowData.getPayloadType() == "JCR_PATH") {
      var path = workflowData.getPayload().toString();
      var node = jcrSession.getItem(path);

      if (node.getPath().indexOf("/content/we-retail/us/en") >= 0) {
       return true;
      } else {
       return false;
      }
     } else {
      return false;
     }
}
```

### Exemple : demande d’activation personnalisée {#example-customized-request-for-activation}

Vous pouvez personnaliser n’importe lequel des workflows personnalisés. Pour appliquer un comportement personnalisé, superposez les détails du workflow approprié.

Par exemple : **Demande d’activation**. Ce workflow est utilisé pour publier des pages dans **Sites** et est déclenché automatiquement lorsqu’un auteur ou une autrice de contenu ne dispose pas des droits de réplication appropriés. Pour plus d’informations, consultez la section [Personnalisation de la création de pages – Personnalisation du workflow de Demande d’activation](/help/sites-developing/customizing-page-authoring-touch.md#customizing-the-request-for-activation-workflow).
