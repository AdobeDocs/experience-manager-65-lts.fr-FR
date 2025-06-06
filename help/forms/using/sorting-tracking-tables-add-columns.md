---
title: Personnaliser les tableaux de tracking
description: Comment personnaliser l’affichage des détails des processus utilisateur dans le tableau des tâches affiché dans l’onglet de suivi de l’espace de travail AEM Forms.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-workspace
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
exl-id: 27589617-4020-490c-b01e-1b169ae0801a
source-git-commit: c3e9029236734e22f5d266ac26b923eafbe0a459
workflow-type: tm+mt
source-wordcount: '330'
ht-degree: 100%

---

# Personnaliser les tableaux de tracking{#customize-tracking-tables}

L’onglet de suivi dans l’espace de travail AEM Forms est utilisé pour afficher les détails des instances de processus dans lesquelles l’utilisateur connecté est impliqué. Afin de visualiser les tableaux de suivi, vous devez d’abord sélectionner le nom d’un processus dans le volet gauche pour afficher la liste de ses instances dans le volet central. Sélectionnez une instance de processus pour afficher un tableau des tâches générées par cette instance dans le volet droit. Par défaut, les colonnes du tableau affichent les attributs de tâche suivants (l’attribut correspondant dans le modèle de tâche apparaît entre parenthèses) :

* ID ( `taskId`)
* Nom ( `stepName`)
* Instructions ( `instructions`)
* Action sélectionnée ( `selectedRoute`)
* Heure de création (`createTime`)
* Heure de fin (`completeTime`)
* Propriétaire ( `currentAssignment.queueOwner`)

Les attributs restants dans le modèle de tâche disponibles à l’affichage dans le tableau de la tâche sont les suivants :

<table>
 <tbody>
  <tr>
   <td><p>actionInstanceId</p> </td>
   <td><p>isOpenFullScreen</p> </td>
   <td><p>reminderCount</p> </td>
  </tr>
  <tr>
   <td><p>classOfTask</p> </td>
   <td><p>isOwner</p> </td>
   <td><p>routeList</p> </td>
  </tr>
  <tr>
   <td><p>consultGroupId</p> </td>
   <td><p>isRouteSelectionRequired</p> </td>
   <td><p>savedFormCount</p> </td>
  </tr>
  <tr>
   <td><p>contentType</p> </td>
   <td><p>isShowAttachments</p> </td>
   <td><p>serializedImageTicket</p> </td>
  </tr>
  <tr>
   <td><p>createTime</p> </td>
   <td><p>isStartTask</p> </td>
   <td><p>serviceName</p> </td>
  </tr>
  <tr>
   <td><p>creationId</p> </td>
   <td><p>isVisible</p> </td>
   <td><p>serviceTitle</p> </td>
  </tr>
  <tr>
   <td><p>currentAssignment</p> </td>
   <td><p>nextReminder</p> </td>
   <td><p>showACLActions</p> </td>
  </tr>
  <tr>
   <td><p>deadline</p> </td>
   <td><p>numForms</p> </td>
   <td><p>showDirectActions</p> </td>
  </tr>
  <tr>
   <td><p>description</p> </td>
   <td><p>numFormsToBeSaved</p> </td>
   <td><p>status</p> </td>
  </tr>
  <tr>
   <td><p>displayName</p> </td>
   <td><p>outOfOfficeUserId</p> </td>
   <td><p>summaryUrl</p> </td>
  </tr>
  <tr>
   <td><p>forwardGroupId</p> </td>
   <td><p>outOfOfficeUserName</p> </td>
   <td><p>supportsSave</p> </td>
  </tr>
  <tr>
   <td><p>isApprovalUI</p> </td>
   <td><p>priority</p> </td>
   <td><p>taskACL</p> </td>
  </tr>
  <tr>
   <td><p>isCustomUI</p> </td>
   <td><p>processInstanceId</p> </td>
   <td><p>taskFormType</p> </td>
  </tr>
  <tr>
   <td><p>isDefaultImage</p> </td>
   <td><p>processInstanceStatus</p> </td>
   <td><p>taskUserInfo</p> </td>
  </tr>
  <tr>
   <td><p>isLocked</p> </td>
   <td><p>processVariables</p> </td>
   <td> </td>
  </tr>
  <tr>
   <td><p>isMustOpenToComplete</p> </td>
   <td><p>readerSubmitOptions</p> </td>
   <td> </td>
  </tr>
 </tbody>
