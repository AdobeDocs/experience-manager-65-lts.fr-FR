---
title: Notes de mise à jour actuelles de Adobe Experience Manager 6.5 LTS, SP1
description: Recherchez les informations de mise à jour actuelles pour Adobe Experience Manager 6.5 LTS, Service Pack 1.
solution: Experience Manager
feature: Release Information
role: User,Admin,Architect,Developer
exl-id: b5a8f555-c061-4fe2-a100-cc01335959cb
source-git-commit: 8c726951cbd99660d2cfd23abef8857a6f4fcf36
workflow-type: tm+mt
source-wordcount: '4939'
ht-degree: 31%

---

# Notes de mise à jour actuelles de Adobe Experience Manager 6.5 LTS, SP1 {#release-notes}

## Informations sur la version {#release-information}

| Produit | [!DNL Adobe Experience Manager] 6.5 LTS |
|---|---|
| Version | Service Pack 1 (SP1) <!-- UPDATE FOR EACH NEW RELEASE --> |
| Type | Mise à jour du pack de services |
| Date | 21 août 2025 <!-- UPDATE FOR EACH NEW RELEASE --> |
| URL de téléchargement | [Distribution logicielle](https://artifactory.corp.adobe.com/artifactory/maven-aem-release-local/com/adobe/aem/cq-quickstart/6.6.1/cq-quickstart-6.6.1.jar) |

<!-- UPDATE ABOVE FOR EACH NEW RELEASE -->

## Éléments compris dans [!DNL Adobe Experience Manager] 6.5 LTS, SP1 {#what-is-new}

<!-- UPDATE EACH RELEASE -->

[!DNL Experience Manager] 6.5 LTS, SP1 comprend de nouvelles fonctionnalités, des améliorations importantes demandées par les clients et des correctifs de bugs. Elle comprend également des améliorations des performances, de la stabilité et de la sécurité publiées depuis la disponibilité initiale de 6,5 LTS en mars 2025. [Installez ce pack de services](#install-update) sur 6.5 LTS.

## Principales fonctionnalités et améliorations

<!-- 6.5 LTS REVIEWERS: WHAT ARE THE KEY FEATURES AND ENHANCEMENTS THAT YOU WANT TO HIGHLIGHT IN THIS RELEASE? -->

<!-- UPDATE EACH RELEASE -->

## Correction de problèmes dans 6.5 LTS, Service Pack 1 {#fixed-issues}

<!-- UPDATE BELOW FOR EACH NEW RELEASE -->

### [!DNL Sites]{#sites-65-LTS-SP1}

#### Accessibilité {#sites-accessibility-65-lts-sp1}

* Correction d’un problème où l’élément d’éditeur de texte dans les fragments de contenu était tronqué par défaut. L’éditeur de texte affiche désormais le contenu complet sans troncature. (SITES-33005)
* Correction d’un problème en raison duquel les chemins d’URL des clics ouvraient la page d’accueil d’Indigo au lieu de l’URL de destination appropriée. (SITES-33004)
* Correction d’un problème d’accessibilité dans un composant AEM personnalisé qui provoquait des échecs de conformité ADA lors des tests automatisés. (SITES-30660)
* Correction de problèmes de conformité ADA dans la boîte de dialogue d’alerte et les messages de workflow en veillant à ce que le texte s’affiche en noir sur les fonds clairs et respecte les exigences de contraste de la norme WCAG 2.0. (SITES-30138)
* Correction d’un problème d’accessibilité en raison duquel le bouton « Catégorie » de l’éditeur d’AEM Sites ne comportait pas de libellé spécifique, ce qui entraînait l’annonce par JAWS de l’utilisation du « menu du bouton Images » au lieu de fournir un libellé descriptif. (SITES-27497)
* Correction d’un problème d’accessibilité en raison duquel les icônes de coche dans l’écran Autorisations effectives ne contenaient pas de texte secondaire, empêchant JAWS de lire et de transmettre leur signification. (SITES-27272)
* Correction d’un problème d’accessibilité en raison duquel la page Autorisations ne fournissait pas d’annonce JAWS claire pour la suppression des autorisations d’utilisateur ou de groupe, ce qui entraînait une confusion pour les utilisateurs de lecteurs d’écran. (SITES-27238)
* Correction d’un problème d’accessibilité en raison duquel les messages d’erreur s’affichaient uniquement sous forme d’icônes sans texte descriptif, empêchant JAWS d’annoncer les erreurs lorsqu’elles se produisaient. (SITES-27155)
* Correction d’un problème d’accessibilité en raison duquel JAWS lisait des descriptions de bouton incorrectes et imprécises dans l’environnement On-Premise AEM, y compris le texte de niveau d’en-tête 2 manquant pour la section Modules . (SITES-27152)
* Correction d’un problème d’accessibilité en raison duquel JAWS n’annonçait pas le nombre de résultats après le filtrage des valeurs dans l’onglet AEM Assets . (SITES-27150)
* Correction d’un problème d’accessibilité en raison duquel la création d’un dossier n’affichait pas de confirmation et JAWS ne l’annonçait pas dans l’interface utilisateur d’Assets. (SITES-27141)
* Correction d’un problème d’accessibilité dans AEM Sites. JAWS n’a pas annoncé d’erreurs de formulaire, le focus a été déplacé vers des éléments d’erreur non interactifs et les erreurs de champ obligatoire n’ont pas été affichées dans l’onglet. (SITES-27138)
* Correction d’un problème d’accessibilité en raison duquel le menu du bouton Chronologies ne comportait pas de libellé spécifique, ce qui entraînait la lecture seule de « menu du bouton Activités » par JAWS sans fournir de description claire. (SITES-27134)
* Correction d’un problème d’accessibilité en raison duquel JAWS n’annonçait pas l’action ou le rôle pour les éléments de conteneur, lisant uniquement « Chemin de navigation v1 » et « Bouton v2 » au lieu de libellés descriptifs. (SITES-27131)
* Correction d’un problème d’accessibilité en raison duquel le pop-up de publication rapide ne fournissait pas un message de réussite correct, empêchant les lecteurs d’écran d’annoncer les commentaires d’achèvement. (SITES-26912)
* Correction d’un problème d’accessibilité dans la vue Colonne corail, en raison duquel les éléments disposant de rôles ARIA nécessitant des rôles enfants ne les contenaient pas, ce qui entraînait une non-conformité aux normes d’accessibilité. (SITES-26898)
* Correction d’un problème d’accessibilité en raison duquel les textes « modèle » et « propriétés » dans le volet de navigation supérieur de la page de création n’étaient pas visibles en mode Reflux, ce qui empêchait l’accès pour les utilisateurs et utilisatrices d’un clavier ou d’un lecteur d’écran. (SITES-26895)
* Correction d’un problème d’accessibilité en raison duquel les infobulles des icônes « recherche », « solution », « aide », « boîte de réception » et « utilisateur » de la barre de navigation supérieure n’étaient pas accessibles via la navigation au clavier. (SITES-26889)
* Correction d’un problème d’accessibilité en raison duquel les champs de formulaire d’onglet de base ne fournissaient pas de suggestions d’erreur, empêchant les utilisateurs de recevoir des conseils lorsque les champs de saisie obligatoires étaient laissés vides. (SITES-26885)
* Correction d’un problème d’accessibilité en raison duquel les lecteurs d’écran NVDA et Narrateur n’annonçaient pas les détails du fichier de modèle dans la page Créer , empêchant les utilisateurs de recevoir des informations complètes par programmation. (SITES-26884)
* Correction d’un problème d’accessibilité qui utilisait un nom incorrect pour la « Zone de texte Titre de la page » dans l’onglet De base, empêchant les lecteurs d’écran de fournir des informations précises aux utilisateurs. (SITES-26879)
* Mise à jour des couleurs de premier plan et d’arrière-plan des boutons pour répondre aux exigences de rapport de contraste minimal de WCAG 2.2 AA, améliorant la lisibilité et l’accessibilité pour tous les utilisateurs. (SITES-26877)
* Correction d’un problème en raison duquel les textes « modèle » et « propriétés » dans le volet de navigation supérieur de la page de création disparaissaient après le redimensionnement, garantissant ainsi la visibilité et l’accessibilité pour les utilisateurs et utilisatrices peu voyants. (SITES-26872)
* Correction d’un problème en raison duquel plusieurs barres de défilement horizontales s’affichaient sur la page principale après l’application d’une redistribution, garantissant ainsi l’affichage d’une seule barre de défilement pour une accessibilité et une visibilité correctes du contenu. (SITES-26800)
* Correction d’un problème d’accessibilité dans l’éditeur de page d’AEM en raison duquel le focus au clavier se réinitialisait de manière inattendue au début de la barre d’outils démographique après l’activation de boutons tels que persona, panier ou abandonné. Le focus reste désormais sur le bouton activé pour prendre en charge les workflows cohérents de navigation au clavier et de lecteur d’écran. (SITES-25306)
* Correction d’un problème d’association des libellés d’accessibilité pour les champs de titre de page et de balises. L’interface AEM associe désormais correctement les libellés d’accessibilité aux champs « Titre » et « Titre de la page » lors de l’utilisation de lecteurs d’écran tels que JAWS. Le correctif garantit une lecture correcte des libellés et améliore la conformité ADA sur la création de pages, les propriétés et les workflows de déplacement. (SITES-27149)
* Correction d’un libellé visuel manquant pour les champs de saisie de commentaire dans la chronologie. Correction des libellés visuels manquants pour les champs d’entrée « Commentaire » sous la section chronologie afin d’améliorer l’accessibilité. La mise à jour garantit que les lecteurs d’écran peuvent annoncer avec précision les libellés des champs. Cette expérience améliore la navigation et l’envoi de formulaires pour les utilisateurs et utilisatrices, en particulier les personnes qui dépendent des technologies d’assistance. (SITES-26903)
* Correction de l’accessibilité du clavier pour le bouton représentant des points de suspension dans les commentaires de la chronologie. Activation de la navigation au clavier pour le bouton représentant des points de suspension en regard des commentaires sous la section Chronologie. Les utilisateurs et utilisatrices peuvent désormais interagir avec le bouton à l’aide de la touche de tabulation, ce qui améliore l’accessibilité pour les utilisateurs et utilisatrices qui nécessitent une navigation au clavier uniquement. (SITES-26891)
* Amélioration des annonces NVDA/Narrator pour les résultats de recherche dans les boîtes de dialogue de sélection. Mise à jour de la boîte de dialogue Ouvrir la sélection pour indiquer si des résultats de recherche sont trouvés ou non lors de l’utilisation de lecteurs d’écran, tels que NVDA ou Narrator. Cette amélioration aide les utilisateurs et utilisatrices qui utilisent des technologies d’assistance à comprendre le résultat de leurs actions de recherche sans confirmation visuelle. (SITES-26883)
* Correction du rôle ARIA pour l’icône représentant des points de suspension en regard du champ de saisie de commentaire. Mise à jour de l’icône représentant des points de suspension à côté du champ de saisie de commentaire pour utiliser le rôle ARIA approprié, afin que les lecteurs d’écran puissent identifier précisément l’élément. Cela permet d’améliorer la conformité en matière d’accessibilité et l’expérience des utilisateurs et utilisatrices qui dépendent des technologies d’assistance. (SITES-26881)
* Correction d’attributs ARIA non valides dans les composants de l’interface d’utilisation Coral. Mise à jour des composants de l’interface d’utilisation Coral pour garantir que tous les attributs ARIA utilisent des valeurs valides, améliorant ainsi la conformité en matière d’accessibilité. En particulier, des cas ont été traités où des valeurs non valides telles que `aria-modal="dialog"` ont été attribuées de manière incorrecte. Cette amélioration permet aux lecteurs d’écran d’interpréter correctement les éléments de boîte de dialogue, ce qui améliore l’accessibilité pour les utilisateurs et utilisatrices qui dépendent des technologies d’assistance. (SITES-26873)
* Amélioration de la visibilité et des infobulles des icônes dans les scénarios Reflow. Optimisation du comportement Reflow pour garantir l’affichage correct des infobulles des icônes **Télécharger**, **Retraiter les ressources** et **Extraire**. Mise en évidence d’un problème d’accessibilité en raison duquel les icônes et leurs libellés devenaient invisibles lorsque la fenêtre était redimensionnée ou que les paramètres de zoom du navigateur étaient modifiés. Cette correction améliore l’accessibilité pour les personnes ayant une mauvaise vue, en maintenant la visibilité et en fournissant des descriptions appropriées des icônes en mode Reflow. (SITES-26871)


#### Interface d’utilisation d’administration{#sites-adminui-65-lts-sp1}

* Correction d’un problème d’accessibilité en raison duquel JAWS n’annonçait pas les rôles de liste ou ne fournissait pas d’instructions de navigation et d’activation dans la boîte de dialogue Créer un site. (SITES-30661)
* La prise en charge des lecteurs d’écran pour les messages de statut dans la vue de filtrage Sites fonctionne comme prévu, en s’assurant que les utilisateurs reçoivent des commentaires clairs et opportuns lors du changement d’affichage. (SITES-24992)
* Le sélecteur de date du rail Filtres s’affiche entièrement dans son conteneur, fournissant une taille cible tactile adéquate et éliminant les problèmes d’écrêtage. (SITES-24988)
* Les balises de filtrage sélectionnées utilisent désormais des libellés sémantiques HTML et ARIA qui correspondent à la présentation visuelle, ce qui garantit une prise en charge précise des rôles et des actions claires pour les technologies d’assistance. (SITES-24980)
* Ajout d’un attribut aria-label à la région Rail de références pour fournir un libellé descriptif unique aux utilisateurs de lecteurs d’écran et assurer une identification cohérente des repères sur la page. (SITES-24973)
* Mise à jour du rail Références afin d’utiliser des unités relatives pour le dimensionnement et le positionnement, ce qui permet au contenu de se mettre à l’échelle et de rester entièrement fonctionnel lorsqu’il est zoomé à 400 % dans une fenêtre d’affichage de 1 280 x 1 024. (SITES-24972)
* Les éléments de tableau confirmés dans la vue Liste de la page d’accueil Sites contiennent les rôles d’en-tête de colonne appropriés, ce qui permet aux lecteurs d’écran d’annoncer les en-têtes pour chaque cellule de données. (SITES-24942)
* NVDA annonce désormais la date de modification dans l’annuaire des arborescences, ce qui garantit que les utilisateurs de lecteurs d’écran reçoivent des informations détaillées complètes sur les ressources. (SITES-24782)
* Correction d’un problème en raison duquel le lecteur d’écran NVDA annonçait du texte incomplet pour les éléments du composant Répertoire d’arborescence dans AEM Sites. Le NVDA lit désormais le texte intégral de chaque élément, ce qui améliore l’accessibilité et la conformité. (SITES-24780)
* Ajout de l’accessibilité clavier au séparateur de fenêtre dans l’annuaire des arborescences, ce qui permet aux utilisateurs de redimensionner la barre latérale gauche à l’aide d’un seul clavier. (SITES-24779)
* Mise à jour des résultats de recherche du menu Aide afin d’inclure des rôles ARIA corrects pour les éléments de liste, en veillant à ce que les lecteurs d’écran annoncent correctement les liens pour une meilleure accessibilité. (SITES-24729)
* Correction d’un problème en raison duquel les lecteurs d’écran n’annonçaient pas le message de statut « X sur Y résultats ». Vous pouvez également ajouter le message « aucun résultat trouvé » après l’application des filtres dans le panneau Filtre de sites, en veillant à ce que les utilisateurs reçoivent une confirmation correcte des résultats. (SITES-24720)
* Correction des affectations de rôle manquantes pour les liens de navigation dans la navigation de l’application. Ajout de rôles ARIA appropriés pour s’assurer que les lecteurs d’écran identifient et annoncent correctement les éléments de navigation. (SITES-24719)
* Remplacement du balisage de rôle de grille incorrect pour les balises de filtrage sélectionnées par des éléments de bouton et ajout de noms accessibles, afin que les lecteurs d’écran annoncent et identifient correctement les balises. (SITES-24717)
* Ajout d’annonces de lecteur d’écran pour le message de statut du rail Références lors de sélections multiples, garantissant que les utilisateurs reçoivent une confirmation des modifications. (SITES-24678)
* Correction du comportement des champs de recherche afin que le premier résultat ne soit pas automatiquement annoncé. Les lecteurs d’écran annoncent maintenant le nombre de résultats trouvés, ce qui permet aux utilisateurs et aux utilisatrices de parcourir la liste sans annonces de focus incorrectes. (SITES-24658)
* Suppression des attributs de `aria-label` incorrects des éléments statiques non interactifs dans la vue Liste pour empêcher les lecteurs d’écran d’annoncer des informations trompeuses ou non pertinentes. (SITES-24515)
* Mise à jour de la case à cocher dans la première colonne de la vue Liste afin d’utiliser le texte de la colonne Titre pour son nom accessible, en veillant à ce que les lecteurs d’écran transmettent précisément l’objectif du champ de formulaire. (SITES-24514)
* Ajout des attributs ARIA appropriés et de la prise en charge des régions actives pour annoncer les messages d’état de chargement aux utilisateurs de lecteurs d’écran lors de la navigation dans le contenu. (SITES-24481)
* Mise à jour de la conception réactive pour éliminer le défilement horizontal lorsque le contenu fait l’objet d’un zoom de 400 % avec une largeur de fenêtre d’affichage de 1 280 × 1 024, afin d’assurer une visibilité complète sans défilement latéral. (SITES-24308)
* Correction de la navigation du focus dans l’interface utilisateur d’administration de Sites afin de suivre un ordre logique, en revenant au bouton « Tout sélectionner » après avoir appuyé sur Échap et en déplaçant le focus vers l’élément interactif suivant après avoir appuyé sur la touche de tabulation. (SITES-24307)
* Mise à jour de l’ordre de focus dans l’interface utilisateur d’administration de Sites afin que le bouton de chemin de navigation dans l’élément `<betty-titlebar-title>` reçoive le focus dans la bonne séquence lors de la navigation au clavier. (SITES-24305)
* Vérification de la fonctionnalité de saut de lien pour s’assurer que déplace le focus du clavier vers la zone de contenu principale, ce qui permet aux utilisateurs du clavier de contourner les éléments d’en-tête et d’accéder efficacement au contenu. (SITES-24061)


#### Interface d’utilisation classique{#sites-classicui-65-lts-sp1}

Correction d’un problème dans l’interface utilisateur classique en raison duquel les libellés de case à cocher manquaient et HTML s’affichait en tant que texte codé dans plusieurs éléments de l’interface utilisateur, y compris la recherche de date et les interfaces non standard. (SITES-31822)

#### [!DNL Content Fragments]{#sites-contentfragments-65-lts-sp1}

AEM empêche désormais la dégradation des performances causée par des métadonnées XMP incorrectes dans les ressources d’image. Les ressources qui contiennent des noms de propriété XMP non valides ou non conformes, comme ceux avec des segments numériques ou des structures non qualifiées, ne déclenchent plus de journaux d’avertissement répétés pendant le traitement. Le système filtre les métadonnées problématiques afin de garantir que l’ingestion et la validation des ressources s’effectuent sans erreur. (SITES-30683)

<!--
#### [!DNL Content Fragments] - Admin{#sites-admin-65-lts-sp1} -->

#### [!DNL Content Fragments] - Éditeur de fragments{#sites-fragments-editor-65-lts-sp1}

Les autres personnes chargées de la création peuvent continuer à publier des fragments de contenu même lorsqu’une autre personne les extrait, ce qui est contraire au comportement prévu de la fonctionnalité d’extraction. Ce correctif empêche les autres utilisateurs et utilisatrices de voir ou d’utiliser les boutons Publier dans l’interface de création lorsqu’un fragment de contenu est verrouillé. (SITES-30578)

<!--
#### [!DNL Content Fragments] - GraphQL API {#sites-graphql-api-65-lts-sp1}

#### [!DNL Content Fragments] - GraphQL Query Editor{#sites-graphql-query-editor-65-lts-sp1}

#### [!DNL Content Fragments] - REST API{#sites-restapi-65-lts-sp1} -->

#### Console des composants{#sites-component-console-65-lts-sp1}

Correction d’un problème dans le composant Liste de produits en raison duquel la case à cocher « Tout sélectionner » ajoutait uniquement les 20 premiers SKU de la page initiale au lieu de tous les SKU dans les résultats de la recherche. (SITES-29191)

#### Back-end principal{#sites-core-backend-65-lts-sp1}

Des métadonnées XMP mal formatées déclenchaient une erreur lors du traitement des ressources d’image dans le `ValidationDataServlet`. Le correctif garantit la conformité de la gestion des métadonnées et évite l’analyse redondante de propriétés non valides. (SITE-30683)

<!--
#### Core Components{#sites-core-components-65-lts-sp1}

#### Campaign integration{#sites-campaign-integration-65-lts-sp1}

#### Experience Fragments{#sites-experiencefragments-65-lts-sp1}

#### Foundation Components (Legacy){#sites-foundation-components-legacy-65-lts-sp1}

#### Launches{#sites-launches-65-lts-sp1}

#### Link Checker{#sites-link-checker-65-lts-sp1} -->

#### MSM - Live Copies{#sites-msm-live-copies-65-lts-sp1}

* Correction d’un `ns.ui.alert is not a function` d’erreur JavaScript qui se produisait lors de la réactivation de l’héritage des composants fantômes dans AEM 6.5 On-prem. (SITES-31993)
* Correction d’un problème en raison duquel l’option Déployer « ultérieurement » permettait de continuer sans sélectionner de date dans AEM 6.5. (SITES-31374)

#### Éditeur de page{#sites-pageeditor-65-lts-sp1}

* Correction d’un problème dans la boîte de dialogue modale du teaser où l’onglet Lien et actions continuait à afficher le style d’erreur, les icônes et l’attribut aria-invalid après une entrée de données valide et une résolution d’erreur. (SITES-25527)
* Correction d’un problème dans l’éditeur de texte modal du teaser, en raison duquel les boutons Listes et Paragraphes ne transmettaient pas leur état développé ou réduit aux lecteurs d’écran, assurant ainsi des mises à jour d’attributs précises avec une extension ARIA. (SITES-25365)
* Correction d’un problème dans la barre d’outils démographique en raison duquel le réglage du curseur du panier avec l’entrée clavier déplaçait le focus vers le bouton Panier au lieu de conserver le focus sur le curseur, améliorant ainsi l’efficacité de la navigation pour les utilisateurs d’un clavier. (SITES-25324)
* Ajout d’un nom accessible au curseur de panier dans la barre d’outils des démographies en attribuant une valeur à son élément de `<label>` associé. Ce correctif a amélioré la compatibilité avec les technologies d’assistance et amélioré la convivialité pour les utilisateurs et utilisatrices de lecteurs d’écran. (SITES-25322)
* Ajout de rôles ARIA et de noms accessibles aux boutons dans la liste déroulante de la barre d’outils Démographie . Ce correctif a permis une identification correcte par les technologies d’assistance et une navigation améliorée pour les utilisateurs utilisant un clavier ou un lecteur d’écran. (SITES-25315)
* Réglage de la disposition de la barre d’outils démographique pour éviter le débordement du contenu au-delà de la fenêtre d’affichage avec un zoom de 200 % du navigateur, en veillant à ce que tous les contrôles restent accessibles sans défilement horizontal. (SITES-25309)
* Correction de la gestion de la sélection dans la barre d’outils démographique afin de conserver la sélection au clavier sur le bouton activé au lieu de réinitialiser le focus sur la position de départ de la barre d’outils. (SITES-25306)
* Le chevauchement des libellés du bouton fonctionne comme prévu, à l’aide d’une info-bulle pour afficher le libellé lorsque des modes avec des largeurs d’écran similaires sont actifs. (SITES-25285)
* La boîte de dialogue modale d’annotation comprend un bouton d’envoi visible qui permet aux utilisateurs et utilisatrices d’envoyer des annotations sans avoir à appuyer sur la touche Échap ni cliquer en dehors de la boîte de dialogue modale. (SITES-25281)
* La boîte de dialogue modale d’annotation comprend un bouton représentant une icône en forme de stylo qui permet aux utilisateurs d’envoyer des annotations, fournissant ainsi une méthode d’envoi claire et accessible. (SITES-25269)
* Correction des annonces du lecteur d’écran pour les boutons Annoter et Fermer l’annotation afin de fournir des commentaires précis et pertinents et de supprimer les informations sans rapport ou déroutantes. (SITES-25268)
* Les sections Zone de travail des pages de l’éditeur AEM prennent désormais en charge l’accessibilité clavier complète. Les utilisateurs et les utilisatrices peuvent activer les titres de section et modifier les boutons à l’aide du clavier uniquement, sans avoir à pointer avec la souris. Cette mise à jour garantit la conformité avec la norme WCAG 2.1.1 et améliore l’accessibilité et l’ergonomie des différents composants (comme les modèles Teaser, Image, Carrousel, Disposition, Distorsion du temps et Annotation). (SITES-25256)
* Suppression du défilement horizontal inutile dans la fenêtre modale du carrousel à 320 px de largeur pour garantir l’affichage de tout le contenu dans la fenêtre d’affichage sans nécessiter de navigation côte à côte. (SITES-25254)
* Suppression du défilement horizontal inutile dans la fenêtre modale d’image à 320 px de largeur pour garantir l’affichage de tout le contenu dans la fenêtre d’affichage sans nécessiter de navigation côte à côte. (SITES-25244)
* Suppression du défilement horizontal inutile dans la boîte de dialogue modale du teaser à 320 px de largeur pour garantir l’affichage de tout le contenu dans la fenêtre d’affichage sans nécessiter de navigation côte à côte. (SITES-25242)
* Activation de la navigation au clavier pour le `List` et `Paragraph Format` menu pop-up, tous deux dans la boîte de dialogue modale du teaser. Ce correctif permet aux utilisateurs d’accéder à ces menus et de les parcourir à l’aide des touches fléchées. (SITES-25235)
* Correction des annonces du lecteur d’écran pour les boutons Annoter et Fermer l’annotation afin de fournir des commentaires précis et pertinents en accord avec les actions associées. (SITES-25234)
* Amélioration du libellé du bouton Aide dans la boîte de dialogue modale du teaser afin de décrire clairement son objectif et de fournir un contexte significatif à tous les utilisateurs et utilisatrices, y compris les utilisateurs et utilisatrices de technologies d’assistance. (SITES-25224)
* Amélioration de la règle d’émulateur pour les utilisateurs de lecteurs d’écran en associant les mesures de règle à leurs appareils respectifs. Remplacez également l’info-bulle par un élément aria-descripbedby . (SITES-24955)
* Aucun correctif n’a été implémenté, car le bouton Modifier fonctionne comme prévu et fournit un contexte informatif plutôt que d’exécuter une action. (SITES-24950)
* L’ordre de focus confirmé sur la page de l’éditeur suit une séquence logique, ce qui permet aux utilisateurs et aux utilisatrices de parcourir tous les éléments interactifs sans passer ou revenir en arrière de manière inattendue. (SITES-24937)
* La zone de travail Mode d’aperçu confirmé met correctement à jour l’espacement du texte lorsque les utilisateurs appliquent des paramètres d’espacement personnalisés, assurant ainsi une mise en forme cohérente dans toutes les zones de contenu. (SITES-24936)
* Le bouton Aperçu vérifié ne déclenche plus de changements de contexte ou d’état, ce qui garantit que les utilisateurs activent délibérément le bouton avant la mise à jour des pages vues. (SITES-24784)
* Ajout d’affectations correctes de rôles ARIA aux liens de navigation de l’application, permettant aux lecteurs d’écran d’identifier et d’annoncer précisément les éléments de navigation pour une meilleure accessibilité. (SITES-24718)
* Mise à jour du bouton Modifier les filtres pour annoncer les états développés et réduits aux lecteurs d’écran, suppression des attributs ARIA redondants et ajustement de l’étiquetage afin de fournir des descriptions claires et non dupliquées. (SITES-24713)
* Ajout d’annonces de lecteurs d’écran pour les messages de statut des résultats de recherche dans la boîte de dialogue Sélection de lien , afin de garantir que les utilisateurs reçoivent une confirmation lorsque les résultats se chargent ou qu’aucune correspondance n’est trouvée. (SITES-24700)
* Ajout d’annonces de lecteur d’écran pour l’état de chargement de la boîte de dialogue modale d’image, afin que les utilisateurs reçoivent des commentaires lorsque la boîte de dialogue modale est en cours de chargement et prête pour l’interaction. (SITES-24697)
* Correction d’un problème d’accessibilité en raison duquel l’en-tête collant masquait le contenu modal du teaser avec un zoom de 200 % et de 400 %, assurant ainsi une visibilité et une convivialité complètes lors de l’utilisation du zoom de la page. (SITES-24523)
* Ajout d’un message de statut indiquant le nombre de résultats de la recherche dans le champ Rechercher/Filtrer, ce qui permet aux lecteurs d’écran d’annoncer les résultats aux utilisateurs. (SITES-24506)
* Ajout d’annonces relatives au lecteur d’écran pour le nombre de résultats de recherche dans le champ Rechercher/Filtrer , afin que les utilisateurs reçoivent immédiatement un retour d’informations lors du chargement des résultats. (SITES-24505)
* Ajout d’un nom accessible à la liste d’onglets du panneau Rail latéral, ce qui permet aux lecteurs d’écran d’annoncer son objectif conformément aux directives WAI-ARIA. (SITES-24492)
* Ajout de libellés descriptifs aux icônes d’éditeur ambiguës, afin de s’assurer que tous les utilisateurs comprennent clairement la fonction de chaque bouton. (SITES-24480)
* Activation de l’accessibilité complète du clavier pour les titres de section et les boutons d’action dans la vue Zone de travail, assurant un fonctionnement cohérent pour les utilisateurs utilisant la souris et le clavier. (SITES-24479)

<!--
#### Replication{#sites-replication-65-lts-sp1}

#### Rich Text Editor{#sites-rte-65-lts-sp1} -->

#### Éditeur universel {#sites-universal-editor-65-lts-sp1}

* Correction d’une condition de concurrence dans QueryTokenService qui provoquait des connexions incorrectes lorsque plusieurs requêtes avec des paramètres de requête déclenchées avant que le service de jeton de connexion ne renvoie un résultat. (SITES-30659)
* Correction d’un problème dans UniversalEditorURLService en raison duquel l’enregistrement d’un tableau de chemins mappés dans Felix ConfigMgr conservait uniquement le premier élément. (SITES-30292)

### [!DNL Assets]{#assets-65-lts-sp1}

Correction d’un problème en raison duquel la synchronisation des ressources du DAM distant avec l’AEM locale de Sites supprimait le statut publié et les propriétés liées à la réplication des ressources. (Assets-48958)

<!--
#### [!DNL Dynamic Media]{#assets-dm-65-lts-sp1}

#### [!DNL Dynamic Media] - Hybrid Mode {#assets-dm-hybrid-65-lts-sp1}



### [!DNL Forms]{#forms-65-lts-sp1}


#### Forms Designer 

#### Forms

#### Forms JEE 
 
#### Forms Captcha {#forms-captcha-65-lts-sp1} 

#### XMLFM {#forms-xmlfm-65-lts-sp1}

#### [!DNL Adaptive Forms] {#adaptive-forms-65-lts-sp1}

#### [!DNL Forms Designer] {#forms-designer-65-lts-sp1} -->



### Foundation {#foundation-65-lts-sp1}

<!--
#### Apache Felix {#foundation-apachefelix-65-lts-sp1}

#### Campaign{#foundation-campaign-65-lts-sp1}

#### Cloud Services{#foundation-cloudservices-65-lts-sp1}



#### Communities {#foundation-communities-65-lts-sp1}

#### Content distribution{#foundation-content-distribution-65-lts-sp1}

#### CRX {#foundation-crx-65-lts-sp1}

#### Granite{#foundation-granite-65-lts-sp1} -->

#### HTL{#foundatoin-htl-5-lts-sp1}

Résolution des cycles de dépendance OSGi qui empêchaient le fonctionnement de la fabrique de moteurs de script HTL, assurant une résolution de service et une exécution de script correctes. (Granite-58275)

#### Intégrations{#foundation-integrations-65-lts-sp1}

* Suppression de l’utilisation de commons-httpclient 3.x du lot `com.adobe.cq.cq-analytics-integration` et remplacement par `org.apache.httpcomponents.httpclient` 4.5.13.B0001 pour s’aligner sur les dernières normes LTS d’AEM 6.5. (CQ-4360586)
* Suppression de l’offre groupée d’intégration obsolète Search&amp;Promote d’AEM afin d’éliminer les composants inutilisés et de réduire les frais de maintenance. (CQ-4358030)
* Ajout de nouveaux cas de test principaux pour l’intégration de SiteCatalyst afin d’améliorer la validation des analyses et d’assurer une couverture plus complète. (CQ-4359991)
* Correction d’un problème dans la section Propriétés de la configuration de Launch où les listes déroulantes Société et Propriété n’apparaissaient pas. En outre, les commandes Enregistrer et Fermer ont déclenché des erreurs malgré le remplissage de tous les champs obligatoires et l’affichage de messages d’erreur incorrects pour Société et Propriété lorsque seul le champ Titre était vide. (CQ-4359853)
* Suppression de l’entrée de chemin de servlet `searchpromote` de la version 6.6 pour s’aligner sur la suppression du lot Search&amp;Promote. (CQ-4359523)
* Correction de cas de test HTTP pour le référentiel Target afin de garantir une validation précise et une fiabilité de test améliorée. (CQ-4359022)
* Suppression de l’utilisation de la mise en cache Guava du module integration-adobeims-console pour éliminer les dépendances de la bibliothèque Guava. (CQ-4358710)
* Workflows d’intégration de la gestion dynamique des balises, tâches de boîte de réception et fonctionnalités de projet validés dans AEM 6.6 pour garantir le bon fonctionnement dans AEM 6.5. (CQ-4358151)
* Validation de la fonctionnalité Content Insight dans AEM 6.6 pour garantir la compatibilité et le bon fonctionnement dans AEM 6.5. (CQ-4357774)
* La fonctionnalité Services cloud validée dans AEM 6.6 permet d’assurer la compatibilité et le bon fonctionnement dans AEM 6.5. (CQ-4357773)
* Validation de l’intégration de la console Adobe IMS dans AEM 6.6 pour garantir la compatibilité et le bon fonctionnement dans AEM 6.5. (CQ-4357772)
* Mise à jour du pipeline Jenkins pour que l’intégration Test&amp;Target s’exécute sur Java 17, résout les tests Selenium qui échouent, déplace certains tests vers Playwright et s’assure que tous les tests unitaires réussissent. (CQ-4357770)
* Intégrations DX, workflow, boîte de réception et projets alignés avec la branche 6.6.0 en mettant à jour les pipelines de création et de test. Résolvez également les problèmes de compatibilité de mise à niveau et validez tous les services concernés pour en optimiser la stabilité et les fonctionnalités. (CQ-4357767)

<!--
#### Jetty{#foundation-jetty-65-lts-sp1} -->

#### Localisation{#foundation-localization-65-lts-sp1}

* Localisation des chaînes dans la boîte de dialogue « Supprimer le contrôle d’accès » de la liste « Autorisations » pour afficher les traductions correctes. (GRANITE-59427)
* Correction d’un problème dans la boîte de dialogue Ajouter une règle « Ou Fractionner les propriétés » de l’éditeur de modèles en raison duquel plusieurs chaînes d’interface utilisateur, y compris les opérateurs et les libellés de champ, semblaient non localisées. Toutes les chaînes s’affichent désormais avec une localisation correcte. (CQ-4354014)
* Ajout de la traduction manquante pour l’info-bulle « Afficher la description de » dans la boîte de dialogue Modifier les modèles de workflow. (CQ-4347996)

#### Oak {#foundation-oak-65-lts-sp1}

Correction d’un problème en raison duquel AEM recréait ou renommait les fichiers de configuration existants sous `/apps/system/config` lors des mises à niveau, en remplaçant les fichiers `.cfg.json` par des fichiers `.config`. (GRANITE-58899)

#### Omnisearch{#foundation-omnisearch-65-lts-sp1}

Correction d’un problème d’accessibilité en raison duquel les espaces réservés s’affichaient incorrectement comme libellés pour les champs de saisie. Ce problème entraîne l’absence de libellés de champ dans la recherche, les fragments d’expérience AEM, les fragments de contenu et les modèles de fragment de contenu. (Granite-61791)

<!--
#### Platform{#foundation-platform-65-lts-sp1} -->

#### Projets{#foundation-projects-65-lts-sp1}

* Correction d’un problème qui affichait un pop-up d’erreur incorrect lors de la suppression d’un projet en mode Calendrier, malgré la suppression réussie du projet. (CQ-4358890)
* Correction d’un problème dans Firefox en raison duquel le pied de page de carte « Collecte de ressources » dans la vue Projet chevauchait la bordure de la carte. Le pied de page s’aligne désormais correctement sans chevauchement. (CQ-4353317)

#### Démarrage rapide{#foundation-quickstart-65-lts-sp1}

* Placer sur la liste bloquée Mise à jour du script de désinstallation afin d’ajuster la plage de versions du lot Guava, ce qui empêche son arrêt lors de l’installation via le gestionnaire de packages. (GRANITE-59559)
* Correction d’une erreur de configuration en plusieurs parties qui se produisait lors des chargements de packages AEMFD sur Tomcat 11 avec JDK 17 en mettant à jour la configuration du serveur pour prendre en charge les installations de packages volumineux sans déclencher d’échecs d’analyse. (GRANITE-58327)
* Correction d’un problème dans l’interface utilisateur de réplication qui affichait une erreur (`#1660`) lors de la modification des agents de réplication en corrigeant la gestion des cases à cocher classiques dans l’interface. (GRANITE-58302)
* Correction de plusieurs erreurs de démarrage du magasin de données S3 lors de l’exécution d’AEM 6.5 LTS avec JDK 21 en résolvant les problèmes d’autorisations de service manquantes, en mettant à jour la gestion de la configuration et en s’assurant que les services requis s’initialisent correctement. (GRANITE-57082)
* Définition de la stratégie de maintenance et de maintenance pour AEM 6.5. Ce correctif incluait les éléments suivants :
   * Cadence du pack de services.
   * Cadence du correctif.
   * Prise en charge parallèle d’AEM 6.6.
   * Mise à jour de la matrice de prise en charge.
   * Responsabilités de propriété du module complémentaire. (GRANITE-50459)

<!--
#### Security{#foundation-security-65-lts-sp1} -->

#### Sling{#foundation-sling-65-lts-sp1}

* Mise à jour de Sling ResourceAccessSecurity vers la version 1.1.2 pour résoudre un `ClassCastException` qui se produisait lorsque plusieurs références `ResourceAccessGate` étaient initialisées `ResourceAccessSecurityImpl`. (NPR-42750)
* Correction d’un problème dans l’intégration d’Adobe Stock en raison duquel la boîte de dialogue Licence était grisée. Ce problème était dû à la suppression des champs d’entrée obligatoires par la fonction `sunt:initList`. La fonction a été trouvée dans les bibliothèques clientes Coral Foundation. Mise à jour des bibliothèques clientes pour conserver les champs nécessaires et activer la fonctionnalité de boîte de dialogue de licence appropriée. (NPR-42748)
* Rétroportage du correctif pour le problème de script Sling qui provoquait des exceptions de pointeurs nuls `DataTimeParseException` et `String.length()` lors de l’installation du package. Mise à jour de Sling Scripting vers la version 2.8.3-1.0.10.6 afin de réduire les erreurs d’installation et d’améliorer la stabilité. (NPR-42640)

<!--
#### Translation{#foundation-translation-65-lts-sp1} -->

#### Interface d’utilisation{#foundation-ui-65-lts-sp1}

* Résolution d’un problème dans l’interface utilisateur de création d’AEM qui limitait l’affichage des groupes d’utilisateurs à 41. Ce problème était dû à une limite de lots par défaut dans le composant Sélecteur de groupe de l’IU Granite. Mise à jour du composant pour afficher tous les groupes sans troncature. (NPR-42749)
* Correction d’un problème dans l’assistant de création de page On-prem en raison duquel les champs obligatoires dans les composants multichamps n’étaient pas revalidés lors de la modification des propriétés de la page. Ce problème permettait aux auteurs de contourner la validation et de traiter des données incomplètes. (GRANITE-58826)
* Correction des attributs ARIA pour le bouton d’aide d’AEM afin de s’assurer que les lecteurs d’écran JAWS annoncent un libellé clair et convivial au lieu d’afficher des métadonnées de texte et d’icône non traduites. (GRANITE-55360)

#### Gestion de contenu web (WCM){#foundation-wcm-65-lts-sp1}

* Ajout de la prise en charge de Java 17 pour les traductions AEM en mettant à jour les lots de traduction, en vérifiant la compatibilité des packages Java, en supprimant les dépendances obsolètes et en assurant une fonctionnalité complète par le biais de tests complets. (CQ-4357525)
* Suppression de la `com.adobe.cq.platform.it.http.workflow.inbox.InboxOnOffTimeIT.testActivateLater` de test Evergreen non fiable pour éviter les échecs erronés lors des tests automatisés. (CQ-4298376)

#### Workflow{#foundation-workflow-65-lts-sp1}

* Ajout de l’attribut `data-detailsurl` manquant dans les éléments de la boîte de réception pour empêcher l’affichage de valeurs non définies dans les URL lors de l’utilisation d’AEM 6.5 LTS avec Java 21. (GRANITE-60158)
* Correction d’une NullPointerException dans la méthode `deactivate` du lot `WorkflowToPublishEventService` lors de l’exécution d’AEM 6.5 LTS avec Java 21, assurant ainsi l’arrêt correct du service de workflow sans erreur. (GRANITE-58151)
* Mise à jour de l’index du workflow pour prendre en charge le partage, la personnalisation en dehors du bureau et la résolution des problèmes de requête de chronologie. (GRANITE-52640)
* Mise à jour de l’index du workflow pour prendre en charge le partage, les fonctionnalités de personnalisation hors bureau et la résolution des problèmes de requête de chronologie. (GRANITE-52294)
* Résolution des échecs de journaux d’erreurs accrus lors de la validation de la comparaison des journaux pour une mise à niveau du programme vers la version 10912 d’AEM, garantissant une exécution stable du workflow. (GRANITE-44268)
* Mise à jour de la méthode d’assainissement des URL dans les référentiels de workflow pour remplacer `url.searchParams` par `url.search`, améliorant ainsi la protection XSS des URL vulnérables. (CQ-4359585)
* Les fonctionnalités de workflow, de boîte de réception et de projets validées dans AEM 6.6 Forms pour garantir le bon fonctionnement et l’intégration correcte. (CQ-4358777)
* Mise en œuvre de l’automatisation pour la publication des artefacts de contenu de workflow via Jenkins, permettant des processus de déploiement rationalisés et cohérents dans AEM 6.5. (CQ-4358472)
* Correction d’un problème dans le workflow de création de tâche de la boîte de réception en raison duquel la boîte de dialogue « Ajouter une tâche » ne se fermait pas après avoir cliqué sur Envoyer, malgré la création de la tâche, en raison d’une erreur de syntaxe JavaScript. (CQ-4355336)
* Correction d’un problème qui empêchait l’enregistrement de la configuration de la vue de la boîte de réception en raison d’une définition de propriété manquante pour `isEndUserConfigurationEnabled`. (CQ-4287757)




## [!DNL Experience Manager Foundation] {#experience-manager-foundation}

La plateforme d’[!DNL Adobe Experience Manager] 6.5 LTS repose sur les versions mises à jour de l’architecture OSGi (Apache Sling et Apache Felix), ainsi que sur le référentiel de contenu Java™ : Apache Jackrabbit Oak 1.68.x.

Eclipse Jetty 11.0.x est utilisé comme moteur de servlet pour Quickstart.

### Prise en charge de Java™  {#java-support}

* Prise en charge de Java™ 17 et Java™ 21.
* Pour des performances optimales, remplacez les valeurs par défaut du GC par d’autres valeurs. Pour plus d’informations, consultez la section [Installation et mise à jour](/help/sites-deploying/custom-standalone-install.md).
* Adobe distribue des mises à jour de maintenance Java™ 17 et Java™ 21 pour l’utilisation par les clientes et les clients dans les projets liés à AEM, lorsqu’elles ne sont pas disponibles publiquement depuis Oracle.

### Conditionnement Uberjar {#uber-jar-packaging}

* Il existe une légère différence dans le packaging Uberjar d’AEM 6.5 LTS. Pour plus d’informations, consultez [Mettre à jour la version AEM Uber Jar](/help/sites-deploying/upgrading-code-and-customizations.md#update-the-aem-uber-jar-version).

### Mise à niveau {#upgrade}

* Pour plus d’informations sur la procédure de mise à niveau, consultez la [documentation de mise à niveau](/help/sites-deploying/upgrade.md).

## Installation et mise à jour {#install-update}

Pour connaître les exigences de configuration, consultez les [instructions d’installation](/help/sites-deploying/custom-standalone-install.md).

Pour obtenir des instructions détaillées, consultez la [documentation de mise à niveau](/help/sites-deploying/upgrade.md).

>[!NOTE]
>
> Pour les nouvelles installations d’AEM 6.5 LTS, les définitions d’index doivent être installées séparément. Pour plus d’informations, consultez [cet article](/help/sites-deploying/pre-upgrade-maintenance-tasks.md#index-definitions).

## Plateformes prises en charge {#supported-platforms}

Recherchez la matrice complète des plateformes prises en charge, y compris le niveau de prise en charge dans les [Exigences techniques AEM 6.5 LTS](/help/sites-deploying/technical-requirements.md).

>[!NOTE]
>
>Les versions 17 et 21 de Java™ sont recommandées pour une utilisation avec AEM 6.5 LTS.

## Fonctionnalités obsolètes et supprimées {#deprecated-and-removed-features}

<!-- CARRY OVER EACH RELEASE -->

Adobe examine continuellement les fonctionnalités du produit afin d’améliorer la valeur client en modernisant ou en remplaçant les anciennes fonctionnalités. Ces modifications sont effectuées avec une attention particulière portée à la rétrocompatibilité.

Pour communiquer la suppression ou le remplacement imminent(e) de fonctionnalités d’Adobe Experience Manager (AEM), les règles suivantes s’appliquent :

1. L’annonce de la suppression arrive en premier. Bien qu’elles soient obsolètes, les fonctionnalités sont toujours disponibles, mais ne sont pas améliorées.
1. La suppression des fonctionnalités obsolètes se produit au plus tôt dans la version majeure suivante. La date cible réelle de suppression est prévue pour une annonce ultérieure.

Ce processus donne aux clients au moins un cycle de version pour adapter leur implémentation à une nouvelle version ou à un produit de remplacement pour une fonctionnalité obsolète, avant que la suppression ne soit effective.


### Fonctionnalités obsolètes {#deprecated-features}

Cette section répertorie les fonctionnalités qu’Adobe a abandonnées dans AEM 6.5 LTS. En règle générale, Adobe rend les fonctionnalités obsolètes avant de les supprimer dans une version ultérieure et fournit une alternative.


Il est conseillé aux clients de réfléchir à leur utilisation de la fonctionnalité dans leur déploiement actuel et de prévoir la modification de leur mise en œuvre de façon à utiliser l’alternative proposée.

| Domaine | Fonctionnalité | Remplacement | Version (SP) |
|---|---|---|---|


### Fonctionnalités supprimées {#removed-features}

Cette section répertorie les fonctionnalités qui ont été supprimées dans AEM 6.5 LTS. Ces fonctionnalités étaient signalées comme obsolètes dans les versions antérieures.

| Domaine | Fonctionnalité | Remplacement | Version (SP) |
|--- |--- |--- |--- |



## Problèmes connus {#known-issues}

<!-- DO THESE KNOWN ISSUES CARRY OVER EACH RELEASE? THE "PRODUCT UPDATES TEAM" IS SUPPOSED TO VERIFY EACH ISSUE AND LET YOU KNOW IF ANYTHING NEEDS TO BE ADDED, DELETED, OR CHANGED IN THIS LIST. -->

### Problème avec le lot de scripts JSP dans AEM 6.5.21-6.5.23 et AEM 6.5 LTS GA

AEM 6.5.21, 6.5.22, 6.5.23 et AEM 6.5 LTS GA sont fournis avec le lot `org.apache.sling.scripting.jsp:2.6.0`, qui contient un problème connu. Le problème se produit généralement sous une charge élevée lorsque l’instance AEM gère de nombreuses requêtes simultanées.

Lorsque ce problème se produit, l’une des exceptions suivantes peut apparaître dans les journaux d’erreurs avec des références à `org.apache.sling.scripting.jsp:2.6.0` :

* `java.io.IOException: classFile.delete() failed`
* `java.io.IOException: tmpFile.renameTo(classFile) failed`
* `java.lang.ArrayIndexOutOfBoundsException: Index 0 out of bounds for length 0`
* `java.io.FileNotFoundException`

Un correctif [cq-6.5.lts.0-hotfix-NPR-42640](https://experience.adobe.com/#/downloads/content/software-distribution/fr/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq660/hotfixes/cq-6.5.lts.0-hotfix-NPR-42640-1.2.zip) est disponible pour résoudre ce problème.

### Échec de la connexion à Dispatcher avec la fonction SSL uniquement {#ssl-only-feature}

Lors de l’activation de la fonction SSL uniquement dans les déploiements AEM, un problème connu affecte la connectivité entre les instances Dispatcher et AEM. Une fois cette fonctionnalité activée, les contrôles d’intégrité peuvent échouer et la communication entre les instances Dispatcher et AEM peut être interrompue. Ce problème se produit spécifiquement lorsque les clients tentent de se connecter via `https + IP` à partir des instances Dispatcher vers AEM. Elle est liée à des problèmes de validation SNI (Server Name Indication).

**Impact :**

* Échec des contrôles d’intégrité avec les codes de réponse HTTP 400
* Trafic rompu entre les instances Dispatcher et AEM
* Contenu diffusé incorrectement via Dispatcher
* Échecs de connexion lors de l’utilisation de HTTPS avec des adresses IP dans la configuration Dispatcher
* Erreurs HTTP 400 « SNI non valide » lors de la connexion via HTTPS + IP

**Environnements affectés :**

* Déploiements d’AEM avec les configurations Dispatcher
* Systèmes sur lesquels la fonction SSL uniquement a été activée
* Configurations Dispatcher utilisant la méthode de connexion `https + IP` aux instances AEM

**Solution :**
Si vous rencontrez ce problème, contactez l’Assistance Client d’Adobe. Un correctif [cq-6.5.lts.0-hotfix-CQ-4359803](https://experience.adobe.com/#/downloads/content/software-distribution/fr/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq660/hotfixes/cq-6.5.lts.0-hotfix-CQ-4359803-1.0.2.zip) est disponible pour résoudre ce problème. N’essayez pas d’activer les fonctions SSL uniquement avant d’avoir appliqué le correctif nécessaire.

## Lots OSGi et packages de contenu inclus{#osgi-bundles-and-content-packages-included}

Les documents texte suivants répertorient les lots OSGi et les packages de contenu inclus dans cette version [!DNL Experience Manager] 6.5 LTS, Service Pack 1 :

* [Liste des lots OSGi inclus dans Experience Manager 6.5 LTS, Service Pack 1](/help/release-notes/assets/65lts_sp1_bundles.txt) <!-- UPDATE FOR EACH NEW RELEASE -->
* [Liste des packages de contenu inclus dans Experience Manager 6.5 LTS, Service Pack 1](/help/release-notes/assets/65lts_sp1_packages.txt) <!-- UPDATE FOR EACH NEW RELEASE -->

## Sites web à accès limité{#restricted-sites}

Ces sites Web sont disponibles uniquement pour les clients. Si vous êtes client et avez besoin d’un accès, contactez votre responsable de compte Adobe.

* [Téléchargement du produit à l’adresse licensing.adobe.com](https://licensing.adobe.com/)
* [Contacter l’assistance clientèle Adobe](https://experienceleague.adobe.com/fr/docs/customer-one/using/home).

