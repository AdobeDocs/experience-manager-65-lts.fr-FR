---
title: Prise en charge de nouveaux paramètres régionaux pour la localisation de formulaires adaptatifs
description: AEM Forms vous permet d’ajouter de nouveaux paramètres régionaux pour localiser les formulaires adaptatifs. Les paramètres régionaux pris en charge par défaut sont l’anglais, le français, l’allemand et le japonais.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: Configuration
docset: aem65
feature: Adaptive Forms,Foundation Components
role: Admin,User
solution: Experience Manager, Experience Manager Forms
exl-id: 9c516c90-1b1d-406a-b42d-909aae8bb634
source-git-commit: c3e9029236734e22f5d266ac26b923eafbe0a459
workflow-type: tm+mt
source-wordcount: '832'
ht-degree: 100%

---

# Prise en charge de nouveaux paramètres régionaux pour la localisation de formulaires adaptatifs{#supporting-new-locales-for-adaptive-forms-localization}

| Version | Lien de l’article |
| -------- | ---------------------------- |
| AEM as a Cloud Service | [Cliquez ici](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-foundation-components/supporting-new-language-localization.html?lang=fr) |
| AEM 6.5 | Cet article |

## À propos des dictionnaires de paramètres régionaux {#about-locale-dictionaries}

La localisation des formulaires adaptatifs repose sur deux types de dictionnaires de paramètres régionaux : 

**Dictionnaire spécifique au formulaire** : il contient des chaînes utilisées dans des formulaires adaptatifs. Par exemple, étiquettes, noms de champs, messages d’erreur, descriptions d’aide, etc. Il est géré sous forme de jeu de fichiers XLIFF pour chaque jeu de paramètres régionaux et accessible à l’adresse `https://<host>:<port>/libs/cq/i18n/translator.html`.

**Dictionnaires globaux** : la bibliothèque client AEM comporte deux dictionnaires globaux, gérés en tant qu’objets JSON. Ces dictionnaires contiennent les messages d’erreur par défaut, les noms des mois, les symboles de devise, les modèles de date et d’heure, etc. Vous pouvez trouver ces dictionnaires dans CRXDe Lite, à l’adresse /libs/fd/xfaforms/clientlibs/I18N. Ces emplacements contiennent des dossiers distincts pour chaque jeu de paramètres régionaux. Étant donné que les dictionnaires globaux ne sont généralement pas mis à jour fréquemment, conserver des fichiers JavaScript distincts pour chaque jeu de paramètres régionaux permet aux navigateurs de les mettre en cache et de réduire l’utilisation de la bande passante du réseau lors de l’accès à différents formulaires adaptatifs sur le même serveur.

### Comment fonctionne la localisation des formulaires adaptatifs  {#how-localization-of-adaptive-form-works}

Deux méthodes permettent d’identifier les paramètres régionaux du formulaire adaptatif. Lors du rendu d’un formulaire adaptatif, il identifie les paramètres régionaux nécessaires en :

* examinant le sélecteur `[local]` dans l’URL du formulaire adaptatif. Le format d’URL est le suivant : `http://host:port/content/forms/af/[afName].[locale].html?wcmmode=disabled`. L’utilisation du sélecteur `[local]` permet de mettre en cache un formulaire adaptatif.

* en examinant les paramètres ci-dessous dans l’ordre spécifié :

   * Paramètre de requête `afAcceptLang`
