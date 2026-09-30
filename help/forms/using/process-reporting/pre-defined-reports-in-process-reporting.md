---
title: Rapports prédéfinis dans Process Reporting
description: Requête pour les données de processus AEM Forms on JEE afin de créer des rapports sur les processus à long terme, leur durée et le volume des workflows
content-type: reference
topic-tags: process-reporting
products: SG_EXPERIENCEMANAGER/6.5/FORMS
docset: aem65
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
hide: true
removedfrom6.5.2025: 'yes'
exl-id: 3bf65798-a8ce-4864-9d77-952bb8d8da43
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
  - id: e8f6de9b-cf88-4405-8d10-15efa08c230e
    internal-label: Experience Manager Forms
feature_v2:
  - id: e72c079d-d036-46d5-b43d-29b276a174c2
    internal-label: Authoring and publishing content
subfeature_v2:
  - id: a26f372d-6d7c-452b-81df-594dd4365ae1
    internal-label: Adaptive Forms
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 2e690827bfa8f3d8227860de4efb802758ae0095
workflow-type: tm+mt
source-wordcount: '703'
ht-degree: 100%
---
# Rapports prédéfinis dans Process Reporting {#pre-defined-reports-in-process-reporting}

## Rapports prédéfinis dans Process Reporting {#pre-defined-reports-in-process-reporting-1}

Process Reporting d’AEM Forms est fourni avec les rapports *prêts à l’emploi* suivants :

* **[Processus à long terme](#long-running-processes)** : rapport de tous les processus AEM Forms dont l’exécution a pris plus que le temps spécifié.
* **[Graphique de durée du processus](#process-duration-report)** : rapport d’un processus AEM Forms spécifié par la durée.
* **[Volume des workflows](#workflow-volume-report)** : rapport des instances en cours d’exécution et terminées d’un processus spécifié par date.

## Processus à long terme {#long-running-processes}

Le rapport Processus à long terme affiche les processus AEM Forms dont l’exécution a pris plus que le temps spécifié.

### Pour exécuter un rapport Processus à long terme {#to-execute-a-long-running-process-report}

1. Pour afficher la liste des rapports prédéfinis dans Process Reporting, sur l’arborescence **Process Reporting**, cliquez sur le nœud **Rapports**.
1. Cliquez sur le nœud du rapport **Processus à long terme**.

   ![long_running_node](assets/long_running_node.png)

   Lorsque vous sélectionnez un rapport, le panneau **Paramètres des rapports** s’affiche à droite de l’arborescence.

   ![panneau des paramètres de rapport des processus à long terme](assets/report_parameters_panel.png)

   Paramètres:

   * **Durée** (*obligatoire*) : spécifiez une durée et une unité de temps. Affichez tous les processus AEM Forms dont l’exécution a duré plus que la durée spécifiée.
   * **Démarré après** (*facultatif*) : sélectionnez une date. Filtrez le rapport pour afficher les instances de processus démarrées après la date spécifiée.
   * **Démarré avant** (*facultatif*) : sélectionnez une date. Filtrez le rapport pour afficher les instances de processus qui ont démarré avant la date spécifiée.

1. Cliquez sur **Lancer** pour exécuter le rapport.

   Le rapport s’affiche dans le panneau **Rapport** à droite de la fenêtre **Process Reporting**.

   ![long_running_processes](assets/long_running_processes.png)

   Utilisez les options situées dans le coin supérieur droit du panneau **Rapport** pour effectuer les opérations suivantes sur le rapport.

   * **Actualiser** : permet d’actualiser le rapport avec les dernières données stockées.
   * **Changer la couleur de la légende** : permet de sélectionner et de modifier la couleur de la légende du rapport.
   * **Exporter au format CSV** : permet d’exporter et de télécharger les données du rapport dans un fichier séparé par des virgules.

## Rapport Durée du processus  {#process-duration-report}

Le rapport Durée du processus affiche le nombre d’instances d’un processus Forms par nombre de jours d’exécution de chaque instance.

### Pour exécuter un rapport Durée du processus {#to-execute-a-process-duration-report}

1. Pour afficher les rapports prédéfinis dans Process Reporting, sur l’arborescence **Process Reporting**, cliquez sur le nœud **Rapports**.
1. Cliquez sur le nœud du rapport **Durée des processus**.

   ![process_duration_node](assets/process_duration_node.png)

   Lorsque vous sélectionnez un rapport, le panneau **Paramètres des rapports** s’affiche à droite de l’arborescence.

   ![panneau des paramètres de rapport des processus à long terme](assets/process_duration_params.png)

   Paramètres:

   * **Sélectionnez un processus** (*obligatoire*) : sélectionnez un processus AEM Forms.

1. Cliquez sur **Lancer** pour exécuter le rapport.

   Le rapport s’affiche dans le panneau **Rapport** à droite de la fenêtre Process Reporting.

   ![process_duration_report](assets/process_duration_report.png)

   Utilisez les options situées dans le coin supérieur droit du panneau **Rapport** pour effectuer les opérations suivantes sur le rapport.

   * **Actualiser** : permet d’actualiser le rapport avec les dernières données stockées.
   * **Changer la couleur de la légende** : permet de sélectionner et de modifier la couleur de la légende du rapport.
   * **Exporter au format CSV** : permet d’exporter et de télécharger les données du rapport dans un fichier séparé par des virgules.

## Rapport Volume des workflows {#workflow-volume-report}

Le rapport Volume des workflows affiche le nombre d’instances en cours d’exécution et terminées d’un processus AEM Forms par jour calendaire.

### Pour exécuter un rapport Volume des workflows {#to-execute-a-workflow-volume-report}

1. Pour afficher les rapports prédéfinis dans Process Reporting, sur la vue arborescente de **Process Reporting**, cliquez sur le nœud **Rapports**.
1. Cliquez sur le nœud rapport **Volume de workflow**.

   ![workflow_volume_node](assets/workflow_volume_node.png)

   Lorsque vous sélectionnez un rapport, le panneau **Paramètres des rapports** s’affiche à droite de l’arborescence.

   ![panneau des paramètres de rapport des processus à long terme](assets/workflow_volume_params.png)

   Paramètres:

   * **Sélectionner un processus** (*obligatoire*) : sélectionnez un processus AEM Forms.

   * **Démarré après** (*facultatif*) : sélectionnez une date. Filtre le rapport afin d’afficher les instances de processus démarrées après la date spécifiée.

   * **Démarré avant** (*facultatif*) : sélectionnez une date. Filtre le rapport pour afficher les instances de processus qui ont démarré avant la date spécifiée.

1. Cliquez sur **Lancer** pour exécuter le rapport.

   Le rapport s’affiche dans le panneau **Rapport** à droite de la fenêtre **Process Reporting**.

   ![workflow_volume_report](assets/workflow_volume_report.png)

   Utilisez les options situées dans le coin supérieur droit du panneau **Rapport** pour effectuer les opérations suivantes sur le rapport.

   * **Actualiser** : permet d’actualiser le rapport avec les dernières données stockées.
   * **Changer la couleur de la légende** : permet de sélectionner et de modifier la couleur de la légende du rapport.
   * **Exporter au format CSV** : permet d’exporter et de télécharger les données du rapport dans un fichier séparé par des virgules.
