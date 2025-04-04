---
title: API pour appeler le service de modèle de données de formulaire à partir de formulaires adaptatifs
description: Décrit l’API invokeWebServices que vous pouvez utiliser pour appeler les services web écrits dans WSDL depuis un champ de formulaire adaptatif.
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: develop
discoiquuid: aa3e50f1-8f5a-489d-a42e-a928e437ab79
feature: Adaptive Forms,Foundation Components
solution: Experience Manager, Experience Manager Forms
role: User, Developer
exl-id: e36be2da-af72-485f-87a6-cef6172037c6
source-git-commit: c3e9029236734e22f5d266ac26b923eafbe0a459
workflow-type: tm+mt
source-wordcount: '533'
ht-degree: 100%

---

# API pour appeler le service de modèle de données de formulaire à partir de formulaires adaptatifs {#api-to-invoke-form-data-model-service-from-adaptive-forms}

<span class="preview"> Adobe recommande d’utiliser les [composants principaux](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html?lang=fr) de capture de données modernes et extensibles pour [créer de nouveaux formulaires adaptatifs](/help/forms/using/create-an-adaptive-form-core-components.md) ou [ajouter des formulaires adaptatifs à des pages AEM Sites](/help/forms/using/create-or-add-an-adaptive-form-to-aem-sites-page.md). Ces composants représentent une avancée significative dans la création de formulaires adaptatifs, ce qui garantit des expériences utilisateur impressionnantes. Cet article décrit l’ancienne approche de la création de formulaires adaptatifs à l’aide de composants de base. </span>

## Vue d’ensemble {#overview}

AEM Forms permet aux créateurs et créatrices de formulaires de simplifier et d’améliorer le remplissage de formulaire en appelant les services configurés dans un modèle de données de formulaire depuis un champ de formulaire adaptatif. Pour appeler un service de modèle de données, vous pouvez créer une règle dans l’éditeur visuel ou spécifier un script JavaScript en utilisant l’API `guidelib.dataIntegrationUtils.executeOperation` dans l’éditeur de code de l’[éditeur de règles](/help/forms/using/rule-editor.md).

Ce document se concentre sur l’écriture d’un script JavaScript en utilisant l’API `guidelib.dataIntegrationUtils.executeOperation` pour appeler un service.

## Utilisation de l’API {#using-the-api}

L’API `guidelib.dataIntegrationUtils.executeOperation` appelle un service depuis un champ de formulaire adaptatif. La syntaxe API se présente comme suit :

```javascript
guidelib.dataIntegrationUtils.executeOperation(operationInfo, inputs, outputs)
```

La structure de l’API `guidelib.dataIntegrationUtils.executeOperation` spécifie les détails sur l’opération de service. La syntaxe de la structure se présente comme suit.

```javascript
var operationInfo = {
formDataModelId,
operationTitle,
operationName
};
var inputs = {
inputField1,
inputFieldN
};
var outputs = {
outputField1,
outputFieldN
}
```

La structure de l’API spécifie les détails suivants concernant l’opération de service.

<table>
 <tbody>
  <tr>
   <th>Paramètre</th>
   <th>Description</th>
  </tr>
  <tr>
   <td><code>operationInfo</code></td>
   <td>Structure permettant de spécifier l’identifiant du modèle de données de formulaire, le titre de l’opération et le nom de l’opération</td>
  </tr>
  <tr>
   <td><code>formDataModelId</code></td>
   <td>Indique le chemin d’accès au référentiel du modèle de données de formulaire, y compris son nom.</td>
  </tr>
  <tr>
   <td><code>operationName</code></td>
   <td>Indique le nom de l’opération de service à exécuter.</td>
  </tr>
  <tr>
   <td><code>inputs</code></td>
   <td>Mappe un ou plusieurs objets de formulaire aux arguments d’entrée pour l’opération de service.</td>
  </tr>
  <tr>
   <td><code>Outputs</code></td>
   <td>Mappe un ou plusieurs objets de formulaire aux valeurs de sortie de l’opération de service afin de renseigner les champs de formulaire<br />. </td>
  </tr>
  <tr>
   <td><code>success</code></td>
   <td>Renvoie des valeurs en fonction des arguments d’entrée pour l’opération de service. Il s’agit d’un paramètre facultatif utilisé comme fonction de rappel.<br /> </td>
  </tr>
  <tr>
   <td><code>failure</code></td>
   <td>Affiche un message d’erreur si la fonction de rappel de succès n’affiche pas les valeurs de sortie en fonction des arguments d’entrée. Il s’agit d’un paramètre facultatif utilisé comme fonction de rappel.<br /> </td>
  </tr>
 </tbody>