Pour remplacer la langue du navigateur des utilisateurs et des utilisatrices, vous pouvez transmettre le paramètre de requête `afAcceptLang` afin de forcer les paramètres régionaux. Par exemple, l’URL ci-dessous a forcé le rendu du formulaire dans les paramètres régionaux japonais :
     `https://'[server]:[port]'/<contextPath>/<formFolder>/<formName>.html?wcmmode=disabled&afAcceptLang=ja`

   * La langue du navigateur défini pour l’utilisateur, qui est spécifiée dans la demande par le biais de l’en-tête `Accept-Language`.

   * Paramètre de langue de l’utilisateur spécifié dans AEM.

   * Les paramètres régionaux du navigateur sont activés par défaut. Pour modifier les paramètres régionaux du navigateur :
      * Ouvrez Configuration Manager. L’URL est `http://[server]:[port]/system/console/configMgr`
      * Recherchez et ouvrez la configuration **[!UICONTROL du canal Web du formulaire adaptatif et de la communication interactive]**.
      * Modifiez le statut de l’option **[!UICONTROL Utiliser les paramètres régionaux du navigateur]** et **[!UICONTROL enregistrez]** la configuration.

Une fois que le paramètre régional est identifié, le formulaire adaptatif sélectionne le dictionnaire qui lui est spécifique. Si le dictionnaire spécifique au formulaire pour les paramètres régionaux nécessaires est introuvable, il utilise le dictionnaire de la langue dans laquelle le formulaire adaptatif a été créé.

En l’absence d’informations sur les paramètres régionaux, le formulaire adaptatif est distribué dans la langue d’origine du formulaire. La langue d’origine est la langue utilisée lors du développement du formulaire adaptatif.

S’il n’existe pas de bibliothèque cliente pour les paramètre régional nécessaire, il cherche une bibliothèque cliente correspondant au code de langue présent dans le paramètre régional. Par exemple, si le paramètre régional demandé est `en_ZA` (anglais d’Afrique du Sud) et qu’il n’existe pas de bibliothèque cliente correspondant à `en_ZA`, le formulaire adaptatif utilise la bibliothèque cliente correspondant à langue `en` (anglais), si elle existe. Toutefois, si aucune de ces bibliothèques n’existe, le formulaire adaptatif utilise le dictionnaire correspondant au paramètre régional `en`.

## Ajoutez la localisation pour les paramètres régionaux non pris en charge {#add-localization-support-for-non-supported-locales}

AEM Forms prend actuellement en charge la localisation du contenu des formulaires adaptatifs vers l’anglais (en), l’espagnol (es), le français (fr), l’italien (it), l’allemand (de), le japonais (ja), le portugais du Brésil (pt-BR), le chinois (zh-CN), le chinois de Taïwan (zh-TW) et le coréen (ko-KR).

Pour ajouter un nouveau paramètre régional lors de l’exécution des formulaires adaptatifs :

