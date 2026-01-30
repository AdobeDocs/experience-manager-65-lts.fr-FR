---
title: Présentation du site de référence de renouvellement de l’assurance automobile We.Finance
description: Découvrez le site de référence de renouvellement de l’assurance automobile « We.Finance » en consultant une présentation.
contentOwner: dekalra
products: SG_EXPERIENCEMANAGER/6.5/FORMS
content-type: reference
docset: aem65
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms,Foundation Components
role: User, Developer
exl-id: 3f9f1a20-9029-4e30-9c9d-ef452512f7e9
source-git-commit: c0bf6864bb344e582c4f88371c892d401ce2827c
workflow-type: tm+mt
source-wordcount: '744'
ht-degree: 48%

---

# Présentation du site de référence du renouvellement de l’assurance automobile `We.Finance`{#we-finance-auto-insurance-renewal-reference-site-walkthrough}

## `We.Finance` du site de référence  {#we-finance-reference-site-scenario}

Le site web `We.Finance` est un site de services financiers conçu pour vous aider à découvrir les fonctionnalités de communication interactive d’AEM Forms.

Lisez une présentation détaillée d’un cas d’utilisation d’assurance automobile `We.Finance` qui montre comment AEM forms et son intégration à Microsoft® Dynamics permettent de personnaliser l’expérience client dans une société de services financiers. La présentation interactive est conçu pour faciliter l’implémentation de transactions numériques complexes et la communication avec les clients dans une société financière.

**La présentation commence par le cas d’utilisation :**

Sarah Rose est déjà cliente `We.Finance` et a acheté une police d’assurance automobile. C’est à ce moment de l’année que Sarah renouvelle sa police d’assurance. Gloria Rios est son assureuse. Le site web `We.Finance` envoie un rappel à Sarah au sujet de son renouvellement de politique. Sarah suit les instructions contenues dans l’e-mail et termine correctement le processus.

## Présentation de la demande d’assurance automobile {#auto-insurance-application-walkthrough}

Le scénario de demande d’assurance automobile `We.Finance` est une narration visuelle pour l’utilisateur et repose sur deux personnes :

* Sarah Rose, cliente `We.Finance`
* Gloria Rios, agent d&#39;assurance, `We.Finance`

### Gloria envoie une communication de renouvellement de police d’assurance depuis `We.Finance` {#gloria-sends-an-insurance-policy-renewal-communication-from-we-finance}

Gloria se connecte à l’instance AEM, clique sur **Renouvellement de l’assurance automobile**, puis sur **Ouvrir l’interface utilisateur de l’agent**. Le clic préremplit le document d’assurance avec les détails de la police de Sarah Rose. Gloria clique sur **Envoyer** et un message « Envoi en cours » apparaît à l’écran. Quelques secondes plus tard, le message « Envoyé » s’affiche.

Sarah reçoit un e-mail dont l’objet est « Votre renouvellement d’assurance automobile ».

![Interface utilisateur de l’agent](assets/agent_ui_email_new.png)

#### Démonstration {#see-it-yourself}

Accédez à **Adobe Experience Manager** > **Forms** > **Forms et documents** > **`We.Finance`** > **Assurance automobile**. Sélectionnez **Communication interactive** du renouvellement de l’assurance automobile, puis cliquez sur **Ouvrir l’interface utilisateur de l’agent**. La communication interactive s’ouvre dans l’interface utilisateur de l’agent. Saisissez une adresse e-mail valide pour envoyer un e-mail contenant le document de police joint, puis cliquez sur Envoyer.

Vous pouvez accéder à la communication interactive du renouvellement de l’assurance automobile et la consulter directement depuis `https://[authorHost]: authorPort]/aem/formdetails.html/content/dam/formsanddocuments/we-finance/autoinsurance/auto-insurance-renewal.`.

### Sarah reçoit une communication de renouvellement de police d’assurance de `We.Finance` et décide de procéder au renouvellement {#sarah-receives-an-insurance-policy-renewal-communication-from-we-finance-and-decides-to-renew}

