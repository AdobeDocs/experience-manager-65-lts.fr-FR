---
title: Personnaliser les images utilisées dans les actions d’itinéraire
description: Comment personnaliser les images utilisées dans les actions d’itinéraire dans l’espace de travail AEM Forms LiveCycle.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-workspace
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
exl-id: 782043c0-79f8-42a4-ae1b-4743b480e523
source-git-commit: b8576049fba41b3bec16046316938274a5046513
workflow-type: tm+mt
source-wordcount: '287'
ht-degree: 100%

---

# Personnaliser les images utilisées dans les actions d’itinéraire {#customize-images-used-in-route-actions}

Pour personnaliser les images utilisées dans les actions d’itinéraire, suivez la procédure décrite à la section [Procédure générique de personnalisation](/help/forms/using/generic-steps-html-workspace-customization.md), suivie des étapes décrites dans cet article.

## Images pour les actions d’itinéraire {#images-for-route-actions}

1. Ajoutez les styles définissant les images dans le CSS à l’emplacement suivant pour les nouvelles actions d’itinéraire :

   `/apps/ws/css/newStyle.css`

   Par exemple : ajoutez un nouveau style appelé `myStyle1` comme indiqué ci-dessous et chargez le fichier image `myStyleIcon1.png` dans le dossier `/apps/ws/image` à l’aide d’un client WebDAV.

   >[!NOTE]
   >
   >Pour plus d’informations, voir [Accès WebDAV](/help/sites-administering/webdav-access.md).

   >[!NOTE]
   >
   >Préférez l’utilisation du nom du style pour qu’il soit identique au nom de l’action d’itinéraire.

   ```css
   .myStyle1{
   
           background-image: url('../images/myStyleIcon1.png');
   
       }
   ```

## Fenêtre contextuelle d’action de la liste des tâches {#task-list-task-action-popup}

