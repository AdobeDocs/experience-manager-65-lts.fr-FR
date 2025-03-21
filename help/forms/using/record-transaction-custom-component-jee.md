---
title: Enregistrement d’une transaction de l’API de composant personnalisé pour AEM Forms sur JEE
description: Découvrez comment utiliser l’API TransactionRecorder pour enregistrer les transactions d’un composant personnalisé.
feature: Transaction Reports
role: Admin, User, Developer
solution: Experience Manager, Experience Manager Forms
hide: true
hidefromtoc: true
exl-id: e2d1b548-ce30-471b-b01c-ce37b737aeb5
source-git-commit: bc91f56d447d1f2c26c160f5c414fd0e6054f84c
workflow-type: tm+mt
source-wordcount: '218'
ht-degree: 100%

---

# Enregistrement d’une transaction pour les API de composant personnalisées pour AEM Forms sur OSGi {#record-a-transaction-for-custom-components}

Lorsque vous utilisez des API facturables dans votre composant personnalisé, vous pouvez activer la création de rapports de transactions pour le composant. Pour activer la création de rapports de transactions, modifiez le fichier `component.xml` du composant et ajoutez la balise donnée ci-dessous sous l’opération pour laquelle la création de rapports de transactions doit être activée.

**Balise** : `<transaction-operation-type>CONVERT</transaction-operation-type> // Supported values are SUBMIT, CONVERT, RENDER.`

| Ancienne balise d’opération | Nouvelle balise d’opération |
| ----------- | ----------- |
| `<operation>`<br> `<.... tags`<br>`<...>`<br>`<operation>` | `<operation>`<br> `<.... tags`<br>`<...>`<br>`<transaction-operation-type>CONVERT</transaction-operation-type`<br>`<operation>` |

Si vous devez capturer plusieurs transactions pour une API, par exemple une API par lot où le nombre de transactions varie en fonction du nombre d’entrées, gérez le nombre de transactions au niveau de l’API.

**Pour enregistrer le nombre des différentes transactions, procédez comme suit :**

1. Importez la classe `"com.adobe.idp.dsc.InvocationContextStack"` dans le code. La classe fait partie du fichier sdk `adobe-livecycle-client.jar`. Le fichier sdk est disponible dans `<AEM_Forms_JEE_Install>\sdk\client-libs\common`.

   >[!NOTE]
   > Mettez à jour le fichier client partagé ci-dessus dans votre projet client avec le nouveau fichier au cas où il serait déjà regroupé.

1. Dans l’API pour laquelle différentes transactions doivent être consignées, procédez comme suit :
   1. Ajoutez une logique afin de pouvoir stocker le nombre de transactions dans une variable entière, telle que `transaction_count`.
   1. Une fois l’opération réussie, ajoutez `InvocationContextStack.recordTransactionCount(transaction_count)`.

<!--For example, you can set count for your custom component by importing class `"com.adobe.idp.dsc.InvocationContextStack"` in the code available at `adobe-livecycle-client.jar`  and determine the transaction count basis API input/result and add (In this case we add count is equal to 3):
`InvocationContextStack.recordTransactionCount(<count>).` to 
`InvocationContextStack.recordTransactionCount(3)`.-->

## Articles connexes

* [Activation et affichage des rapports de transaction pour AEM Forms sur JEE](/help/forms/using/transaction-report-overview-jee.md)
* [Liste des API facturables pour AEM Forms sur JEE](/help/forms/using/transaction-reports-billable-apis-jee.md)