</table>

## Exemple de script pour appeler un service {#sample-script-to-invoke-a-service}

L’exemple de script suivant utilise l’API `guidelib.dataIntegrationUtils.executeOperation` pour appeler l’opération de service `getAccountById` configurée dans le modèle de données de formulaire `employeeAccount`.

L’opération `getAccountById` utilise la valeur du champ de formulaire `employeeID` comme entrée pour l’argument `empId` et renvoie le nom de l’employé, le numéro de compte et le solde du compte pour l’employé correspondant. Les valeurs de sortie sont renseignées dans les champs de formulaire spécifiés. Par exemple, la valeur de l’argument `name` est renseignée dans l’élément de formulaire `fullName` et la valeur de l’argument `accountNumber`, dans l’élément de formulaire `account`.

```javascript
var operationInfo = {
"formDataModelId": "/content/dam/formsanddocuments-fdm/employeeAccount",
"operationName": "getAccountDetails"
};
var inputs = {
"empid" : employeeID
};
var outputs = {
"name" : fullName,
"accountNumber" : account,
"balance" : balance
};
guidelib.dataIntegrationUtils.executeOperation(operationInfo, inputs, outputs);
```

## Utilisation de l’API avec la fonction de rappel {#using-the-api-callback}

Vous pouvez également appeler le service de modèle de données de formulaire à l’aide de l’API `guidelib.dataIntegrationUtils.executeOperation` avec une fonction de rappel. La syntaxe API se présente comme suit :

```javascript
guidelib.dataIntegrationUtils.executeOperation(operationInfo, inputs, outputs, callbackFunction)
```

La fonction d’appel peut avoir des fonctions de rappel `success` et `failure`.

### Exemple de script avec fonctions de rappel de succès et d’échec {#callback-function-success-failure}

L’exemple de script suivant utilise l’API `guidelib.dataIntegrationUtils.executeOperation` pour appeler l’opération de service `GETOrder` configurée dans le modèle de données de formulaire `employeeOrder`.

L’opération `GETOrder` prend la valeur du champ de formulaire `Order ID` comme entrée pour l’argument `orderId` et renvoie la valeur de quantité de commande dans la fonction de rappel `success`.  Si la fonction de rappel `success` ne renvoie pas la quantité de commande, la fonction de rappel `failure` affiche le message `Error occured`.

>[!NOTE]
>
>Si vous utilisez la fonction de rappel `success`, les valeurs de sortie ne sont pas renseignées dans les champs de formulaire spécifiés.

```javascript
var operationInfo = {
    "formDataModelId": "/content/dam/formsanddocuments-fdm/employeeOrder",
    "operationTitle": "GETOrder",
    "operationName": "GETOrder"
};
var inputs = {
    "orderId" : Order ID
};
var outputs = {};
var success = function (wsdlOutput, textStatus, jqXHR) {
order_quantity.value = JSON.parse(wsdlOutput).quantity;
 };
var failure = function(){
alert('Error occured');
};
guidelib.dataIntegrationUtils.executeOperation(operationInfo, inputs, outputs, success, failure);
```