</table>

Pour les personnalisations suivantes dans le tableau de la tâche, vous devez effectuer des modifications sémantiques dans le code source. Reportez-vous à la section [Introduction à la personnalisation de l’espace de travail AEM Forms](/help/forms/using/introduction-customizing-html-workspace.md) pour savoir comment effectuer des modifications sémantiques à l’aide du SDK de l’espace de travail et créer un package minimisé à partir de la source modifiée.

## Modification des colonnes du tableau et de leur ordre {#changing-table-columns-and-their-order}

1. Pour modifier les attributs de tâche affichés dans le tableau et leur ordre, configurez le fichier /ws/js/runtime/templates/processinstancehistory.html :

   ```html
   <table>
       <thead>
           <tr>
               <!-- put the column headings in order here, for example-->
               <th><%= $.t('history.fixedTaskTableHeader.taskName')%></th>
               <th><%= $.t('history.fixedTaskTableHeader.taskInstructions')%></th>
               <th><%= $.t('history.fixedTaskTableHeader.taskRoute')%></th>
               <th><%= $.t('history.fixedTaskTableHeader.taskCreateTime')%></th>
               <th><%= $.t('history.fixedTaskTableHeader.taskCompleteTime')%></th>
           </tr>
       </thead>
   </table>
   ```

   ```html
   <table>
       <tbody>
           <%_.each(obj, function(task){%>
           <tr>
               <!-- Put the task attributes in the order of headings, for example, -->
               <td><%= task.stepName %></td>
               <td><%= task.instructions %></td>
               <td><%= !task.selectedRoute?'':(task.selectedRoute=='null'?'Default':task.selectedRoute) %></td>
               <td><%= task.createTime?task.formattedCreateTime:'' %></td>
               <td><%= task.completeTime? task.formattedCompleteTime:'' %></td>
           </tr>
           <%});%>
       </tbody>
   </table>
   ```

## Tri d’un tableau de suivi {#sorting-a-tracking-table}

Pour trier le tableau de la liste des tâches lorsque vous cliquez sur l’en-tête de colonne :

1. Enregistrez un gestionnaire de clic pour `.fixedTaskTableHeader th` dans le fichier `js/runtime/views/processinstancehistory.js`.

   ```javascript
   events: {
       //other handlers
       "click .fixedTaskTableHeader th": "onTaskTableHeaderClick",
       //other handlers
   }
   ```

   Dans le gestionnaire, appelez la fonction `onTaskTableHeaderClick` de `js/runtime/util/history.js`.

   ```javascript
   onTaskTableHeaderClick: function (event) {
           history.onTaskTableHeaderClick(event);
   }
   ```

1. Exposez la méthode `TaskTableHeaderClick` dans `js/runtime/util/history.js`.

   La méthode trouve l’attribut de tâche à partir de l’événement de clic, trie la liste de tâches en fonction de cet attribut et effectue le rendu de la table de tâches avec la liste de tâches triée.

   Le tri est effectué à l’aide de la fonction de tri Backbone sur la collection de liste de tâches en fournissant une fonction de comparaison.

   ```javascript
       return {
           //other methods
           onTaskTableHeaderClick  : onTaskTableHeaderClick,
           //other methods
       };
   ```

   ```javascript
   onTaskTableHeaderClick = function (event) {
           var target = $(event.target),
            comparator,
               attribute;
           if(target.hasClass('taskName')){
            attribute = 'stepName';
           } else if(target.hasClass('taskInstructions')){
               attribute = 'instructions';
           } else if(target.hasClass('taskRoute')){
               attribute = 'selectedRoute';
           } else if(target.hasClass('taskCreateTime')){
               attribute = 'createTime';
           } else if(target.hasClass('taskCompleteTime')){
               attribute = 'completeTime';
           }
           taskList.comparator = function (task) {
            return task.get(attribute);
           };
           taskList.sort();
           render();
       };
   ```
