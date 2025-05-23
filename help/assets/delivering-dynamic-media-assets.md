---
title: Diffusion de ressources Dynamic Media
description: Découvrez comment diffuser des ressources Dynamic Media, telles que des vidéos et des images, sur vos pages web.
role: User, Admin
feature: Asset Management,Renditions
solution: Experience Manager, Experience Manager Assets
exl-id: b91173b4-f1d1-4aad-97d2-782bc8aeaeab
source-git-commit: 47b82956b41c3f78bed5ae220c7e993ce29e0385
workflow-type: tm+mt
source-wordcount: '313'
ht-degree: 100%

---

# Diffusion de ressources Dynamic Media{#delivering-dynamic-media-assets}

La diffusion des ressources Dynamic Media (vidéos et images) dépend de la mise en œuvre de votre site web.

Avec Dynamic Media, vous disposez de plusieurs options :

* Si votre site web est hébergé sur Adobe Experience Manager, vous souhaiterez ajouter les ressources Dynamic Media directement à votre page.
* Si votre site web n’est pas hébergé par Experience Manager, les possibilités suivantes s’offrent à vous :

   * Incorporation de votre vidéo ou image sur votre site Web.
   * Liez des URL à votre application web. Utilisez la liaison lorsque vous souhaitez présenter un lecteur vidéo dans une fenêtre pop-up ou modale.
   * Si votre site est réactif, vous pouvez [diffuser des images optimisées](/help/assets/responsive-site.md).

>[!NOTE]
>
>L’imagerie dynamique fonctionne avec vos paramètres d’image prédéfinis et utilise des informations à la dernière milliseconde de la diffusion pour réduire davantage encore la taille du fichier d’image en fonction de la vitesse de connexion du réseau et du navigateur. Voir [Imagerie numérique](/help/assets/imaging-faq.md) pour plus d’informations.

Pour plus d’informations, reportez-vous aux rubriques suivantes :

* [Ajout de ressources Dynamic Media aux pages Web](/help/assets/adding-dynamic-media-assets-to-pages.md)
* [Incorporation de la visionneuse de vidéos ou d’images dans une page web](/help/assets/embed-code.md)
* [Activation de la protection de lien dynamique dans Dynamic Media](/help/assets/hotlink-protection.md)
* [Liaison d’URL à votre application Web](/help/assets/linking-urls-to-yourwebapplication.md)
* [Diffusion d’images optimisées pour un site réactif](/help/assets/responsive-site.md)
* [Diffusion de contenu HTTP2](/help/assets/http2.md)
* [Utilisation de jeux de règles de transformation d’URL](/help/assets/using-rulesets-to-transform-urls.md)

## Diffusion de ressources Dynamic Media via HTTP/2 {#http-delivery-of-dynamic-media-assets}

Experience Manager prend à présent en charge la diffusion de tout le contenu Dynamic Media (images et vidéo) sur HTTP/2. En d’autres termes, une URL publiée ou un code intégré pour l’image ou la vidéo peut être intégré à toute application qui accepte une ressource hébergée. Cette ressource publiée est ensuite diffusée au moyen du protocole HTTP/2. Cette méthode de distribution améliore la communication entre les navigateurs et les serveurs, ce qui permet d’améliorer les temps de réponse et de chargement de toutes vos ressources Dynamic Media.

Pour en savoir plus, consultez la [Foire aux questions sur la diffusion HTTP/2 du contenu](/help/sites-administering/scene7-http2faq.md).
