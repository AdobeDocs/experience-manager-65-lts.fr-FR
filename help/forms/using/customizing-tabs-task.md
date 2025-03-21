---
title: Personnalisation des onglets d’une tâche
description: Comment personnaliser les noms des onglets de vos tâches dans l’espace de travail AEM Forms LiveCycle.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-workspace
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
exl-id: 88f5093c-f249-4e4b-900a-5897f47e513c
source-git-commit: c3e9029236734e22f5d266ac26b923eafbe0a459
workflow-type: tm+mt
source-wordcount: '101'
ht-degree: 100%

---

# Personnalisation des onglets d’une tâche {#customizing-tabs-for-a-task}

Vous pouvez personnaliser les noms des onglets pour le `Start Process`composant dans l’affichage `Start Process` Uber et le `Task Details` composant `ToDo` de l’affichage Uber.

1. Suivez la [Procédure générique de personnalisation de l’espace de travail AEM Forms](/help/forms/using/generic-steps-html-workspace-customization.md).
1. Modifiez la valeur de `tabname` dans le fichier `translation.json`.

   Par exemple, modifiez `/apps/ws/locales/en-US/translation.json`/ pour l’anglais de la façon suivante.

   * Pour des tâches lancées dans le processus de démarrage, utilisez le fragment de code ci-dessous dans le bloc `"startprocess" : {}`.

   ```json
   "tabname" : {
               "form" : "Application",
               "details" : "Overview",
               "attachments" : "Attachments",
               "notes" : "Helper Notes"
           }
   ```

   * Pour des tâches dans Tâches, utilisez le fragment de code suivant dans le bloc `"todo" : {}`.

   ```json
   "tabname" : {
               "summary" : "Bird's-eye view",
               "history" : "Past",
               "form" : "Form",
               "details" : "Overview",
               "attachments" : "Attachments",
               "notes" : "Notes"
   }
   ```

   >[!NOTE]
   >
   >Ajoutez la paire clé-valeur correspondante pour toutes les langues prises en charge.
