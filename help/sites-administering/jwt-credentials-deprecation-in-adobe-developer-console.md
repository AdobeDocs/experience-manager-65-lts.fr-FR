---
title: Obsolescence des informations d’identification JWT dans Adobe Developer Console
description: Découvrez l’impact de l’obsolescence des informations d’identification JWT dans Adobe Developer Console sur AEM.
solution: Experience Manager, Experience Manager Sites
feature: Security
role: Admin
exl-id: 7b6b02fd-fcb2-45ae-a239-e0c68de2bcbb
source-git-commit: 929a2175449a371ecf81226fedb98a0c5c6d7166
workflow-type: tm+mt
source-wordcount: '352'
ht-degree: 96%

---

# Obsolescence des informations d’identification JWT dans Adobe Developer Console {#jwt-credentials-deprecation-in-adobe-developer-console}

>[!NOTE]
> AEM as a Cloud Service doit référencer l’[article comparable pour la version AEMaaCS](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/security/jwt-credentials-deprecation-in-adobe-developer-console.html?lang=fr) pour plus d’informations.

Les clientes et clients Adobe utilisent [Adobe Developer Console](https://developer.adobe.com/console) pour générer des informations d’identification qui permettent l’accès à diverses API. Les clientes et clients effectuent un choix parmi différents types d’informations d’identification, allant d’OAuth serveur à serveur jusqu’à l’application monopage. L’un de ces types d’informations d’identification, celui des informations d’identification du compte de service (JWT), a été abandonné au profit des informations d’identification OAuth serveur à serveur. Les informations d’identification du nouveau compte de service (JWT) ne peuvent plus être créées à partir du 3 juin 2024, et les informations d’identification JWT existantes ne fonctionneront plus à partir du 27 janvier 2025. Vous pouvez [en savoir plus sur l’obsolescence](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/migration).

Cet article fournit un contexte supplémentaire sur la manière dont les clientes et clients Adobe Experience Manager (AEM) 6.5 doivent gérer l’obsolescence.

Le principal point à retenir est qu’AEM prend désormais en charge les nouvelles informations d’identification OAuth de serveur à serveur pour AEM. Vous avez peut-être reçu un e-mail contenant des instructions pour migrer vos informations d’identification JWT. Cette migration peut maintenant être effectuée.

Les sections ci-dessous répertorient les scénarios où les clientes et clients doivent (ou dans certains cas ne doivent pas) remplacer leurs informations d’identification de compte de service (JWT) par des informations d’identification OAuth serveur à serveur, maintenant qu’AEM les prend en charge. [Découvrez comment](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/migration#migration-overview) migrer les informations d’identification.

## Intégrer AEM à d’autres solutions Adobe {#integrating-aem-with-other-adobe-solutions}

**Action** : migrez votre configuration, car AEM prend désormais en charge les informations d’identification OAuth.

**Versions d’AEM appropriées** : Adobe Managed Services.

Les clientes et clients AEM utilisent AEM pour configurer des intégrations à de nombreuses autres solutions Adobe. Par exemple, Adobe Target, Adobe Analytics et d’autres.

![Intégration d’AEM à d’autres solutions](/help/sites-administering/assets/jwt-deprecation.png)

Voir [Configurer des intégrations IMS pour AEM](/help/sites-administering/setting-up-ims-integrations-for-aem.md) pour plus de détails sur la façon d’effectuer ce qui suit :

* créer des configurations avec des informations d’identification OAuth ;
* migrer les configurations créées avec les informations d’identification JWT pour utiliser les informations d’identification OAuth.

## API Cloud Manager {#cloud-manager-apis}

**Action** : confirmez quand celles-ci peuvent être migrées des informations d’identification JWT vers les informations d’identification OAuth.

**Versions d’AEM appropriées** : Adobe Managed Services.

Les clientes et clients créent des projets Adobe Developer Console pour pouvoir appeler les [API Cloud Manager](https://developer.adobe.com/experience-cloud/cloud-manager/guides/getting-started/create-api-integration/). Les informations d’identification du projet Adobe Developer doivent être migrées vers le type OAuth serveur à serveur avant que les informations d’identification JWT obsolètes n’expirent en janvier 2025.
