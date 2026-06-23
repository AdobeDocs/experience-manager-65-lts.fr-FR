---
title: Notes de mise à jour actuelles pour Adobe Experience Manager 6.5 LTS, SP2
description: Recherchez les informations de mise à jour actuelles pour Adobe Experience Manager 6.5 LTS, pack de services 2.
solution: Experience Manager
feature: Release Information
role: User,Admin,Developer
exl-id: b5a8f555-c061-4fe2-a100-cc01335959cb
source-git-commit: d2484f59e701a30a9b8f62ab308b7e5993c53694
workflow-type: tm+mt
source-wordcount: '7743'
ht-degree: 96%

---


# Notes de mise à jour actuelles pour Adobe Experience Manager 6.5 LTS, SP2 {#release-notes}

## Informations sur la version {#release-information}

| Produit | [!DNL Adobe Experience Manager] 6.5 LTS |
|---|---|
| Version | Pack de services 2 (SP2) <!-- UPDATE FOR EACH NEW RELEASE --> |
| Type | Mise à jour du pack de services |
| Date | 19 février 2026 <!-- UPDATE FOR EACH NEW RELEASE --> |
| URL de téléchargement | [Distribution logicielle](https://experience.adobe.com/#/downloads/content/software-distribution/fr/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/servicepack-lts/cq-quickstart-6.6.2.jar) |


<!-- UPDATE ABOVE FOR EACH NEW RELEASE -->

>[!IMPORTANT]
>
> **Correctif obligatoire** - Pour éviter des problèmes SNFE (SegmentNotFoundException) liés à la compression hors ligne lors de l’installation du SP2, installez le correctif décrit dans [Problèmes connus – Corruption du référentiel lors de la compression en ligne](#repository-corruption-during-online-compaction-after-offline-compaction-granite-65146).

## Éléments inclus dans [!DNL Adobe Experience Manager] 6.5 LTS, SP2 {#what-is-new}

<!-- UPDATE EACH RELEASE -->

[!DNL Experience Manager] 6.5 LTS, SP2 comprend de nouvelles fonctionnalités, des améliorations importantes demandées par la clientèle, ainsi que correctifs. Cette version comprend également des améliorations en termes de performances, de stabilité et de sécurité, publiées depuis la mise à disposition initiale de la version 6.5 LTS en mars 2025. [Installez ce Pack de services](#install-update) sur la version 6.5 LTS.

## Fonctionnalité clé et amélioration

**AEM Sites**

AEM 6.5 LTS SP2 comprend désormais des API OpenAPI pour [la gestion de modèles et de fragments de contenu](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/stable/sites/65lts/) et [les lancements](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/stable/sites/launches/). Ces API permettent d’accéder aux fragments de contenu et aux lancements pour la création et la planification. Elles utilisent les mêmes API OpenAPI modernes qu’AEM as a Cloud Service.

**AEM Forms**

**Éléments compris dans AEM Forms 6.5 LTS SP2**

* Nouvelle prise en charge de RDBMK avec JBoss® EAP 8.0.

* Ajout de la prise en charge de WebSphere® Liberty Profile (WLP). WLP est pris en charge uniquement avec Oracle Database et IBM® Sumeru JDK 21.

* Amélioration de l’expérience d’utilisation dans l’éditeur visuel de règles. Cette mise à jour inclut les fonctionnalités suivantes :

   * Rechargement automatique de la vue récapitulative après un enregistrement pour afficher le statut de la règle mis à jour

   * Affichage des boutons (bascule) Ajouter et Supprimer au lieu de les masquer

   * Envoi de commentaires clairs lorsqu’une opération d’enregistrement de règle échoue. (FORMS-21261)

* Ajout de l’interface API (interface de programmation d’applications) Runtime pour activer/désactiver le mode d’export hérité du langage XML (Extensible Markup Language) dans AEM Forms, en remplaçant le paramètre `Dcom.adobe.fd.forms.export.legacy`. Cette amélioration permet de changer de mode d’export plus efficacement et ainsi d’améliorer la flexibilité du workflow. (FORMS-23115)

* Ajout de la prise en charge de JSON (JavaScript Object Notation) avec les balises d’espace de noms dans les formulaires adaptatifs. Cette amélioration permet de gérer plus efficacement les structures de données JSON, afin d’améliorer les fonctionnalités d’intégration et de traitement des données. (FORMS-22519)

* Ajout du bouton Télécharger le document de référence (DoR) / l’envoi du formulaire OOTB (prêt à l’emploi) dans l’éditeur de règles. Cette amélioration permet d’utiliser la fonction downloadDoR sans écrire de code personnalisé, ce qui améliore la convivialité et l’efficacité. (FORMS-21263)

* Ajout de la prise en charge de JSON (JavaScript Object Notation) avec les balises d’espace de noms dans les formulaires adaptatifs. Cette amélioration permet aux utilisateurs et utilisatrices de préremplir les formulaires de manière plus précise et plus efficace, pour une meilleure intégration des données et une réduction des erreurs de saisie manuelle. (FORMS-10883)

<!-- UPDATE THE EACH RELEASE -->

## Problèmes corrigés dans la version 6.5 LTS, Pack de services 2 {#fixed-issues}

### [!DNL Sites]{#sites-65-LTS-SP2}

#### Accessibilité {#sites-accessibility-65-lts-sp2}

* Le composant Texte perdait le focus au clavier lorsque les créateurs et créatrices plaçaient le pointeur de la souris sur des éléments du navigateur de composant lors de la modification. Ce problème perturbait la saisie et déclenchait un échec d’accessibilité conformément à WCAG 3.2.1. Ce correctif empêche le déplacement du focus lors du survol et maintient le composant Texte actif lors de l’interaction avec l’explorateur de composant. (SITES-35370)
* Correction du problème de gestion du focus dans le champ de texte enrichi Description qui empêchait la navigation vers l’avant avec la touche de tabulation. L’éditeur de texte enrichi se bloquait, car le composant utilisait une commande clavier non standard pour déplacer le focus, ce qui interrompait la navigation prévue dans la boîte de dialogue. Le correctif permet d’appliquer l’interaction clavier standard et conserve l’enchaînement logique des onglets dans toute la boîte de dialogue. (SITES-35228)
* Correction d’un problème dans l’éditeur Sites qui perturbait le comportement attendu lors de la création de pages et entraînait une interaction incohérente des composants. Les réponses de l’interface d’utilisation étaient peu fiables, interféraient avec les tâches de modification standard et réduisaient l’efficacité des workflows. La mise à jour affine la logique de l’éditeur sous-jacent et restaure une interaction stable et prévisible entre les composants affectés. (SITES-35227)
* Une régression interrompait le sélecteur de ressources dans l’éditeur de page et l’empêchait de se charger dans des scénarios spécifiques de modification de page. Il est désormais possible d’ouvrir et d’utiliser normalement le sélecteur de ressources lors de la sélection ou de l’exploration de ressources à l’étape de modification d’une page. Cette modification restaure un accès cohérent aux workflows de sélection de ressources qui ne parvenaient pas à se charger correctement. (SITES-35226)
* Suppression d’un problème dans l’éditeur Sites qui provoquait un comportement incohérent lors de l’interaction avec la page et perturbait les workflows de création standard. Ce défaut entraînait des réponses inattendues de l’interface d’utilisation qui interféraient avec la configuration des composants et les mises à jour de contenu. La mise à jour stabilise les fonctionnalités affectées et restaure l’exécution fiable des actions de modification sur plusieurs pages. (SITES-35225)
* Suppression d’un défaut dans l’interface de création de Sites qui provoquait un comportement incohérent lors de la modification des pages et perturbait les workflows standard. L’interface d’utilisation renvoyait des réponses inattendues qui interféraient avec l’interaction des composants et les mises à jour de contenu. La mise à jour stabilise les fonctionnalités affectées et restaure un comportement fiable et prévisible dans tous les scénarios de modification. (SITES-35224)
* AEM Sites inclut désormais la prise en charge de texte `alt` sur les images pour répondre aux exigences ADA et WCAG. La sortie de page n’omet plus les attributs `alt`, de sorte que les lecteurs d’écran reçoivent un texte secondaire correct. (SITES-27153)
* Correction de la disposition de la barre d’outils `Note Add` afin que le bouton Ajouter ne chevauche plus le titre à une largeur de fenêtre d’affichage de 320 px. Amélioration de la redistribution sur petit écran afin que les commandes restent lisibles et utilisables à un zoom de 400 %. (SITES-25376)
* Correction des annonces de lecteurs d’écran manquantes pour les erreurs de boîte de dialogue de sélection de lien. L’interface d’utilisation publie désormais le texte d’erreur par le biais d’un conteneur de messages de statut, de sorte que NVDA lit le message dès qu’il s’affiche. (SITES-25368)
* Suppression des rôles de grille ARIA et de cellule de grille de la liste des ressources du rail latéral. Restauration de la sémantique de liste standard et de l’ordre de focus au clavier, ce qui permet d’améliorer la navigation du lecteur d’écran et réduit les arrêts supplémentaires dans les onglets. (SITES-25361)
* Correction du séquencement du focus dans le rail latéral Ressources. Utilisez uniquement le clavier pour accéder à toutes les actions sur les ressources, y compris Modifier, via un chemin de tabulation cohérent. (SITES-25360)
* Correction du dépassement de la disposition dans la fenêtre contextuelle Recherche de ressources à une largeur de fenêtre d’affichage de 320 px. Le contenu de la fenêtre contextuelle est désormais redistribué et reste lisible, de sorte que les contrôles ne se chevauchent plus ou ne dépassent plus la boîte de dialogue. (SITES-25330)
* Correction de la sortie NVDA pour le bouton Modifier. NVDA annonce maintenant l’action Modifier, et non le « bouton Aperçu activé ». (SITES-25320)
* Correction des saisies de texte de la barre d’outils Démographies sans nom qui provoquaient une sortie de lecteur d’écran silencieuse ou générique. Chaque entrée expose désormais un nom accessible clair basé sur des libellés, ce qui améliore la navigation au clavier et avec les technologies d’assistance. (SITES-25316)
* Correction de l’ordre de focus au clavier de la barre d’outils Démographique pendant la navigation de la Prévisualisation de la disposition. La navigation tabulaire passe désormais directement du bouton Démographique aux commandes de la barre d’outils, sans passer à la barre d’outils secondaire. (SITES-25305)
* Correction d’un ordre d’annonce incorrect pour les libellés Écrans plus petits et Tablette sur la règle Modifier la disposition. Les lecteurs d’écran annoncent maintenant ces libellés aux marqueurs de règle appropriés, qui correspondent à la mise en page. (SITES-25291)
* Correction du dépassement de la barre d’outils Modifier la disposition à un zoom de 200 %. Le contenu reste désormais dans la fenêtre d’affichage et reste accessible par défilement. (SITES-25288)
* Résolution d’un ordre de focus incorrect dans la superposition Annotations. La tabulation au clavier permet désormais de faire défiler les contrôles de superposition et les éléments d’annotation. La page parente n’a plus le focus derrière la superposition. (SITES-25282)
* Correction de la gestion du focus de la fenêtre contextuelle Nuanciers. La boîte de dialogue déplace désormais le focus vers un en-tête clair et démarre la sortie du lecteur d’écran à ce point d’entrée. NVDA ne lit plus le contenu complet de la boîte de dialogue hors séquence. (SITES-25275)
* Correction de la gestion du focus de la fenêtre contextuelle Distorsion du temps après la fermeture du sélecteur de date. `Escape` retourne désormais au bouton Sélecteur de date. La sélection de la date place désormais le focus sur le champ de saisie en regard du contrôle du sélecteur de date, ce qui empêche la perte de focus et l’accès à la page d’arrière-plan. (SITES-25264)
* Correction de la gestion du focus au clavier pour la boîte de dialogue Supprimer l’annotation. L’action Annuler renvoie désormais le focus sur la commande `Delete` qui a ouvert la boîte de dialogue, et non sur la commande Confirmer la valeur hexadécimale. Les lecteurs d’écran n’annoncent plus le contenu de boîte de dialogue sans rapport après l’action Annuler. (SITES-25258)
* Correction de la gestion du focus pour la boîte de dialogue contextuelle Annotation. L’ouverture de la boîte de dialogue permet désormais de placer le focus sur l’en-tête de boîte de dialogue et empêche NVDA de lire le contenu de la zone de travail et le texte de boîte de dialogue sans rapport. La navigation au clavier reste désormais dans la boîte de dialogue jusqu’à la fermeture. (SITES-25257)
* Correction de problèmes de disposition de la fenêtre contextuelle Recherche à une largeur de 320 px. Le contenu de la fenêtre contextuelle se redistribue désormais proprement et évite les chevauchements avec le répertoire de l’arborescence. Il est désormais possible d’afficher les résultats et de naviguer dans le répertoire sans contrôles masqués. (SITES-25246)
* Le texte modal de recherche n’est plus tronqué après l’augmentation de l’espacement. La disposition arborescente conserve désormais une séparation nette, de sorte que les libellés et les entrées restent lisibles. Il est désormais possible d’effectuer des recherches et de naviguer sans chevauchement ni coupure de texte. (SITES-25245)
* L’activation de l’Annotation déplace désormais le focus au clavier dans le contenu de l’annotation, et non pas sur le bouton Quitter l’annotation. L’ordre de tabulation suit une séquence logique et permet d’atteindre les commandes associées sans navigation inversée. (SITES-25241)
* Les liens Définir la date et Quitter la distorsion du temps ne comportaient pas d’indicateur de focus visible lors de la navigation au clavier. L’interface d’utilisation affiche désormais un style de focus distinct et à fort contraste pour pouvoir identifier le lien actif en un coup d’œil. (SITES-25232)
* L’en-tête contextuel du teaser ne bloque plus le déplacement de la boîte de dialogue à l’aide du clavier. Les commandes au clavier permettent désormais de saisir, déplacer et déposer des éléments, ce qui améliore la convivialité et la maniabilité globale des lecteurs d’écran. (SITES-25226)
* AEM utilise désormais un libellé accessible et significatif pour le bouton Informations contextuelles du teaser. Les lecteurs d’écran annoncent un nom d’action clair au lieu de la chaîne de texte secondaire de l’icône par défaut. (SITES-25223)
* Les lecteurs d’écran annoncent maintenant l’action correcte lors de l’activation du bouton Modifier. NVDA ne rapporte plus le message « Bouton Aperçu activé », qui entraînait des commentaires trompeurs et une confusion lors de la navigation au clavier. (SITES-25208)
* Le développement du rail de gauche déplace désormais le focus au clavier vers la première commande de ce rail. La séquence de tabulation ne passe plus à la barre d’outils secondaire ou n’apparaît pas dans la liste intermédiaire. Il est désormais donc possible d’accéder au contenu du rail de gauche à l’aide du clavier sans navigation inverse. (SITES-24998)
* Le contenu de la barre d’émulateur de l’appareil reste désormais entièrement visible à une largeur de fenêtre de 320 px. Le texte et les commandes de la barre d’outils sont renvoyés à la ligne au lieu d’être tronqués, ce qui réduit le chevauchement et améliore la lisibilité. (SITES-24953)
* AEM affiche désormais le libellé complet de l’appareil iPhone dans la barre d’outils de l’émulateur. Le texte n’est plus tronqué à la largeur par défaut, ce qui améliore la lisibilité et la clarté de sélection des appareils. (SITES-24952)
* Les en-têtes de tableau de vue Liste exposent désormais l’état de tri via ARIA. Les lecteurs d’écran annoncent un ordre croissant ou décroissant après une action de tri des colonnes. (SITES-24943)
* AEM conserve désormais la visibilité des libellés du menu Autres actions en mode Carte lors des modifications de l’espacement du texte. Les options de menu conservent le texte complet, y compris la publication rapide, et le menu reste lisible pendant les paramètres d’espacement du texte WCAG. (SITES-24941)
* La barre de menu Actions de la carte expose désormais un nom accessible en mode Carte. Les lecteurs d’écran annoncent clairement l’objectif de la barre de menus, et le contrôle vocal peut cibler le contrôle par nom. (SITES-24938)
* Le mode Carte ne repose plus sur la sémantique de grille ARIA, ce qui entraînait un comportement déroutant du lecteur d’écran. L’interface d’utilisation fournit désormais des rôles et des libellés significatifs pour le contenu de la carte et la barre d’actions de la carte, ce qui réduit les commandes manquantes lors de l’utilisation du clavier. (SITES-24933)
* L’info-bulle `Delete Modal` s’affiche désormais à chaque survol de l’icône d’infobulle. Les actions de focus affichent désormais le même texte d’infobulle, ce qui améliore l’accès répété lors de l’utilisation de la souris et du clavier. (SITES-24778)
* Le volet de navigation de gauche du rail suit désormais l’ordre de sélection attendu du clavier une fois le rail configuré. Le focus de tabulation se trouve dans la zone du rail de gauche sélectionnée au lieu de l’élément Basculer l’affichage, ce qui améliore la clarté de navigation du lecteur d’écran. (SITES-24754)
* Correction de commentaires NVDA incorrects lors de la navigation par nuance dans la boîte de dialogue contextuelle Préférences d’utilisation. NVDA lit désormais le libellé de la nuance qui reçoit le focus, ce qui supprime la sortie de couleur trompeuse. L’ensemble de nuanciers prend désormais en charge la navigation au clavier cohérente et la reconnaissance claire de la sélection. (SITES-24739)
* Réduction de la verbosité de la sortie NVDA pour la commande `Spin`. Suppression de l’étiquetage de groupe redondant qui dupliquait le libellé d’entrée, de sorte que NVDA annonce le nom de la commande une seule fois. La navigation au clavier et dans le lecteur d’écran affiche désormais une seule annonce claire. (SITES-24725)
* La boîte de dialogue Carrousel place désormais le focus sur l’en-tête de boîte de dialogue au lieu de l’onglet Éléments. Les commandes Annuler et Échap restaurent le focus sur la commande ayant lancé la boîte de dialogue, ce qui réduit la sortie NVDA verbose. (SITES-24716)
* La boîte de dialogue Sélection de lien aligne désormais le libellé de programmation sur le libellé à l’écran pour les éléments de l’arborescence de dernier niveau. La navigation à touche fléchée déclenche une annonce de lecteur d’écran fiable pour chaque élément et supprime la sortie d’étiquette trompeuse. (SITES-24710)
* La boîte de dialogue de sélection d’ouverture de lien se repositionne désormais correctement sous une fenêtre d’affichage de 320 px. Le contenu n’excède plus la fenêtre contextuelle ou est tronqué, et la fenêtre contextuelle n’affiche plus de barre de défilement horizontale. (SITES-24709)
* La boîte de dialogue de sélection d’ouverture de lien restaure désormais le focus au clavier sur le déclencheur de boîte de dialogue après Fermer ou Annuler. Le focus ne passe plus à l’entrée Lien, ce qui maintient le contexte du lecteur d’écran stable et réduit les étapes de navigation. (SITES-24707)
* La boîte de dialogue contextuelle de l’image suit désormais une séquence de focus logique. Le focus n’ignore plus les commandes ou les abandons précédents sur le repère de page après Annuler et les personnes retrouvent le focus sur le bouton Configurer après la sortie. (SITES-24693)
* La boîte de dialogue contextuelle Rail des références piège désormais le focus au clavier. La touche de tabulation et Maj+Tab font toujours partie des commandes de boîte de dialogue et le focus ne quitte plus le contenu de la page. Les lecteurs d’écran n’annoncent que le contenu de la boîte de dialogue. (SITES-24683)
* La boîte de dialogue contextuelle Sélection du chemin d’accès hypertexte met désormais le focus sur l’en-tête de boîte de dialogue lors de l’ouverture. La commande Annuler ferme la boîte de dialogue et restaure le focus sur le bouton de boîte de dialogue Ouvrir, ce qui empêche la perte de focus et la sortie redondante du lecteur d’écran. (SITES-24672)
* Le champ Rechercher utilise désormais un libellé persistant à l’écran au lieu du texte d’espace réservé. Le libellé reste visible lors de la saisie, ce qui améliore la clarté pour les personnes utilisant un clavier, un lecteur d’écran et un système vocal. (SITES-24529)
* La boîte de dialogue contextuelle du teaser place désormais le focus sur l’en-tête de boîte de dialogue à l’ouverture. La fermeture de la boîte de dialogue renvoie le focus à la commande `Configure`, ce qui empêche la perte de focus et une sortie excessive du lecteur d’écran. (SITES-24522)
* Le panneau Ressources du rail latéral comprend désormais une commande Fermer. L’action Fermer renvoie le focus au clavier au bouton (bascule) Rail latéral et empêche l’affichage forcé du contenu du panneau. (SITES-24489)
* La touche de tabulation du clavier atteint désormais les boutons et les liens dans les tableaux d’administration. Il n’est plus nécessaire de naviguer entre les cellules à l’aide de la touche fléchée pour trouver des commandes interactives. (SITES-24285)
* La boîte de dialogue du composant Image n’expose plus l’aide décorative et les icônes Plein écran en tant qu’images. Les lecteurs d’écran ignorent désormais ces icônes, se concentrant sur les contrôles exploitables et le contenu des champs. (SITES-2940)
* L’administrateur de sites supprime désormais le rôle d’image des icônes de miniature de dossier. La technologie d’assistance ignore ces éléments décoratifs, en se concentrant sur les noms de dossier et les actions. (SITES-2852)
* L’arborescence de contenu achemine désormais le focus au clavier vers l’élément d’arborescence actif ou le premier élément d’arborescence. Le conteneur d’arborescence n’agit plus comme un arrêt de tabulation vide, ce qui empêche les pièges de focus Maj+Tabulation. (SITES-1577)

#### Interface d’utilisation d’administration{#sites-adminui-65-lts-sp2}

Les paramètres du mode Liste de la console Sites ne reflétaient pas les colonnes affichées en mode Liste. La boîte de dialogue s’est ouverte avec des cases à cocher décochées et un nombre de colonnes sélectionnées incorrect. La boîte de dialogue de synchronisation des correctifs affiche les colonnes de grille actives et met à jour le compteur pour qu’il corresponde à la visibilité réelle des colonnes. (SITES-38576)

#### Interface d’utilisation classique{#sites-classicui-65-lts-sp2}

Après une mise à niveau, la modification de composant de texte de l’interface d’utilisation classique affichait des balises HTML brutes au lieu du texte enrichi. Le pack de services 2 corrige le rendu de l’éditeur de texte enrichi de l’interface d’utilisation classique afin que l’éditeur affiche le contenu formaté et conserve les balises stockées. Le correctif arrête également l’extension des balises lors de modifications répétées et enregistre ces dernières. (SITES-38709)

#### [!DNL Content Fragments]{#sites-contentfragments-65-lts-sp2}

La prise en charge des événements découplés ne comportait pas les événements OSGi requis pour les fragments de contenu et les modèles dans 6.5 LTS. La mise à jour ajoute le lot d’événements ainsi que les dépendances requises, et inclut une version 6.5 de LTS. Les événements de fragment de contenu et de modèle se déclenchent désormais correctement et prennent en charge les workflows de l’API Launches. (SITES-35329)

#### [!DNL Content Fragments] - Admin{#sites-admin-65-lts-sp2}

* Modification de la gestion des composants dans l’interface de création de Sites pour arrêter tout comportement irrégulier lors des mises à jour de page. Ce défaut entraînait des réponses imprévisibles de l’éditeur qui interféraient avec les modifications de contenu de routine et réduisaient l’efficacité des workflows. La mise à jour aligne la logique de l’éditeur sur les modèles d’interaction attendus et offre des performances fiables lors des activités de création. (SITES-35078) CRITIQUE

* Une régression a interrompu le mode Liste de la console Ressources pour les fragments de contenu et déclenché une erreur lors du rendu de la liste. La mise à jour corrige la logique liste-affichage après la suppression de aperçu-infos et restaure une sortie de liste stable. La console affiche désormais les fragments de contenu sans échec et permet de conserver les interactions de liste utilisables. (SITES-38683)
* L’éditeur de fragment de contenu localise désormais le libellé Tags. L’éditeur localise également le libellé Collections, de sorte que le texte de l’interface d’utilisation correspond au paramètre régional sélectionné. (SITES-977)


#### [!DNL Content Fragments] - Éditeur de fragments{#sites-fragments-editor-65-lts-sp2}

* Les balises de variation de fragment de contenu disparaissaient lorsque le bouton (bascule) de la fonctionnalité restait désactivé après la refactorisation. Le correctif restaure la prise en charge des balises de variation même lorsque ce bouton est désactivé. Les créateurs et créatrices peuvent à nouveau ajouter et afficher des balises de variation dans l’éditeur de fragment de contenu. (SITES-38682) CRITIQUE
* Les fragments de contenu modifiés disparaissaient de la liste de la console Ressources lorsque les créateurs et créatrices revenaient à partir de l’éditeur de fragment de contenu. La mise en cache du navigateur a renvoyé une liste obsolète et a masqué le fragment mis à jour jusqu’à une actualisation manuelle. Le correctif ajoute la gestion du contrôle du cache pour le chemin de retour de l’éditeur afin que la liste se recharge correctement et que le fragment modifié reste visible. (SITES-35374) CRITIQUE

* L’éditeur de texte enrichi du fragment de contenu présentait des problèmes de disposition et visuels après de récentes modifications de style de l’interface d’utilisation. Le pack de services 2 affine le style de l’éditeur de texte enrichi afin que la barre d’outils et la zone modifiable s’affichent correctement et restent lisibles. L’éditeur de fragment de contenu s’aligne désormais sur l’aspect et le comportement de l’éditeur de page. (SITES-38684)
* La suppression des portées IMS du sélecteur de ressources Polaris interrompait l’intégration du fragment de contenu au point d’entrée de diffusion. Les créateurs et créatrices rencontraient des échecs lors de l’ouverture du sélecteur de ressources distant et de la sélection de ressources. La mise à jour ajoute à nouveau les portées IMS nécessaires et restaure un accès stable au niveau de la diffusion. (SITES-35837)
* Le panneau Contenu associé n’affiche plus d’espace réservé codé en dur « non défini ». L’éditeur de fragment de contenu résout désormais ce texte par le biais de ressources de localisation, afin que les éditeurs voient le texte traduit de l’interface utilisateur. (SITES-33675)
  <!-- REMOVED FROM BUG LIST FEBRUARY 13, 2026 * Preview error messaging now uses localized strings instead of raw `Cannot print fragment's Json` text. The Content Fragment Editor now shows translated output across locales during GraphQL endpoint resolution failures. (SITES-33666)-->
* L’éditeur de fragment de contenu affiche désormais un libellé d’onglet Général traduit dans tous les paramètres régionaux. L’éditeur remplace le texte d’onglet non localisé et supprime les identifiants internes des titres d’onglet. (SITES-30715)
* L’éditeur de fragment de contenu affiche désormais les noms traduits pour les types de ressources autorisés. La liste de sélecteur ne mélange plus les chaînes internes et les libellés en anglais uniquement lorsque les créateurs et créatrices configurent des restrictions de référence de contenu. (SITES-29699)

#### [!DNL Content Fragments] - API GraphQL {#sites-graphql-api-65-lts-sp2}

* Amélioration de la gestion de la validation des requêtes GraphQL pour arrêter les échecs de déploiement causés par des erreurs d’exécution de filtre. Le défaut générait des exceptions lors du démarrage de l’application et entraînait l’échec du déploiement dans les environnements affectés. La révision garantit un comportement de validation cohérent et permet un déploiement fluide sans interruptions de validation des requêtes à l’exécution. (SITES-34301) CRITIQUE

* La boîte de dialogue Modifier le point d’entrée GraphQL affiche désormais des chaînes d’interface localisées. La boîte de dialogue n’affiche plus de texte en anglais uniquement, tel que « Le schéma GraphQL provient de la configuration », et les libellés associés s’affichent correctement dans toutes les langues. (SITES-34018)

#### [!DNL Content Fragments] - Requêteur GraphQL{#sites-graphql-query-editor-65-lts-sp2}

* Amélioration de la gestion de la validation des requêtes GraphQL pour arrêter les échecs de déploiement causés par des erreurs d’exécution de filtre. Le défaut générait des exceptions lors du démarrage de l’application et entraînait l’échec du déploiement dans les environnements affectés. La révision garantit un comportement de validation cohérent et permet un déploiement fluide sans interruptions de validation des requêtes à l’exécution. (SITES-35529)
* L’explorateur GraphQL n’échoue plus lorsqu’un nom d’explorateur de configurations contient des caractères CJK. La création du point d’entrée et l’accès aux requêtes enregistrées fonctionnent normalement et la page du requêteur de GraphQL ne comporte pas d’erreur. (SITES-31616)

#### [!DNL Content Fragments] - Éditeur de modèles{#sites-model-editor-65-lts-sp2}

* Les modèles de fragment de contenu imbriqués cessaient de fonctionner lorsque la refactorisation liait la fonctionnalité à un bouton (bascule) désactivé. Le correctif restaure la prise en charge des modèles imbriqués sans nécessiter de modifications du bouton (bascule). Les créateurs et créatrices peuvent à nouveau créer et utiliser des modèles imbriqués dans l’éditeur de modèles. (SITES-38681) CRITIQUE

* Le panneau de filtrage Modèles de fragment de contenu n’expose plus les chaînes non localisées. AEM affiche désormais des libellés de filtre localisés et des valeurs de statut localisées dans tous les paramètres régionaux. (SITES-30863)
* L’éditeur de modèle de fragment de contenu effectue désormais le rendu des chaînes localisées pour la boîte de dialogue d’avertissement de verrouillage. L’interface d’utilisation remplace les messages en anglais non localisés par des ressources de paramètres régionaux dans les langues prises en charge. (SITES-28592)

#### [!DNL Content Fragments] - API REST{#sites-restapi-65-lts-sp2}

AEM Headless nécessitait une branche de version dédiée pour éviter la dépendance et les conflits de version de bundle avec les principaux builds. La mise à jour ajoute une branche `release/6.5lts` en mode découplé et aligne les jeux de dépendances et les versions de bundle. Jenkins crée désormais correctement la base de code découplée sans collisions de versions. (SITES-36585)

<!-- #### Component console{#sites-component-console-65-lts-sp2} -->

#### API de contenu{#sites-content-api-65-lts-sp2}

Un défaut de basculement de fonctionnalité signalait de manière incorrecte le statut de l’API Page Management. La mise à jour ajoute un indicateur d’activation dédié et l’évalue avec le bouton (bascule) existant. L’API Page Management affiche désormais un statut stable. L’API Site Management reste expérimentale. (SITES-39284)

#### Back-end principal{#sites-core-backend-65-lts-sp2}

* Modification de l’expérience de création de Sites pour résoudre un comportement incohérent qui perturbait les workflows de modification de pages standard. Les créateurs et créatrices rencontraient des résultats inattendus lors de l’interaction des composants, ce qui interférait avec les mises à jour de contenu et réduisait la fiabilité. La modification restaure un comportement stable de l’éditeur et assure l’exécution cohérente des actions de création dans les scénarios affectés. (SITES-35162) CRITIQUE

* Amélioration du comportement de création de Sites afin de résoudre un problème qui interrompait la modification des pages et provoquait des résultats incohérents lors de l’interaction avec les composants. Les créateurs et créatrices rencontraient des réponses inattendues de l’interface d’utilisation qui interféraient avec les mises à jour de contenu et réduisaient la fiabilité des workflows. La modification restaure la gestion de l’état de l’éditeur stable et assure l’exécution prévisible des actions de création dans les scénarios affectés. (SITES-34499)

<!--
#### Core Components{#sites-core-components-65-lts-sp2}

#### Campaign integration{#sites-campaign-integration-65-lts-sp2}

#### Experience Fragments{#sites-experiencefragments-65-lts-sp2}

#### Foundation Components (Legacy){#sites-foundation-components-legacy-65-lts-sp2}
-->

#### Lancements{#sites-launches-65-lts-sp2}

* La chronologie des sites affichait un texte en anglais codé en dur lors de la promotion du lancement : « Version créée ... avant la promotion du lancement ». La mise à jour remplace la chaîne codée en dur par une gestion des messages localisée. La chronologie affiche désormais le texte localisé et aligne l’entrée sur le comportement de localisation AEM standard. (SITES-39157)
* L’étendue de la promotion de lancement dérivait lorsque les créateurs et créatrices promouvaient une sous-page à l’aide de Promouvoir la page active et les sous-pages. AEM promouvait également des pages non liées et provoquait des modifications inattendues de sites en direct. Le correctif corrige le calcul de la portée de lancement afin que seule la sous-arborescence sélectionnée soit promue. (SITES-38315)
* Les fragments de contenu dans les lancements ne participaient pas à l’index `damAssetLucene` et limitaient les résultats de recherche et l’efficacité des requêtes. Cette modification ajoute les chemins de fragment de contenu de lancement à la définition d’index. Les requêtes de recherche et personnalisées trouvent désormais les fragments de contenu sous `/content/launches`. (SITES-35634)
* L’interface des lancements affichait les contrôles de lancement de fragment de contenu même si le produit n’expose pas les lancements de fragment de contenu dans l’interface d’utilisation tactile. Cette modification supprime les chemins de code du lancement de fragment de contenu de cq-launches-content et ajuste le filtrage de la liste de lancement. Les créateurs et créatrices voient désormais les options de lancement de page cohérentes sans les entrées de lancement de fragment de contenu. (SITES-35633)
* Le démarrage rapide d’AEM 6.5 LTS ne comportait pas les lots de lancements requis et les conditions préalables, ce qui bloquait l’activation de l’API OpenAPI Launches. La mise à jour ajoute les lots de lancements et les dépendances requises, telles que la prise en charge des mesures, les mises à jour DAM-cfm et la configuration de la file d’attente. Les API de lancement s’exécutent désormais sur Quickstart 6.5 LTS avec les composants d’exécution requis présents. (SITES-35297)
* Le packaging des lancements de fragments de contenu regroupait de nouvelles versions de dépendance et des bibliothèques GraphQL inutiles, ce qui compliquait l’intégration à AEM 6.5 LTS. Cette modification aligne les versions de dépendance sur la référence LTS d’AEM 6.5 et supprime les dépendances GraphQL inutilisées. La résolution de bundle reste désormais cohérente et le démarrage des lancements de fragments de contenu reste stable. (SITES-35295)
* Les lancements AEM exécutent désormais un pipeline Jenkins dédié pour la branche 6.5 LTS. Le pipeline s’exécute de nuit et génère et envoie des alertes en cas d’échec par e-mail. Cette configuration augmente la couverture de test et détecte rapidement les régressions. (SITES-35293)
* AEM 6.5 LTS est désormais livré avec un bundle d’API Launches mis à jour avec des versions d’artefact alignées. Le bundle suit la ligne de code principale tout en conservant la version 6.5 LTS correcte. Cette mise à jour stabilise la consommation de l’API Launches sur la pile LTS 6.5. (SITES-35292)
* AEM 6.5 LTS comprend désormais un bundle launches-core mis à jour avec des versions dépendantes alignées. La mise à jour ajoute une gestion de base des lancements pour l’UUID de fragment et l’UUID de référence. Le traitement de lancement conserve désormais un comportement cohérent dans les lancements et les workflows de fragments de contenu. (SITES-35290)
* Amélioration de l’éditeur Sites pour résoudre les comportements incohérents qui perturbaient les workflows normaux de création de pages. Les créateurs et créatrices rencontraient une interaction de composant inattendue qui interférait avec les mises à jour de contenu et réduisait la fiabilité de la modification. La modification restaure une gestion cohérente de l’état de l’interface d’utilisation et garantit une exécution prévisible des actions de création dans les scénarios affectés. (SITES-35138)
* La modification des lancements affiche désormais le texte d’erreur localisé au lieu de la chaîne `Provided path is not a launch` codée en dur. L’interface d’utilisation effectue désormais le rendu des messages traduits dans toutes les langues lorsque Modifier reçoit un chemin de lancement non valide. (SITES-33360)
* AEM 6.5 LTS comprend désormais le travail de port latéral OpenAPI Launches. La mise à jour apporte les bundles API Launches, les packages de contenu et les artefacts de démarrage rapide requis à la parité et active les scénarios de fragment de contenu Launches OpenAPI avec une validation CI stable. (SITES-32050)
* L’interface d’utilisation de Launches localise désormais le libellé du modèle remplacé. Les détails de remplacement du modèle affichent désormais le texte traduit au lieu d’une chaîne en anglais uniquement. (SITES-29525)
* AEM a résolu une clé de localisation manquante dans **Sites** > **Lancements** > **Modifier**. L’interface affiche désormais un message d’erreur traduit à la place de la chaîne « Impossible de mettre à jour la liste source de lancement » brute. (SITES-21499)
* L’interface d’utilisation de promotion de Launch affiche désormais des libellés de statut et des actions localisés. La zone d’aperçu affiche le texte traduit des éléments **Supprimé**, **Nouveau** et **Affichage**, plutôt que des chaînes anglaises brutes. (SITES-13540)
* La création du lancement affiche désormais les messages d’erreur localisés. L’interface d’utilisation n’affiche plus de chaînes en anglais brutes, telles que `Unable to create launch page`, `Source root resource is not a page` ou `Mandatory parameter is missing`. (SITES-13085)


<!-- #### Link Checker{#sites-link-checker-65-lts-sp2} -->


#### MSM - Live Copies{#sites-msm-live-copies-65-lts-sp2}

* L’administration avait une visibilité limitée sur le traitement d’envoi au moment de la modification de MSM lors des modifications de contenu. Le correctif ajoute une journalisation détaillée autour de la réception des événements MSM et de l’exécution du déploiement. La sortie de débogage affiche désormais les événements déclenchés, les chemins de contenu modifiés et la personne à l’origine de la modification. (SITES-38029)
* Dans AEM, correction d’un problème de mise en page de localisation dans le champ de date Déploiement du plan directeur. L’invite de date s’adapte désormais au contrôle et reste lisible dans les langues prises en charge, y compris `fr_FR`. (SITES-14961)

<!-- #### Page editor{#sites-pageeditor-65-lts-sp2} -->

#### Réplication{#sites-replication-65-lts-sp2}

La publication de l’éditeur de page gère désormais les URL contenant des sélecteurs ou des suffixes. La requête publiée envoie désormais le chemin d’accès à la page JCR, et non une chaîne d’URL de sélecteur ou de suffixe, de sorte que l’activation se termine et que le contenu est mis en ligne. La réplication renvoie désormais un statut d’erreur en cas d’échec, ce qui empêche les messages erronés de type « publication démarrée ». (NPR-43288)

<!-- #### Rich Text Editor{#sites-rte-65-lts-sp2} -->

#### Éditeur de modèles{#sites-template-editor-65-lts-sp2}

Le texte du statut du modèle s’affichait verticalement dans **Outils** > **Général** > **Modèles** pour certains paramètres régionaux. Le libellé « obsolète » rompait la mise en page et se lisait comme une colonne de caractères. Le correctif corrige le style du statut du modèle de sorte que le libellé s’affiche sur une seule ligne horizontale. (SITES-36797)

#### Éditeur universel {#sites-universal-editor-65-lts-sp2}

* Une configuration OSGi par défaut a été définie comme `preview=true` et forçait l’éditeur universel à démarrer en mode Aperçu. Cette mise à jour corrige la valeur par défaut et restaure le comportement standard de l’entrée en production. L’éditeur universel s’ouvre désormais en mode Production, sauf si l’administration active explicitement le mode Aperçu. (SITES-37193)
* La commandeOuvrir de l’éditeur universel est désormais définie par défaut sur le mode Aperçu dans les environnements de développement et d’évaluation. La commande ajoute `preview=true`, ce qui permet d’aligner les contrôles de création sur le contexte de prévisualisation et d’éviter les ouvertures accidentelles en production. (SITES-33839)

### [!DNL Assets]{#assets-65-lts-sp2}

La mise en relation des ressources fonctionne désormais pour les noms de fichier qui incluent des espaces. La nouvelle logique client de mise en relation gère désormais correctement les chemins contenant des espaces et évite les erreurs source `undefined` lors de la sélection de la relation. La boîte de dialogue Mettre en relation s’ouvre désormais et enregistre les relations sans blocages ni rotations de l’interface d’utilisation. DAM permet désormais de mettre en relation, dériver et dissocier des ressources sans renommer les fichiers. (Assets-56418)

#### [!DNL Dynamic Media]{#assets-dm-65-lts-sp2}

* Nouvelle intégration du lecteur vidéo Dynamic Media (déploiement limité) - Une nouvelle expérience de lecteur vidéo Dynamic Media est désormais disponible dans le démarrage rapide d’AEM 6.6. Actuellement, cette amélioration n’est activée que pour les clients initiaux dans le cadre d’un déploiement contrôlé. (Assets-60165)
* Correction d’un problème en raison duquel l’option Sélectionner une miniature de la boîte de dialogue des propriétés vidéo n’ouvrait pas le sélecteur de ressources, ce qui restaurait la possibilité pour les personnes de choisir des miniatures personnalisées pour les ressources vidéo. (Assets-58926)
* Dans la vidéo Dynamic Media, ajout de la prise en charge de la sélection de l’arabe dans la liste déroulante Langue des sous-titres et des pistes audio, ce qui permet la gestion des sous-titres arabes directement dans AEM. (Assets-61771)

<!-- #### [!DNL Dynamic Media] - Hybrid Mode {#assets-dm-hybrid-65-lts-sp2} -->

### [!DNL Forms]{#forms-65-lts-sp2}

* La fonctionnalité `Data Source / Enter Keyword` de l’éditeur de modèle de données de formulaire (FDM) rencontrait des problèmes, ce qui affectait la capacité à rechercher et à sélectionner des sources de données. (FORMS-23971)
* Sur les appareils mobiles, le composant Tableau dans les formulaires adaptatifs affichait un en-tête masqué en haut, ce qui entraînait une mauvaise annonce du contenu par les lecteurs d’écran. Ce problème affectait les personnes utilisant des lecteurs d’écran pour la navigation. (FORMS-23754)
* Des problèmes se produisaient dans les formulaires adaptatifs basés sur les composants principaux référençant les types de ressources marqués comme granite:InternalArea, ce qui affectait les fonctionnalités de plusieurs composants granite dans le module complémentaire Forms local. (FORMS-23632)
* L’envoi du formulaire échoue après la mise à niveau vers AEM 6.5 LTS SP1. L’élément com.adobe.cq.social.commons.CollabUtil était manquant, ce qui provoquait des erreurs de compilation JSP et des échecs d’action d’e-mail. (FORMS-23457)
* Des problèmes de traduction de hCaptcha incorrecte se produisaient dans les formulaires adaptatifs basés sur les composants principaux. Cela affectait la capacité des personnes non anglophones à remplir des formulaires avec précision. (FORMS-23426)
* Les personnes rencontraient des échecs d’envoi de formulaire avec une exception SAXParseException : « Le contenu n’est pas autorisé dans prolog » (HTTP 500). Ce problème se produisait en raison d’une valeur null dans le code XML des données de préremplissage, ce qui entraînait l’échec de l’analyse XML côté serveur. (FORMS-22633)
* Échec des audits WCAG (Web Content Accessibility Guidelines) pour les formulaires adaptatifs. Ce problème est dû à un balisage de navigation par tabulation du formulaire non valide. En d’autres termes, un élément hors liste est rendu en tant qu’enfant direct d’une liste, où seuls les éléments de liste sont autorisés. Ce problème empêchait le formulaire de transmettre les validateurs d’accessibilité et les organisations affectées qui doivent respecter les exigences légales ou de conformité interne. (FORMS-22101)
* Des problèmes d’accessibilité se produisaient dans le document d’enregistrement (DoR) / le PDF d’envoi où les champs de formulaire vides n’étaient pas balisés en tant qu’éléments de formulaire. Cela entraînait des difficultés pour les lecteurs d’écran, ce qui affectait la capacité des personnes atteintes d’une déficience visuelle à naviguer dans les formulaires et à les remplir efficacement. (FORMS-21989)
* Un problème affectait les notes de bas de page des composants d’un sous-panneau, qui ne s’affichaient pas lors du chargement du formulaire. Ce problème se produisait lorsque l’élément avec la note de bas de page était le dernier composant de la page. (FORMS-21925)
* Des problèmes se produisaient lors de la sélection de composants dans l’éditeur AEM Forms. Lors de la navigation entre les onglets et le retour au premier onglet, certains conteneurs ne pouvaient plus être sélectionnés, ce qui empêchait une identification et une interaction faciles. (FORMS-21814)
* Une vulnérabilité de sécurité a été détectée dans le tableau de bord des formulaires adaptatifs. Plus précisément, un problème XSS (cross-site scripting) a été identifié dans le fichier startpointcontrol.js, ce qui peut potentiellement permettre l’exécution de scripts malveillants. (FORMS-20679)
* Dans les déploiements de clusters LTS AEM Forms 6.5 sur JBoss® EAP 8, les fichiers `domain/configuration/domain_oracle.xml`, `domain_mysql.xml` et `domain_mssql.xml` ne contiennent plus de balise `<security>` en double qui provoquait un code XML non valide et empêchait le démarrage du contrôleur de domaine. (FORMS-24687)
* En mode clé en main, la mise à jour du port de base de données est désormais correctement appliquée lors de la nouvelle installation et de la mise à niveau. En mode Nouvelle installation, les personnes peuvent choisir parmi tous les ports disponibles, et en mode Mise à niveau, le port de base de données mis à jour dans lc_turnkey.xml est correctement référencé pendant le processus de mise à niveau. (FORMS-24689)
* Lors de la configuration de JBoss® EAP 8.0 sous Linux®, les scripts shell modifiés sous Windows ne provoquent plus d’erreurs `/bin/sh^M: bad interpreter or $'\r': command not found` en raison des fins de ligne CRLF. (FORMS-24688)
* Sur les déploiements Forms JEE LTS s’exécutant sur JBoss® EAP 8, l’interface d’utilisation Reader Extensions peut échouer avec une erreur de serveur interne. (FORMS-24894)
* Sous Linux®, les utilisateurs rencontraient des problèmes d’exécution ou de déploiement lorsque le gestionnaire de configuration LTS de Forms JEE s’exécutait avec une valeur de `OSFileSetIntendedFor` indéfinie ou incorrecte dans `configurationManager/config/solcomp/LFS_Foundation.properties`, ce qui empêchait la configuration d’être correctement adaptée à Linux®. Après l’installation et avant d’exécuter Configuration Manager, définissez `OSFileSetIntendedFor=Linux` dans ce fichier. (FORMS-24741)

<!--
#### Forms JEE 

#### Forms Captcha {#forms-captcha-65-lts-sp2}

#### XMLFM {#forms-xmlfm-65-lts-sp2}

#### [!DNL Adaptive Forms] {#adaptive-forms-65-lts-sp2}

#### [!DNL Forms Designer] {#forms-designer-65-lts-sp2}

#### Forms Designer

#### AdaptIve Forms

#### Forms Captcha

#### Forms Management UI
-->


### Foundation {#foundation-65-lts-sp2}

#### Apache Felix {#foundation-apachefelix-65-lts-sp2}

* La sécurité d’accès aux ressources Sling s’exécute désormais sur la version 1.1.2. ResourceAccessSecurityImpl ne renvoie plus une ClassCastException lors de l’initialisation lorsque plusieurs services ResourceAccessGateHandler s’enregistrent. L’initialisation s’effectue désormais de manière fiable et évite les échecs de démarrage dans les environnements comportant plusieurs handlers. (NPR-42750)
* La console JMX et la console web envoient désormais un élément `Content-Type: text/css header` pour les ressources CSS de la console. La vérification MIME stricte ne bloque plus le chargement des feuilles de style, de sorte que l’interface d’utilisation `/system/console/jmx` s’affiche avec un style normal. (GRANITE-63677)
* AEM évite désormais les entrées ACL en double pour le groupe `contributor` dans l’élément `WEB-INF/resources/provisioning/model.txt` généré. La sortie WAR contient désormais un bloc ACL cohérent, ce qui empêche les différences d’autorisation déroutantes pendant la révision. (GRANITE-63269)
* AEM n’efface plus les paramètres des listes Autorisé et Non autorisé du pare-feu de désérialisation lors des opérations d’actualisation des bundles. La mise à jour de la logique d’enregistrement des filtres aligne l’instance de pare-feu active sur la configuration enregistrée, de sorte que la protection reste activée sans redémarrage. (GRANITE-61382)
* Felix Web Console ne génère plus d’erreurs `NullPointerException` intermittentes lors de l’accès à `/system/console`. La mise à jour de la gestion de ServiceTracker empêche un état de suivi nul. La connexion à la console et la navigation restent stables lors des demandes répétées et de la validation automatisée. (GRANITE-61042)

<!--
#### Campaign{#foundation-campaign-65-lts-sp2}

#### Cloud Services{#foundation-cloudservices-65-lts-sp2}

#### Communities {#foundation-communities-65-lts-sp2}

#### Content distribution{#foundation-content-distribution-65-lts-sp2}
-->

#### CRX {#foundation-crx-65-lts-sp2}

CRXDE Lite n’affiche plus d’onglet vide lors de l’ouverture d’un fichier JSP après une mise à niveau du pack de services. AEM est désormais livré avec le code code CodeMirror correspondant et le code du module complémentaire, ce qui empêche l’erreur fatale du navigateur et permet à l’éditeur de rester utilisable. (GRANITE-64333)

#### Granite{#foundation-granite-65-lts-sp2}

Le programme de validation de la sécurité des expressions gère désormais les valeurs de configuration OSGi vides ou nulles. Il applique des valeurs par défaut sécurisées, ignore les tableaux vides et enregistre des journaux effacés, empêchant NullPointerException et les résultats de validation imprévisibles. (NPR-43163)

<!-- #### HTL{#foundatoin-htl-5-lts-sp2} -->

#### Intégrations{#foundation-integrations-65-lts-sp2}

AEM synchronise désormais les activités Adobe Target même lorsque les dates de début et de fin existent. La payload Target formate désormais les dates d’activité sous la forme d’horodatages ISO 8601 complets, comprenant les secondes, les millisecondes et le fuseau horaire. Target ne rejette plus la requête avec `InvalidJson.Json`. Les activités planifiées passent désormais à un statut synchronisé au lieu de rester désynchronisées. (CQ-4360733)

<!--
#### Jetty{#foundation-jetty-65-lts-sp2}

#### Localization{#foundation-localization-65-lts-sp2} 

#### Omnisearch{#foundation-omnisearch-65-lts-sp2}

#### Platform{#foundation-platform-65-lts-sp2}

#### Projects{#foundation-projects-65-lts-sp2}
-->

#### Oak {#foundation-oak-65-lts-sp2}

Le pack de services 2 LTS d’AEM 6.5 nécessite le connecteur S3, version 1.60.10 ou ultérieure. La configuration du magasin de données S3 inclut désormais `crossRegionAccess` et `mode` afin que l’administration puisse activer l’accès au compartiment inter-régions et basculer le stockage vers GCP si nécessaire. `s3EndPoint` s’attend désormais à ce qu’une région soit alignée sur `s3Region`, ou qu’elle reste vide afin que le pilote génère le point d’entrée. (GRANITE-64873)


#### Démarrage rapide{#foundation-quickstart-65-lts-sp2}

* Sling met à jour la liste autorisée de connexion d’administration pour utiliser une terminologie inclusive et de nouveaux PID de configuration. Cette modification s’aligne sur la base Sling JCR 3.2.0. (GRANITE-63756)

  **Impact**

   * Sling rend obsolètes ces PID et vous devez les supprimer de vos configurations :
      * PID factory : `org.apache.sling.jcr.base.internal.LoginAdminWhitelist.fragment`
      * PID global : `org.apache.sling.jcr.base.internal.LoginAdminWhitelist`
Ces anciennes configurations utilisent des propriétés, telles que `whitelist.name` et `whitelist.bundles`.

   * Sling assure toujours une rétrocompatibilité partielle pour les PID obsolètes, mais ne les utilise pas pour les nouvelles configurations. Utilisez plutôt les PID `LoginAdminAllowList.*` plus récents.
   * N’exécutez pas simultanément des configurations obsolètes et nouvelles. Des configurations mixtes peuvent créer de l’ambiguïté et produire un comportement inattendu. Lorsque vous migrez vers AEM 6.5 LTS SP2, supprimez complètement les PID obsolètes.

  **Ce que vous devez faire**

   1. Recherchez les configurations de liste autorisée qui utilisent des PID `LoginAdminWhitelist*`.
   1. Remplacez-les par les nouveaux PID appropriés :

      * PID factory : `org.apache.sling.jcr.base.LoginAdminAllowList.fragment`
      * PID global : `org.apache.sling.jcr.base.LoginAdminAllowList`

      Pour plus d’informations, voir [Approche obsolète de la recherche de bundles de liste autorisée pour les connexions d’administration](https://sling.apache.org/documentation/the-sling-engine/service-authentication.html#deprecated-approach-to-allowlist-bundles-for-administrative-login).

* AEM 6.5 LTS SP2 met à jour l’ensemble de bundles de couches de base pour Sling, Oak et Felix. Ces mises à niveau renforcent la stabilité d’exécution principale et alignent les versions dépendantes sur la plateforme. (GRANITE-61874)

<!--
#### Security{#foundation-security-65-lts-sp2}

AEM now prevents NullPointerException errors when a logged-in user lacks read access for some groups and opens the Groups tab. The tab now hides groups without access and renders group membership details without a blank or unresponsive UI. (NPR-43311)
-->

#### Sling{#foundation-sling-65-lts-sp2}

AEM comprend désormais le moteur Sling 2.16.6. Cette modification élimine les violations XSS signalées par les outils de sécurité et améliore la sécurité et la stabilité du rendu principal. (NPR-43105)

<!--
#### Translation{#foundation-translation-65-lts-sp2}

#### User interface{#foundation-ui-65-lts-sp2}
-->

#### WCM{#foundation-wcm-65-lts-sp2}

Les traductions AEM n’échouent plus sur Java 17 ou Java 21 en raison de problèmes de format XLIFF. Le pipeline d’export produit désormais un XLIFF conforme aux normes que les fournisseurs de traduction acceptent. Cette modification supprime les interruptions de la tâche de traduction et restaure un transfert prévisible entre AEM et les services de traduction. Les workflows de traduction restent désormais stables sur les runtimes Java pris en charge. (CQ-4360217)

#### Workflow{#foundation-workflow-65-lts-sp2}

EmailNotificationService-Processor ne déclenche plus des erreurs de type « Segment introuvable » répétées lors de la gestion des notifications de workflow. La mise à jour de la gestion des exceptions détecte SegmentNotFoundException et arrête la boucle de traitement au lieu de continuer les lectures non valides. L’exécution du workflow reste stable et le bruit du journal diminue lors de l’accès à la boîte de réception et à l’élément de travail. (GRANITE-62635)




## À propos d’[!DNL Experience Manager Foundation] {#experience-manager-foundation}

La plateforme d’[!DNL Adobe Experience Manager] 6.5 LTS repose sur les versions mises à jour de l’architecture OSGi (Apache Sling et Apache Felix), ainsi que sur le référentiel de contenu Java™ : Apache Jackrabbit Oak 1.68.x.

Eclipse Jetty 11.0.x est utilisé comme moteur de servlet pour Quickstart.

### Prise en charge de Java™  {#java-support}

* Prise en charge de Java™ 17 et Java™ 21.
* Pour des performances optimales, remplacez les valeurs par défaut du GC par d’autres valeurs. Pour plus d’informations, consultez la section [Installation et mise à jour](/help/sites-deploying/custom-standalone-install.md).
* Adobe distribue des mises à jour de maintenance Java™ 17 et Java™ 21 pour l’utilisation par les clientes et les clients dans les projets liés à AEM, lorsqu’elles ne sont pas disponibles publiquement depuis Oracle.

### Packaging Uberjar {#uber-jar-packaging}

UberJar pour AEM 6.5 LTS SP2 utilise la version 6.6.2 d’AEM 6.5 LTS UberJar. Vous pouvez récupérer les artefacts UberJar correspondants à partir du référentiel central Maven. Contrairement à AEM 6.5, AEM 6.5 LTS sépare les API publiques et les API obsolètes en deux artefacts différents.

Pour compiler par rapport aux API publiques, utilisez ce qui suit :

```xml
<dependency>
    <groupId>com.adobe.aem</groupId>
    <artifactId>uber-jar</artifactId>
    <version>6.6.2</version>
    <classifier>apis</classifier>
    <scope>provided</scope>
</dependency>
```

Si votre code dépend également d’API obsolètes, ajoutez ce qui suit :

```xml
<dependency>
    <groupId>com.adobe.aem</groupId>
    <artifactId>uber-jar</artifactId>
    <version>6.6.2</version>
    <classifier>deprecated-apis</classifier>
    <scope>provided</scope>
</dependency>
```

Voir également [Mise à jour de la version AEM Uber Jar](/help/sites-deploying/upgrading-code-and-customizations.md#update-the-aem-uber-jar-version).

### Mise à niveau {#upgrade}

* Pour plus d’informations sur la procédure de mise à niveau, consultez la [documentation de mise à niveau](/help/sites-deploying/upgrade.md).
* Pour obtenir des instructions détaillées sur la mise à niveau, consultez [Mise à niveau vers AEM Forms 6.5 sous JEE](https://experienceleague.adobe.com/fr/docs/experience-manager-65-lts/content/forms/upgrade-aem-forms/upgrade).

#### Bonnes pratiques relatives aux mises à niveau du pack de services d’AEM 6.5 LTS

<!-- THE INFORMATION UNDER THIS HEADING CAME FROM CQDOC-23078 -->

**Environment**
S’applique à : AEM 6.5 LTS (On-Premise) avec pack de services 2 (SP2). Le SP2 est fourni sous la forme d’un fichier JAR de démarrage rapide.

**En quoi cette mise à niveau est-elle importante**
Le SP2 pour AEM 6.5 LTS est fourni sous la forme d’un fichier JAR de démarrage rapide plutôt que d’un fichier ZIP à installer via le gestionnaire de modules. Les clients et clientes On-Prem effectuent une mise à niveau en remplaçant le fichier JAR de démarrage rapide, en le décompressant et en redémarrant. Cette méthode est conforme à la procédure de mise à niveau statique d’Adobe.

**Flux de mise à niveau recommandé (création ou publication)**

1. Vérifiez que votre instance AEM 6.5 LTS est saine et accessible.
1. Téléchargez le fichier JAR de démarrage rapide (par exemple, `cq-quickstart-6.6.x.jar`) à partir de la distribution logicielle.
1. Arrêtez l’instance en cours.
1. Dans le répertoire d’installation d’AEM (en dehors de `crx-quickstart/`), remplacez le fichier JAR de démarrage rapide précédent par le fichier JAR du SP2.
1. Décompressez le fichier JAR :

   ```java
   java -jar cq-quickstart-6.6.x.jar -unpack
   ```

   (Ajustez les indicateurs de tas selon les besoins.)

1. Renommez le fichier JAR décompressé pour qu’il corresponde au rôle et au port, par exemple `cq-author-4502.jar` ou `cq-publish-4503.jar`.
1. Démarrez AEM et confirmez la mise à niveau dans l’interface d’utilisation (Aide > À propos) et les journaux.

**Bonne qualité**

* Exécutez la mise à niveau dans des environnements inférieurs/de test avant la production.
* Effectuez une sauvegarde complète et restaurable (référentiel et magasins de données externes) avant de commencer.
* Consultez les conseils sur la mise à niveau statique d’Adobe et les exigences techniques (Java 17/21 recommandé pour LTS).

>[!NOTE]
>
>Les noms de fichier indiqués ci-dessus (par exemple, `cq-quickstart-6.6.x.jar`) reflètent le nom de l’artefact de démarrage rapide observé pour cette version LTS. Utilisez toujours le nom de fichier exact que vous téléchargez à partir de la distribution logicielle.

## Installation et mise à jour{#install-update}

Pour connaître les exigences de configuration, consultez les [instructions d’installation](/help/sites-deploying/custom-standalone-install.md).

>[!NOTE]
>
> Si vous effectuez une mise à niveau directement vers LTS SP1 à partir d’anciens SP 6.5, suivez les instructions données pour la [mise à niveau](/help/sites-deploying/upgrade.md) 6.5 à 6.5 LTS GA.


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

Adobe examine continuellement les fonctionnalités du produit afin de les améliorer et d’offrir plus de valeur client en modernisant ou en remplaçant les fonctionnalités héritées. Ces modifications sont implémentées en tenant compte de la rétrocompatibilité.

Pour garantir la transparence et permettre une planification adéquate, Adobe suit ce processus d’obsolescence pour Adobe Experience Manager (AEM) :

* L’obsolescence est d’abord annoncée. Les fonctionnalités obsolètes restent disponibles, mais ne sont plus améliorées.
* La suppression n’intervient pas avant la prochaine version majeure. Le calendrier de suppression prévu est communiqué séparément.
* Un cycle de publication minimum est fourni pour que les clients puissent effectuer la transition vers des alternatives prises en charge avant la suppression d’une fonctionnalité.

### Fonctionnalités obsolètes {#deprecated-features}

Cette section répertorie les fonctionnalités qu’Adobe a abandonnées dans AEM 6.5 LTS. En règle générale, Adobe rend les fonctionnalités obsolètes avant de les supprimer dans une version ultérieure et fournit une alternative.

Il est conseillé aux clients de vérifier s’ils utilisent la fonctionnalité dans leur déploiement actuel. Planifiez de modifier leur mise en œuvre afin d’utiliser l’alternative fournie.

| Domaine | Fonctionnalité | Remplacement | Version (SP) |
| --- | --- | --- | --- |
| Démarrage rapide | API Mongo | Les API Mongo sont désormais obsolètes et leur suppression est prévue dans les prochaines versions. | 6.5 TS SP2 |
| Sites | Prise en charge des fragments de contenu dans l’API REST AEM Assets | AEM 6.5 LTS SP2 fournit des API OpenAPI modernes pour la gestion des fragments de contenu et des modèles, de sorte que les anciens points d’entrée de la prise en charge des fragments de contenu dans l’API REST AEM Assets sont désormais obsolètes.<br>Adobe prévoit de conserver ces anciens points d’entrée disponibles jusqu’à une annonce de fin de vie. Adobe ne prévoit pas d’autres améliorations pour les points d’entrée obsolètes. | 6.5 LTS SP2 |
| Sites | [Éditeur SPA](/help/sites-developing/spa-overview.md) | Les éditeurs recommandés pour la gestion du contenu découplé dans AEM sont les suivants : <br>- [Éditeur universel](/help/sites-developing/universal-editor/introduction.md) pour la modification visuelle.<br>- [Éditeur de fragments de contenu](/help/assets/content-fragments/content-fragments-managing.md) pour la modification de formulaires. | 6.5 LTS GA |
| [!DNL Foundation] | Prise en charge de com.adobe.granite.oauth.server | Intégration Adobe IMS |  |

### Fonctionnalités supprimées {#removed-features}

Cette section répertorie les fonctionnalités qui ont été supprimées dans AEM 6.5 LTS. Ces fonctionnalités étaient signalées comme obsolètes dans les versions antérieures.

* La prise en charge de la persistance du référentiel RDBMK pour CRX a été supprimée.
* Dans les environnements en cluster, MongoMK est désormais la seule option prise en charge pour la persistance du référentiel.

| Domaine | Fonctionnalité | Remplacement | Version (SP) |
| --- | --- | --- | --- |
| Commerce | AEM CIF Classic n’est pas pris en charge. | Migrez vers [AEM CIF](/help/commerce/cif/migration.md). | 6.5 LTS GA |
| Solutions | Social / Communities n’est pas pris en charge. | Aucun remplacement n’est disponible. | 6.5 LTS GA |
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

### AEM Forms

* Dans Configuration Manager, l’initialisation de la base de données échoue pendant Bootstrap dans le mode personnalisé clé en main LTS JEE d’AEM Forms 6.5 lorsqu’aucun module ou uniquement des composants limités sont sélectionnés. L’échec est dû à une dépendance manquante (xalan-2.7.2.jar), ce qui entraînait une erreur. L’ajout du fichier JAR à adobe-livecycle-jboss.ear\lib résout le problème. (FORMS-24690)
* Sur Forms JEE, les déploiements du Service Pack 2 LTS s’exécutant sur WebSphere® Liberty Profile peuvent entraîner l’échec de la fonctionnalité de messagerie. Lors de l’utilisation des fonctionnalités de messagerie, le serveur consigne une erreur : `Could not convert socket to TLS`. (FORMS-24692)
* Sur Forms JEE LTS s’exécutant sur JBoss®, les fonctionnalités liées aux e-mails peuvent échouer. Lors de l’utilisation des fonctionnalités de messagerie, le serveur consigne une erreur : `Error IMAPProvider not a subtype`. Installez le correctif à partir de [Distribution logicielle](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/hotfix/adobe-core-jboss.ear) pour résoudre ce problème. (FORMS-24892)

### Corruption du référentiel lors du compactage en ligne après le compactage hors ligne (GRANITE-65146) {#repository-corruption-during-online-compaction-after-offline-compaction-granite-65146}

Les utilisateurs et utilisatrices peuvent rencontrer une corruption du référentiel lors du compactage en ligne si le compactage hors ligne a été précédemment exécuté sur le référentiel JCR. Une erreur de type `SegmentNotFoundException` (SNFE) peut se produire dans ce scénario et peut entraîner une corruption du référentiel.

Pour résoudre ce problème, installez le correctif à partir de la [Distribution logicielle](https://experience.adobe.com/#/downloads/content/software-distribution/fr/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq660/hotfixes/cq-6.5.lts.2-hotfix-GRANITE-65388-1.0.zip). Comme le correctif comprend un bundle `oak-segment-tar` de bas niveau, l’instance redémarre après l’installation.

Planifiez le temps d’arrêt de l’instance lors de son application. Pour la compression hors ligne, utilisez le fichier jar [`oak-run` correspondant](https://experience.adobe.com/#/downloads/content/software-distribution/fr/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq660/hotfixes/oak-run-1.88.1-B006.jar) également disponible sur la Distribution logicielle.

>[!NOTE]
>
> * Pour toutes les opérations `oak-run`, utilisez le fichier jar [`oak-run` 1.88.1-B006](https://experience.adobe.com/#/downloads/content/software-distribution/fr/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq660/hotfixes/oak-run-1.88.1-B006.jar).
>
> * Démarrez AEM en définissant la propriété système `oak.compaction.legacy=true`.

### Lot de `com.adobe.granite.apicontroller` manquant dans AEM 6.5 LTS SP2 (GRANITE-67640) {#missing-apicontroller-bundle-granite-67640}

Le lot `com.adobe.granite.apicontroller` est manquant dans AEM 6.5 LTS SP2. Ce lot contrôle la manière dont les lots OSGi sont résolus et peut empêcher les lots de se résoudre sur d’autres lots, ce qui est utile pour limiter les API exposées.

Installez le correctif à partir de [Distribution logicielle](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq660/hotfixes/cq-6.5.lts.2-hotfix-GRANITE-67640-1.0.zip) pour utiliser cette fonctionnalité.

>[!NOTE]
>
> Après avoir installé le correctif, vérifiez le statut de tous les lots installés pour vous assurer que la configuration par défaut de `com.adobe.granite.apicontroller` n’a pas introduit de restrictions de résolution involontaires susceptibles d’affecter les implémentations personnalisées existantes.

### Les commentaires JSON ne sont plus pris en charge dans Sling-Initial-Content (SP2) {#json-comments-no-longer-supported-in-sling-initial-content}

Ce problème affecte le développement et l’administration de lots OSGi qui déploient des lots qui utilisent `Sling-Initial-Content` avec des fichiers JSON.

À compter d’AEM 6.5 LTS SP2, les fichiers JSON utilisés dans les lots `Sling-Initial-Content` n’acceptent plus les commentaires (`//` ou `/* */`). Les versions précédentes d’AEM acceptaient les commentaires car le fournisseur de `javax.json` était indulgent à ce sujet. AEM 6.5 LTS SP2 a mis à niveau `org.apache.sling.jcr.contentloader` vers la version 2.6.0, qui a basculé l’analyseur JSON sur `jakarta.json`. Bien que la [spécification JSON (RFC 8259)](https://datatracker.ietf.org/doc/html/rfc8259) ne définisse pas de syntaxe pour les commentaires, les versions antérieures d’AEM les ont acceptés en raison de la clémence du fournisseur de `javax.json`. Le fournisseur de `jakarta.json` ne propose pas cette extension.

L’échec n’est pas signalé : les nœuds de contenu ne parviennent pas à se charger lors de l’activation du lot sans qu’aucune erreur ne soit visible pour le programme d’installation. Si du contenu est manquant de manière inattendue après la mise à niveau vers SP2, vérifiez les journaux du programme d’installation OSGi pour détecter les erreurs d’analyse JSON. Pour identifier les lots affectés, recherchez `//` ou `/* */` dans les fichiers JSON répertoriés sous les en-têtes de manifeste `Sling-Initial-Content`.

>[!CAUTION]
>
> Supprimez tous les commentaires des fichiers JSON dans les lots `Sling-Initial-Content` pour éviter les échecs de chargement de contenu après la mise à niveau vers AEM 6.5 LTS SP2.

### Installez les index Oak requis pour les API Sites en mode découplé{#site-headless-api}

Certaines API déplacées vers Sites en mode découplé nécessitent des index Oak supplémentaires pour une fonctionnalité complète.

Installez le package `cq-dam-cfm-indices` pour utiliser les fonctionnalités suivantes :

* Lister les modèles de fragment de contenu
* Répertorier les fragments de contenu
* API de recherche
* Workflows

Téléchargez le package d’index [cq-dam-cfm-indices](https://experience.adobe.com/#/downloads/content/software-distribution/fr/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/cq-dam-cfm-indices-1.1.2.zip) à partir du portail de distribution logicielle Adobe.

### Échec de connexion à Dispatcher avec la fonction SSL uniquement (corrigé dans AEM 6.5 LTS SP1 et versions ultérieures){#ssl-only-feature}

>[!NOTE]
>
> Ce problème est uniquement présent dans la version AEM 6.5 LTS en disponibilité générale.

Lors de l’activation de la fonction SSL uniquement dans les déploiements AEM, un problème connu affecte la connectivité entre les instances Dispatcher et AEM. Une fois cette fonctionnalité activée, les contrôles d’intégrité peuvent échouer et la communication entre les instances Dispatcher et AEM peut être interrompue. Ce problème se produit plus particulièrement lorsque les clientes et clients tentent de se connecter via `https + IP` à partir des instances Dispatcher vers AEM. Il est lié aux problèmes de validation SNI (Server Name Indication).

**Impact**

* Échec des contrôles d’intégrité avec les codes de réponse HTTP 400.
* Trafic rompu entre les instances Dispatcher et AEM.
* Contenu diffusé incorrectement via Dispatcher.
* Échecs de connexion lors de l’utilisation de HTTPS avec des adresses IP dans la configuration Dispatcher.
* Erreurs HTTP 400 « SNI non valide » lors de la connexion via HTTPS + IP.

**Environnements affectés**

* Déploiements d’AEM avec les configurations Dispatcher.
* Systèmes sur lesquels la fonction SSL uniquement a été activée.
* Configurations Dispatcher utilisant la méthode de connexion `https + IP` aux instances AEM.

**Solution**

Si vous rencontrez ce problème, contactez l’Assistance Client d’Adobe. Un correctif [cq-6.5.lts.0-hotfix-CQ-4359803](https://experience.adobe.com/#/downloads/content/software-distribution/fr/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq660/hotfixes/cq-6.5.lts.0-hotfix-CQ-4359803-1.0.2.zip) est disponible pour résoudre ce problème. N’essayez pas d’activer les fonctions SSL uniquement avant d’avoir appliqué le correctif nécessaire.

## Lots OSGi et modules de contenu inclus{#osgi-bundles-and-content-packages-included}

Les fichiers zip suivants contiennent les documents texte qui répertorient les lots OSGi et les packages de contenu inclus dans cette version du pack de services LTS Experience Manager 6.5 :

* [lots OSGi](/help/release-notes/assets/65lts_sp2_bundles.zip)
* [Packages de contenu](/help/release-notes/assets/65lts_sp2_packages.zip)

## Sites web à accès limité{#restricted-sites}

Ces sites Web sont disponibles uniquement pour les clients. Si vous êtes client et avez besoin d’un accès, contactez votre responsable de compte Adobe.

* [Téléchargement du produit à l’adresse licensing.adobe.com](https://licensing.adobe.com/)
* [Contacter l’assistance clientèle Adobe](https://experienceleague.adobe.com/fr/docs/support-resources/adobe-support-tools-guide/adobe-customer-support-experience).