1. [Ajouter des paramètres régionaux au service GuideLocalizationService](../../forms/using/supporting-new-language-localization.md#p-add-a-locale-to-the-guide-localization-service-br-p)

1. [Ajouter une bibliothèque XFA cliente pour des paramètres régionaux](../../forms/using/supporting-new-language-localization.md#p-add-xfa-client-library-for-a-locale-br-p)

1. [Ajouter la bibliothèque cliente de formulaires adaptatifs pour un paramètre régional](../../forms/using/supporting-new-language-localization.md#p-add-adaptive-form-client-library-for-a-locale-br-p)
1. [Ajouter la prise en charge des paramètres régionaux pour la langue du dictionnaire](../../forms/using/supporting-new-language-localization.md#p-add-locale-support-for-the-dictionary-br-p)
1. [Redémarrer le serveur](../../forms/using/supporting-new-language-localization.md#p-restart-the-server-p)

### Ajouter des paramètres régionaux au Guide Localization Service {#add-a-locale-to-the-guide-localization-service-br}

1. Accédez à `https://'[server]:[port]'/system/console/configMgr`.
1. Cliquez pour modifier le composant **Guide Localization Service**.
1. Ajoutez le paramètre régional souhaité à la liste des paramètres régionaux pris en charge.

![GuideLocalizationService](assets/configservice.png)

### Ajouter la bibliothèque XFA cliente pour des paramètres régionaux {#add-xfa-client-library-for-a-locale-br}

Créez un nœud de type `cq:ClientLibraryFolder` sous `etc/<folderHierarchy>`, avec la catégorie `xfaforms.I18N.<locale>` et ajoutez les fichiers ci-dessous à la bibliothèque cliente :

* **I18N.js** qui définit `xfalib.locale.Strings` pour `<locale>`, comme défini dans `/etc/clientlibs/fd/xfaforms/I18N/ja/I18N`.

* **js.txt** qui contient les éléments suivants :

```text
/libs/fd/xfaforms/clientlibs/I18N/Namespace.js
I18N.js
/etc/clientlibs/fd/xfaforms/I18N/LogMessages.js
```

### Ajouter la bibliothèque cliente de formulaires adaptatifs pour un paramètre régional {#add-adaptive-form-client-library-for-a-locale-br}

Créez un nœud de type `cq:ClientLibraryFolder` sous `etc/<folderHierarchy>`, avec la catégorie `guides.I18N.<locale>` et les dépendances `xfaforms.3rdparty`, `xfaforms.I18N.<locale>` et `guide.common`.

Ajouter les fichiers suivants à la bibliothèque cliente :

* **i18n.js** qui définit `guidelib.i18n`, comportant des motifs « calendarSymbols », `datePatterns`, `timePatterns`, `dateTimeSymbols`, `numberPatterns`, `numberSymbols`, `currencySymbols`, `typefaces` pour `<locale>` conformément aux spécifications XFA décrites dans [Spécification du jeu de paramètres régionaux](https://helpx.adobe.com/content/dam/Adobe/specs/xfa_spec_3_3.pdf). Vous pouvez également voir comment les autres paramètres locaux sont définis sur `/etc/clientlibs/fd/af/I18N/fr/javascript/i18n.js`.
* **LogMessages.js** qui définit `guidelib.i18n.strings` et `guidelib.i18n.LogMessages` pour `<locale>`, défini dans `/etc/clientlibs/fd/af/I18N/fr/javascript/LogMessages.js`.
* **js.txt** qui contient les éléments suivants :

```text
i18n.js
LogMessages.js
```

### Ajouter la prise en charge des paramètres régionaux pour la langue du dictionnaire {#add-locale-support-for-the-dictionary-br}

Exécutez cette étape uniquement si l’élément `<locale>` que vous ajoutez ne se trouve pas parmi `en`, `de`, `es`, `fr`, `it`, `pt-br`, `zh-cn`, `zh-tw`, `ja`, `ko-kr`.

1. Créez un nœud `nt:unstructured` `languages` sous `etc`, s’il n’existe pas déjà.

1. Ajoutez une propriété comprenant plusieurs valeurs `languages` au nœud, s’il ne sont pas déjà présents.
1. Ajoutez les valeurs des paramètres régionaux par défaut `<locale>` `de`, `es`, `fr`, `it`, `pt-br`, `zh-cn`, `zh-tw`, `ja`, `ko-kr`, si elles ne sont pas déjà présentes.

1. Ajoutez `<locale>` aux valeurs de la propriété `languages` de `/etc/languages`.

L’élément `<locale>` s’affiche au niveau de `https://'[server]:[port]'/libs/cq/i18n/translator.html`.

### Redémarrer le serveur {#restart-the-server}

Redémarrez le serveur AEM pour que les paramètres régionaux ajoutés entrent en vigueur.

>[!NOTE]
>
> Il est recommandé d’utiliser la commande « Ctrl+C » pour redémarrer le SDK. Le redémarrage du SDK AEM à l’aide de méthodes alternatives, par exemple l’arrêt des processus Java, peut entraîner des incohérences dans l’environnement de développement AEM.

## Exemples de bibliothèques pour ajouter la prise en charge de l’espagnol {#sample-libraries-for-adding-support-for-spanish}

Exemples de bibliothèques clientes pour ajouter la prise en charge de l’espagnol

[Obtenir le fichier](assets/sample.zip)
