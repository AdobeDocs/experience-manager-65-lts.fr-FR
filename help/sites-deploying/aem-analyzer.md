---
title: Évaluation de la complexité de la mise à niveau à l’aide d’AEM Analyzer
description: Découvrez comment utiliser AEM Analyzer pour évaluer la complexité de votre mise à niveau.
topic-tags: upgrading
feature: Upgrading
solution: Experience Manager, Experience Manager Sites
role: Admin
exl-id: 87c30912-c89a-42f1-b37b-ec439e7318c7
source-git-commit: 6b846e456466492f4be2c1e5a1f6b3913ae4dab4
workflow-type: tm+mt
source-wordcount: '2071'
ht-degree: 22%

---

# Évaluation de la complexité de la mise à niveau à l’aide d’AEM Analyzer {#assessing-the-upgrade-complexity-with-the-aem-analyzer}

## Vue d’ensemble {#overview}

L’analyseur LTS d’AEM 6.5 fournit une évaluation de votre implémentation AEM actuelle en indiquant les zones qui doivent être mises à jour afin de fournir une expérience de mise à niveau transparente vers la version 6.5 LTS.

L’outil génère un rapport qui identifie les zones de refactorisation potentielle.

## Rapport Analyseur LTS AEM 6.5 {#aem-65lts-analyzer-report}

Le rapport de l’analyseur LTS d’AEM 6.5 permet de mieux comprendre le degré de préparation général à la mise à niveau. Le rapport se compose de résultats appartenant à des catégories de problèmes qui doivent être résolus afin d’assurer une mise à niveau réussie vers AEM 6.5 LTS.

Le rapport Analyseur LTS d’AEM 6.5 comprend les catégories suivantes :

* Fonctionnalités de l’application qui doivent être reconfigurées
* Éléments du référentiel qui doivent être déplacés vers un emplacement pris en charge
* Problèmes de configuration
* Fonctionnalités d’AEM 6.5 supprimées par une nouvelle fonctionnalité ou qui ne sont actuellement pas prises en charge sur AEM 6.5 LTS
* Suppression de l’utilisation de l’API Java et Java

Des informations supplémentaires sur les catégories, ainsi que sur les implications et solutions possibles associées à ces catégories, sont fournies via des liens depuis le rapport de l’analyseur LTS d’AEM 6.5.

## Disponibilité {#analyzer-availability}

Il est possible de télécharger AEM Analyzer sous la forme d’un fichier zip à partir du [portail de distribution de logiciels](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html). Vous pouvez installer le package par le biais du [Gestionnaire de packages](/help/sites-administering/package-manager.md) sur votre instance AEM source.

## Points importants concernant l’utilisation d’AEM Analyzer {#important-considerations-for-using-aem-analyzer}

Consultez la section ci-dessous pour comprendre les points importants à prendre en compte pour exécuter l’analyseur AEM :

* Le rapport de l’analyseur est créé à l’aide de la sortie de l’outil AEM Pattern Detector. La version de l’outil de détection des motifs utilisée par Analyzer est incluse dans le package d’installation d’AEM Analyzer
* AEM Analyzer ne peut être exécuté que par l’utilisateur **administrateur** ou un utilisateur du groupe **administrateurs**
* Analyzer est pris en charge sur les instances AEM avec version 6.5 et ultérieure.

>[!NOTE]
>
>Pour éviter toute incidence sur les instances critiques de l’entreprise, il est recommandé d’exécuter AEM Analyzer dans un environnement d’évaluation aussi proche que possible de l’environnement de production concernant la personnalisation, la configuration, les contenus et les applications utilisateur. Vous pouvez également l’exécuter sur un clone de l’environnement de création de production.

* La génération du contenu du rapport AEM Analyzer peut prendre un temps considérable, de quelques minutes à quelques heures. Le temps nécessaire dépend fortement de la taille et de la nature du contenu du référentiel AEM, de la version d’AEM, etc
* En raison du temps important qui peut être nécessaire pour générer le contenu du rapport, il est généré par un processus en arrière-plan et conservé dans un cache. L’affichage et le téléchargement du rapport doivent être relativement rapides, car il utilise le cache de contenu jusqu’à son expiration ou s’il est explicitement actualisé. Pendant la génération du contenu du rapport, vous pouvez fermer l’onglet de votre navigateur et revenir plus tard pour afficher le rapport une fois que son contenu est disponible dans le cache.

## Affichage du rapport de l’analyseur AEM {#viewing-the-aem-analyzer-report}

Pour afficher le rapport AEM Analyzer, procédez comme suit :

