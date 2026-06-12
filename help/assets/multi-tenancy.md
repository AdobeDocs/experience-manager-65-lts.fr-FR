---
title: Fonction multiclient pour les collections, les fragments de code et les modèles de fragments de code
description: Découvrez comment la fonction multiclient permet de séparer du contenu dans le référentiel CRX en fonction de l’organisation du client afin d’empêcher tout accès non autorisé.
contentOwner: AG
role: Developer,Admin,Leader
feature: Collections
solution: Experience Manager, Experience Manager Assets
exl-id: 39e14f89-8e60-4b5e-8859-d69ebd51864e
source-git-commit: e3106e87f72484568667873c1772abd30a108e51
workflow-type: tm+mt
source-wordcount: '228'
ht-degree: 87%

---

# Fonction multiclient pour les collections, les fragments de code et les modèles de fragments de code {#multi-tenancy-for-collections-snippets-and-snippet-templates}

La fonction multiclient permet de séparer du contenu dans CRX en fonction du préfixe et de l’identifiant d’organisation, de sorte à protéger le contenu contre tout accès non autorisé par les utilisateurs d’autres organisations.

[!DNL Adobe Experience Manager Assets] stocke les données de chaque organisation à un chemin d’accès différent. Le chemin d’accès propre à chaque organisation est identifié par le préfixe et l’ID d’organisation
est inclus à l’emplacement traditionnel où différents types de ressources sont stockés dans CRX.

Par exemple, si vous créez un dossier nommé `Demo`, [!DNL Experience Manager] Assets stocke généralement le dossier à l’adresse `../content/dam/Demo`. Lorsque le multiclient est activé, vous pouvez désormais stocker les données à l’adresse `../content/dam/<organization prefix>/<organization id>Demo`.

Par exemple, pour les utilisateurs d’[!DNL Adobe Marketing Cloud] d’[!DNL Assets] (à la demande) qui sont affectés à l’organisation `aodpremium`, vous pouvez utiliser la fonctionnalité multiclient afin de configurer le chemin d’accès `../content/dam/<mac>/<aodpremium>Demo` pour séparer leur contenu. Dans cet exemple, `mac` est le préfixe de l’organisation et `aodpremium` est l’ID d’organisation.

En fonction de l’organisation et de l’identifiant de l’utilisateur, ce chemin d’accès s’affiche dans l’interface d’[!DNL Assets] et dans différents assistants, notamment les assistants Déplacement et Création de fragment de code, pour appliquer la séparation.

La fonctionnalité multiclient vous permet de séparer les types de ressources et de composants suivants :

* Collections
* Collections publiques
* Catalogues (notamment l’assistant Ajouter/Sélectionner une page)
* Modèles
* Modèles d’extrait de code
* Lightbox
