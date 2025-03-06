---
product: adobe experience manager
description: Documentation de Adobe Experience Manager 6.5 LTS.
git-repo: https://github.com/AdobeDocs/experience-manager-65-lts.fr-FR
index: y
type: Documentation
solution: Experience Manager
feature-set: Experience Manager Assets,Experience Manager Sites,Experience Manager, Experience Manager Forms, Experience Manager Cloud Manager
cloud: Experience Cloud
recommendations: noDisplay
source-git-commit: 766b9eaad3ebe43db3659e8ba4afb8b4496a1f3a
workflow-type: tm+mt
source-wordcount: '84'
ht-degree: 52%

---


# Métadonnées pour utilisation interne

Les métadonnées dans le système de création GitHub sont hiérarchiques et sont définies selon les niveaux de précédent croissants suivants.

1. metadata.md
1. Table des matières
1. Article

Les métadonnées définies dans le fichier metadata.md s’appliquent à l’intégralité du référentiel, mais peuvent être remplacées aux niveaux de la table des matières et de l’article. Tout remplacement des métadonnées doit être effectué au niveau le plus bas possible.

Les métadonnées du référentiel experience-manager-cloud-service.en sont le minimum requis.

metadata.md

* `product`
* `git-repo`
* `index`
* `solution-title`
* `solution-hub-url`
* `getting-started-title`
* `getting-started-url`
* `tutorials-title`
* `tutorials-url`

Tables des matières

* `sub-product`
* `user-guide-title`

Article

* `title`
* `description`
* `contentOwner` (uniquement sur le contenu des ressources de base sous `/help/assets`)
