---
title: Analytics avec des fournisseurs externes
description: Découvrez comment configurer votre propre instance d’extraits de code Analytics génériques pour définir une nouvelle configuration de service.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: integration
content-type: reference
docset: aem65
solution: Experience Manager, Experience Manager Sites
feature: Integration
role: Admin
exl-id: 73f40fd7-69b9-436c-b6b4-a7d6bfbaae6f
source-git-commit: c3e9029236734e22f5d266ac26b923eafbe0a459
workflow-type: tm+mt
source-wordcount: '445'
ht-degree: 100%

---

# Analytics avec des fournisseurs externes {#analytics-with-external-providers}

Analytics peut vous apporter des informations importantes et intéressantes sur l’utilisation de votre site web.

Différentes configurations sont disponibles par défaut pour l’intégration au service approprié, par exemple :

* [Adobe Analytics](/help/sites-administering/adobeanalytics.md)
* [Adobe Target](/help/sites-administering/target.md)

Vous pouvez également configurer votre propre instance d’**extraits de code Analytics génériques** pour définir une nouvelle configuration de service.

Les informations sont alors collectées au moyen de petits extraits de code, qui sont ajoutés à des pages web. Par exemple :

>[!CAUTION]
>
>Ne pas inclure de scripts dans les balises `script`.

```
var _gaq = _gaq || [];
_gaq.push(['_setAccount', 'UA-XXXXX-X']);
_gaq.push(['_trackPageview']);

(function() {
    var ga = document.createElement('script'); ga.type = 'text/javascript'; ga.async = true;
    ga.src = ('https:' == document.location.protocol ? 'https://ssl' : 'https://www') + '.google-analytics.com/ga.js';
    var s = document.getElementsByTagName('script')[0]; s.parentNode.insertBefore(ga, s);
})();
```

Ces fragments de code permettent de collecter des données et de générer des rapports. Les données réelles collectées dépendent du fournisseur et du fragment de code réel utilisé. Voici des exemples de statistiques :

* le nombre de visiteurs et visiteuses au fil du temps
* le nombre de pages visitées
* les termes de recherche utilisés
* les pages de destination

>[!CAUTION]
>
>Le site de démonstration de Geometrixx-Outdoors est configuré de manière à ajouter les attributs indiqués dans Propriétés de la page au code source html (juste avant la balise de fin `</html>`) dans le script `js` correspondant.
>
>Si votre propre dossier `/apps` n’hérite pas du composant Page par défaut (`/libs/foundation/components/page`), vous (ou les développeurs et développeuses) devez vous assurer que les scripts `js` sont inclus, par exemple, en incluant `cq/cloudserviceconfigs/components/servicescomponents` ou en utilisant un mécanisme similaire.
>
>Autrement, aucun des services (Générique, Analytics, Target, etc.) ne fonctionnera.

## Création d’un service à l’aide d’un extrait de code générique {#creating-a-new-service-with-a-generic-snippet}

Pour la configuration de base, suivez les étapes suivantes :

1. Ouvrez la console **Outils**.
1. Dans le volet de gauche, développez les **Configurations des Services cloud**.
1. Double-cliquez sur **Extrait de code Analytics générique** pour ouvrir la page :

   ![Extrait de code Analytics générique](assets/analytics_genericoverview.png)

1. Cliquez sur + pour ajouter une nouvelle configuration à l’aide de la boîte de dialogue. Attribuez au minimum un nom, par exemple Google Analytics :

   ![Création d’une configuration](assets/analytics_addconfig.png)

1. Cliquez sur **Créer**, la boîte de dialogue Extrait de code s’affiche immédiatement. Collez l’extrait de code JavaScript approprié dans le champ :

   ![Modification du composant](assets/analytics_snippet.png)

1. Cliquez sur **OK** pour enregistrer.

## Utilisation de votre nouveau service dans des pages {#using-your-new-service-on-pages}

Après avoir créé la configuration de service, vous devez maintenant configurer les pages nécessaires pour l’utiliser :

1. Accédez à la page.
1. Ouvrez les **Propriétés de page** dans le sidekick, puis l’onglet **Services cloud**.
1. Cliquez sur **Ajouter un service**, puis sélectionnez le service requis. Par exemple, l’**extrait de code Analytics générique** :

   ![Ajout d’un service cloud](assets/analytics_selectservice.png)

1. Cliquez sur **OK** pour enregistrer.
1. Vous revenez à l’onglet **Services cloud**. L’**extrait de code Analytics générique** figure maintenant dans la liste avec le message `Configuration reference missing`. Utilisez la liste déroulante pour sélectionner votre instance de service spécifique. Par exemple, google-analytics :

   ![Ajout d’une configuration de service cloud](assets/analytics_selectspecificservice.png)

1. Cliquez sur **OK** pour enregistrer.

   L’extrait de code est désormais visible si vous affichez la source de la page.

   Après un certain laps de temps, vous pouvez afficher les statistiques collectées.

   >[!NOTE]
   >
   >Si la configuration est associée à une page qui contient des pages enfants, ces pages héritent elles aussi du service.