Sarah reçoit un e-mail contenant une pièce jointe de `We.Finance`, lui rappelant que sa police d’assurance automobile est sur le point d’expirer. La pièce jointe contient la version imprimée de la lettre d’assurance automobile de Sarah.

Sarah clique sur l’option **Renouveler maintenant** et est redirigée vers la version web de sa lettre d’assurance automobile. En haut de cette lettre, Sarah trouve le temps restant dans la politique avant son expiration. Cette page donne un aperçu de la police d’assurance. Il détaille le numéro de police, le montant dû, les offres de remise et les récompenses de fidélité. Cliquez sur **Renouveler maintenant** au bas de la police.

![ref1](assets/ref1.png)

#### Fonctionnement {#how-it-works}

Les versions web et imprimées de votre lettre d’assurance automobile sont créées à l’aide des fonctionnalités multicanales des communications interactives.

Le bouton Renouveler maintenant figurant dans l’e-mail est lié à l’application Renouveler l’assurance automobile , qui est une communication interactive sur une instance de publication.

#### Démonstration {#see-it-yourself-1}

Vous devriez recevoir un e-mail avec un fichier PDF joint. Le fichier PDF est une version imprimée de votre lettre d’assurance automobile. Cliquez sur **Renouveler maintenant** pour accéder à la version web de la police. Vérifiez vos informations personnelles et les détails de la police, puis cliquez sur **Renouveler maintenant** pour être redirigé vers une autre communication interactive.

Le bouton **Renouveler maintenant** figurant dans l’e-mail redirige Sarah vers la version web de la police. Vous pouvez consulter l’URL suivante :

`https://[authorServer]:[authorPort]/content/document.html?schema=fdm&documentId=/content/forms/af/we-finance/autoinsurance/auto-insurance-renewal/channels/web.html&customerId=1`

Vous pouvez vérifier le résumé détaillé de votre renouvellement d’assurance automobile et cliquer sur **Renouveler maintenant** au bas de la page.

### Sarah accède à la page de paiement {#sarah-reaches-the-payment-page}

Le site web `We.Finance` dirige Sarah vers la page de paiement. Sarah vérifie à nouveau son numéro de police et la date d’expiration dans ses dossiers. Sur le côté droit de la page, Sarah vérifie le récapitulatif des paiements de son renouvellement avec une réduction premium de 10 % sur le montant total.

#### Fonctionnement {#how-it-works-1}

Le bouton Renouveler maintenant redirige Sarah vers la page de paiement. La page de paiement est un formulaire adaptatif.

#### Démonstration {#see-it-yourself-2}

Cliquez sur **Renouveler maintenant** pour accéder à la page de paiement. Saisissez vos informations de carte de crédit, puis cliquez sur **Effectuer un paiement**.

Vous pouvez accéder à la page de paiement dans une instance de création à l’adresse suivante :

`https://[authorServer]:[authorPort]/content/document.html?documentId=/content/forms/af/we-finance/credit-card/ccbillpayment.html&schema=fdm&customerId=1`

### Sarah effectue le paiement et termine le processus. {#sarah-makes-the-payment-and-completes-the-process}

Sarah remplit ses informations de carte de crédit et clique sur **Effectuer un paiement**.

#### Fonctionnement {#how-it-works-2}

Lorsque Sarah remplit les détails de la carte de crédit et clique sur Envoyer, son paiement par carte de crédit est traité et un message de remerciement configuré dans le formulaire adaptatif s’affiche à l’écran.

#### Démonstration {#see-it-yourself-3}

Vous pouvez afficher le message de confirmation après avoir cliqué sur Effectuer un paiement à l’adresse suivante :

`https://[authorServer]:[authorPort]/content/forms/af/we-finance/credit-card/ccbillpayment/jcr:content/guideContainer.guideThankYouPage.html?owner=admin&status=Submitted`