1. Sélectionnez Adobe Experience Manager et accédez à **Outils - Opérations - 6.5 LTS Modernizer**

   ![Afficher le rapport de l’analyseur 1](/help/sites-deploying/assets/view-analyzer-report-1.png)

1. Cliquez sur **AEM 6.5 LTS Analyzer** pour l’ouvrir

   ![Afficher le rapport de l’analyseur 2](/help/sites-deploying/assets/view-analyzer-report-2.png)

1. Cliquez sur **Générer le rapport** pour exécuter l’analyseur AEM

   ![Afficher le rapport de l’analyseur 3](/help/sites-deploying/assets/view-analyzer-report-3.png)

1. Pendant que l’analyseur AEM génère le rapport, vous pouvez voir la progression de l’outil à l’écran. Il affiche la progression en termes de pourcentage d’achèvement. Il affiche également le nombre d’éléments analysés et le nombre de résultats

   ![Afficher le rapport de l&#39;analyseur 4](/help/sites-deploying/assets/view-analyzer-report-4.png)

1. Une fois le rapport de l’analyseur LTS 6.5 généré, il affiche un résumé et le nombre des résultats sous forme de tableau organisé selon le type de résultat et le niveau d’importance. Pour obtenir plus de détails sur un résultat donné, vous pouvez cliquer sur le nombre correspondant au type de résultat du tableau

   ![Afficher le rapport de l’analyseur 5](/help/sites-deploying/assets/view-analyzer-report-5.png)

1. Vous avez la possibilité de télécharger le rapport au format CSV (valeurs séparées par des virgules) en cliquant sur **Exporter au format CSV**. Vous pouvez forcer l’analyseur à effacer son cache et à générer de nouveau le rapport en cliquant sur **Actualiser le rapport**. Si le cache arrive à expiration, vous devrez générer de nouveau le rapport.

## Interprétation du rapport de l’analyseur AEM {#interpreting-the-aem-analyzer-report}

Lorsque l’outil 6.5 LTS Analyzer est exécuté dans l’instance AEM, le rapport s’affiche sous la forme de résultats dans la fenêtre d’outil.

Le format du rapport est le suivant :

* **Report Overview** : informations sur le rapport lui-même qui incluent les informations suivantes :

   * **Heure du rapport** : date à laquelle le contenu du rapport a été généré et rendu disponible pour la première fois
   * **Délai d’expiration** : délai d’expiration du cache du contenu du rapport
   * **Période de génération** : durée pendant laquelle le rapport a été généré
   * **Nombre de résultats** : nombre total de résultats inclus dans le rapport

* **Présentation du système** : informations sur le système AEM sur lequel Analyzer a été exécuté
* **Finding Categories** : différentes sections traitant chacune d’un ou plusieurs résultats pour une même catégorie. Chaque section comprend les éléments suivants : nom de la catégorie, sous-types, nombre et importance des résultats, résumé, lien vers la documentation de la catégorie et informations relatives à chaque résultat.

  ![Résumé du rapport Analyzer](/help/sites-deploying/assets/analyzer-report-summary.png)

  Un niveau d’importance est attribué à chaque résultat pour indiquer une priorité absolue concernant l’action.

>[!NOTE]
>
>Pour en savoir plus sur chaque catégorie de résultat, consultez [Catégories du détecteur de motifs](https://experienceleague.adobe.com/en/docs/experience-manager-pattern-detection/table-of-contents/aso).

Pour comprendre les niveaux d’importance, suivez le tableau ci-dessous :

| Importance | Description |
|---|---|
| INFO | Ce résultat est fourni à titre d’information. |
| ADVISORY | Ce résultat peut poser un problème de mise à niveau. Il est recommandé d’approfondir les investigations. |
| CRITIQUE | Il est très probable que ce résultat constitue un problème de mise à niveau qui doit être résolu pour éviter toute perte de fonction ou de performances. |

## Interprétation du rapport CSV de l’analyseur LTS d’AEM 6.5 {#interpreting-the-aem-65lts-analyzer-report}

Lorsque vous cliquez sur l’option **CSV** de votre instance AEM, le format CSV du rapport de l’analyseur est créé à partir du cache de contenu et renvoyé à votre navigateur. En fonction des paramètres de votre navigateur, ce rapport sera automatiquement téléchargé sous la forme d’un fichier portant le nom `report.csv` par défaut.

Si le cache a atteint son délai d’expiration, le rapport est de nouveau généré avant la création et le téléchargement du fichier CSV.

Le format CSV du rapport contient des informations générées à partir de la sortie du détecteur de motifs, triées et organisées par types de catégories, sous-types et niveaux d’importance. Son format est adapté pour permettre l’affichage et la modification dans une application comme Microsoft Excel. Il est destiné à fournir toutes les informations de recherche dans un format répétable qui peut s’avérer utile lors de la comparaison de rapports au fil du temps pour mesurer les progrès.

Les colonnes du rapport au format CSV sont les suivantes :

* **code** : code de catégorie
* **type** : nom de la catégorie
* **subtype** : sous-type de catégorie
* **importance** : niveau d’importance
* **identifier** : identifiant principal du résultat
* **message** : message fourni pour le résultat
* **context** : chaîne JSON concernant les données du résultat.

Une valeur « `\N` » dans une colonne pour un résultat individuel indique qu’aucune donnée n’a été fournie.

## Interface HTTP {#http-interface}

L’analyseur LTS 6.5 fournit une interface HTTP qui peut être utilisée comme alternative à son interface utilisateur dans AEM. L’interface prend en charge les commandes `HEAD` et `GET`. Il peut être utilisé pour générer le rapport de l’analyseur et le renvoyer dans l’un des trois formats suivants : JSON, CSV et valeurs séparées par des tabulations (TSV).

Les URL suivantes sont disponibles pour l’accès HTTP, où `<host>` est le nom d’hôte, ainsi que le port si nécessaire, du serveur sur lequel Analyzer est installé :

* `http://<host>/apps/aem66-analyzer/analysis/report.json` pour le format JSON
* `http://<host>/apps/aem66-analyzer/analysis/report.csv` pour le format CSV
* `http://<host>/apps/aem66-analyzer/analysis/report.tsv` pour le format TSV

### Exécution d’une requête HTTP {#executing-an-http-request}

Pour exécuter une requête HTTP, une méthode simple consiste à ouvrir un onglet dans le navigateur dans lequel vous vous êtes déjà connecté à AEM en tant qu’administrateur. Vous pouvez renseigner l’URL dans l’onglet du navigateur et afficher ou télécharger les résultats grâce au navigateur.

Vous pouvez également utiliser un outil de ligne de commande tel que `curl` ou `wget`, mais aussi toute autre application cliente HTTP. Si vous n’utilisez pas un onglet de navigateur avec une session authentifiée, vous devez fournir un nom d’utilisateur et un mot de passe d’administration en commentaire.

Voici un exemple de la manière dont cela peut être effectué :

```shell
curl -u admin:admin 'http://localhost:4502/apps/aem66-analyzer/analysis/report.csv' > report.csv.
```

## Ajustement de la durée de vie du cache {#adjusting-the-cache-lifetime}

La durée de vie par défaut du cache de l’analyseur LTS d’AEM 6.5 est de 24 heures. Avec l’option permettant d’actualiser un rapport et de régénérer le cache, à la fois dans l’instance AEM et l’interface HTTP, cette valeur par défaut sera probablement appropriée pour la plupart des utilisateurs de l’analyseur LTS d’AEM 6.5. Si la génération du rapport dure trop longtemps pour votre instance AEM, vous pouvez ajuster la durée de vie du cache afin de minimiser la nouvelle génération du rapport.

La valeur de durée de vie du cache est stockée en tant que propriété `maxCacheAge` sur le nœud de référentiel suivant :

```
/apps/aem66-analyzer/content/modernizer/analyzer/jcr:content
```

La valeur de cette propriété est la durée de vie du cache en secondes. Un administrateur peut ajuster la durée de vie du cache à l’aide de CRX/DE Lite.

## Utilisation du Transformateur de contenu {#using-content-transformer}

### Disponibilité {#content-transformer-availability}

Le transformateur de contenu est fourni avec l’analyseur LTS d’AEM 6.5, qui peut être téléchargé sous la forme d’un fichier zip à partir du portail de distribution de logiciels .

### Points importants concernant l’utilisation du Transformateur de contenu {#important-considerations-for-using-content-transformer}

Consultez la section ci-dessous pour comprendre les points importants à prendre en compte pour l’utilisation du transformateur de contenu (CT) :

* Pour utiliser le transformateur de contenu, vous devez d’abord exécuter l’analyseur AEM sur votre environnement AEM
* Bien que vous puissiez exécuter le Transformateur de contenu dans votre environnement de production, il est recommandé de l’exécuter sur un clone de celui-ci. Plus important encore, vous devez vous assurer que AEM Analyzer et le CT sont exécutés sur le même environnement
* Vous devez être administrateur ou administratrice de l’environnement dans lequel vous souhaitez exécuter le transformateur de contenu
* Une opération de suppression qui peut modifier le contenu source crée un package de sauvegarde des chemins d’accès sources sous `/etc/packages/modernizer-content-transformation` par défaut avant la transformation. Bien que la boîte de dialogue Supprimer l’opération ait une option pour désactiver/activer la création du package de sauvegarde, il est vivement recommandé de toujours sélectionner Activer la création du package .
* Chaque page du transformateur de contenu est configurée pour répertorier un maximum de 50 résultats. Par conséquent, un maximum de 50 résultats peuvent être transformés à la fois. Cela permet de fournir une réponse rapide dans l’interface utilisateur.

### Ouverture du Transformateur de contenu {#opening-the-content-transformer}

1. Connectez-vous à l’instance AEM source en tant qu’administrateur et accédez à la page de démarrage à l’adresse *https://host:port/aem/start.htm*
1. Accédez à **Outils - Opérations - 6.5 LTS Modernizer**

   ![Ouverture du transformateur de contenu 1](/help/sites-deploying/assets/opening-content-transformer-1.png)

1. Cliquez sur la vignette **Transformateur de contenu pour le rapport Analyseur LTS 6.5**

   ![Ouverture du transformateur de contenu 2](/help/sites-deploying/assets/opening-content-transformer-2.png)

1. Si le rapport d’analyse n’est pas généré, la page **Transformer le contenu** s’affiche **Aucun rapport**. Le même message **Aucun rapport** s’affiche également si tous les résultats liés au contenu ont été supprimés

   ![Ouverture du transformateur de contenu 3](/help/sites-deploying/assets/opening-content-transformer-3.png)

1. Vous trouverez ci-dessous un exemple de ce à quoi ressemblera la page Aperçu du transformateur de contenu si la création du rapport de l’analyseur AEM a réussi et s’il a détecté des problèmes liés au contenu.

Le délai d’expiration restant pour le rapport AEM Analyzer s’affiche sur le rail latéral. Il est recommandé d’exécuter le transformateur de contenu avec le dernier rapport d’AEM Analyzer afin d’éviter de passer à côté de résultats liés au contenu

![Ouverture du transformateur de contenu 4](/help/sites-deploying/assets/opening-content-transformer-4.png)

1. Vous pouvez filtrer les problèmes en fonction du code de motif, du sous-type, de l’importance et du Source

   ![Ouverture du transformateur de contenu 5](/help/sites-deploying/assets/opening-content-transformer-5.png)

### Suppression de chemins d’accès {#removing-paths}

1. Vous pouvez sélectionner tous les problèmes ou certains problèmes spécifiques et sélectionner **Supprimer** pour les résoudre

   ![Suppression des chemins 1](/help/sites-deploying/assets/removing-paths-1.png)

   >[!NOTE]
   >Une opération de suppression crée un package de sauvegarde des chemins d’accès sources sous `/etc/packages/modernizer-content-transformation` par défaut, avant la transformation. Bien que la boîte de dialogue Supprimer l’opération ait une option pour désactiver/activer la création du package de sauvegarde, il est vivement recommandé de toujours sélectionner Activer la création du package .

   ![Suppression des chemins d’accès 2](/help/sites-deploying/assets/removing-paths-2.png)

1. Un exemple de package de sauvegarde créé pour l’opération de suppression des chemins d’accès est illustré ci-dessous. Vous pouvez cliquer sur **Installer** pour rétablir les chemins d’accès sources

   ![Suppression de chemins d’accès 3](/help/sites-deploying/assets/removing-paths-3.png)

   >[!CAUTION]
   >
   >Ne supprimez pas les `/etc/packages/modernizer-content-transformation`, car il s’agit de l’emplacement où se trouvent les packages de sauvegarde. Vous pouvez supprimer cet emplacement pour réduire la taille du référentiel uniquement lorsque vous êtes sûr de ne plus avoir besoin de ces packages.

1. Vous pouvez éventuellement regrouper les résultats de contenu sélectionnés pour une utilisation ultérieure. Pour ce faire, sélectionnez les résultats à inclure, puis cliquez sur **Package** dans le coin supérieur gauche. Saisissez un nom de package, choisissez un chemin d’accès au package, puis cliquez sur le bouton **Package** pour terminer le processus.

   ![Suppression de chemins d’accès 3](/help/sites-deploying/assets/removing-paths-4.png)

### Problèmes connus {#known-issues}

* Parfois, l’opération de suppression peut afficher la notification : *« Certains chemins n’ont pas été supprimés avec succès. Vérifiez les journaux et réessayez.* ». Cependant, si les chemins d’accès ont été réellement supprimés, vous pouvez ignorer ce message en toute sécurité
* De même, l’opération du package peut échouer avec l’erreur : *« Erreur lors de l’exécution de l’opération souhaitée, vérifiez les journaux et réessayez.* ». Cela est probablement dû à l’expiration de la session. Dans ce cas, il est recommandé de réessayer l’opération pour résoudre le problème.
