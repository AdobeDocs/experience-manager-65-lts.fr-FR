---
title: Notes de mise à jour actuelles pour Adobe Experience Manager 6.5 LTS, SP3
description: Recherchez les informations de mise à jour actuelles pour Adobe Experience Manager 6.5 LTS, Service Pack 3.
solution: Experience Manager
feature: Release Information
role: User,Admin,Developer
exl-id: b5a8f555-c061-4fe2-a100-cc01335959cb
source-git-commit: 79f3d3211a79ce62242273df0cdecd24cd8900cf
workflow-type: tm+mt
source-wordcount: '6705'
ht-degree: 26%

---


# Notes de mise à jour actuelles pour Adobe Experience Manager 6.5 LTS, SP3 {#release-notes}

## Informations sur la version {#release-information}

| Produit | [!DNL Adobe Experience Manager] 6.5 LTS |
|---|---|
| Version | Service Pack 3 (SP3) <!-- UPDATE FOR EACH NEW RELEASE --> |
| Type | Mise à jour du pack de services |
| Date | 20 août 2026 <!-- UPDATE FOR EACH NEW RELEASE --> |
| URL de téléchargement | [Distribution logicielle](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/servicepack-lts/cq-quickstart-6.6.3.jar) |


<!-- UPDATE ABOVE FOR EACH NEW RELEASE -->

