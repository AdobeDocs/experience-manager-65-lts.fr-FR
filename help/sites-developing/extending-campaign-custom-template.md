---
title: Créer le modèle de page AEM personnalisé avec des composants de formulaire Adobe Campaign
description: Créer un modèle de page personnalisé qui utilise des composants de formulaire Adobe Campaign
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: extending-aem
content-type: reference
solution: Experience Manager, Experience Manager Sites
feature: Developing
role: Developer
exl-id: 59a79455-c108-4f4b-93c1-d8c6f23aec88
source-git-commit: c3e9029236734e22f5d266ac26b923eafbe0a459
workflow-type: tm+mt
source-wordcount: '313'
ht-degree: 100%

---

# Créer le modèle de page AEM personnalisé avec des composants de formulaire Adobe Campaign{#creating-custom-aem-page-template-with-adobe-campaign-form-components}

Cette page vous explique comment créer un modèle de page personnalisé qui utilise des composants [Formulaire Adobe Campaign](/help/sites-authoring/adobe-campaign-components.md) en examinant le mode d’implémentation du modèle Geometrixx-outdoors (`/apps/geometrixx-outdoors/components/page_campaign_profile`). Elle vous donne également des informations importantes dont vous pourriez avoir besoin lors de la création de votre propre modèle personnalisé.

>[!NOTE]
>
>[Les exemples d’e-mail et de formulaire sont disponibles uniquement dans Geometrixx](/help/sites-developing/we-retail.md). Téléchargez un exemple de contenu Geometrixx à partir du partage de modules.

>[!CAUTION]
>
>Les composants d’e-mail AEM ont été abandonnés. En raison de la nature de l’e-mail, en particulier son contenu et son style, les composants d’e-mail fournis prêts-à-l’emploi par AEM ne sont que rarement réutilisés par les clients car ils ont besoin d’implémenter des styles personnalisés dans les composants requis pour les projets.
>
>Les composants d’e-mail peuvent être implémentés au niveau du projet. Les composants d’e-mail AEM obsolètes illustrent la manière dont cela peut être réalisé. Toutefois, n’utilisez pas ces composants obsolètes sur les projets.


Pour créer un modèle de page AEM personnalisé à l’aide des composants de formulaire Adobe Campaign, assurez-vous que vous disposez des éléments suivants :

1. **resourceSuperType correct**

   Assurez-vous que le composant de page hérite de `mcm/campaign/components/profile`.

   Cela est nécessaire pour que les servlets obtiennent et enregistrent des informations.

   * `com.day.cq.mcm.campaign.servlets.TemplateListServlet`
   * `com.day.cq.mcm.campaign.servlets.SaveProfileServlet`

   ![chlimage_1-201](assets/chlimage_1-201.png)

1. **Paramètres de ClientContext**

   Lorsque vous observez les paramètres de ClientContext (`/etc/designs/geometrixx-outdoors/jcr:content/page_campaign_profile`), vous voyez ceci :

   * ClientContext pointe vers `/etc/clientcontext/campaign`.
   * Il existe également un nœud *config* supplémentaire.

   ![chlimage_1-202](assets/chlimage_1-202.png)

1. **head.jsp (/apps/geometrixx-outdoors/components/page_campaign_profile/head.jsp)**

   Dans **head.jsp**, les lignes suivantes qui utilisent **clientcontext-config** et **cloudservice-hook** :

   ```
   <cq:include path="config" resourceType="cq/personalization/components/clientcontext_optimized/config"/>
   <sling:include path="contexthub" resourceType="granite/contexthub/components/contexthub"/>
   <cq:include script="/libs/cq/cloudserviceconfigs/components/servicelibs/servicelibs.jsp"/>
   ```

1. **body.jsp (/apps/geometrixx-outdoors/components/page_campaign_profile/body.jsp)**

   Dans le fichier **body.jsp**, les Cloud Services sont chargés au bas de la page :

   ```
   <cq:include path="cloudservices" resourceType="cq/cloudserviceconfigs/components/servicecomponents"/>
   ```

1. **Propriétés de page Campaign**

   Pour pouvoir sélectionner un modèle Adobe Campaign, les propriétés de page sont étendues avec l’onglet **Campagne** :

   `/apps/geometrixx-outdoors/components/page_campaign_profile/dialog/items/tabs/items/campaign`

   ![chlimage_1-203](assets/chlimage_1-203.png)

1. **Paramètres de modèle**

   Les valeurs par défaut suivantes sont affichées dans le modèle (`/apps/geometrixx-outdoors/templates/campaign_profile/jcr:content`) :

   | **acMapping** | mapRecipient (pour Adobe Campaign 6.1), profile (pour Adobe Campaign Standard) |
   |---|---|
   | **acTemplateId** | courrier |

   ![chlimage_1-204](assets/chlimage_1-204.png)
