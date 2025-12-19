---
title: Notes de mise à jour actuelles pour Adobe Experience Manager 6.5 LTS, SP1
description: Recherchez les informations de mise à jour actuelles pour Adobe Experience Manager 6.5 LTS, pack de services 1.
solution: Experience Manager
feature: Release Information
role: User,Admin,Architect,Developer
exl-id: b5a8f555-c061-4fe2-a100-cc01335959cb
source-git-commit: 6ca845ce5f4b97bfc5a360b3426f7284fb9cd401
workflow-type: tm+mt
source-wordcount: '7476'
ht-degree: 98%

---

# Notes de mise à jour actuelles pour Adobe Experience Manager 6.5 LTS, SP1 {#release-notes}

## Informations sur la version {#release-information}

| Produit | [!DNL Adobe Experience Manager] 6.5 LTS |
|---|---|
| Version | Pack de services 1 (SP1), correctif pour GRANITE-61551 <!-- UPDATE FOR EACH NEW RELEASE --> |
| Type | Mise à jour du pack de services |
| Date | 9 septembre 2025 <!-- UPDATE FOR EACH NEW RELEASE --> |
| URL de téléchargement | [Distribution logicielle](https://experience.adobe.com/#/downloads/content/software-distribution/fr/aem.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Fadobe%2Fpackages%2Fcq660%2Fhotfixes%2Fcq-6.5.lts.1-hotfix-GRANITE-61551-1.2.zip) |

<!-- OLD URL TO JAR
(https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/servicepack-lts/cq-quickstart-6.6.1.jar) | -->


<!-- UPDATE ABOVE FOR EACH NEW RELEASE -->

## Éléments compris dans [!DNL Adobe Experience Manager] 6.5 LTS, SP1 {#what-is-new}

<!-- UPDATE EACH RELEASE -->

[!DNL Experience Manager] 6.5 LTS, SP1 comprend de nouvelles fonctionnalités, des améliorations importantes demandées par la clientèle, ainsi que des correctifs. Cette version comprend également des améliorations en termes de performances, de stabilité et de sécurité, publiées depuis la mise à disposition initiale de la version 6.5 LTS en mars 2025. [Installez ce Pack de services](#install-update) sur la version 6.5 LTS.

## Principales fonctionnalités et améliorations

### Formulaires

AEM 6.5 Forms LTS on JEE est désormais disponible. Pour plus d’informations sur les environnements pris en charge, consultez le document Combinaisons de plateformes prises en charge . Les liens du programme d’installation sont disponibles sur la page Versions d’AEM Forms .

<!-- 6.5 LTS REVIEWERS: WHAT ARE THE KEY FEATURES AND ENHANCEMENTS THAT YOU WANT TO HIGHLIGHT IN THIS RELEASE? -->

<!-- UPDATE EACH RELEASE -->

## Problèmes corrigés dans la version 6.5 LTS, Pack de services 1 {#fixed-issues}

<!-- UPDATE BELOW FOR EACH NEW RELEASE -->

### [!DNL Sites]{#sites-65-LTS-SP1}

#### Accessibilité {#sites-accessibility-65-lts-sp1}

* Correction d’un problème en raison duquel l’élément d’éditeur de texte dans les fragments de contenu était tronqué par défaut. L’éditeur de texte affiche désormais l’ensemble du contenu sans troncature. (SITES-33005)
* Correction d’un problème en raison duquel les chemins d’URL des clics ouvraient la page d’accueil d’Indigo au lieu de l’URL de destination appropriée. (SITES-33004)
* Correction d’un problème d’accessibilité dans un composant AEM personnalisé qui provoquait des échecs de conformité ADA lors des tests automatisés. (SITES-30660)
* Correction de problèmes de conformité ADA dans la boîte de dialogue d’alerte et les messages de workflow en veillant à ce que le texte s’affiche en noir sur fonds clairs et respecte les exigences de contraste de la norme WCAG 2.0. (SITES-30138)
* Correction d’un problème d’accessibilité en raison duquel le bouton « Catégorie » de l’éditeur AEM Sites ne comportait pas d’étiquette spécifique, ce qui entraînait l’annonce par JAWS de l’utilisation du « menu du bouton Images » au lieu de fournir une étiquette descriptive. (SITES-27497)
* Correction d’un problème d’accessibilité en raison duquel les icônes de coche dans l’écran Autorisations effectives ne contenaient pas de texte secondaire, empêchant JAWS de lire et de transmettre leur signification. (SITES-27272)
* Correction d’un problème d’accessibilité en raison duquel la page Autorisations ne fournissait pas d’annonce JAWS claire pour la suppression des autorisations d’utilisateur et d’utilisatrice ou de groupe, ce qui entraînait une confusion pour les utilisateurs et utilisatrices de lecteurs d’écran. (SITES-27238)
* Correction d’un problème d’accessibilité en raison duquel les messages d’erreur s’affichaient uniquement sous forme d’icônes sans texte descriptif, empêchant JAWS d’annoncer les erreurs lorsqu’elles se produisaient. (SITES-27155)
* Correction d’un problème d’accessibilité en raison duquel JAWS lisait des descriptions de bouton incorrectes et imprécises dans l’environnement On-Premise AEM, y compris le texte de niveau d’en-tête 2 manquant pour la section Modules. (SITES-27152)
* Correction d’un problème d’accessibilité en raison duquel JAWS n’annonçait pas le nombre de résultats après le filtrage des valeurs dans l’onglet AEM Assets. (SITES-27150)
* Correction d’un problème d’accessibilité en raison duquel la création d’un dossier n’affichait pas de confirmation et JAWS ne l’annonçait pas dans l’interface d’utilisation d’Assets. (SITES-27141)
* Correction d’un problème d’accessibilité dans AEM Sites. JAWS n’annonçait pas les erreurs de formulaire, la cible était déplacée vers des éléments d’erreur non interactifs et les erreurs de champ obligatoire n’étaient pas affichées dans l’onglet. (SITES-27138)
* Correction d’un problème d’accessibilité en raison duquel le menu du bouton Chronologies ne comportait pas de libellé spécifique, ce qui entraînait la lecture seulement du « menu du bouton Activités » par JAWS sans fournir de description claire. (SITES-27134)
* Correction d’un problème d’accessibilité en raison duquel JAWS n’annonçait pas l’action ou le rôle pour les éléments de conteneur, lisant uniquement « Chemin de navigation v1 » et « bouton v2 » au lieu de libellés descriptifs. (SITES-27131)
* Correction d’un problème d’accessibilité en raison duquel le pop-up de publication rapide ne fournissait pas un message de réussite correct, empêchant les lecteurs d’écran d’annoncer les commentaires d’achèvement. (SITES-26912)
* Correction d’un problème d’accessibilité dans la vue de colonne Coral en raison duquel les éléments disposant de rôles ARIA nécessitant des rôles enfant ne les contenaient pas, ce qui entraînait une non-conformité aux normes d’accessibilité. (SITES-26898)
* Correction d’un problème d’accessibilité en raison duquel les textes « modèle » et « propriétés » dans le volet de navigation supérieur de la page de création n’étaient pas visibles en mode Reflow, ce qui empêchait l’accès pour les utilisateurs et utilisatrices d’un clavier ou d’un lecteur d’écran. (SITES-26895)
* Correction d’un problème d’accessibilité en raison duquel les infobulles des icônes « recherche », « solution », « aide », « boîte de réception » et « utilisateur ou utilisatrice » du volet de navigation supérieur n’étaient pas accessibles via la navigation au clavier. (SITES-26889)
* Correction d’un problème d’accessibilité en raison duquel les champs de formulaire de l’onglet De base ne fournissaient pas de suggestions d’erreur, empêchant les utilisateurs et utilisatrices de recevoir des conseils lorsque les champs de saisie obligatoires étaient laissés vides. (SITES-26885)
* Correction d’un problème d’accessibilité en raison duquel les lecteurs d’écran NVDA et Narrateur n’annonçaient pas les détails du fichier de modèle dans la page Créer, empêchant les utilisateurs et utilisatrices de recevoir des informations complètes par programmation. (SITES-26884)
* Correction d’un problème d’accessibilité qui utilisait un nom incorrect pour la « zone de texte Titre de la page » dans l’onglet De base, empêchant les lecteurs d’écran de fournir des informations précises aux utilisateurs et utilisatrices. (SITES-26879)
* Mise à jour des couleurs de premier plan et d’arrière-plan des boutons pour répondre aux exigences de rapport de contraste minimal de WCAG 2.2 AA, améliorant ainsi la lisibilité et l’accessibilité pour tous les utilisateurs et utilisatrices. (SITES-26877)
* Correction d’un problème en raison duquel les textes « modèle » et « propriétés » dans le volet de navigation supérieur de la page de création disparaissaient après le redimensionnement, garantissant ainsi la visibilité et l’accessibilité pour les personnes malvoyantes. (SITES-26872)
* Correction d’un problème en raison duquel plusieurs barres de défilement horizontales s’affichaient sur la page principale après l’application de Reflow, garantissant ainsi l’affichage d’une seule barre de défilement pour une accessibilité et une visibilité correctes du contenu. (SITES-26800)
* Correction d’un problème d’accessibilité dans l’éditeur de page AEM en raison duquel la cible au clavier se réinitialisait de manière inattendue au début de la barre d’outils démographique après l’activation de boutons tels que Persona, Panier ou Abandonné. Le focus reste désormais sur le bouton activé pour prendre en charge les workflows cohérents de navigation au clavier et de lecteur d’écran. (SITES-25306)
* Correction d’un problème d’association des libellés d’accessibilité pour les champs de titre de page et de balises. L’interface AEM associe désormais correctement les libellés d’accessibilité aux champs « Titre » et « Titre de la page » lors de l’utilisation de lecteurs d’écran tels que JAWS. Le correctif garantit une lecture correcte des libellés et améliore la conformité ADA sur la création de pages, les propriétés et les workflows de déplacement. (SITES-27149)
* Correction d’un libellé visuel manquant pour les champs de saisie de commentaire dans la chronologie. Correction des libellés visuels manquants pour les champs d’entrée « Commentaire » sous la section chronologie afin d’améliorer l’accessibilité. La mise à jour garantit que les lecteurs d’écran peuvent annoncer avec précision les libellés des champs. Cette expérience améliore la navigation et l’envoi de formulaires pour les utilisateurs et utilisatrices, en particulier les personnes qui dépendent des technologies d’assistance. (SITES-26903)
* Correction de l’accessibilité du clavier pour le bouton représentant des points de suspension dans les commentaires de la chronologie. Activation de la navigation au clavier pour le bouton représentant des points de suspension en regard des commentaires sous la section Chronologie. Les utilisateurs et utilisatrices peuvent désormais interagir avec le bouton à l’aide de la touche de tabulation, ce qui améliore l’accessibilité pour les utilisateurs et utilisatrices qui nécessitent une navigation au clavier uniquement. (SITES-26891)
* Amélioration des annonces NVDA/Narrator pour les résultats de recherche dans les boîtes de dialogue de sélection. Mise à jour de la boîte de dialogue Ouvrir la sélection pour indiquer si des résultats de recherche sont trouvés ou non lors de l’utilisation de lecteurs d’écran, tels que NVDA ou Narrator. Cette amélioration aide les utilisateurs et utilisatrices qui utilisent des technologies d’assistance à comprendre le résultat de leurs actions de recherche sans confirmation visuelle. (SITES-26883)
* Correction du rôle ARIA pour l’icône représentant des points de suspension en regard du champ de saisie de commentaire. Mise à jour de l’icône représentant des points de suspension à côté du champ de saisie de commentaire pour utiliser le rôle ARIA approprié, afin que les lecteurs d’écran puissent identifier précisément l’élément. Cela permet d’améliorer la conformité en matière d’accessibilité et l’expérience des utilisateurs et utilisatrices qui dépendent des technologies d’assistance. (SITES-26881)
* Correction d’attributs ARIA non valides dans les composants de l’interface d’utilisation Coral. Mise à jour des composants de l’interface d’utilisation Coral pour garantir que tous les attributs ARIA utilisent des valeurs valides, améliorant ainsi la conformité en matière d’accessibilité. En particulier, des cas ont été traités où des valeurs non valides telles que `aria-modal="dialog"` ont été attribuées de manière incorrecte. Cette amélioration permet aux lecteurs d’écran d’interpréter correctement les éléments de boîte de dialogue, ce qui améliore l’accessibilité pour les utilisateurs et utilisatrices qui dépendent des technologies d’assistance. (SITES-26873)
* Amélioration de la visibilité et des infobulles des icônes dans les scénarios Reflow. Optimisation du comportement Reflow pour garantir l’affichage correct des infobulles des icônes **Télécharger**, **Retraiter les ressources** et **Extraire**. Mise en évidence d’un problème d’accessibilité en raison duquel les icônes et leurs libellés devenaient invisibles lorsque la fenêtre était redimensionnée ou que les paramètres de zoom du navigateur étaient modifiés. Cette correction améliore l’accessibilité pour les personnes ayant une mauvaise vue, en maintenant la visibilité et en fournissant des descriptions appropriées des icônes en mode Reflow. (SITES-26871)


#### Interface d’utilisation d’administration{#sites-adminui-65-lts-sp1}

* Correction d’un problème d’accessibilité en raison duquel JAWS n’annonçait pas les rôles de liste ou ne fournissait pas d’instructions de navigation et d’activation dans la boîte de dialogue Créer un site. (SITES-30661)
* La prise en charge des lecteurs d’écran pour les messages de statut dans la vue de filtrage Sites fonctionne comme prévu, garantissant ainsi que les utilisateurs et utilisatrices reçoivent des commentaires clairs et opportuns lors du changement d’affichage. (SITES-24992)
* Le sélecteur de date du rail Filtres s’affiche entièrement dans son conteneur, fournissant ainsi une taille cible tactile adéquate et éliminant les problèmes d’écrêtage. (SITES-24988)
* Les balises de filtrage sélectionnées utilisent désormais des libellés sémantiques HTML et ARIA qui correspondent à la présentation visuelle, ce qui garantit une prise en charge exacte des rôles et des actions claires pour les technologies d’assistance. (SITES-24980)
* Ajout d’un attribut aria-label à la région Rail de références pour fournir un libellé descriptif unique aux utilisateurs et utilisatrices de lecteurs d’écran et assurer une identification cohérente des repères sur la page. (SITES-24973)
* Mise à jour du Rail de références afin d’utiliser des unités relatives pour le dimensionnement et le positionnement, pour que le contenu soit mis à l’échelle et reste entièrement fonctionnel lorsqu’il est agrandi à 400 % dans un viewport de 1 280 x 1 024. (SITES-24972)
* Les éléments de tableau confirmés dans la vue Liste de la page d’accueil Sites contiennent les rôles d’en-tête de colonne appropriés, ce qui permet aux lecteurs d’écran d’annoncer les en-têtes pour chaque cellule de données. (SITES-24942)
* NVDA annonce désormais la date de modification dans le répertoire de l’arborescence, ce qui garantit que les utilisateurs et utilisatrices de lecteurs d’écran reçoivent des informations détaillées complètes sur les ressources. (SITES-24782)
* Correction d’un problème en raison duquel le lecteur d’écran NVDA annonçait du texte incomplet pour les éléments du composant Répertoire d’arborescence dans AEM Sites. NVDA lit désormais l’ensemble du texte de chaque élément, ce qui améliore l’accessibilité et la conformité. (SITES-24780)
* Ajout de l’accessibilité clavier au séparateur de fenêtre dans le répertoire d’arborescence, ce qui permet aux utilisateurs et utilisatrices de redimensionner la barre latérale gauche à l’aide d’un clavier seulement. (SITES-24779)
* Mise à jour des résultats de recherche du menu Aide afin d’inclure des rôles ARIA corrects pour les éléments de liste, en veillant à ce que les lecteurs d’écran annoncent correctement les liens pour une meilleure accessibilité. (SITES-24729)
* Correction d’un problème en raison duquel les lecteurs d’écran n’annonçaient pas le message de statut « X sur Y résultats ». ou le message « aucun résultat trouvé » après l’application de filtres dans le panneau de filtrage de Sites, garantissant ainsi que les utilisateurs et utilisatrices reçoivent une confirmation correcte des résultats. (SITES-24720)
* Correction des affectations de rôle manquantes pour les liens de navigation dans la navigation de l’application. Ajout de rôles ARIA appropriés pour s’assurer que les lecteurs d’écran identifient et annoncent correctement les éléments de navigation. (SITES-24719)
* Remplacement du balisage de rôle de grille incorrect pour les balises de filtrage sélectionnées par des éléments de bouton et ajout de noms accessibles, garantissant ainsi que les lecteurs d’écran annoncent et identifient correctement les balises. (SITES-24717)
* Ajout d’annonces du lecteur d’écran pour le message de statut du rail de références lors de sélections multiples, garantissant que les utilisateurs et utilisatrices reçoivent une confirmation des modifications. (SITES-24678)
* Correction du comportement des champs de recherche afin que le premier résultat ne soit pas automatiquement annoncé. Les lecteurs d’écran annoncent désormais le nombre de résultats trouvés, ce qui permet aux utilisateurs et utilisatrices de parcourir la liste sans annonces de cibles incorrectes. (SITES-24658)
* Suppression des attributs `aria-label` incorrects des éléments statiques non interactifs dans la vue Liste pour empêcher les lecteurs d’écran d’annoncer des informations trompeuses ou non pertinentes. (SITES-24515)
* Mise à jour de la case à cocher dans la première colonne de la vue Liste afin d’utiliser le texte de la colonne Titre pour son nom accessible, ce qui garantir que les lecteurs d’écran transmettent précisément l’objectif du champ de formulaire. (SITES-24514)
* Ajout des attributs ARIA appropriés et de la prise en charge des régions actives pour annoncer les messages d’état de chargement aux utilisateurs et utilisatrices de lecteurs d’écran lors de la navigation dans le contenu. (SITES-24481)
* Mise à jour de la conception réactive pour éliminer le défilement horizontal lorsque le contenu est agrandi à 400 % avec une largeur de viewport de 1 280 × 1 024, afin d’assurer une visibilité complète sans défilement latéral. (SITES-24308)
* Correction de la navigation de la cible dans l’interface d’utilisation d’administration de Sites afin de suivre un ordre logique, en ramenant la cible sur le bouton « Tout sélectionner » après avoir appuyé sur Echap et en déplaçant la cible vers l’élément interactif suivant après avoir appuyé sur la touche de tabulation. (SITES-24307)
* Mise à jour de l’ordre de la cible dans l’interface d’utilisation d’administration de Sites afin que le bouton de chemin de navigation dans l’élément `<betty-titlebar-title>` soit la cible dans l’ordre approprié lors de la navigation au clavier. (SITES-24305)
* Vérification de la fonctionnalité de saut de lien pour s’assurer qu’elle déplace la cible au clavier vers la zone de contenu principale, ce qui permet aux utilisateurs et utilisatrices du clavier de contourner les éléments d’en-tête et d’accéder efficacement au contenu. (SITES-24061)


#### Interface d’utilisation classique{#sites-classicui-65-lts-sp1}

Correction d’un problème dans l’interface d’utilisation classique en raison duquel les libellés de case à cocher manquaient et HTML s’affichait en tant que texte codé dans plusieurs éléments de l’interface d’utilisation, y compris la recherche de date et les interfaces non standard. (SITES-31822)

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

Correction d’un problème dans le composant Liste de produits en raison duquel la case à cocher « Tout sélectionner » ajoutait uniquement les 20 premiers SKU de la page initiale au lieu de tous les SKU dans les résultats de la recherche. (SITES-29191)

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

* Correction d’une erreur JavaScript `ns.ui.alert is not a function` qui se produisait lors de la réactivation de l’héritage des composants fantômes dans AEM 6.5 On-prem. (SITES-31993)
* Correction d’un problème en raison duquel l’option de déploiement « Ultérieurement » permettait de continuer sans sélectionner de date dans AEM 6.5. (SITES-31374)

#### Éditeur de page{#sites-pageeditor-65-lts-sp1}

* Correction d’un problème dans le modal du teaser en raison duquel l’onglet Lien et actions continuait à afficher le style d’erreur, les icônes et l’attribut aria-invalid après une saisie de données valide et une résolution d’erreur. (SITES-25527)
* Correction d’un problème dans l’éditeur de texte modal du teaser en raison duquel les boutons Listes et Paragraphes ne transmettaient pas leur état développé ou réduit aux lecteurs d’écran, assurant ainsi des mises à jour d’attributs précises avec une extension ARIA. (SITES-25365)
* Correction d’un problème dans la barre d’outils Démographique en raison duquel le réglage du curseur du panier avec la saisie au clavier déplaçait la cible vers le bouton Panier au lieu de conserver la cible sur le curseur, améliorant ainsi l’efficacité de la navigation pour les utilisateurs et utilisatrices d’un clavier. (SITES-25324)
* Ajout d’un nom accessible au curseur de panier dans la barre d’outils Démographique en attribuant une valeur à son élément `<label>` associé. Ce correctif a amélioré la compatibilité avec les technologies d’assistance et optimisé la convivialité pour les utilisateurs et utilisatrices de lecteurs d’écran. (SITES-25322)
* Ajout de rôles ARIA et de noms accessibles aux boutons dans la liste déroulante de la barre d’outils Démographique. Ce correctif a permis une identification correcte par les technologies d’assistance et une navigation améliorée pour les utilisateurs et utilisatrices d’un clavier ou d’un lecteur d’écran. (SITES-25315)
* Réglage de la disposition de la barre d’outils Démographique pour éviter le débordement du contenu au-delà du viewport à un zoom de 200 % du navigateur, ce qui garantit que tous les contrôles restent accessibles sans défilement horizontal. (SITES-25309)
* Correction de la gestion de la cible dans la barre d’outils Démographique afin de conserver la cible au clavier sur le bouton activé au lieu de réinitialiser la cible sur la position de départ de la barre d’outils. (SITES-25306)
* Le chevauchement des libellés de boutons fonctionne comme prévu, à l’aide d’une infobulle pour afficher le libellé lorsque des modes avec des largeurs d’écran similaires sont actifs. (SITES-25285)
* Le modal d’annotation comprend un bouton d’envoi visible qui permet aux utilisateurs et utilisatrices d’envoyer des annotations sans devoir appuyer sur la touche Echap ni cliquer en dehors de la boîte de dialogue modale. (SITES-25281)
* Le modal d’annotation comprend un bouton représentant une icône en forme de stylo qui permet aux utilisateurs et utilisatrices d’envoyer des annotations, fournissant ainsi une méthode d’envoi claire et accessible. (SITES-25269)
* Correction des annonces du lecteur d’écran pour les boutons Annoter et Fermer l’annotation afin de fournir des commentaires précis et pertinents et de supprimer les informations sans rapport ou déroutantes. (SITES-25268)
* Les sections Zone de travail des pages de l’éditeur AEM prennent désormais en charge l’accessibilité clavier complète. Les utilisateurs et les utilisatrices peuvent activer les titres de section et modifier les boutons à l’aide du clavier uniquement, sans avoir à pointer avec la souris. Cette mise à jour garantit la conformité avec la norme WCAG 2.1.1 et améliore l’accessibilité et l’ergonomie des différents composants (comme les modèles Teaser, Image, Carrousel, Disposition, Distorsion du temps et Annotation). (SITES-25256)
* Suppression du défilement horizontal inutile dans le modal du carrousel de 320 pixels de largeur pour garantir l’affichage de tout le contenu dans le viewport sans recourir à la navigation côte à côte. (SITES-25254)
* Suppression du défilement horizontal inutile dans le modal de l’image de 320 pixels de largeur pour garantir l’affichage de tout le contenu dans le viewport sans recourir à la navigation côte à côte. (SITES-25244)
* Suppression du défilement horizontal inutile dans le modal du teaser de 320 pixels de largeur pour garantir l’affichage de tout le contenu dans le viewport sans recourir à la navigation côte à côte. (SITES-25242)
* Activation de la navigation au clavier pour le menu pop-up `List` et `Paragraph Format`, tous deux dans le modal du teaser. Ce correctif permet aux utilisateurs et utilisatrices d’accéder à ces menus et de les parcourir à l’aide des touches fléchées. (SITES-25235)
* Correction des annonces du lecteur d’écran pour les boutons Annoter et Fermer l’annotation afin de fournir des commentaires précis et pertinents en accord avec les actions associées. (SITES-25234)
* Amélioration du libellé du bouton Aide dans le modal du teaser afin de décrire clairement son objectif et de fournir un contexte explicite à tous les utilisateurs et utilisatrices, y compris les utilisateurs et utilisatrices de technologies d’assistance. (SITES-25224)
* Amélioration de la règle d’émulateur pour les utilisateurs et utilisatrices de lecteurs d’écran en associant les mesures de règle à leurs appareils respectifs. Remplacement également de l’infobulle par un élément aria-descripbedby. (SITES-24955)
* Aucun correctif n’a été implémenté, car le bouton Modifier fonctionne comme prévu et fournit un contexte informatif plutôt que d’exécuter une action. (SITES-24950)
* L’ordre de focus confirmé sur la page de l’éditeur suit une séquence logique, ce qui permet aux utilisateurs et utilisatrices de parcourir tous les éléments interactifs sans passer ou revenir en arrière de manière inattendue. (SITES-24937)
* La zone de travail du mode d’aperçu confirmée met correctement à jour l’espacement du texte lorsque les utilisateurs et utilisatrices appliquent des paramètres d’espacement personnalisés, assurant ainsi une mise en forme cohérente dans toutes les zones de contenu. (SITES-24936)
* Le bouton Aperçu vérifié ne déclenche plus de changements de contexte ou d’état, ce qui garantit que les utilisateurs et utilisatrices activent délibérément le bouton avant la mise à jour des pages vues. (SITES-24784)
* Ajout d’affectations de rôles ARIA correctes aux liens de navigation de l’application, permettant aux lecteurs d’écran d’identifier et d’annoncer précisément les éléments de navigation pour une meilleure accessibilité. (SITES-24718)
* Mise à jour du bouton Modifier les filtres pour annoncer les états développés et réduits aux lecteurs d’écran, les attributs ARIA redondants supprimés et l’étiquetage ajusté afin de fournir des descriptions claires et uniques. (SITES-24713)
* Ajout d’annonces du lecteur d’écran pour les messages de statut des résultats de la recherche dans la boîte de dialogue de sélection de lien, afin de garantir que les utilisateurs et utilisatrices reçoivent une confirmation lors du chargement des résultats ou qu’aucune correspondance n’est trouvée. (SITES-24700)
* Ajout d’annonces du lecteur d’écran pour l’état de chargement du modal de l’image, afin que les utilisateurs et utilisatrices reçoivent des commentaires lorsque le modal est en cours de chargement et prêt pour l’interaction. (SITES-24697)
* Correction d’un problème d’accessibilité en raison duquel l’en-tête ancré masquait le contenu du modal du teaser à un zoom de 200 % et de 400 %, assurant ainsi une visibilité et une convivialité totales lors de l’agrandissement de la page. (SITES-24523)
* Ajout d’un message de statut indiquant le nombre de résultats de la recherche dans le champ Rechercher/Filtrer, ce qui permet aux lecteurs d’écran d’annoncer les résultats aux utilisateurs et utilisatrices. (SITES-24506)
* Ajout d’annonces du lecteur d’écran pour le nombre de résultats de la recherche dans le champ Rechercher/Filtrer, afin que les utilisateurs et utilisatrices reçoivent immédiatement des commentaires lors du chargement des résultats. (SITES-24505)
* Ajout d’un nom accessible à la liste d’onglets du panneau Rail latéral, ce qui permet aux lecteurs d’écran d’annoncer son objectif conformément aux directives WAI-ARIA. (SITES-24492)
* Ajout de libellés descriptifs aux icônes d’éditeur ambiguës, afin de s’assurer que tous les utilisateurs et utilisatrices comprennent clairement la fonction de chaque bouton. (SITES-24480)
* Activation de l’accessibilité complète au clavier pour les titres de section et les boutons d’action dans la vue Zone de travail, assurant un fonctionnement cohérent pour les utilisateurs et utilisatrices d’une souris et d’un clavier. (SITES-24479)

<!--
#### Replication{#sites-replication-65-lts-sp1}

#### Rich Text Editor{#sites-rte-65-lts-sp1} -->

#### Éditeur universel {#sites-universal-editor-65-lts-sp1}

* Correction d’une condition de concurrence dans QueryTokenService qui provoquait des connexions incorrectes lorsque plusieurs requêtes avec des paramètres de requête déclenchées avant que le service login-token ne renvoie un résultat. (SITES-30659)
* Correction d’un problème dans UniversalEditorURLService en raison duquel l’enregistrement d’un tableau de chemins mappés dans Felix ConfigMgr ne conservait que le premier élément. (SITES-30292)

### [!DNL Assets]{#assets-65-lts-sp1}

Correction d’un problème en raison duquel la synchronisation des ressources du DAM distant vers l’AEM local Sites supprimait le statut publié et les propriétés liées à la réplication des ressources. (ASSETS-48958)

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

* Suppression de l’utilisation de commons-httpclient 3.x de l’offre groupée `com.adobe.cq.cq-analytics-integration` et remplacement par `org.apache.httpcomponents.httpclient` 4.5.13.B0001 pour respecter les dernières normes d’AEM 6.5 LTS. (CQ-4360586)
* Suppression de l’offre groupée d’intégration obsolète Search&amp;Promote d’AEM afin d’éliminer les composants inutilisés et de réduire les frais de maintenance. (CQ-4358030)
* Ajout de nouveaux cas de test principaux pour l’intégration de SiteCatalyst afin d’améliorer la validation des analyses et d’assurer une couverture plus complète. (CQ-4359991)
* Correction d’un problème dans la section Propriétés de la configuration de Launch en raison duquel les listes déroulantes Société et Propriété n’apparaissaient pas. En outre, Enregistrer et Fermer déclenchaient des erreurs malgré le remplissage de tous les champs obligatoires et des messages d’erreur incorrects s’affichaient pour Société et Propriété lorsque seul le champ Titre était vide. (CQ-4359853)
* Suppression de l’entrée de chemin de servlet `searchpromote` de la version 6.6 pour s’aligner sur la suppression de l’offre groupée Search&amp;Promote. (CQ-4359523)
* Correction de cas de tests HTTP pour le référentiel Target afin de garantir une validation précise et une fiabilité de test améliorée. (CQ-4359022)
* Suppression de l’utilisation de la mise en cache Guava du module integration-adobeims-console pour éliminer les dépendances de la bibliothèque Guava. (CQ-4358710)
* Validation de workflows d’intégration de DTM, de tâches de boîte de réception et de fonctionnalités de projet dans AEM 6.6 pour garantir le bon fonctionnement dans AEM 6.5. (CQ-4358151)
* Validation de la fonctionnalité Content Insight dans AEM 6.6 pour garantir la compatibilité et le bon fonctionnement dans AEM 6.5. (CQ-4357774)
* Validation de la fonctionnalité Services cloud dans AEM 6.6 pour garantir la compatibilité et le bon fonctionnement dans AEM 6.5. (CQ-4357773)
* Validation de l’intégration de la console Adobe IMS dans AEM 6.6 pour garantir la compatibilité et le bon fonctionnement dans AEM 6.5. (CQ-4357772)
* Mise à jour du pipeline Jenkins pour que l’intégration Test&amp;Target s’exécute sur Java 17, résoudre les tests Selenium qui échouent, déplacer certains tests vers Playwright et s’assurer que tous les tests unitaires aboutissent. (CQ-4357770)
* Alignement d’intégrations DX, de workflow, de boîte de réception et de projets avec la branche 6.6.0 en mettant à jour les pipelines de création et de test. Résolution également de problèmes de compatibilité de mise à niveau et validation de tous les services concernés pour en optimiser la stabilité et la fonctionnalité. (CQ-4357767)

<!--
#### Jetty{#foundation-jetty-65-lts-sp1} -->

#### Localisation{#foundation-localization-65-lts-sp1}

* Localisation des chaînes dans la boîte de dialogue « Supprimer le contrôle d’accès » de la liste « Autorisations » pour afficher les traductions correctes. (GRANITE-59427)
* Correction d’un problème dans la boîte de dialogue Ajouter une règle « Propriétés de la Division OU » de l’éditeur de modèles en raison duquel plusieurs chaînes d’interface d’utilisation, y compris des opérateurs et des libellés de champs, semblaient non localisées. Toutes les chaînes s’affichent désormais avec une localisation correcte. (CQ-4354014)
* Ajout de la traduction manquante pour l’infobulle « Afficher la description de » dans la boîte de dialogue Modifier les modèles de workflow. (CQ-4347996)

#### Oak {#foundation-oak-65-lts-sp1}

Correction d’un problème en raison duquel AEM recréait ou renommait les fichiers de configuration existants sous `/apps/system/config` lors des mises à niveau, en remplaçant des fichiers `.cfg.json` par des fichiers `.config`. (GRANITE-58899)

#### Omnisearch{#foundation-omnisearch-65-lts-sp1}

Correction d’un problème d’accessibilité en raison duquel les espaces réservés apparaissaient de manière incorrecte en tant que libellés pour les champs de saisie. Ce problème entraîne l’absence de libellés de champs dans la recherche, les fragments d’expérience AEM, les fragments de contenu et les modèles de fragment de contenu. (Granite-61791)

<!--
#### Platform{#foundation-platform-65-lts-sp1} -->

#### Projets{#foundation-projects-65-lts-sp1}

* Correction d’un problème qui affichait un pop-up d’erreur incorrect lors de la suppression d’un projet dans la vue Calendrier malgré la suppression réussie du projet. (CQ-4358890)
* Correction d’un problème dans Firefox en raison duquel le pied de page de la vignette « Collection de ressources » dans la vue Projet chevauchait la bordure de la vignette. Le pied de page est désormais correctement aligné sans chevauchement. (CQ-4353317)

#### Démarrage rapide{#foundation-quickstart-65-lts-sp1}

* Mise à jour du script de désinstallation afin d’ajuster la plage de versions de l’offre groupée Guava, ce qui empêche son placement sur la liste bloquée lors de l’installation via le gestionnaire de modules. (GRANITE-59559)
* Correction d’un problème dans l’interface d’utilisation de réplication qui affichait une erreur (`#1660`) lors de la modification des agents de réplication en corrigeant la gestion des cases à cocher classiques dans l’interface. (GRANITE-58302)
* Correction de plusieurs erreurs de démarrage du magasin de données S3 lors de l’exécution d’AEM 6.5 LTS avec JDK 21 en corrigeant les autorisations de service manquantes, en mettant à jour la gestion de la configuration et en s’assurant que les services requis s’initialisent correctement. (GRANITE-57082)
* Définition de la stratégie de maintenance et de soutien d’AEM 6.5. Ce correctif comprenait les éléments suivants :
   * Cadence de pack de services.
   * Cadence de correctif.
   * Prise en charge parallèle avec AEM 6.6.
   * Matrice de support mise à jour.
   * Module complémentaire des responsabilités de propriété. (GRANITE-50459)

<!--
#### Security{#foundation-security-65-lts-sp1} -->

#### Sling{#foundation-sling-65-lts-sp1}

* Mise à jour de Sling ResourceAccessSecurity vers la version 1.1.2 afin de résoudre une `ClassCastException` qui se produisait lorsque plusieurs références `ResourceAccessGate` initialisaient `ResourceAccessSecurityImpl`. (NPR-42750)
* Correction d’un problème dans l’intégration d’Adobe Stock en raison duquel la boîte de dialogue Licence apparaissait grisée. Ce problème était dû à la suppression de champs de saisie obligatoires par la fonction `sunt:initList`. La fonction se trouvait dans les bibliothèques clientes Coral Foundation. Mise à jour des bibliothèques clientes pour conserver les champs nécessaires, permettant ainsi à la boîte de dialogue de la licence de fonctionner correctement. (NPR-42748)
* Correction d’une erreur inattendue de compilation JSP avec `org.apache.sling.scripting.jsp 2.6.0`. (NPR-42640)

<!--
#### Translation{#foundation-translation-65-lts-sp1} -->

#### Interface d’utilisation{#foundation-ui-65-lts-sp1}

* Correction d’un problème dans l’interface d’utilisation de création AEM qui limitait l’affichage des groupes d’utilisateurs à 41. Ce problème était dû à une limite de lot par défaut dans le composant du sélecteur de groupe de l’interface d’utilisation Granite. Mise à jour du composant pour afficher tous les groupes sans troncature. (NPR-42749)
* Correction d’un problème dans l’assistant de création de page On-Prem en raison duquel des champs obligatoires de composants à plusieurs champs n’étaient pas revalidés lors de la modification des propriétés de la page. Par ailleurs, ce problème permettait aux créateurs et créatrices de contourner la validation et de poursuivre avec des données incomplètes. (GRANITE-58826)
* Correction des attributs ARIA du bouton d’aide dans AEM afin de s’assurer que les lecteurs d’écran JAWS annoncent un libellé clair et convivial au lieu d’afficher une icône et des métadonnées texte non traduites. (GRANITE-55360)

#### Gestion de contenu web (WCM){#foundation-wcm-65-lts-sp1}

* Ajout de la prise en charge de Java 17 pour les traductions d’AEM en mettant à jour les offres groupées traduites, en vérifiant la compatibilité du package Java, en supprimant les dépendances obsolètes et en assurant la fonctionnalité grâce à des tests complets. (CQ-4357525)
* Suppression du test Evergreen `com.adobe.cq.platform.it.http.workflow.inbox.InboxOnOffTimeIT.testActivateLater` défectueux pour empêcher les faux échecs lors des tests automatisés. (CQ-4298376)

#### Workflow{#foundation-workflow-65-lts-sp1}

* Ajout de l’attribut `data-detailsurl` manquant dans les éléments de boîte de réception afin d’empêcher l’affichage de valeurs non définies dans les URL lors de l’utilisation d’AEM 6.5 LTS avec Java 21. (GRANITE-60158)
* Correction d’une exception NullPointerException dans la méthode `deactivate` de l’offre groupée `WorkflowToPublishEventService` lors de l’exécution d’AEM 6.5 LTS avec Java 21, garantissant ainsi un arrêt correct du service de workflow sans erreur. (GRANITE-58151)
* Mise à jour de l’index de workflow pour prendre en charge le partage, la personnalisation d’absence du bureau et la résolution des problèmes de requête chronologique. (GRANITE-52640)
* Mise à jour de l’index de workflow pour prendre en charge le partage, les fonctionnalités de personnalisation d’absence du bureau et la résolution des problèmes de requête chronologique. (GRANITE-52294)
* Correction d’un nombre accru d’échecs de journaux d’erreurs lors de la validation de comparaison d’une mise à niveau du programme vers AEM version 10912, garantissant ainsi la stabilité de l’exécution du workflow. (GRANITE-44268)
* Mise à jour de la méthode de nettoyage des URL dans les référentiels de workflows afin de remplacer `url.searchParams` par `url.search`, améliorant ainsi la protection XSS pour les URL vulnérables. (CQ-4359585)
* Validation des fonctionnalités de workflow, de boîte de réception et de projets dans AEM Forms 6.6 pour assurer le bon fonctionnement et l’intégration. (CQ-4358777)
* Implémentation de l’automatisation pour la publication d’artefacts Workflow-Contenu via Jenkins, ce qui permet d’obtenir des processus de déploiement simplifiés et cohérents dans AEM 6.5. (CQ-4358472)
* Correction d’un problème dans le workflow Créer une tâche de la boîte de réception en raison duquel la boîte de dialogue « Ajouter une tâche » ne se fermait pas après avoir cliqué sur Envoyer, malgré la création de la tâche, en raison d’une erreur de syntaxe JavaScript. (CQ-4355336)
* Correction d’un problème qui empêchait l’enregistrement de la configuration de la vue Boîte de réception en raison d’une définition de propriété manquante pour `isEndUserConfigurationEnabled`. (CQ-4287757)

## Formulaires

### Concepteur Forms

* Lorsque la personne exporte les données d’un PDF XFA à l’aide de l’API exportData, le fichier XML obtenu présente des incohérences par rapport aux données XML exportées manuellement à l’aide d’Acrobat Reader. Les valeurs de certains champs étaient manquantes dans la sortie par rapport à la sortie générée à partir d’Acrobat Reader. (LC-3922791)
* La génération d’un PDF balisé avec le service Output dans Workbench ajoute une balise de libellé inattendue sous la balise de référence dans un élément de table des matières. (LC-3922756)
* Lors de l’aplatissement de PDF dynamiques à remplir au format PDF/A à l’aide du service Output, l’état dynamique n’est pas conservé. Ce problème entraîne une perte de données et des problèmes de conformité potentiels, en particulier si le balisage est activé. (LC-3922708)
* Lorsque la personne place des légendes de champ avec un alignement inférieur ou droit dans AEM Forms Designer, l’arborescence des balises inclut uniquement la légende sans la valeur correspondante, ce qui entraîne un balisage d’accessibilité incomplet. (LC-3922619)
* Les codes QR dans les PDF générés deviennent illisibles. Le texte secondaire des codes QR échoue également aux tests d’accessibilité, ce qui affecte la compatibilité des lecteurs d’écran. (LC-3922551)
* Lorsqu’un utilisateur ou une utilisatrice effectue le rendu d’une lettre dans l’interface d’utilisation de l’agent, le contenu ne s’affiche pas correctement en raison de l’API FormService.render(). (LC-3922461)
* Lorsqu’un utilisateur ou une utilisatrice tente de créer des fichiers PDF/A à partir de XDP avec le style Sunken Square dans AEM Forms, cela entraîne des problèmes de rendu des bordures. (LC-3922180)
* L’aplatissement des formulaires dynamiques liés à un schéma XSD entraîne une perte de données partielle, car certaines données de formulaire liées ne sont pas conservées dans le PDF final. (LC-3922008)
* Lorsqu’un utilisateur ou une utilisatrice tente d’exporter des données à partir de PDF interactifs à l’aide de l’API extractData dans AEM Forms 6.5.13 et versions ultérieures, les données sont manquantes par rapport à l’exportation manuelle. (LC-3921983)
* La conversion de formulaires XDP en PDF statiques avec AEM Forms Designer ou le service Output crée plusieurs balises `Link-OBJR`. Ces problèmes provoquent un problème de conformité en matière d’accessibilité, car une seule balise de lien unifié est attendue. (LC-3921977)

### Formulaires adaptatifs

* Dans AEM Forms, l’activation de l’option « Autoriser le texte enrichi pour le titre » sur le panneau racine entraîne une interaction incorrecte avec l’option « Exclure le titre du document de référence » sur un panneau imbriqué, qui masque alors à tort le titre du panneau racine. Ce comportement se produit dans le document de référence généré. (FORMS-19696)
* Le système ignore le `sling:resourceType` personnalisé attribué par le biais d’`aem:afProperties` dans un schéma JSON. Le type de ressource personnalisée est ignoré lors du rendu. (FORMS-19691)
* Lorsqu’une personne envoie un formulaire adaptatif avec des pièces jointes préremplies à l’aide d’URI, l’envoi du formulaire échoue avec une NullPointerException en raison de données binaires manquantes. (FORMS-19371) (FORMS-19486)
* Lorsqu’une personne charge un PDF sous la section « Formulaires et documents », la fonction de chronologie cesse de fonctionner. (FORMS-19407) (FORMS-19234)
* Lorsqu’une personne charge des fichiers à l’aide du composant de pièce jointe prêt à l’emploi dans AEM Forms, des vulnérabilités en matière de sécurité sont identifiées. Le problème peut entraîner l’interception du processus de soumission par des entités non autorisées. (FORMS-19271)
* Lorsqu’un utilisateur ou une utilisatrice configure un formulaire adaptatif standard dans AEM Forms pour générer automatiquement un document de référence, le champ « Titre » dans les propriétés du document d’Acrobat Reader n’affiche pas le titre capturé du document de référence. Par défaut, le titre du formulaire ne remplace pas le nom de fichier. (FORMS-19263)
* Lorsqu’une personne ouvre une communication interactive dans l’interface d’utilisation de l’agent, les données préremplies ne peuvent pas être complètement effacées ; une fois supprimées, elles sont automatiquement remplies avec les mêmes données. (FORMS-19151)
* Lorsqu’un utilisateur ou une utilisatrice prévisualise un champ de type date dans l’interface Agent, la date change de façon inattendue. Le problème est causé par des différences de fuseau horaire entre le paramètre UTC de la machine virtuelle et l’interprétation locale de la date par le système. (FORMS-19115)
* Lorsqu’un utilisateur ou une utilisatrice soumet un formulaire, les pièces jointes peuvent être dupliquées, entraînant plusieurs envois du même fichier. (FORMS-19045)(FORMS-19051).
* L’ajout de coordinateurs et coordinatrices aux ensembles de politiques dans Document Security échoue dans les environnements de production et inférieurs. (FORMS-18603, FORMS-18212, FORMS-19697)
* Lorsqu’une personne clique sur « datepicker-calendar-icon » en mode bureau avec un champ vide, une erreur se produit en raison de la variable _$focusedDate non définie, interrompant les scripts personnalisés associés. (FORMS-18483)(FORMS-18268)
* Lorsqu’un client ou une cliente prévisualise une lettre, le champ « Montant en mots » ne s’affiche pas correctement ou ne met pas à jour correctement les valeurs numériques, ce qui entraîne un mauvais alignement et des espaces manquants dans le contenu. (FORMS-18437, FORMS-17330, FORMS-18209, FORMS-18557, CTG-4150848,FORMS-19614, LC-3922004)
* Lorsqu’un client ou une cliente prévisualise une lettre enregistrée sur RHEL, le contenu ne s’aligne pas correctement, des espaces sont manquants et des caractères inattendus tels que « x » apparaissent. (FORMS-18422)(FORMS-17641).
* Lorsqu’une personne navigue entre les onglets d’AEM Forms, la sélection de composants dans le premier onglet ne répond plus. (FORMS-18345)
* Lorsqu’une personne convertit un fichier HTML en PDF à l’aide de l’option WebToPDF, la section d’en-tête est manquante dans le PDF de sortie, y compris les balises de métadonnées et de titre. (FORMS-18223, FORMS-17835, FORMS-19642, FORMS-18224)
* Dans le SDK du gestionnaire de processus AEM JEE, lorsqu’une personne appelle la méthode retryAction(long actionOid), le système tente à nouveau, de manière incorrecte, la première action trouvée dans la table tb_action_instance. Ce workflow se produit même lorsqu’un identifiant d’action spécifique est fourni, ou lorsqu’il est nul, ce qui engendre des effets inattendus. (FORMS-18187)
* L’utilisateur ou l’utilisatrice rencontre des problèmes : les fonctions d’enregistrement des brouillons et de soumission échouent sans afficher de message d’erreur. (FORMS-18069)
* La transition des composants de base basés sur XSD vers les composants principaux empêche l’implémentation de références entre fichiers dans les schémas JSON, ce qui a un impact sur la migration des formulaires adaptatifs. (FORMS-18065)
* Lorsqu’une personne prévisualise une lettre dans l’interface d’utilisation de l’agent, le champ de date affiche une valeur incorrecte en raison de problèmes de conversion d’heure IC (communication interactive). Ces dysfonctionnements sont liés à des écarts de fuseau horaire entre l’environnement VM et l’interprétation de l’heure par le système (UTC contre heure locale). (FORMS-17988) (FORMS-17248)
* Lorsqu’une personne prévisualise des lettres à l’aide de modèles Notice IC dans AEM Forms, les délais de génération de PDF varient considérablement, passant de 1,5 seconde à plus de 10 secondes, même sur le même serveur. Cette incohérence affecte les workflows critiques de l’entreprise. (FORMS-17951)
* Lorsqu’un utilisateur ou une utilisatrice associe un objet de signature manuscrite (Scribble Signature) dans un formulaire adaptatif à un XDP via l’option « Sources de données », les modifications ne peuvent pas être enregistrées. Cela est dû à des erreurs persistantes de validation du ratio d’aspect, même avec des valeurs valides. (FORMS-17587)
* Lorsqu’un utilisateur ou une utilisatrice utilise un XDP spécifique contenant de nombreux champs masqués pour les fragments de document, AEM crée des nœuds CRX avec la propriété `cm:optional` définie sur faux, ce qui entraîne l’échec de la soumission dans communication interactive (IC). (FORMS-17538)
* Lorsqu’un client ou une cliente prévisualise une lettre, le champ de zone numérique ne gère pas correctement les valeurs négatives lorsque des limites numériques pour Lead et Frac sont définies. Ce problème se produit en raison de l’utilisation de parseFloat, qui traite le signe moins comme faisant partie du nombre. (FORMS-17451)
* Lors de la prévisualisation d’une lettre, la présence du caractère générique « * » dans le fichier Adobe.json est détectée, ce qui soulève des interrogations quant à son utilité et aux risques liés à sa modification. (FORMS-17317)
* Lorsqu’une personne utilise un lecteur d’écran dans « Demander un compte joint d’épargne à taux fixe », les en-têtes sont annoncés à tort comme « cliquables », ce qui entraîne des problèmes d’accessibilité. (FORMS-17038)
* Lorsqu’un formulaire est incorporé, il manque un attribut de titre à l’iframe généré, ce qui entraîne un problème de conformité en matière d’accessibilité. (FORMS-17010)
* Le téléchargement d’un formulaire depuis l’interface Forms Manager inclut toujours les dépendances associées, telles que les thèmes et les fragments. (FORMS-15811)
* Lorsqu’un utilisateur ou une utilisatrice accède au formulaire sur un appareil mobile (iOS ou Android™), les boutons « Suivant » et « Précédent » de la première page sont désactivés. Toutefois, le lecteur d’écran ne les identifie pas comme tels. (FORMS-15773)
* Lorsqu’une personne enregistre un formulaire volumineux avec des fragments et un chargement différé activés, la récupération des brouillons échoue, ce qui perturbe le workflow. (FORMS-19890, FORMS-19808)
* Certaines personnes ont rencontré des problèmes lors de l’enregistrement des propriétés du formulaire adaptatif basé sur les composants principaux. Cette erreur est due au fait que des scripts redondants issus de l’éditeur de formulaire adaptatif basé sur les composants principaux sont inclus, ce qui entraîne des conflits dans le formulaire adaptatif. éditeur. (FORMS-17474)
* Certaines personnes ont rencontré des problèmes avec la page de signature Adobe Sign GovCloud qui ne s’affichait pas dans un iframe. (FORMS-16803)
* Certaines personnes ont rencontré des erreurs lors de la sélection des références pour les fragments de formulaire adaptatif basé sur les composants principaux. Le message d’erreur « Impossible de rendre la référence : il ne s’agit pas d’un chemin absolu » s’est affiché, empêchant le rendu correct des références. (FORMS-19678)
* Ajout de la prise en charge de la conversion multithread avec Acrobat DC, ce qui permet aux utilisateurs et aux utilisatrices d’effectuer plus efficacement des conversions simultanées de documents Word, Excel et PowerPoint en documents PDF. (FORMS-21310)
* Ajout de l’inclusion de l’offre groupée `com.adobe.granite.toggle.impl.dev` dans le pack de services 24 d’AEM, permettant des processus de développement plus rationnels en le supprimant du module complémentaire Forms. (FORMS-20139)
* Suppression de FeatureToggleRenderConditionServlet de forms-foundation et de l’offre groupée com.adobe.granite.toggle.impl.dev du module complémentaire Forms. Cette mise à jour garantit qu’après l’installation du module complémentaire Forms, la condition de rendu est correctement résolue, améliorant ainsi les fonctionnalités du composant pour la clientèle. (FORMS-20138)
* Les utilisateurs et les utilisatrices ont connu des performances lentes en raison de requêtes longues dans les formulaires adaptatifs. Cette mise à jour rétroporte les modifications de requête afin d’améliorer l’efficacité. Les clientes et les clients peuvent désormais créer un index avec pour nom de balise aemformsAFReferences. (FORMS-21411)
* Les utilisateurs et les uont présenté des positions d’en-tête incorrectement alignées lors de la conversion d’HTML au format de document portable (PDF) avec WebtoPDF. Ce problème affectait la cohérence de la mise en page du document et la lisibilité de la sortie. (FORMS-21502, FORMS-21540)
* Les utilisateurs et les utilisatrices ont connu des échecs de validation PDF/A-1b malgré la réussite de la vérification Preflight. Ce problème affectait les contrôles de conformité des documents destinés à la clientèle Enterprise utilisant des outils de validation PDF. (FORMS-20196)
* Les utilisateurs et les utilisatrices rencontraient des chaînes non traduites dans l’interface d’utilisation, ce qui entraînait une confusion et des difficultés de compréhension de l’interface. (FORMS-6542)
* Les utilisateurs et les utilisatrices expérimentaient des problèmes liés aux notifications par e-mail. L’étape de workflow Envoyer un e-mail a échoué à envoyer les messages, ce qui perturbait les processus de communication automatisés. (FORMS-17961)
* Les tests des workflows de formulaires ont échoué, ce qui affectait la capacité des utilisateurs et des utilisatrices à exécuter efficacement les processus de workflow. (FORMS-16231)
* Les utilisateurs et les utilisatrices n’ont pas pu utiliser la fonctionnalité de chronologie des fichiers PDF dans les formulaires AEM. Ce problème a affecté la capacité des utilisateurs et des utilisatrices à suivre efficacement les modifications et les révisions de documents. Lors du chargement d’un PDF dans la section Formulaires et documents de l’espace AEM Forms, l’affichage de la chronologie cessait de fonctionner. (FORMS-19408)
* Les utilisateurs et les utilisatrices rencontrent une exception de pointeur nul lors de l’interaction avec OData. Cela entraîne des interruptions dans les processus de récupération des données. (FORMS-20348)
* Suppression de la bibliothèque google.common.collect suite à la suppression de Guava, une bibliothèque Java open source. Cette mise à jour garantit une meilleure compatibilité et de meilleures performances pour la clientèle Enterprise qui utilise Adaptive Forms. (FORMS-17031)
* Lorsque la validation côté serveur (SSV) est activée, les envois de formulaires peuvent échouer. Si vous rencontrez ce problème, contactez l’assistance [d’Adobe](https://business.adobe.com/in/support/main.html) pour obtenir de l’aide. (FORMS-21966)

### Captcha de formulaires

* Ajout de la prise en charge de `Hcaptcha` et de `Turnstile` pour les formulaires adaptatifs basés sur les composants de base. (FORMS-16562)
* Les utilisateurs et les utilisatrices ont rencontré des problèmes d’éléments qui se chevauchent dans la boîte de dialogue `Create hCaptcha Configuration`. Lors du remplissage des champs obligatoires, l’icône d’information chevauchait l’icône d’erreur, ce qui entraînait une confusion pendant la configuration. (FORMS-16916)
* Les utilisateurs et les utilisatrices ont constaté qu’une configuration incorrecte était appliquée à reCAPTCHA dans les formulaires adaptatifs basés sur les composants de base. Lorsque le conteneur de configuration n’était pas sélectionné pour un formulaire, plusieurs configurations présentes dans le dossier `conf/global` provoquaient le problème. (FORMS-19237)
* Les utilisateurs et les utilisatrices ont rencontré des problèmes avec reCAPTCHA qui n’était pas rendu. Cela affectait les envois de formulaires et la validation de la sécurité pour la clientèle Enterprise. (FORMS-17136, FORMS-19596)
* Les utilisateurs et les utilisatrices rencontrent un problème où la taille de reCAPTCHA Enterprise n’est pas reflétée dans l’interface utilisateur. (FORMS-16574)
* Les utilisateurs et les utilisatrices ont rencontré des problèmes avec la fonctionnalité ReCaptcha en raison d’un ResourceResolver non fermé dans `ReCaptchaConfigurationServiceImpl`, ce qui provoquait des échecs de validation intermittents lors des envois de formulaire. (FORMS-19241)
* Les utilisateurs et les utilisatrices ont rencontré des problèmes de validation reCAPTCHA lors de la création de formulaires dans Sites. Les formulaires AEM ne reconnaissaient pas correctement le nom du formulaire, ce qui provoquait des échecs de validation. (FORMS-20486)
* Les utilisateurs et les utilisatrices ont pu soumettre des formulaires même lorsque le score reCAPTCHA Enterprise était de 1,0, ce qui entraînait des risques potentiels pour la sécurité. (FORMS-16766){{$include }}
* Amélioration des alertes reCAPTCHA dans les formulaires adaptatifs en mettant à jour les codes d’erreur d’envoi à 400. En outre, les alertes de journal ont été affinées pour faire la distinction entre les délais d’expiration, les expirations, les échecs de détection des robots et pour améliorer la précision du dépannage et l’observabilité du système. (FORMS-19240)
* Fermeture d’une instance ResourceResolver restée ouverte dans ReCaptchaConfigurationServiceImpl afin d’éviter des fuites potentielles de ressources et d’améliorer la stabilité du système lors de l’utilisation des intégrations reCAPTCHA dans les formulaires AEM. (FORMS-19242)
* Amélioration de la gestion de la configuration CAPTCHA pour les formulaires AEM en garantissant que la configuration correcte est associée à chaque formulaire lorsque plusieurs entrées existent dans le dossier /conf/global. Empêche l’utilisation involontaire de paramètres CAPTCHA incorrects lorsque le conteneur de configurations n’est pas explicitement sélectionné. (FORMS-19239)

### Interface d’utilisation de gestion des formulaires

* Les utilisateurs et les utilisatrices ont rencontré des chaînes non localisées dans le processus de création de dossier `Forms` > `Create Watchfolder` > ` Watchfolder`. Lors de la création d’un dossier de contrôle, des chaînes telles que `Watchfolder creation` et `Watchfolder created successfully` étaient introuvables, ce qui affectait l’expérience de l’interface d’utilisation. (FORMS-15234)

## [!DNL Experience Manager Foundation] {#experience-manager-foundation}

La plateforme d’[!DNL Adobe Experience Manager] 6.5 LTS repose sur les versions mises à jour de l’architecture OSGi (Apache Sling et Apache Felix), ainsi que sur le référentiel de contenu Java™ : Apache Jackrabbit Oak 1.68.x.

Eclipse Jetty 11.0.x est utilisé comme moteur de servlet pour Quickstart.

### Prise en charge de Java™  {#java-support}

* Prise en charge de Java™ 17 et Java™ 21.
* Pour des performances optimales, remplacez les valeurs par défaut du GC par d’autres valeurs. Pour plus d’informations, consultez la section [Installation et mise à jour](/help/sites-deploying/custom-standalone-install.md).
* Adobe distribue des mises à jour de maintenance Java™ 17 et Java™ 21 pour l’utilisation par les clientes et les clients dans les projets liés à AEM, lorsqu’elles ne sont pas disponibles publiquement depuis Oracle.

### Packaging Uberjar {#uber-jar-packaging}

* Il existe une légère différence dans le packaging Uberjar d’AEM 6.5 LTS. Pour plus d’informations, consultez [Mettre à jour la version AEM Uber Jar](/help/sites-deploying/upgrading-code-and-customizations.md#update-the-aem-uber-jar-version).

### Mise à niveau {#upgrade}

* Pour plus d’informations sur la procédure de mise à niveau, consultez la [documentation de mise à niveau](/help/sites-deploying/upgrade.md).

#### Bonnes pratiques relatives aux mises à niveau du pack de services d’AEM 6.5 LTS

<!-- THE INFORMATION UNDER THIS HEADING CAME FROM CQDOC-23078 -->

**Environnement**
Application : clients et clientes AEM 6.5 LTS (On-Premise) installant le pack de services 1 (SP1). Le SP1 est fourni sous la forme d’un fichier JAR de démarrage rapide.

**Pourquoi est-ce important**
Le SP1 pour AEM 6.5 LTS est fourni sous la forme d’un fichier JAR de démarrage rapide plutôt que d’un fichier ZIP à installer via le gestionnaire de modules. Les clients et clientes On-Prem effectuent une mise à niveau en remplaçant le fichier JAR de démarrage rapide, en le décompressant et en redémarrant. Cette méthode est conforme à la procédure de mise à niveau statique d’Adobe.

**Flux de mise à niveau recommandé (création ou publication)**

1. Vérifiez que votre instance AEM 6.5 LTS est saine et accessible.
1. Téléchargez le fichier JAR de démarrage rapide du SP1 (par exemple, `cq-quickstart-6.6.x.jar`) à partir de la distribution logicielle.
1. Arrêtez l’instance en cours.
1. Dans le répertoire d’installation d’AEM (en dehors de `crx-quickstart/`), remplacez le fichier JAR de démarrage rapide précédent par le fichier JAR du SP1.
1. Décompressez le fichier JAR :

   ```java
   java -jar cq-quickstart-6.6.x.jar -unpack
   ```

   (Ajustez les indicateurs de tas selon les besoins.)

1. Renommez le fichier JAR décompressé pour qu’il corresponde au rôle et au port, par exemple `cq-author-4502.jar` ou `cq-publish-4503.jar`.
1. Démarrez AEM et confirmez la mise à niveau dans l’interface d’utilisation (Aide > À propos) et les journaux.

**Bonne qualité**

* Exécutez la mise à niveau dans des environnements inférieurs/de test avant la production.
* Effectuez des sauvegardes complètes et restaurables (référentiel et magasins de données externes) avant de commencer.
* Consultez les conseils sur la mise à niveau statique d’Adobe et les exigences techniques (Java 17/21 recommandé pour LTS).

>[!NOTE]
>
>Les noms de fichier indiqués ci-dessus (par exemple, `cq-quickstart-6.6.x.jar`) reflètent le nom de l’artefact de démarrage rapide du SP1 observé pour cette version LTS. Utilisez toujours le nom de fichier exact que vous téléchargez à partir de la distribution logicielle.

## Installation et mise à jour {#install-update}

Pour connaître les exigences de configuration, consultez les [instructions d’installation](/help/sites-deploying/custom-standalone-install.md).

>[!NOTE]
>
> Si vous effectuez une mise à niveau directement vers LTS SP1 à partir d’anciens SP 6.5, suivez les instructions données pour la [mise à niveau](/help/sites-deploying/upgrade.md) 6.5 à 6.5 LTS GA.


Pour obtenir des instructions détaillées, consultez la [documentation de mise à niveau](/help/sites-deploying/upgrade.md).

>[!NOTE]
>
> Pour les nouvelles installations d’AEM 6.5 LTS, les définitions d’index doivent être installées séparément. Pour plus d’informations, consultez [cet article](/help/sites-deploying/pre-upgrade-maintenance-tasks.md#index-definitions).

## Installation et mise à jour du module complémentaire AEM Forms {#install-update-aem-forms-add-on}

Pour obtenir des instructions détaillées, consultez la section [Exécution d’une mise à niveau statique](https://experienceleague.adobe.com/fr/docs/experience-manager-65/content/release-notes/aem-forms-current-service-pack-installation-instructions).



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
| --- | --- | --- | --- |
| Sites | [Éditeur SPA](/help/sites-developing/spa-overview.md) | Les éditeurs recommandés pour la gestion du contenu découplé dans AEM sont les suivants : <br>- [Éditeur universel](/help/sites-developing/universal-editor/introduction.md) pour la modification visuelle.<br>- [Éditeur de fragment de contenu](/help/assets/content-fragments/content-fragments-managing.md) pour la modification basée sur les formulaires. | 6.5 LTS GA |

### Fonctionnalités supprimées {#removed-features}

Cette section répertorie les fonctionnalités qui ont été supprimées dans AEM 6.5 LTS. Ces fonctionnalités étaient signalées comme obsolètes dans les versions antérieures.

| Domaine | Fonctionnalité | Remplacement | Version (SP) |
| --- | --- | --- | --- |
| Commerce | AEM CIF Classic n’est pas pris en charge. | Migrez vers [AEM CIF](/help/commerce/cif/migration.md). | 6.5 LTS GA |
| Solutions | Social/Communities n’est pas pris en charge. | Aucun remplacement n’est disponible. | 6.5 LTS GA |
| Screens | Screens n’est pas pris en charge. | Aucun remplacement n’est disponible. | 6.5 LTS GA |
| Assets | `dam-pim` et `dam-rating` ne sont pas pris en charge, car les lots dépendent de Social. | Aucun remplacement n’est disponible. | 6.5 LTS GA |
| Assets | `com.day.cq.dam.scene7.api.model.Scene7ViewerConfig#getSettings()` a été supprimé. | Utilisez l’autre API `com.day.cq.dam.scene7.api.model.Scene7ViewerConfig#getSettingsList()` qui a été ajoutée. | 6.5 LTS GA |
| Portail | AEM Portal Director n’est pas pris en charge. | Aucun remplacement n’est disponible. | 6.5 LTS GA |
| Granite | Le lot `com.adobe.granite.socketio` est supprimé. | Aucun remplacement n’est disponible. | 6.5 LTS GA |
| Granite | `com.adobe.granite.crx-explorer` n’est pas pris en charge. | Aucun remplacement n’est disponible. | 6.5 LTS GA |
| Granite | `crx2oak` n’est pas pris en charge. | Sélectionnez la version appropriée d’[Oak-upgrade](https://mvnrepository.com/artifact/org.apache.jackrabbit/oak-upgrade). | 6.5 LTS GA |
| Adobe | `com.adobe.cq.cq-searchpromote-integration` n’est pas pris en charge. | Aucun remplacement n’est disponible. | 6.5 LTS GA |
| Guava | Toutes les dépendances guava sont désormais supprimées dans AEM. Par conséquent, le lot `com.adobe.granite.osgi.wrapper.guava-15.0.0-0002` ne fait pas partie d’AEM. | La clientèle peut ajouter Guava elle-même si elle en dépend ou remplacer le code Guava par des collections Java ou d’autres alternatives si possible. | 6.5 LTS GA |
| `We.Retail` | L’exemple de site `We-retail` n’est pas pris en charge. | Aucun remplacement n’est disponible. | 6.5 LTS GA |
| Open Source | Le lot `oak-solr-osgi` n’est pas pris en charge. | Aucun remplacement n’est disponible. | 6.5 LTS GA |
| Open Source | `org.apache.servicemix.bundles.abdera-parser`, `org.apache.servicemix.bundles.jdom` et `org.apache.sling.atom.taglib` ne sont pas pris en charge. | Aucun remplacement n’est disponible. | 6.5 LTS GA |
| Open Source | Les packages `org.apache.commons.io` sont désormais exportés depuis `org.apache.commons.commons-io`. | Aucune modification n’est requise. | 6.5 LTS GA |
| Open Source | Les packages `javax.mail` sont exportés à partir du lot `com.sun.javax.mail`. | Aucune modification n’est requise. | 6.5 LTS GA |
| Open Source | Les packages `org.apache.jackrabbit.api` sont désormais exportés à partir du lot `org.apache.jackrabbit.oak-jackrabbit-api` . | Aucune modification n’est requise. | 6.5 LTS GA |
| Open Source | `com.github.jknack.handlebars` n’est pas pris en charge. | Sélectionnez la [version](https://mvnrepository.com/artifact/com.github.jknack/handlebars) appropriée. | 6.5 LTS GA |


## Problèmes connus {#known-issues}

<!-- DO THESE KNOWN ISSUES CARRY OVER EACH RELEASE? THE "PRODUCT UPDATES TEAM" IS SUPPOSED TO VERIFY EACH ISSUE AND LET YOU KNOW IF ANYTHING NEEDS TO BE ADDED, DELETED, OR CHANGED IN THIS LIST. -->


### Échec de connexion à Dispatcher avec la fonction SSL uniquement (corrigé dans AEM 6.5 LTS SP1 et versions ultérieures){#ssl-only-feature}

>[!NOTE]
>
> Ce problème est uniquement présent dans la version AEM 6.5 LTS en disponibilité générale.

Lors de l’activation de la fonction SSL uniquement dans les déploiements AEM, un problème connu affecte la connectivité entre les instances Dispatcher et AEM. Une fois cette fonctionnalité activée, les contrôles d’intégrité peuvent échouer et la communication entre les instances Dispatcher et AEM peut être interrompue. Ce problème se produit plus particulièrement lorsque les clientes et clients tentent de se connecter via `https + IP` à partir des instances Dispatcher vers AEM. Il est lié aux problèmes de validation SNI (Server Name Indication).

**Impact :**

* Échec des contrôles d’intégrité avec les codes de réponse HTTP 400
* Trafic rompu entre les instances Dispatcher et AEM
* Contenu diffusé incorrectement via Dispatcher
* Échecs de connexion lors de l’utilisation de HTTPS avec des adresses IP dans la configuration Dispatcher
* Erreurs HTTP 400 « SNI non valide » lors de la connexion via HTTPS + IP

**Environnements affectés :**

* Déploiements d’AEM avec les configurations Dispatcher
* Systèmes sur lesquels la fonction SSL uniquement a été activée
* Configurations Dispatcher utilisant la méthode de connexion `https + IP` aux instances AEM

**Solution :**
Si vous rencontrez ce problème, contactez l’Assistance Client d’Adobe. Un correctif [cq-6.5.lts.0-hotfix-CQ-4359803](https://experience.adobe.com/#/downloads/content/software-distribution/fr/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq660/hotfixes/cq-6.5.lts.0-hotfix-CQ-4359803-1.0.2.zip) est disponible pour résoudre ce problème. N’essayez pas d’activer les fonctions SSL uniquement avant d’avoir appliqué le correctif nécessaire.

### Page Autorisations vide dans l’interface utilisateur de sécurité d’AEM 6.5 LTS SP1

>[!NOTE]
>
> Ce problème est uniquement présent dans la version AEM 6.5 LTS SP1.

Lors de l’accès à la page Autorisations sous Outils -> Sécurité dans AEM 6.5 LTS SP1, une page vierge s’affiche au lieu des autorisations d’un utilisateur ou d’un groupe.

**Solution :**
Un correctif [cq-6.5.lts.1-hotfix-GRANITE-62993-1.0.zip](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq660/hotfixes/cq-6.5.lts.1-hotfix-GRANITE-62993-1.0.zip) est disponible pour résoudre ce problème.

### Forms JEE

* Les utilisateurs des environnements Linux peuvent rencontrer des échecs de script du programme d’installation ou de Configuration Manager (LCM) en raison de terminaisons de ligne de type Windows. Convertissez tous les fichiers .sh à l’aide de dos2unix avant d’exécuter le programme d’installation ou LCM pour éviter les erreurs d’exécution.

## Lots OSGi et modules de contenu inclus{#osgi-bundles-and-content-packages-included}

Les documents texte suivants répertorient les offres groupées OSGi et les modules de contenu inclus dans cette version d’[!DNL Experience Manager] 6.5 LTS, Pack de services 1.

* [Liste des offres groupées OSGi incluses dans Experience Manager 6.5 LTS, Pack de services 1](/help/release-notes/assets/65lts_sp1_bundles.txt) <!-- UPDATE FOR EACH NEW RELEASE -->
* [Liste des packages de contenu inclus dans Experience Manager 6.5 LTS, Pack de services 1](/help/release-notes/assets/65lts_sp1_packages.txt) <!-- UPDATE FOR EACH NEW RELEASE -->

## Sites web à accès limité{#restricted-sites}

Ces sites Web sont disponibles uniquement pour les clients. Si vous êtes client et avez besoin d’un accès, contactez votre responsable de compte Adobe.

* [Téléchargement du produit à l’adresse licensing.adobe.com](https://licensing.adobe.com/)
* [Contacter l’assistance clientèle Adobe](https://experienceleague.adobe.com/fr/docs/customer-one/using/home).