<!-- **Mandatory Hotfix** – To avoid SNFE (SegmentNotFoundException) issues with offline compaction when installing SP2, install the hotfix described in [Known issues – Repository corruption during online compaction](#repository-corruption-during-online-compaction-after-offline-compaction-granite-65146). -->

## Éléments compris dans [!DNL Adobe Experience Manager] 6.5 LTS, SP3 {#what-is-new}

<!-- UPDATE EACH RELEASE -->

[!DNL Experience Manager] 6.5 LTS, SP3 comprend de nouvelles fonctionnalités, des améliorations importantes demandées par les clients et des correctifs de bugs. Elle améliore les performances, la sécurité et la localisation sur l’ensemble de la plateforme depuis la disponibilité initiale de 6,5 LTS en mars 2025. [Installez ce Pack de services](#install-update) sur la version 6.5 LTS.

### Présentation des problèmes résolus {#fixed-issues-overview}

[!DNL Adobe Experience Manager] 6.5 LTS, SP3 résout les problèmes liés à [!DNL Sites] et [!DNL Experience Manager Foundation]. Ces correctifs améliorent l’accessibilité, la fiabilité de création, la diffusion de contenu découplé, la gestion multisite et la stabilité de la plateforme. Les sections qui suivent énumèrent chaque correctif avec son numéro de référence.

La plupart des modifications s’appliquent aux [!DNL Sites] :

* Les améliorations de l’accessibilité représentent le groupe le plus important. Les mises à jour améliorent la navigation au clavier, les commentaires du lecteur d’écran, la gestion du focus, le balisage sémantique, le contraste du texte et le dimensionnement de la cible tactile dans l’éditeur de page, le rail latéral Assets, les filtres et les interfaces de création associées.
* Les correctifs d’[!DNL Content Fragments] couvrent l’éditeur de fragments, l’éditeur de modèles, l’API REST et l’API GraphQL. Les mises à jour corrigent la localisation, la validation des champs, le comportement de modification et la gestion des réponses.
* Les correctifs de Live Copies MSM permettent aux auteurs de déployer les modifications de manière fiable à partir des pages de plan directeur et de conserver la configuration de déploiement existante.
* La prise en charge de Crosswalk est disponible sur Adobe Managed Services, y compris les lots, les utilisateurs système et la configuration requis.
* D’autres correctifs portent sur les interfaces admin et classiques, les composants principaux, la console des composants, l’intégration de Campaign, les fragments d’expérience et les lancements.

Les modifications restantes s’appliquent aux [!DNL Experience Manager Foundation] :

* Les mises à jour de localisation traduisent le texte auparavant uniquement en anglais dans les rapports d’intégrité, la console des opérations et plusieurs interfaces de création.
* Les correctifs de stabilité restaurent le point d’entrée de surveillance de l’intégrité, maintiennent le service de messagerie en cours d’exécution après des erreurs de configuration intermittentes, et corrigent la variable de workflow et la modification du package de workflow.
* Cette version ajoute également la prise en charge d’AEM Context Service et résout les problèmes de sécurité, de traduction et d’interface utilisateur.

Pour obtenir la liste complète, voir [Correction de problèmes dans 6.5 LTS, Service Pack 3](#fixed-issues).


<!-- ## Key features and enhancements -->



<!-- UPDATE THE EACH RELEASE -->

## Correction de problèmes dans 6.5 LTS, Service Pack 3 {#fixed-issues}

### [!DNL Sites]{#sites-65-LTS-SP3}

* Le pack de services 3 d’AEM 6.5 LTS comprend les lots Crosswalk, le package de contenu, les utilisateurs système, les mappages service-utilisateur, les basculements de fonctionnalités et la configuration OSGi requise. Les nouvelles installations fournissent automatiquement les conditions préalables requises pour Crosswalk et ne nécessitent qu’une configuration d’exécution spécifique au client. (SITES-41596)
* AEM 6.5 LTS, Service Pack 3 met à jour `cq-wcm-core` pour prendre en charge Crosswalk sur Adobe Managed Services. La mise à jour ajoute la création de modèles et l’accès à l’éditeur universel tout en supprimant le code personnalisé obsolète et les bascules de fonctionnalités. (SITES-37657)


#### Accessibilité {#sites-accessibility-65-lts-sp3}

* La zone de travail de l’éditeur de page prend désormais en charge la gestion des composants à l’aide du clavier uniquement. Les auteurs peuvent utiliser Insérer un composant, Couper, Coller et Supprimer pour ajouter, réorganiser et supprimer des composants. (SITES-25359) CRITIQUE
* Utilisez le clavier pour réorganiser les lignes du tableau en mode Liste de sites sans utiliser de glisser-déposer. Les commandes au clavier permettent aux utilisateurs de sélectionner une ligne, de la déplacer vers une autre position et de terminer l’emplacement. (SITES-24946) CRITIQUE

* L’éditeur Propriétés personnalisées prend désormais en charge les interactions clavier avec ses commandes de mise en forme. Les auteurs peuvent déplacer la sélection parmi les options de la barre d’outils, sélectionner un style de texte et mettre en forme les valeurs de propriété à l’aide d’un seul clavier. (SITES-40333) MAJEUR

* La sélection du clavier ignore désormais la liste Composants du panneau latéral lorsque l’interaction disponible nécessite un glisser-déposer. Cette modification empêche les utilisateurs et utilisatrices du clavier de saisir un workflow de sélection de composant inutilisable. (SITES-40752)
* La fermeture d’un recouvrement restaure désormais le focus sur son contrôle de déclenchement. Les utilisateurs d’un clavier et d’un lecteur d’écran ne reviennent plus à la superposition ou perdent leur position dans l’interface. (SITES-40819)
* La navigation au clavier ne déplace plus le focus vers le contenu de page masqué. Cette modification maintient une séquence de mise au point prévisible et empêche les perturbations de la navigation. (SITES-41430)
* Le bouton Verrouiller fournit désormais un retour d’informations précis pour le lecteur d’écran, en fonction de son titre. Les utilisateurs et utilisatrices entendent un libellé d’action clair au lieu d’une description longue. (SITES-41431)
* Un indicateur visuel identifie désormais l&#39;option sélectionnée dans la zone de liste Modifier le fichier ou le dossier. L’indicateur aide les utilisateurs et utilisatrices à comprendre le chemin de navigation et à reconnaître le dossier actif. (SITES-25532)
* Les lecteurs d’écran annoncent désormais le sens de tri croissant ou décroissant une fois. Un libellé descriptif identifie clairement l’action du bouton et supprime les commentaires en double. (SITES-25534)
* AEM Sites offre désormais une prise en charge plus large de l’accessibilité dans les workflows de création courants. Les mises à jour améliorent l’interaction au clavier, les libellés d’interface, la gestion des priorités et les commentaires sur les technologies d’assistance. (SITES-38239)
* Les éléments de la barre d’outils affichent désormais des libellés visibles lorsqu’ils reçoivent le focus au clavier. Au clavier, les utilisateurs peuvent identifier chaque commande avant de l’activer. (SITES-40751)
* Les utilisateurs d’un clavier ou d’un lecteur d’écran peuvent désormais quitter le menu de la boîte de réception sans la laisser ouverte. Le menu se ferme automatiquement et conserve un chemin de navigation clair. (SITES-25518)
* Les échantillons de couleurs affichent désormais une icône d’état sélectionné avec un contraste suffisant. L’indicateur plus clair permet aux utilisateurs et utilisatrices de reconnaître l’échantillon actif dans différentes couleurs d’arrière-plan. (SITES-25523)
* La barre d’outils Modifier la disposition signale désormais précisément l’appareil actuel à la technologie d’assistance. Les boutons de l’appareil ne suggèrent plus que les utilisateurs peuvent activer et désactiver chaque bouton. (SITES-25524)
* La boîte de dialogue modale de recherche affiche désormais le libellé **Trier par** avec un contraste de texte suffisant. Le style mis à jour améliore la lisibilité pour les utilisateurs souffrant de déficience visuelle. (SITES-25531)
* Les boutons de tri de la vue Liste de sites répondent désormais aux exigences de contraste minimales. Les utilisateurs et utilisatrices peuvent identifier plus facilement chaque commande de tri et son état sur l’arrière-plan du tableau. (SITES-25372)
* La liste Assets du rail latéral ne se recharge plus lorsque le champ Filtre reçoit le focus au clavier. Les utilisateurs peuvent entrer dans le champ sans déplacement de contenu inattendu ni annonces de chargement répétées de lecteur d’écran. (SITES-25377)
* Les onglets de la barre latérale Fragment de contenu fournissent désormais des libellés accessibles cohérents. NVDA annonce le nom de l’onglet au lieu d’annoncer l’élément de sous-navigation sélectionné. (SITES-25509)
* Le menu Aide se ferme lorsque le focus du clavier ou du lecteur d’écran se déplace en dehors de celui-ci. Les utilisateurs peuvent continuer à parcourir les commandes d’en-tête ou le contenu de la page sans quitter le menu ouvert. (SITES-25517)
* Le texte saisi dans les champs de la barre d’outils Démographie répond désormais aux exigences de contraste minimales. Les utilisateurs peuvent lire plus clairement les valeurs de profil par rapport à l’arrière-plan du champ de texte. (SITES-25318)
* Le menu Informations sur la page affiche désormais les options sélectionnées avec un contraste de texte suffisant. Le style plus clair permet aux utilisateurs de suivre la sélection du clavier tout au long du menu. (SITES-25321)
* Les cases à cocher dans les boîtes de dialogue Teaser, Image et Carrousel exposent désormais leurs instructions associées aux lecteurs d’écran. Les utilisateurs entendent la description complémentaire lorsque le focus au clavier atteint chaque case à cocher. (SITES-25364)
* Les contrôles de l’éditeur de texte communiquent désormais leur état actuel à la technologie d’assistance. Les lecteurs d’écran identifient le format de paragraphe actif et l’option cible de lien hypertexte sélectionnée. (SITES-25367)
* Les lecteurs d’écran annoncent maintenant clairement le bouton **Rotation de l’appareil** et l’orientation actuelle de l’appareil. L’activation du contrôle signale la nouvelle orientation sans utiliser de libellé qui décrit l’action opposée. (SITES-25292)
* La navigation au clavier ignore désormais les commandes masquées dans la barre d’outils Démographie réduite. Les utilisateurs peuvent se déplacer dans la Prévisualisation de la mise en page sans rencontrer d’options de barre d’outils indisponibles. (SITES-25304)
* Les libellés de texte de la barre d’outils Démographie répondent désormais aux exigences de contraste minimales lors de la prévisualisation de la mise en page. Les utilisateurs peuvent lire plus clairement des libellés tels que Recommandé en arrière-plan de la barre d’outils. (SITES-25307)
* La barre d’outils Démographie affiche désormais les indicateurs de focus du bouton avec un contraste suffisant. Les utilisateurs peuvent identifier le Commerce actif, le persona ou la commande Appareil lors de la navigation au clavier. (SITES-25308)
* La barre d’outils Modifier la disposition utilise un indicateur de sélection groupé pour le sélecteur d’appareils. La composition comprend les commandes **Sélectionner l’appareil** et **Rotation de l’appareil** associées au comportement prévu de la barre d’outils. (SITES-25283)
* La barre d’outils Modifier la mise en page ne tronque plus le libellé **iPhone 8 Plus** lorsque les utilisateurs sélectionnent un autre appareil. Le nom complet de l’appareil reste visible dans tous les états du bouton. (SITES-25284)
* L’option Modifier la disposition fournit désormais un contexte de mesure aux lecteurs d’écran. Les utilisateurs entendent une étiquette descriptive et le format de mesure au lieu d’une série de nombres inexpliqués. (SITES-25287)
* La barre d’outils Modifier la disposition met désormais en surbrillance le bouton **Bureau** lorsque l’affichage du bureau est actif. L’indicateur visuel efface la sélection actuelle de l’appareil. (SITES-25290)
* Le focus au clavier reste désormais visible sur le bouton d’échantillon pour toutes les couleurs disponibles. L’ajout d’un espacement empêche l’indicateur de focus de se fondre dans la nuance sélectionnée. (SITES-25253)
* Les lecteurs d’écran identifient désormais correctement le champ Date de distorsion du temps. Le champ ne fournit plus de commentaires trompeurs suggérant qu’il ouvre une boîte de dialogue. (SITES-25263)
* Le libellé du bouton Annotation répond désormais aux exigences de contraste minimales dans ses états par défaut et de survol. Les utilisateurs peuvent lire le libellé clairement sur l’arrière-plan du bouton. (SITES-25267)
* Les lecteurs d’écran annoncent désormais des libellés significatifs pour les commandes dans la boîte de dialogue Annotation. Chaque bouton communique son action sans préfixe d’annotation inutile. (SITES-25277)
* Le bouton Modifier du rail latéral d’Assets fournit désormais une cible tactile plus large. Les utilisateurs peuvent activer le contrôle de manière plus fiable sans sélectionner d’élément à proximité. (SITES-25221)
* L’éditeur de page utilise désormais une hiérarchie d’en-tête logique. Les lecteurs d’écran identifient le titre de la page comme en-tête principal et les titres des rails latéraux comme en-têtes subordonnés. (SITES-25222)
* La boîte de dialogue Annotation expose désormais son titre sous la forme d’un en-tête sémantique. Les utilisateurs de lecteurs d’écran peuvent identifier le titre et parcourir la structure de la boîte de dialogue à l’aide des commandes d’en-tête. (SITES-25248)
* Les utilisateurs de lecteurs d’écran reçoivent désormais des commentaires lorsqu’ils filtrent la liste Insérer un nouveau composant . Le champ de recherche décrit son comportement de filtrage, et un message de statut indique le nombre de résultats. (SITES-25251)
* Le panneau Composants du rail latéral utilise désormais des balises de liste sémantiques. Les lecteurs d’écran peuvent annoncer le nombre d’éléments et prendre en charge une navigation efficace dans les listes. (SITES-25214)
* Les boutons Infos utilisent désormais des icônes plus grandes dans le panneau Composants . Les utilisateurs peuvent localiser et reconnaître plus facilement chaque commande. (SITES-25217)
* Les titres des composants restent désormais visibles lorsque les utilisateurs augmentent l’espacement du texte. Les titres longs s’encapsulent au lieu de tronquer ou de chevaucher le contenu voisin. (SITES-25219)
* Le bouton Rail latéral Assets **Modifier** indique désormais qu’il ouvre un nouvel onglet du navigateur. Les repères visuels et les lecteurs d’écran préparent les utilisateurs avant la navigation. (SITES-25220)
* Le mode Annotation place désormais le focus au clavier sur la barre d’outils d’annotation lorsque celle-ci s’ouvre. Les utilisateurs d’un clavier ou d’un lecteur d’écran peuvent se déplacer parmi les commandes dans une séquence logique sans revenir en arrière à partir du bouton **Fermer**. (SITES-24996)
* Les boutons Sélectionner pour les champs Chemin d’accès et Balises n’utilisent plus d’icône de case à cocher. L&#39;icône mise à jour indique que le contrôle ouvre une boîte de dialogue de sélection au lieu de changer un état coché. (SITES-25210)
* Le champ Filtre du panneau Composants du rail latéral comporte désormais un libellé accessible valide. Les lecteurs d’écran annoncent l’objectif du champ au lieu de s’appuyer sur une icône ou un texte d’espace réservé. (SITES-25212)
* Le rail latéral d’Assets masque désormais les miniatures décoratives des lecteurs d’écran. Les utilisateurs n’entendent plus deux fois le nom de la ressource lorsqu’ils naviguent dans la grille de la ressource. (SITES-25213)
* Les boutons d’accordéon du rail Filtres affichent désormais les indicateurs de focus avec un contraste suffisant. Utilisez le clavier pour suivre la cible lors de la navigation dans les catégories de filtres. (SITES-24986)
* Le rail Filtres affiche désormais la sélection du clavier clair autour des boutons radio. Un contraste accru permet aux utilisateurs de suivre leur position dans les options de filtre. (SITES-24987)
* Le chargement des messages de statut sur la page Filtres répond désormais aux exigences minimales en matière de contraste du texte. Les utilisateurs peuvent lire les commentaires sur la progression lorsqu’ils basculent entre les vues Carte et Liste. (SITES-24991)
* Le titre de la page dans la zone de travail de l’éditeur utilise désormais le balisage sémantique d’en-tête. Les technologies d’assistance peuvent annoncer le titre et l’inclure dans la navigation d’en-tête. (SITES-24993)
* Le développement du menu Émulateur déplace désormais le focus au clavier vers le premier élément de menu. La réduction du menu garde le focus dans la séquence logique secondaire de la barre d’outils. (SITES-24954)
* Le texte du tableau Vue en direct répond désormais aux exigences minimales en matière de contraste. Les utilisateurs peuvent lire clairement les détails de la Live Copy dans des états normaux et de survol. (SITES-24956)
* Le rail Références utilise désormais un balisage d’en-tête sémantique pour son titre. Les lecteurs d’écran annoncent le titre lors du chargement initial et lorsque les utilisateurs parcourent les dossiers. (SITES-24967)
* Les liens des cartes décrivent désormais clairement leurs destinations. Les utilisateurs de lecteurs d’écran peuvent identifier chaque lien sans entendre les métadonnées complètes de la carte. (SITES-24975)
* Les boutons du menu d’en-tête n’indiquent plus aux lecteurs d’écran qu’ils ouvrent des boîtes de dialogue. Les lecteurs d’écran annoncent plutôt l’état développé ou réduit de chaque bouton, qui décrit avec précision le comportement du menu. (SITES-24742)
* Le texte du bouton Supprimer offre désormais un contraste suffisant sur son arrière-plan rouge. Les utilisateurs peuvent identifier plus facilement l’action avant de confirmer la suppression. (SITES-24772)
* Les cartes zone de travail n’exposent plus d’images et de liens d’en-tête distincts menant à la même destination. Un lien unique réduit les arrêts de clavier en double et les annonces répétées du lecteur d’écran. (SITES-24947)
* La vue Liste affiche désormais le bouton glisser-déposer avec une plus grande visibilité visuelle. La mise à jour de la taille, de l’épaisseur et du contraste de l’icône facilite la localisation et l’utilisation du contrôle. (SITES-24951)
* Les boutons d’en-tête fournissent désormais des noms accessibles concis : Recherche, Applications, Aide, Boîte de réception et Utilisateur. Les lecteurs d’écran n’annoncent plus de termes redondants tels que « cliquable » ou « graphique » lors de la navigation au clavier. (SITES-24715)
* Les liens dans la navigation de l’application affichent désormais une accentuation visuelle plus forte. Une taille et un poids de texte accrus améliorent la lisibilité pour les utilisateurs présentant une faible vision ou des différences de vision des couleurs. (SITES-24723)
* Les liens de la boîte de réception utilisent désormais le balisage de liste sémantique. Les lecteurs d’écran peuvent identifier les liens en tant que groupe associé, annoncer le nombre d’éléments et prendre en charge une navigation plus efficace. (SITES-24730)
* Les commandes d’info-bulles de la boîte de dialogue Préférences utilisateur exposent désormais des noms accessibles descriptifs. Les lecteurs d’écran annoncent l’objectif de chaque contrôle au lieu de dire « vide » avant de lire le contenu de l’info-bulle. (SITES-24732)
* Chaque repère de rail de filtre comprend désormais un libellé accessible unique. Les lecteurs d’écran peuvent distinguer le rail de filtre des autres régions de page et l’identifier lors de la navigation. (SITES-24686)
* Les boîtes de dialogue de l’éditeur séparent désormais les boutons Aide et Activer/désactiver le plein écran de l’élément d’en-tête. Les lecteurs d’écran identifient ces commandes interactives avec précision et ne les annoncent plus comme des en-têtes. (SITES-24696)
* Le bouton Rapport CSV avertit désormais les utilisateurs avant d’ouvrir un nouvel onglet du navigateur. Son libellé accessible communique le comportement aux utilisateurs d’un lecteur d’écran ou d’un clavier avant l’activation. (SITES-24704)
* Le rail de filtre charge désormais les libellés pour les recherches enregistrées et Sélectionner le répertoire de recherche de manière cohérente. Le bouton Filtres n’insère plus d’éléments de libellé lors des interactions de sélection, de clavier ou de souris. (SITES-24706)
* Les boutons Fermer et Supprimer l’emplacement fournissent désormais des cibles tactiles plus grandes. Les utilisateurs peuvent activer l’un des contrôles de manière plus fiable sans sélectionner d’éléments adjacents. (SITES-24530)
* Le bouton Supprimer l’emplacement et son indicateur de focus répondent désormais aux exigences de contraste minimales. Un contraste plus fort permet aux utilisateurs d’identifier la commande et de suivre le focus au clavier. (SITES-24531)
* Les iFrames d’éditeur incluent désormais des titres descriptifs sur la zone de travail, les rails latéraux, les boîtes de dialogue de composant et l’aperçu de la disposition. Les lecteurs d’écran peuvent identifier chaque image lorsque le focus y entre. (SITES-24650)
* L’amélioration du contraste du texte facilite la lecture des messages du rail de références. La modification clarifie les invites qui demandent une sélection ou signalent les références indisponibles. (SITES-24666)
* Le panneau Composants donne à chaque icône d’information un libellé accessible significatif. Les lecteurs d’écran identifient de manière cohérente le contrôle qui affiche une description de composant. (SITES-24500)
* La sélection du clavier entoure désormais l’ensemble du bouton Afficher la description de la signature. Le contour visible permet aux utilisateurs de suivre leur position et d’éviter d’activer un autre contrôle. (SITES-24503)
* La boîte de dialogue du composant Teaser n’expose plus les boutons Aide et Activer/désactiver le plein écran en tant qu’en-têtes. Les lecteurs d’écran annoncent les deux commandes sous forme de boutons et conservent la structure d’en-tête correcte. (SITES-24525)
* Le contrôle d’en-tête Adobe Experience Manager indique correctement son état développé ou réduit. Le contrôle ouvre et ferme le contenu de navigation, de sorte que les lecteurs d’écran reçoivent des informations d’état valides. (SITES-24528)
* Les résultats du filtre marquent les icônes de globe comme décoratives et suppriment leurs noms accessibles. Les lecteurs d’écran ignorent les icônes au lieu d’annoncer des descriptions trompeuses. (SITES-3057)
* La boîte de dialogue Distorsion du temps associe désormais les erreurs de saisie d’heure au champ Heures ou Minutes correspondant. Les lecteurs d’écran annoncent le champ affecté avec le message de validation. (SITES-10980)
* L’élément d’arborescence de contenu sélectionné ne fait plus partie du libellé Modifier le fichier ou le contrôle de dossier. Les lecteurs d’écran entendent un nom de contrôle clair sans texte d’état supplémentaire. (SITES-24496)
* Les repères de région du rail latéral d’Assets exposent désormais des noms accessibles distincts. Les utilisateurs de lecteurs d’écran peuvent identifier et parcourir chaque zone géographique sans ambiguïté. (SITES-24497)
* Les lecteurs d’écran ignorent désormais les icônes Aide décorative et Plein écran de la boîte de dialogue Carrousel. La navigation au clavier ne déclenche plus les annonces d’icônes inutiles. (SITES-2912)
* Les lecteurs d’écran ignorent désormais les icônes de la barre d’outils décorative dans la boîte de dialogue Teaser . Les contrôles Aide, Plein écran, Mise en forme et Lien ne génèrent plus d’annonces redondantes. (SITES-2934)


#### Interface d’utilisation d’administration{#sites-adminui-65-lts-sp3}

* AEM permet désormais aux membres du groupe d’administrateurs de déverrouiller des pages et d’emprunter l’identité d’utilisateurs. Les membres du groupe peuvent effectuer les deux tâches administratives via leur accès existant. (SITES-14732)
* La vue Administration d’Assets met désormais à jour une carte de ressource une fois que les auteurs ont sélectionné **Rétablir cette version** dans le journal. La miniature affiche immédiatement la version restaurée et n’affiche plus de contenu d’aperçu obsolète. (SITES-46590)


#### Interface d’utilisation classique{#sites-classicui-65-lts-sp3}

Les propriétés de la copie de la langue indonésienne affichent le code de langue d’identification correct. Le rail Références ne remplace plus IN lorsque les auteurs créent ou révisent une copie de langue indonésienne. (SITES-44918)


#### [!DNL Content Fragments]{#sites-contentfragments-65-lts-sp3}

La console Assets répond désormais lorsque les utilisateurs appliquent des filtres de recherche. La modification d’un filtre de modèle de fragment de contenu actualise les résultats au lieu de laisser la liste de ressources actuelle inchangée. (SITES-38686) MAJEUR


#### [!DNL Content Fragments] - Admin{#sites-admin-65-lts-sp3}

* La page Assets localise désormais l’info-bulle d’un fragment de contenu verrouillé. Les utilisateurs voient le libellé traduit **Extrait par** lorsqu’ils survolent l’indicateur de verrouillage. (SITES-42531) MAJEUR

* AEM localise le message de validation Nom non valide fourni lors de la création du fragment de contenu. Les caractères de titre non pris en charge ne déclenchent plus de texte en anglais dans les interfaces non anglaises. (SITES-19796)
* AEM traduit la chaîne Modèles de fragment de contenu lors de la création de fragments de contenu. L’interface d’Assets n’affiche plus le texte anglais de ce libellé dans les environnements localisés. (SITES-22336)
* Les services de fragments de contenu ne reposent plus sur une logique de basculement de fonctionnalités obsolète. La mise en œuvre rationalisée supprime les branches dépendantes du basculement et assure la cohérence du comportement du pack de services. (SITES-38688)
* AEM traduit l’option Plus tard lors de la publication planifiée de fragments de contenu. Le workflow de publication correspond à la langue de l’interface active. (SITES-42532)
* AEM traduit la chaîne principale dans la boîte de dialogue de téléchargement des fragments de contenu. La section Eléments correspond à la langue de l’interface active. (SITES-42534)


#### [!DNL Content Fragments] - Éditeur de fragments{#sites-fragments-editor-65-lts-sp3}

* L’éditeur de fragment de contenu positionne désormais correctement les menus déroulants de l’éditeur de texte enrichi. Chaque menu reste aligné avec son contrôle de barre d&#39;outils et garde visibles les contrôles de mise en forme à proximité. (SITES-44005) CRITIQUE

* Le bouton Modifier le fragment de contenu s’affiche désormais et fonctionne immédiatement pour les entrées de champs multiples de référence. Les auteurs n’ont plus besoin d’enregistrer, de fermer et de rouvrir le fragment de contenu parent avant de modifier un fragment incorporé. (SITES-43733) MAJEUR

* L’éditeur de fragment de contenu affiche une composition de focus lorsque les auteurs sélectionnent un champ de texte multiligne. La composition ne duplique plus ou ne chevauche plus les contrôles voisins. (SITES-39253)
* La création de fragment de contenu affiche le texte d’espace réservé CJC sans style italique. Les caractères japonais, coréens, chinois simplifié et chinois traditionnel conservent l’apparence prévue. (SITES-43548)
* L’éditeur de fragment de contenu actualise la bannière d’état une fois que les auteurs ont enregistré ou publié un fragment. Les auteurs peuvent confirmer les états Modifié, Enregistré ou Publié sans recharger l’onglet du navigateur. (SITES-45897)
* L’éditeur de fragment de contenu valide les champs de manière cohérente après les modifications de l’IU Granite. Les bibliothèques clientes mises à jour restaurent le comportement de validation attendu. (SITES-46650)


#### [!DNL Content Fragments] - API GraphQL {#sites-graphql-api-65-lts-sp3}

* Les réponses JSON GraphQL incluent désormais des références d’image incorporées lorsque les noms de fichier DAM contiennent des espaces ou des caractères non-ASCII. Les applications clientes peuvent récupérer et générer ces images sans renommer les ressources. (SITES-42191) MAJEUR
* L’API GraphQL de fragments de contenu comprend désormais plusieurs mises à jour du traitement des requêtes et de la gestion des réponses. Les modifications empêchent les en-têtes et valeurs de cache en double, améliorent le codage, conservent les informations de statut de la requête persistante, gèrent les en-têtes vides et renvoient les erreurs de point d’entrée appropriées. (SITES-40159) MAJEUR
* PersistedQueryServlet traite désormais les variables codées dans des requêtes persistantes GraphQL valides sans enregistrer de fausses erreurs ou d’avertissements. Les requêtes continuent à renvoyer des réponses réussies tandis que les journaux reflètent leur statut d’exécution réel. (SITES-39354) MAJEUR

* Le rechargement de la page Points d’entrée GraphQL conserve le message d’état vide localisé. La page ne revient plus en anglais lorsqu’il n’existe aucun point d’entrée. (SITES-43586)


<!--#### [!DNL Content Fragments] - GraphQL Query Editor{#sites-graphql-query-editor-65-lts-sp3}-->


#### [!DNL Content Fragments] - Éditeur de modèles{#sites-model-editor-65-lts-sp3}

* La console Modèles de fragment de contenu affiche désormais les miniatures chargées pour les configurations dont le nom contient des caractères localisés. Les auteurs ne perdent plus les aperçus des miniatures lorsque les noms de configuration utilisent du texte non anglais. (SITES-39242) MAJEUR

* L’éditeur de modèle de fragment de contenu affiche du texte localisé **Libellé du champ** dès que les auteurs ajoutent un composant à la zone de travail. Les auteurs n’ont plus besoin d’enregistrer et de rouvrir le modèle pour voir la traduction. (SITES-45383)
* L’éditeur de modèle de fragment de contenu localise le message de validation affiché lorsque les auteurs sélectionnent un type de modèle non valide pour un composant composite. Le message correspond désormais au paramètre régional actif au lieu de s’afficher uniquement en anglais. (SITES-41117)
* L’éditeur de modèle de fragment de contenu localise tout le texte de la boîte de dialogue Le modèle est verrouillé . La boîte de dialogue ne mélange plus les étiquettes de bouton et les instructions en anglais avec le texte d’interface traduit. (SITES-28592)



#### [!DNL Content Fragments] - API REST{#sites-restapi-65-lts-sp3}

Le lot d’API REST de fragment de contenu découplé supprime les basculements de fonctionnalités obsolètes et le code conditionnel associé. Le comportement de l’API pris en charge reste inchangé, tandis que le lot ne conserve que les options de basculement requises pour les fonctionnalités actives. (SITES-39113)



#### Console des composants{#sites-component-console-65-lts-sp3}

L’outil de recherche de contenu répertorie désormais les ressources dont les noms contiennent des caractères non codables sans échec ni génération d’exceptions. La page Utilisation en direct des composants charge également en continu des jeux de résultats volumineux sans afficher de lignes vides lors du défilement. (SITES-44672) MAJEUR

<!--
#### Content API{#sites-content-api-65-lts-sp3}

#### Core backend{#sites-core-backend-65-lts-sp3}
-->

#### Composants principaux{#sites-core-components-65-lts-sp3}

* Les composants multichamps stockent désormais une sélection de ressources distantes distincte pour chaque entrée. Les auteurs peuvent sélectionner, modifier et enregistrer des images distantes sans dupliquer une image sur chaque élément multichamp. (SITES-42376) MAJEUR
* ThumbnailServlet arrête désormais le traitement après avoir redirigé une demande de ressource manquante. Cette modification empêche les exceptions de pointeurs nuls répétées et la journalisation excessive des erreurs lors de la navigation dans la gestion des ressources numériques et la console. (SITES-41238) MAJEUR


#### Intégration de campagne{#sites-campaign-integration-65-lts-sp3}

Le Content Servlet Campaign conserve désormais le type de contenu de réponse JSON lors des requêtes de contenu. Cette modification arrête les entrées de journal `WARN` et `ERROR` qui se sont produites à plusieurs reprises après une mise à niveau à partir d’AEM 6.5.24. (SITES-46902) MAJEUR


#### Fragments d’expérience{#sites-experiencefragments-65-lts-sp3}

Les auteurs peuvent désormais parcourir plus de 40 modèles tout en créant une variation de fragment d’expérience. Chaque page supplémentaire conserve le filtre de dossier d’origine et affiche les modèles correspondants suivants. (SITES-41531) MAJEUR


<!-- #### Foundation Components (Legacy){#sites-foundation-components-legacy-65-lts-sp3} -->


#### Lancements{#sites-launches-65-lts-sp3}

L’historique des promotions Launch affiche désormais du texte localisé dans la chronologie Sites. La chronologie traduit les messages « Version créée de » et « avant la promotion du lancement » dans les paramètres régionaux pris en charge. (SITES-13389)


<!-- #### Link Checker{#sites-link-checker-65-lts-sp3} -->



#### MSM - Live Copies{#sites-msm-live-copies-65-lts-sp3}

* Les dossiers de Live Copy de fragments de contenu conservent désormais cq:rolloutConfigs lorsque les auteurs enregistrent des propriétés inchangées. Les auteurs peuvent ensuite mettre à jour les paramètres de déploiement sans perdre la configuration existante. (SITES-43729) CRITIQUE

* Les auteurs peuvent désormais déployer les modifications de composant à partir de la barre d’outils modifiable sur une page de plan directeur. Le déploiement se termine sans erreur JavaScript et propage les modifications à la Live Copy. (SITES-46052) MAJEUR
* Les auteurs peuvent désormais effectuer des déploiements MSM à partir de pages de plan directeur après une mise à niveau. La boîte de dialogue de déploiement charge les Live Copies disponibles et active ses commandes de déploiement au lieu de rester dans un état de chargement perpétuel. (SITES-43116) MAJEUR

* L’aperçu de Live Copy applique désormais des formats de date localisés dans l’état de la relation. Les champs **Dernière modification du Source de Live Copy**, **Dernière modification de la Live Copy** et **Dernier déploiement** correspondent aux paramètres régionaux de l’utilisateur. (SITES-40756)
* La désactivation d’un parent de plan directeur et de ses pages enfants dans une requête génère désormais un événement de déploiement par chemin d’accès. Le gestionnaire de déploiement n’exécute plus les actions en double pour la même page enfant. (SITES-44987)


#### Éditeur de page{#sites-pageeditor-65-lts-sp3}

* Les auteurs peuvent désormais créer et appliquer des balises avec des lettres majuscules ou des espaces lors d’un enregistrement des propriétés de page. AEM stocke immédiatement la valeur de balise normalisée et conserve l’affectation de la page. (SITES-42550) CRITIQUE

* Faire défiler le menu Style ne supprime plus la mise en surbrillance du style sélectionné. Les auteurs peuvent confirmer leur sélection en cours tout en examinant les autres options disponibles. (SITES-30874) MAJEUR

* Le bouton Lien de l’éditeur de texte enrichi s’ouvre désormais lorsque les auteurs accèdent à AEM via HTTP. La création d’un lien ne déclenche plus d’erreur de `crypto.randomUUID`. (SITES-39467)
* Les auteurs peuvent désormais copier et coller les composants de fragment de contenu configurés dans des conteneurs de disposition vides. Le composant collé conserve sa référence de fragment de contenu d’origine et n’affiche plus l’erreur *Choisir une variation d’expérience*. (SITES-41586)
* L’éditeur d’image honore désormais les proportions de recadrage personnalisées lors de la modification en ligne hybride. Chaque cible de dépôt d’image utilise sa propre configuration. Par conséquent, les sélections de recadrage s’appliquent correctement en dehors du mode plein écran. (SITES-45771)

<!--
#### Replication{#sites-replication-65-lts-sp3}

#### Rich Text Editor{#sites-rte-65-lts-sp3}

#### Template Editor{#sites-template-editor-65-lts-sp3}

#### Universal editor {#sites-universal-editor-65-lts-sp3}

### [!DNL Assets]{#assets-65-lts-sp3}

#### [!DNL Dynamic Media]{#assets-dm-65-lts-sp3}

#### [!DNL Dynamic Media] - Hybrid Mode {#assets-dm-hybrid-65-lts-sp3}
-->



<!--
### [!DNL Forms]{#forms-65-lts-sp3}
-->



### Foundation {#foundation-65-lts-sp3}

#### AEM Context Service {#foundation-aem-context-service-65-lts-sp3}

Le LTS AEM 6.5 introduit la prise en charge d’AEM Context Service. Le déploiement ajoute les API de service, l’intégration de l’agent, l’approvisionnement AMS, l’intégration Experience Cloud, la surveillance de la production, les runbooks opérationnels et les rapports d’utilisation. (GRANITE-65148)

#### Apache Felix {#foundation-apachefelix-65-lts-sp3}

Le service de messagerie AEM continue désormais à envoyer des e-mails lorsque des erreurs de configuration intermittentes se produisent. Les administrateurs n’ont plus besoin de redémarrer le lot de messagerie Day Communique 5 pour restaurer la diffusion des e-mails. (GRANITE-66817) MAJEUR

<!--
#### Campaign{#foundation-campaign-65-lts-sp3}

#### Cloud Services{#foundation-cloudservices-65-lts-sp3}

#### Communities {#foundation-communities-65-lts-sp3}

#### Content distribution{#foundation-content-distribution-65-lts-sp3}

#### CRX {#foundation-crx-65-lts-sp3}

#### Granite{#foundation-granite-65-lts-sp3}

#### HTL{#foundation-htl-5-lts-sp3}

#### Integrations{#foundation-integrations-65-lts-sp3}

#### Jetty{#foundation-jetty-65-lts-sp3}
-->

#### Localisation{#foundation-localization-65-lts-sp3}

* La console Opérations localise désormais le texte précédemment non traduit dans les rapports d’intégrité. Les utilisateurs voient les messages d’état traduits, les avertissements, les résultats de maintenance et les informations sur les performances. (NPR-44280) MAJEUR

* La tâche de maintenance du journal d’audit affiche désormais une clause d’exclusion de responsabilité localisée. Les administrateurs peuvent consulter les conseils juridiques et de conformité dans la langue de leur choix avant de configurer la purge automatisée des journaux d’audit. (NPR-44188)
* La page Modifier l’utilisateur affiche désormais une erreur localisée lorsque les utilisateurs réorganisent les profils modifiés. Le message explique clairement que les profils modifiés ne peuvent pas être déplacés tant que les utilisateurs n’ont pas enregistré leurs modifications. (NPR-44282)
* AEM localise désormais les info-bulles dans les propriétés de la liste de fragments de contenu. Le guide traduit explique la sélection de modèles, le filtrage des balises, les chemins de contenu, les limites d’éléments et les paramètres de tri. (SITES-14969)
* Les liens d’aide des composants dans l’éditeur de modèles ouvrent désormais la documentation localisée. Les auteurs obtiennent des conseils qui correspondent à leur langue sélectionnée au lieu de pages de composants en anglais uniquement. (SITES-15058)
* L’éditeur de stratégie de composant localise désormais les erreurs qui signalent une ressource non modifiable ou une création de nœud ayant échoué. Les auteurs de modèles reçoivent ces messages dans la langue sélectionnée. (SITES-17475)

<!-- #### Omnisearch{#foundation-omnisearch-65-lts-sp3} -->

#### Tableau de bord des opérations{#foundation-operations-dashboard-65-lts-sp3}

Le point d’entrée `/system/health/systemalive.json` reste désormais disponible après la mise à niveau du LTS AEM par les clients. Une configuration de contexte de servlet corrigée empêche les réponses HTTP 404 et prend en charge les systèmes de surveillance de l’intégrité qui reposent sur le point d’entrée . (GRANITE-69457) CRITIQUE

#### Plateforme{#foundation-platform-65-lts-sp3}

La liste autorisée expression-option HTL par défaut reconnaît désormais `decorationTagName` et `cssClassName`. Le rendu de la grille réactive standard ne remplit plus les `error.log` avec des avertissements répétés d’option inconnue. (GRANITE-67152)

<!--
#### Projects{#foundation-projects-65-lts-sp3}

#### Oak {#foundation-oak-65-lts-sp3}

#### Quickstart{#foundation-quickstart-65-lts-sp3} 
-->


#### Sécurité{#foundation-security-65-lts-sp3}

L’action **Copier le groupe** ouvre désormais le formulaire attendu au lieu d’afficher une page vierge. Les administrateurs peuvent saisir un nouvel ID de groupe et une nouvelle description, puis dupliquer un groupe de sécurité existant. (NPR-44302) MAJEUR


<!-- #### Sling{#foundation-sling-65-lts-sp3} -->


#### Traduction{#foundation-translation-65-lts-sp3}

Les projets de traduction conservent désormais un statut précis au fur et à mesure de la progression des workflows. La création du lancement et la propagation du statut suivent le comportement de workflow attendu, éliminant les métadonnées de projet incohérentes. (NPR-43420)


#### Interface d’utilisation{#foundation-ui-65-lts-sp3}

* Le libellé Pays/zone géographique s’affiche désormais dans la langue d’interface sélectionnée. Les interfaces localisées n’affichent plus le libellé anglais. (NPR-43883)
* La sélection d’une page sœur active désormais **Sélectionner** dans les sélecteurs de chemin d’accès multichamp composite. Les auteurs peuvent confirmer le nouveau chemin d’accès sans agrandir la fenêtre du navigateur ou répéter la sélection. (GRANITE-69323)


<!-- #### WCM{#foundation-wcm-65-lts-sp3} -->


#### Workflow{#foundation-workflow-65-lts-sp3}

* Les pages Package de workflow prennent désormais en charge les composants Arborescence de contenu et Définition de ressource modifiable dans l’éditeur de page de l’interface utilisateur tactile. Les auteurs peuvent parcourir le contenu du package et inspecter ou mettre à jour ses composants sans utiliser l’interface utilisateur classique. (GRANITE-67348) MAJEUR
* L’éditeur de page de l’interface utilisateur tactile effectue désormais le rendu de l’arborescence de contenu pour les pages du package de workflow. Les auteurs peuvent inspecter la structure du package et modifier les composants Définition de ressource via le même éditeur. (GRANITE-67186) MAJEUR

* La boîte de dialogue Variable de processus affiche désormais les commandes correctes pour les variables de modèle de données de formulaire, JSON, XML et de document. Les auteurs ne voient plus les balises HTML brutes lorsqu’ils créent ces variables non primitives. (GRANITE-67915)



## À propos d’[!DNL Experience Manager Foundation] {#experience-manager-foundation}

La plateforme d’[!DNL Adobe Experience Manager] 6.5 LTS repose sur les versions mises à jour de l’architecture OSGi (Apache Sling et Apache Felix), ainsi que sur le référentiel de contenu Java™ : Apache Jackrabbit Oak 1.68.x.

Eclipse Jetty 11.0.x est utilisé comme moteur de servlet pour Quickstart.

### Prise en charge de Java™  {#java-support}

* Prise en charge de Java™ 17 et Java™ 21.
* Pour des performances optimales, remplacez les valeurs par défaut du GC par d’autres valeurs. Pour plus d’informations, consultez la section [Installation et mise à jour](/help/sites-deploying/custom-standalone-install.md).
* Adobe distribue des mises à jour de maintenance Java™ 17 et Java™ 21 pour l’utilisation par les clientes et les clients dans les projets liés à AEM, lorsqu’elles ne sont pas disponibles publiquement depuis Oracle.

### Packaging Uberjar {#uber-jar-packaging}

UberJar pour AEM 6.5 LTS SP3 utilise la version 6.6.3 d’AEM 6.5 LTS UberJar. Vous pouvez récupérer les artefacts UberJar correspondants à partir du référentiel central Maven. Contrairement à AEM 6.5, AEM 6.5 LTS sépare les API publiques et les API obsolètes en deux artefacts différents.

Pour compiler par rapport aux API publiques, utilisez ce qui suit :

```xml
<dependency>
    <groupId>com.adobe.aem</groupId>
    <artifactId>uber-jar</artifactId>
    <version>6.6.3</version>
    <classifier>apis</classifier>
    <scope>provided</scope>
</dependency>
```

Si votre code dépend également d’API obsolètes, ajoutez ce qui suit :

```xml
<dependency>
    <groupId>com.adobe.aem</groupId>
    <artifactId>uber-jar</artifactId>
    <version>6.6.3</version>
    <classifier>deprecated-apis</classifier>
    <scope>provided</scope>
</dependency>
```

Voir également [Mise à jour de la version AEM Uber Jar](/help/sites-deploying/upgrading-code-and-customizations.md#update-the-aem-uber-jar-version).

### Mise à niveau {#upgrade}

* Pour plus d’informations sur la procédure de mise à niveau, consultez la [documentation de mise à niveau](/help/sites-deploying/upgrade.md).
* Pour obtenir des instructions détaillées sur la mise à niveau, consultez [Mise à niveau vers AEM Forms 6.5 sous JEE](https://experienceleague.adobe.com/fr/docs/experience-manager-65-lts/content/forms/upgrade-aem-forms/upgrade).

## Bonnes pratiques relatives aux mises à niveau du pack de services d’AEM 6.5 LTS

<!-- THE INFORMATION UNDER THIS HEADING CAME FROM CQDOC-23078 -->

Application : clients AEM 6.5 LTS (On-Premise) installant le pack de services 3 (SP3). Le SP3 est fourni sous la forme d’un fichier JAR Quickstart.

**En quoi cette mise à niveau est-elle importante**
Le SP2 pour AEM 6.5 LTS est fourni sous la forme d’un fichier JAR de démarrage rapide plutôt que d’un fichier ZIP à installer via le gestionnaire de modules. Les clients On-Premise effectuent une mise à niveau en remplaçant le fichier JAR Quickstart, en le décompressant et en redémarrant. Cette méthode est cohérente avec la procédure de mise à niveau standard d’Adobe.


**Flux de mise à niveau recommandé (création ou publication)**

1. Vérifiez que votre instance AEM 6.5 LTS est saine et accessible.
1. Téléchargez le fichier JAR de démarrage rapide (par exemple, `cq-quickstart-6.6.x.jar`) à partir de la distribution logicielle.
1. Arrêtez l’instance en cours.
1. Dans le répertoire d’installation d’AEM (en dehors de `crx-quickstart/`), remplacez le fichier JAR de démarrage rapide précédent par le fichier JAR SP3.
1. Décompressez le fichier JAR :

   ```java
   java -jar cq-quickstart-6.6.x.jar -unpack
   ```

   (Ajustez les indicateurs de tas selon les besoins.)

1. Renommez le fichier JAR décompressé pour qu’il corresponde au rôle et au port, par exemple `cq-author-4502.jar` ou `cq-publish-4503.jar`.
1. Démarrez AEM et confirmez la mise à niveau dans l’interface d’utilisation (Aide > À propos) et les journaux.

**Bonnes pratiques**

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


Pour obtenir des instructions détaillées, consultez la [documentation de mise à niveau](/help/sites-deploying/upgrade.md), car la même documentation s’applique aux mises à jour du pack de services LTS.

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

Il est conseillé aux clients de vérifier s’ils utilisent la fonctionnalité dans leur déploiement actuel. Planifiez la modification de votre implémentation afin d’utiliser l’alternative fournie.

| Domaine | Fonctionnalité | Remplacement | Version (SP) |
| --- | --- | --- | --- |
| Démarrage rapide | API Mongo | Les API Mongo sont désormais obsolètes et leur suppression est prévue dans les prochaines versions. | 6.5 TS SP2 |
| Sites | Prise en charge des fragments de contenu dans l’API REST AEM Assets | AEM 6.5 LTS SP2 fournit des API OpenAPI modernes pour la gestion des fragments de contenu et des modèles, de sorte que les anciens points d’entrée de la prise en charge des fragments de contenu dans l’API REST AEM Assets sont désormais obsolètes.<br>Adobe prévoit de conserver ces anciens points d’entrée disponibles jusqu’à une annonce de fin de vie. Adobe ne prévoit pas d’autres améliorations pour les points d’entrée obsolètes. | 6.5 LTS SP2 |
| Sites | [Éditeur SPA](/help/sites-developing/spa-overview.md) | Les éditeurs recommandés pour la gestion du contenu découplé dans AEM sont les suivants : <br>- [Éditeur universel](/help/sites-developing/universal-editor/introduction.md) pour la modification visuelle.<br>- [Éditeur de fragments de contenu](/help/assets/content-fragments/content-fragments-managing.md) pour la modification de formulaires. | 6.5 LTS GA |
| [!DNL Foundation] | Prise en charge de com.adobe.granite.oauth.server | Intégration Adobe IMS | |

### Fonctionnalités supprimées {#removed-features}

Cette section répertorie les fonctionnalités qui ont été supprimées dans AEM 6.5 LTS. Ces fonctionnalités étaient signalées comme obsolètes dans les versions antérieures.

* La prise en charge de RDBMK pour la persistance du référentiel Adobe CRX a été supprimée.
* Dans les environnements en cluster, MongoMK est désormais la seule option prise en charge pour la persistance du référentiel.

| Domaine | Fonctionnalité | Remplacement | Version (SP) |
| --- | --- | --- | --- |
| Sites | Résumé textuel du fragment de contenu | Aucun remplacement n’est disponible. | 6.5 LTS SP3 |
| Commerce | AEM CIF Classic n’est pas pris en charge. | Migrez vers [AEM CIF](/help/commerce/cif/migration.md). | 6.5 LTS GA |
| Solutions | Social / Communities n’est pas pris en charge. | Aucun remplacement n’est disponible. | 6.5 LTS GA |
| Screens | Screens n’est pas pris en charge. | Aucun remplacement n’est disponible. | 6.5 LTS GA |
| Assets | `dam-pim` et `dam-rating` ne sont pas pris en charge, car les bundles dépendent de Social. | Aucun remplacement n’est disponible. | 6.5 LTS GA |
| Assets | `com.day.cq.dam.scene7.api.model.Scene7ViewerConfig#getSettings()` a été supprimé. | Utilisez l’autre API `com.day.cq.dam.scene7.api.model.Scene7ViewerConfig#getSettingsList()` qui a été ajoutée. | 6.5 LTS GA |
| Portail | AEM Portal Director n’est pas pris en charge. | Aucun remplacement n’est disponible. | 6.5 LTS GA |
| Granite | Le bundle `com.adobe.granite.socketio` est supprimé. | Aucun remplacement n’est disponible. | 6.5 LTS GA |
| Granite | `com.adobe.granite.crx-explorer` n’est pas pris en charge. | Aucun remplacement n’est disponible. | 6.5 LTS GA |
| Granite | `crx2oak` n’est pas pris en charge. | Sélectionnez la version appropriée d’[Oak-upgrade](https://mvnrepository.com/artifact/org.apache.jackrabbit/oak-upgrade). | 6.5 LTS GA |
| Adobe | `com.adobe.cq.cq-searchpromote-integration` n’est pas pris en charge. | Aucun remplacement n’est disponible. | 6.5 LTS GA |
| Guava | Toutes les dépendances guava sont désormais supprimées dans AEM. Par conséquent, le bundle `com.adobe.granite.osgi.wrapper.guava-15.0.0-0002` ne fait pas partie d’AEM. | La clientèle peut ajouter Guava elle-même si elle en dépend ou remplacer le code Guava par des collections Java ou d’autres alternatives si possible. | 6.5 LTS GA |
| `We.Retail` | L’exemple de site `We-retail` n’est pas pris en charge. | Aucun remplacement n’est disponible. | 6.5 LTS GA |
| Open Source | Le bundle `oak-solr-osgi` n’est pas pris en charge. | Aucun remplacement n’est disponible. | 6.5 LTS GA |
| Open Source | `org.apache.servicemix.bundles.abdera-parser`, `org.apache.servicemix.bundles.jdom` et `org.apache.sling.atom.taglib` ne sont pas pris en charge. | Aucun remplacement n’est disponible. | 6.5 LTS GA |
| Open Source | Les packages `org.apache.commons.io` sont désormais exportés depuis `org.apache.commons.commons-io`. | Aucune modification n’est requise. | 6.5 LTS GA |
| Open Source | Les packages `javax.mail` sont exportés à partir du bundle `com.sun.javax.mail`. | Aucune modification n’est requise. | 6.5 LTS GA |
| Open Source | Les packages `org.apache.jackrabbit.api` sont désormais exportés à partir du bundle `org.apache.jackrabbit.oak-jackrabbit-api` . | Aucune modification n’est requise. | 6.5 LTS GA |
| Open Source | `com.github.jknack.handlebars` n’est pas pris en charge. | Sélectionnez la [version](https://mvnrepository.com/artifact/com.github.jknack/handlebars) appropriée. | 6.5 LTS GA |

## Problèmes connus {#known-issues}

### AEM Forms

* Dans Configuration Manager, l’initialisation de la base de données échoue pendant Bootstrap dans le mode personnalisé clé en main LTS JEE d’AEM Forms 6.5 lorsqu’aucun module ou uniquement des composants limités sont sélectionnés. L’échec est dû à une dépendance manquante (xalan-2.7.2.jar), ce qui entraînait une erreur. L’ajout du fichier JAR à Adobe-livecycle-jboss.ear\lib résout le problème. (FORMS-24690)
* Sur les déploiements du pack de services 2 LTS de Forms JEE s’exécutant sur WebSphere® Liberty Profile, la fonctionnalité de messagerie échoue. Lors de l’utilisation des fonctionnalités de messagerie, le serveur consigne une erreur : `Could not convert socket to TLS`. (FORMS-24692)
* Sur Forms JEE LTS s’exécutant sur JBoss®, la fonctionnalité liée aux e-mails échoue. Lors de l’utilisation des fonctionnalités de messagerie, le serveur consigne une erreur : `Error IMAPProvider not a subtype`. Pour résoudre ce problème, installez le correctif à partir de [Distribution logicielle](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/hotfix/adobe-core-jboss.ear). (FORMS-24892)

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

Pour utiliser cette fonctionnalité, installez le correctif à partir de [Distribution logicielle](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq660/hotfixes/cq-6.5.lts.2-hotfix-GRANITE-67640-1.0.zip).

>[!NOTE]
>
> Pour vous assurer que la configuration par défaut de `com.adobe.granite.apicontroller` n’introduit aucune restriction de résolution involontaire affectant les implémentations personnalisées existantes, vérifiez le statut de tous les lots installés après l’installation du correctif.

### Les commentaires JSON ne sont plus pris en charge dans Sling-Initial-Content (SP2) {#json-comments-no-longer-supported-in-sling-initial-content}

Ce problème affecte le développement et l’administration de bundles OSGi qui déploient des bundles qui utilisent `Sling-Initial-Content` avec des fichiers JSON.

À compter d’AEM 6.5 LTS SP2, les fichiers JSON utilisés dans les bundles `Sling-Initial-Content` n’acceptent plus les commentaires (`//` ou `/* */`). Les versions précédentes d’AEM acceptaient les commentaires car le fournisseur de `javax.json` était indulgent à ce sujet. AEM 6.5 LTS SP2 a mis à niveau `org.apache.sling.jcr.contentloader` vers la version 2.6.0, qui a basculé l’analyseur JSON sur `jakarta.json`. Bien que la [spécification JSON (RFC 8259)](https://datatracker.ietf.org/doc/html/rfc8259) ne définisse pas de syntaxe pour les commentaires, les versions antérieures d’AEM les ont acceptés en raison de la clémence du fournisseur de `javax.json`. Le fournisseur de `jakarta.json` ne propose pas cette extension.

L’échec n’est pas signalé : les nœuds de contenu ne parviennent pas à se charger lors de l’activation du bundle sans qu’aucune erreur ne soit visible pour le programme d’installation. Si du contenu est manquant de manière inattendue après la mise à niveau vers SP2, vérifiez les journaux du programme d’installation OSGi pour détecter les erreurs d’analyse JSON. Pour identifier les bundles affectés, recherchez `//` ou `/* */` dans les fichiers JSON répertoriés sous les en-têtes de manifeste `Sling-Initial-Content`.

>[!CAUTION]
>
> Pour éviter les échecs de chargement de contenu après la mise à niveau vers AEM 6.5 LTS SP2, supprimez tous les commentaires des fichiers JSON dans les lots `Sling-Initial-Content`.

### La mise à niveau du lot Jackson affecte le connecteur GlobalLink. {#jackson-upgrade-globallink-connector}

AEM 6.5 LTS SP3 met à niveau le lot `jackson`. Cette modification affecte les déploiements qui utilisent le connecteur de traduction GlobalLink.

Si vous utilisez le lot `gs4tr-globallink-adaptors-aem.core` dans une version antérieure à la version 3.4.0, mettez à niveau le lot vers une version compatible. La version 3.4.0 ou une version ultérieure fonctionne avec le lot `jackson` mis à niveau dans le SP3.

>[!NOTE]
>
> Mettez à niveau le lot `gs4tr-globallink-adaptors-aem.core` vers la version 3.4.0 ou une version ultérieure avant ou pendant la mise à jour du SP3 afin d’éviter des problèmes de compatibilité avec le connecteur GlobalLink.


### Installez les index Oak requis pour les API Sites en mode découplé{#site-headless-api}

Certaines API déplacées vers Sites en mode découplé nécessitent des index Oak supplémentaires pour une fonctionnalité complète.

Pour utiliser les fonctionnalités suivantes, installez le package `cq-dam-cfm-indices` :

* Lister les modèles de fragment de contenu
* Répertorier les fragments de contenu
* API de recherche
* Workflows

Téléchargez le package d’index [cq-dam-cfm-indices](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Fcq-dam-cfm-indices-1.1.5.zip) à partir du portail de distribution logicielle Adobe.

### Échec de connexion à Dispatcher avec la fonction SSL uniquement (corrigé dans AEM 6.5 LTS SP1 et versions ultérieures){#ssl-only-feature}

>[!NOTE]
>
> Ce problème est uniquement présent dans la version AEM 6.5 LTS en disponibilité générale.

Lors de l’activation de la fonction SSL uniquement dans les déploiements AEM, un problème connu affecte la connectivité entre les instances Dispatcher et AEM. Après l’activation de cette fonctionnalité, les contrôles d’intégrité échouent et la communication entre les instances Dispatcher et AEM est interrompue. Ce problème se produit plus particulièrement lorsque les clientes et clients tentent de se connecter via `https + IP` à partir des instances Dispatcher vers AEM. Il est lié aux problèmes de validation SNI (Server Name Indication).

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

Si vous rencontrez ce problème, contactez le service clientèle d’Adobe. Un correctif [cq-6.5.lts.0-hotfix-CQ-4359803](https://experience.adobe.com/#/downloads/content/software-distribution/fr/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq660/hotfixes/cq-6.5.lts.0-hotfix-CQ-4359803-1.0.2.zip) est disponible pour résoudre ce problème. N’essayez pas d’activer les fonctions SSL uniquement avant d’avoir appliqué le correctif nécessaire.

## Lots OSGi et modules de contenu inclus{#osgi-bundles-and-content-packages-included}

Les fichiers zip suivants contiennent les documents texte qui répertorient les lots OSGi et les packages de contenu inclus dans cette version du pack de services LTS Experience Manager 6.5 :

* [lots OSGi](/help/release-notes/assets/65lts_sp3_bundles.zip)
* [Packages de contenu](/help/release-notes/assets/65lts_sp3_packages.zip)

## Sites web à accès limité{#restricted-sites}

Ces sites Web sont disponibles uniquement pour les clients. Si vous êtes client et avez besoin d’un accès, contactez votre responsable de compte Adobe.

* [Téléchargement du produit à l’adresse licensing.adobe.com](https://licensing.adobe.com/)
* [Contacter l’assistance clientèle Adobe](https://experienceleague.adobe.com/fr/docs/support-resources/adobe-support-tools-guide/adobe-customer-support-experience).