1. Créez un menu déroulant d’actions de liste de tâches, voir [Création du code de l’espace de travail AEM Forms](introduction-customizing-html-workspace.md#building-html-workspace-code). Vous devez utiliser le package de développement.

1. Copiez `/libs/ws/js/runtime/templates/task.html` dans `/apps/ws/js/runtime/templates/task.html`.

1. Si le nom du style CSS est identique au nom de l’action d’itinéraire provenant du serveur, modifiez le code suivant dans `/apps/ws/js/runtime/templates/task.html` :

   ```jsp
   <%if(routeList == null){%>
               <li>
                   <a href="javascript:void(0);" title="<%= $.t('taskaction.directcommand.'+availableCommands.directCommands[0])%>" value="<%= availableCommands.directCommands[0]%>" data-action="route"><%= $.t('taskaction.directcommand.'+availableCommands.directCommands[0])%></a>
               </li>
               <%}else{%>
               <%for(var i = 0; i<availableCommands.directCommands.length; i++){%>
               <li>
                   <a href="javascript:void(0);" title="<%= availableCommands.directCommands[i]%>" value="<%= availableCommands.directCommands[i]%>" data-action="route"><%= availableCommands.directCommands[i]%></a>
               </li>
               <%}%>
               <%}%>
   
   To
   
   <%if(routeList == null){%>
               <li class="<%= availableCommands.directCommands[0]%>" alt="<%= $.t('taskaction.directcommand.'+availableCommands.directCommands[0]+'.value')%>">
                   <a href="javascript:void(0);" title="<%= $.t('taskaction.directcommand.'+availableCommands.directCommands[0])%>" value="<%= availableCommands.directCommands[0]%>" data-action="route"><%= $.t('taskaction.directcommand.'+availableCommands.directCommands[0])%></a>
               </li>
               <%}else{%>
               <%for(var i = 0; i<availableCommands.directCommands.length; i++){%>
               <li class="<%= availableCommands.directCommands[i]%>" alt="<%= $.t('taskaction.directcommand.'+availableCommands.directCommands[i]+'.value')%>">
                   <a href="javascript:void(0);" title="<%= availableCommands.directCommands[i]%>" value="<%= availableCommands.directCommands[i]%>" data-action="route"><%= availableCommands.directCommands[i]%></a>
               </li>
               <%}%>
               <%}%>
   ```

1. Si le nom du style CSS est différent du nom de l’action d’itinéraire provenant du serveur, modifiez le code suivant dans `/apps/ws/js/runtime/templates/task.html`. Il ajoute une pile des conditions de servlet `if-else` pour mapper le style avec le nom de l’action d’itinéraire.

```jsp
<%if(routeList == null){%>
            <li>
                <a href="javascript:void(0);" title="<%= $.t('taskaction.directcommand.'+availableCommands.directCommands[0])%>" value="<%= availableCommands.directCommands[0]%>" data-action="route"><%= $.t('taskaction.directcommand.'+availableCommands.directCommands[0])%></a>
            </li>
            <%}else{%>
            <%for(var i = 0; i<availableCommands.directCommands.length; i++){%>
            <li>
                <a href="javascript:void(0);" title="<%= availableCommands.directCommands[i]%>" value="<%= availableCommands.directCommands[i]%>" data-action="route"><%= availableCommands.directCommands[i]%></a>
            </li>
            <%}%>
            <%}%>

To

<%if(routeList == null){%>
            <li class="<%= availableCommands.directCommands[0]%>" alt="<%= $.t('taskaction.directcommand.'+availableCommands.directCommands[0]+'.value')%>">
                <a href="javascript:void(0);" title="<%= $.t('taskaction.directcommand.'+availableCommands.directCommands[0])%>" value="<%= availableCommands.directCommands[0]%>" data-action="route"><%= $.t('taskaction.directcommand.'+availableCommands.directCommands[0])%></a>
            </li>
            <%}else{%>
            <%for(var i = 0; i<availableCommands.directCommands.length; i++){%>
                <%if(availableCommands.directCommands[i].equals("myAction1")){%>
                     <li class="myStyle1" alt="<%= $.t('taskaction.directcommand.'+availableCommands.directCommands[i]+'.value')%>">
                         <a href="javascript:void(0);" title="<%= availableCommands.directCommands[i]%>" value="<%= availableCommands.directCommands[i]%>" data-action="route"><%= availableCommands.directCommands[i]%></a>
                     </li>
                <%}else if(availableCommands.directCommands[i].equals("myAction2")){%>
                     <li class="myStyle2" alt="<%= $.t('taskaction.directcommand.'+availableCommands.directCommands[i]+'.value')%>">
                         <a href="javascript:void(0);" title="<%= availableCommands.directCommands[i]%>" value="<%= availableCommands.directCommands[i]%>" data-action="route"><%= availableCommands.directCommands[i]%></a>
                     </li>
                <%}%>
            <%}%>
            <%}%>
```

## Menu déroulant de l’action de tâche Détails de la tâche {#task-details-task-action-popup}

1. Copiez `/libs/ws/js/runtime/templates/taskdetails.html` dans `/apps/ws/js/runtime/templates/taskdetails.html`.

1. Si le nom du style CSS est identique au nom de l’action d’itinéraire provenant du serveur, modifiez le code suivant dans `/apps/ws/js/runtime/templates/taskdetails.html` :

   ```jsp
   <%for (var i = 0; i < availableCommands.directCommands.length; i++) {%>
                           <li class="routeAction">
                               <a href="javascript:void(0);" title="<%= availableCommands.directCommands[i]%>" value="<%= availableCommands.directCommands[i]%>" data-action="route"><%= availableCommands.directCommands[i]%></a>
                           </li>
                       <%}%>
   
   To
   
   <%for (var i = 0; i < availableCommands.directCommands.length; i++) {%>
                           <li class="routeAction">
                               <a href="javascript:void(0);" title="<%= availableCommands.directCommands[i]%>" value="<%= availableCommands.directCommands[i]%>" data-action="route">
                               <i class="<%= availableCommands.directCommands[i]%>" value="<%= availableCommands.directCommands[i]%>" data-action="route"/>
                               </a>
                           </li>
                       <%}%>
   ```

1. Si le nom du style CSS est différent du nom de l’action d’itinéraire provenant du serveur, modifiez le code suivant dans `/apps/ws/js/runtime/templates/taskdetails.html`. Il ajoute une pile des conditions de servlet `if-else` pour mapper le style avec le nom de l’action d’itinéraire.

   ```jsp
   <%for (var i = 0; i < availableCommands.directCommands.length; i++) {%>
                           <li class="routeAction">
                               <a href="javascript:void(0);" title="<%= availableCommands.directCommands[i]%>" value="<%= availableCommands.directCommands[i]%>" data-action="route"><%= availableCommands.directCommands[i]%></a>
                           </li>
                       <%}%>
   
   To
   
   <%for (var i = 0; i < availableCommands.directCommands.length; i++) {%>
                   <%if(availableCommands.directCommands[i].equals("myAction1")){%>
                       <li class="routeAction">
                               <a href="javascript:void(0);" title="<%= availableCommands.directCommands[i]%>" value="<%= availableCommands.directCommands[i]%>" data-action="route">
                               <i class="myStyle1" value="<%= availableCommands.directCommands[i]%>" data-action="route"/>
                               </a>
                           </li>
                   <%}else if(availableCommands.directCommands[i].equals("myAction2")){%>
                       <li class="routeAction">
                               <a href="javascript:void(0);" title="<%= availableCommands.directCommands[i]%>" value="<%= availableCommands.directCommands[i]%>" data-action="route">
                               <i class="myStyle2" value="<%= availableCommands.directCommands[i]%>" data-action="route"/>
                               </a>
                           </li>
                   <%}%>
               <%}%>
   ```

1. Ouvrez `/apps/ws/js/registry.js` pour le modifier et recherchez le texte suivant :
   `"text!/lc/libs/ws/js/runtime/templates/taskdetails.html"`

1. Remplacez le texte par le texte suivant :
   `"text!/lc/apps/ws/js/runtime/templates/taskdetails.html"`
