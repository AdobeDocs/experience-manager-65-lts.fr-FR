---
title: Présentation des concepts des métadonnées
description: Découvrez l’utilité des métadonnées et leurs types, pour simplifier la catégorisation et l’organisation des ressources.
contentOwner: AG
role: User, Admin
feature: Metadata
solution: Experience Manager, Experience Manager Assets
exl-id: 16ab2e64-9c12-43ae-a8d2-f71e63899c68
source-git-commit: c3e9029236734e22f5d266ac26b923eafbe0a459
workflow-type: tm+mt
source-wordcount: '2665'
ht-degree: 100%

---

# Présentation des concepts des métadonnées {#why-we-need-metadata}

Les métadonnées sont des données de description des données. À cet égard, elles font référence à vos ressources numériques (ou actifs), par exemple une image. Les métadonnées sont essentielles pour gérer efficacement des ressources.

Elles constituent un ensemble de toutes les données disponibles pour cette image, mais sans qu’elles y soient contenues. Voici quelques exemples de métadonnées :

* Nom de la ressource.
* Heure et date de la dernière modification.
* Taille de la ressource au moment du stockage dans le référentiel.
* Nom du dossier où elle se trouve.
* Ressources connexes ou balises appliquées.

Les propriétés de métadonnées de base décrites ci-dessus sont utilisées par [!DNL Experience Manager] pour gérer les ressources et permettre aux utilisateurs de les visualiser. Par exemple, ordonner les ressources selon la date de leur dernière modification est utile pour identifier des ressources ajoutées récemment.

Vous pouvez ajouter d’autres données de niveau supérieur à des ressources numériques, par exemple :

* Type de ressource (image, vidéo, clip audio ou document).
* Propriétaire.
* Intitulé.
* Description.
* Balises affectées à cette ressource.

D’autres métadonnées permettent de classer les fichiers de manière plus détaillée à mesure que le volume d’informations numériques augmente. Il est ainsi possible de gérer quelques centaines de fichiers en ne prenant en compte que leurs noms. Pour autant, cette approche n’est pas évolutive. Elle est insuffisante si le nombre de personnes concernées et la quantité de ressources gérées augmentent.

Avec l’ajout de métadonnées, la valeur d’une ressource numérique augmente, car elle devient :

* plus accessible : les systèmes et les utilisateurs peuvent la trouver facilement ;
* plus facile à gérer : vous pouvez rechercher plus facilement des ressources avec un même ensemble de propriétés et leur apporter des modifications ;
* complète : la ressource contient davantage d’informations et de contexte grâce à un plus grand nombre de métadonnées.

Ainsi, [!DNL Assets] vous fournit les moyens adéquats pour créer, gérer et échanger des métadonnées pour vos ressources numériques.

## Types de métadonnées {#types-of-metadata}

Les deux types de métadonnées de base sont les métadonnées techniques et les métadonnées descriptives.

Les métadonnées techniques sont utiles pour les applications logicielles qui traitent des ressources numériques. Elles ne doivent pas être gérées manuellement. [!DNL Experience Manager Assets] et d’autres logiciels déterminent automatiquement les métadonnées techniques qui peuvent changer lorsque la ressource est modifiée. Les métadonnées techniques disponibles d’une ressource dépendent largement de son type de fichier. Voici quelques exemples de métadonnées techniques :

* taille d’un fichier ;
* dimensions (hauteur et largeur) d’une image ;
* débit d’un fichier audio ou vidéo ;
* résolution (niveau de détail) d’une image.

Les métadonnées descriptives concernent le domaine d’application (par exemple, l’entreprise d’où provient une ressource) et ne peuvent pas être déterminées automatiquement. Elles sont créées manuellement ou semi-automatiquement. Par exemple, une caméra GPS peut automatiquement suivre la latitude et la longitude et ajouter un balisage géographique à l’image.

La création manuelle d’informations descriptives de métadonnées coûte cher. Des normes ont donc été mises en place pour faciliter l’échange de métadonnées entre les systèmes logiciels et les organisations. [!DNL Experience Manager Assets] prend en charge l’ensemble des normes pertinentes pour la gestion des métadonnées.

## Normes de codage {#encoding-standards}

Il existe différentes manières d’incorporer des métadonnées dans des fichiers. Un certain nombre de normes de codage sont prises en charge :

* XMP : utilisé par [!DNL Assets] pour stocker les métadonnées extraites dans le référentiel.
* ID3 : pour les fichiers audio et vidéo.
* Exif : pour les fichiers image.
* Autres normes/normes héritées : [!DNL Microsoft Word], [!DNL PowerPoint], [!DNL Excel], etc.

### XMP {#xmp}

[!DNL Extensible Metadata Platform] (XMP) est une norme ouverte utilisée par [!DNL Experience Manager Assets] pour la gestion des métadonnées. La norme permet le codage universel des métadonnées en l’incorporant dans tous les formats de fichier. Adobe et d’autres entreprises prennent en charge la norme XMP, car elle offre un modèle de contenu enrichi. Si vous utilisez la norme XMP et [!DNL Experience Manager Assets], vous disposez d’une plateforme puissante sur laquelle vous appuyer. Pour plus d’informations, voir la section [XMP](https://www.adobe.com/products/xmp.html).

### ID3 {#id}

Les données stockées dans ces balises ID3 s’affichent lorsque vous relisez un fichier audio numérique sur votre ordinateur ou sur un lecteur MP3 portable.

Les balises ID3 sont conçues pour le format de fichier MP3. Informations supplémentaires sur les formats :

* Les balises ID3 fonctionnent dans les fichiers MP3 et mp3PRO.
* Le format WAV ne contient pas de balises.
* Le format WMA possède des balises propriétaires qui n’autorisent pas l’implémentation Open Source.
* Le format Ogg Vorbis utilise des commentaires Xiph incorporés dans le conteneur Ogg.
* AAC utilise un format de balisage propriétaire.

### Exif {#exif}

Le format de fichier d’image échangeable (Exif) est le plus utilisé dans la photographie numérique pour les métadonnées. Il permet d’incorporer un vocabulaire fixe de propriétés de métadonnées dans de nombreux formats de fichiers, tels que JPEG, TIFF, RIFF et WAV. Exif stocke les métadonnées sous la forme de paires constituées d’un nom de métadonnée et d’une valeur de métadonnée. Ces paires nom-valeur de métadonnées sont également appelées balises, à ne pas confondre avec le balisage dans [!DNL Experience Manager]. Les caméras numériques modernes créent des métadonnées Exif que les logiciels graphiques modernes savent prendre en charge. Le format Exif est le plus petit dénominateur commun pour la gestion des métadonnées, en particulier concernant les images.

Le fait que ce format ne soit pas pris en charge par quelques formats de fichiers image très appréciés comme BMP, GIF ou PNG constitue une limite majeure.

Les champs de métadonnées définis par Exif sont généralement de nature technique et d’une utilité limitée pour la gestion descriptive des métadonnées. Ainsi, [!DNL Experience Manager Assets] permet de mapper les propriétés Exif dans des [schémas de métadonnées courants](metadata-schemas.md) et dans [XMP](xmp-writeback.md).

### Autres métadonnées {#other-metadata}

Les autres métadonnées qui peuvent être incorporées à partir de fichiers comprennent celles de [!DNL Microsoft Word], [!DNL PowerPoint], [!DNL Excel], etc.

## Présentation des schémas de métadonnées {#metadata-schemata}

Les schémas de métadonnées sont des ensembles prédéfinis de définitions de propriétés de métadonnées qui peuvent être utilisés dans différentes applications. Les propriétés sont toujours associées à une ressource, ce qui signifie que les propriétés « concernent » cette ressource.

Vous pouvez également concevoir vos propres schémas de métadonnées s’il n’en existe aucun qui réponde à vos besoins. Ne dupliquez pas les informations existantes. Au sein d’une organisation, la séparation des schémas facilite le partage des métadonnées. [!DNL Experience Manager] fournit une liste par défaut des schémas de métadonnées les plus utilisés. La liste vous permet de lancer rapidement votre stratégie de métadonnées et de choisir rapidement les propriétés de métadonnées dont vous avez besoin.

Les schémas de métadonnées pris en charge sont répertoriés ci-dessous.

### Métadonnées standard {#standard-metadata}

* DC – [!DNL Dublin Core] est un ensemble de métadonnées important et largement utilisé.
* DICOM – Digital Imaging and Communications in Medicine.
* `Iptc4xmpCore` et `iptc4xmpExt` – International Press Communications Standard contient de nombreuses métadonnées spécifiques à un sujet.
* RDF – Resource Description Framework : pour les métadonnées web de sémantique générique.
* XMP – [!DNL Extensible Metadata Platform].
* `xmpBJ` – Basic Job Ticketing.

### Métadonnées spécifiques à l’application {#application-specific-metadata}

Les métadonnées spécifiques à l’application englobent des métadonnées techniques et descriptives. Si vous utilisez ces types de métadonnées, il se peut que d’autres applications ne soient pas en mesure de les exploiter. Par exemple, il est possible qu’une autre application de rendu d’image ne puisse pas accéder aux métadonnées [!DNL Adobe Photoshop]. Vous pouvez créer une étape de workflow qui transforme une propriété spécifique à l’application en propriété standard.

* ACDSee – Métadonnées gérées par le programme [!DNL ACDSee]. Voir [www.acdsee.com/](https://www.acdsee.com/).
* Album – [!DNL Adobe Photoshop Album].
* CQ – Utilisées par [!DNL Experience Manager Assets].
* DAM – Utilisées par [!DNL Experience Manager Assets].
* DEX – [!DNL Optima SC Description explorer] est une collection d’outils pour la gestion des métadonnées et des fichiers pour les systèmes d’exploitation Windows.
* CRS – [Adobe Photoshop Camera Raw](https://helpx.adobe.com/fr/camera-raw/using/introduction-camera-raw.html).
* LR – [!DNL Adobe Lightroom].
* MediaPro – [iView MediaPro](https://fr.wikipedia.org/wiki/Phase_One_Media_Pro).
* MicrosoftPhoto et MP – Microsoft Photo.
* PDF et PDF/X.
* Photoshop et psAux – [!DNL Adobe Photoshop].

### Métadonnées de Digital Rights Management {#digital-rights-management-metadata}

* CC – [!DNL Creative Commons].
* [!DNL XMPRights].
* PLUS – [Picture Licensing Universal System](https://www.useplus.com).
* PRISM – [Exigences de publication pour les métadonnées standard du secteur (Publishing Requirements for Industry Standard Metadata)](https://www.w3.org/submissions/2020/SUBM-prism-20200910/Image_Guide.pdf).
* PRL – PRISM Rights Language.
* PUR – PRISM Usage Rights.
* `xmpPlus` – Intégration de PLUS avec XMP.

### Métadonnées spécifiques à la photographie {#photography-specific-metadata}

* Exif – De nombreuses informations techniques issues de l’appareil photo, notamment la position GPS.
* CRS – Schéma [!DNL Camera Raw].
* `iptc4xmpCore` et `iptc4xmpExt`.
* TIFF – Métadonnées d’image (pas seulement pour les images TIFF).

### Métadonnées spécifiques à l’impression {#print-specific-metadata}

* PDF et PDF/X – Adobe PDF et applications tierces.
* PRISM – [Exigences de publication pour les métadonnées standard du secteur (Publishing Requirements for Industry Standard Metadata)](https://www.w3.org/submissions/2020/SUBM-prism-20200910/Image_Guide.pdf).
* XMP – [!DNL Extensible Metadata Platform].
* `xmpPG` – Métadonnées XMP pour le texte paginé.

### Métadonnées multimédias {#multimedia-specific-metadata}

* `xmpDM` – [!DNL Dynamic Media].
* `xmpMM` – Gestion des médias.

## Référence des schémas de métadonnées {#metadata-schemata-reference}

La référence ci-après contient des informations sur un schéma de métadonnées spécifique (dans l’ordre alphabétique) ainsi qu’une liste de propriétés et de leur définition.

### Dublin Core {#dublin-core}

La métadonnée Dublin Core fournit un ensemble de conventions normalisé pour décrire les ressources afin de faciliter leur recherche. Dans [!DNL Assets], Dublin Core décrit les ressources numériques, y compris les vidéos, le son, les images et les documents.

Le DCMES (Dublin Core Metadata Element Set) contient 15 éléments de métadonnées qui sont répertoriés dans le tableau ci-après. Chaque élément Dublin Core est facultatif et peut être utilisé plusieurs fois. Vous pouvez ajouter ou supprimer des informations de métadonnées Dublin Core comme vous le feriez pour les métadonnées spécifiques au type de média.

Outre le DCMES, il existe d’autres éléments de métadonnées créés par la Dublin Core Initiative. Pour plus d’informations, voir la [Dublin Core Initiative](https://dublincore.org/).

| Propriété | Description |
| ----------- | ------------------------------------------------------------------------------------------------------------------------ |
| contributor | Personne ou entreprise chargée d’apporter des contributions au contenu. |
| coverage | Emplacement géographique ou période que couvre la ressource. |
| creator | Personne ou entreprise chargée de la création du contenu. |
| date | Date ou période associée à la ressource. |
| description | Informations supplémentaires sur la ressource. |
| format | Format de fichier, support physique ou dimensions de la ressource. [!DNL Experience Manager] utilise `dc:format` pour représenter le type MIME de la ressource. |
| identifier | Référence unique à la ressource. |
| language | Langue de la ressource (`en` pour l’anglais, par exemple). |
| publisher | Personne ou entreprise chargée de rendre la ressource disponible. |
| relation | Ressource connexe. |
| rights | Informations sur la personne qui dispose des droits sur cette ressource. |
| source | Ressource connexe à partir de laquelle la ressource est dérivée. |
| objet | Objet de la ressource. |
| title | Nom de la ressource. |
| type | Nature ou genre de la ressource. |

### IPTC {#iptc}

L’International Press Telecommunications Council (IPTC) est un consortium d’agences de presse à travers le monde. L’un de ses objectifs est de développer et de maintenir des normes techniques. L’IPTC a défini un ensemble de normes de métadonnées pour les images que les photographes ont adopté de façon quasiment universelle. Ces normes de métadonnées faisaient partie de la norme plus générale connue sous le nom de IPTC Information Interchange Model (IIM), créée dans les années 1990.

Bien que les informations d’en-tête IPTC aient été globalement remplacées par XMP, un schéma de base IPTC et un schéma d’extension sont disponibles pour XMP. Dans les programmes d’image, les propriétés XMP et IPTC sont synchronisées.

## Workflows pilotés par les métadonnées {#metadata-driven-workflows}

La création de workflows pilotés par les métadonnées permet d’automatiser certains processus, ce qui en améliore l’efficacité. Dans un workflow piloté par les métadonnées, le système de gestion des workflows exécute ainsi une action prédéfinie après avoir lu un workflow. Voici quelques exemples d’utilisation des workflows pilotés par les métadonnées :

* Le workflow peut vérifier si une image contient un titre. Dans le cas contraire, le système vous avertit d’ajouter un titre.
* Le workflow peut vérifier si une mention de droit d’auteur relative à un fichier permet la distribution ou non. Ainsi, le système envoie la ressource à un serveur ou à un autre.
* Un workflow peut rechercher des ressources sans métadonnées obligatoires prédéfinies ou des ressources contenant des métadonnées *non valides*.

## Métadonnées XMP {#xmp-metadata}

XMP (Extensible Metadata Platform) est la norme de métadonnées utilisée par [!DNL Adobe Experience Manager Assets] pour la gestion des métadonnées. XMP offre un format standard pour la création, le traitement et l’échange de métadonnées pour une multitude d’applications.

En plus d’un codage de métadonnées universel qui peut être incorporé dans tous les formats de fichier, XMP fournit un [modèle de contenu](#xmp-core-concepts) riche et est [pris en charge par Adobe](#advantages-of-xmp) et d’autres sociétés. Ainsi, les utilisateurs XMP, en association avec, disposent d’une plateforme puissante sur laquelle s’appuyer.[!DNL Assets]

La [spécification XMP](https://www.adobe.com/devnet/xmp.html) est disponible auprès d’Adobe.

### Présentation de la norme XMP {#what-is-xmp}

Adobe a introduit pour la première fois la norme XMP dans le cadre du logiciel Adobe Acrobat. Depuis, la norme XMP a été largement adoptée. [!DNL Assets] prend en charge de manière native XMP : la plateforme de métadonnées extensible pilotée par Adobe. XMP est une norme destinée au traitement et au stockage de métadonnées normalisées et propriétaires dans les ressources numériques. La norme XMP est conçue pour être la norme commune permettant à plusieurs applications de fonctionner efficacement avec les métadonnées.

Les spécialistes de la production, par exemple, utilisent la prise en charge XMP intégrée dans les applications d’Adobe pour transmettre des informations sur plusieurs formats de fichiers. Le référentiel d’[!DNL Assets] extrait les métadonnées XMP et les utilise pour gérer le cycle de vie du contenu et offre la possibilité de créer des workflows d’automatisation.

XMP normalise la façon dont les métadonnées sont définies, créées et traitées en fournissant un modèle de données, un modèle de stockage et des schémas. Tous ces concepts sont abordés dans cette section.

Toutes les métadonnées héritées d’EXIF, d’ID3 ou de Microsoft Office sont automatiquement converties au format XMP, qui peut être étendu pour prendre en charge le schéma de métadonnées spécifiques au client comme les catalogues de produits.

Dans la norme XMP, les métadonnées sont constituées d’un ensemble de propriétés. Ces propriétés sont toujours associées à
une entité spécifique appelée ressource ; c’est-à-dire qu’elles portent sur celle-ci. S’il y a XMP, la ressource est toujours la ressource.

### Écosystème XMP {#xmp-ecosystem}

XMP définit un modèle de [métadonnées](https://fr.wikipedia.org/wiki/Métadonnée) qui peut être utilisé avec n’importe quel ensemble défini d’éléments de métadonnées. XMP définit également des [schémas](https://en.wikipedia.org/wiki/XML_schema) particuliers pour les propriétés de base utiles pour enregistrer l’historique d’une ressource lorsqu’elle passe par plusieurs étapes de traitement, depuis la photographie, la [numérisation](https://fr.wikipedia.org/wiki/Scanner_(informatique)) ou la création au format texte, en passant par les étapes de retouche photo ([recadrage](https://fr.wikipedia.org/wiki/Recadrage_(image)) ou réglage des couleurs, par exemple), pour l’assembler dans une image finale. XMP permet à chaque programme logiciel ou appareil d’ajouter en cours de route ses propres informations à une ressource numérique, qui peut ensuite être conservée dans le fichier numérique final.

XMP est le plus souvent sérialisé et stocké à l’aide d’un sous-ensemble du [W3C](https://fr.wikipedia.org/wiki/World_Wide_Web_Consortium) [Resource Description Framework](https://fr.wikipedia.org/wiki/Resource_Description_Framework) (RDF), exprimé à son tour en format [XML](https://fr.wikipedia.org/wiki/Extensible_Markup_Language).

### Avantages de la norme XMP {#advantages-of-xmp}

La norme XMP présente les avantages suivants par rapport aux autres normes de codage et schémas :

* Les métadonnées basées sur la norme XMP sont très puissantes et précises.
* La norme XMP permet de définir plusieurs valeurs pour une propriété.
* XMP dispose d’un encodage normalisé, ce qui vous permet d’échanger facilement des métadonnées.
* Le format XMP est extensible. Vous pouvez ajouter d’autres informations à vos ressources.

La norme XMP a été conçue pour être extensible, ce qui vous permet d’ajouter des types de métadonnées personnalisés dans les données XMP. En revanche, ce n’est pas le cas d’EXIF qui présente une liste des propriétés qui ne peut pas être étendue.

>[!NOTE]
>
>XMP ne permet généralement pas l’incorporation des types de données binaires. Pour transporter des données binaires dans XMP, par exemple des images miniatures, elles doivent être codées dans un format compatible avec XML tel que `Base64`.

### Concepts de XMP {#xmp-core-concepts}

Les sections ci-après décrivent les notions fondamentales relatives à XMP, notamment les espaces de noms et les schémas, les propriétés et les valeurs, ainsi que les variantes linguistiques.

#### Espaces de noms et schémas {#namespaces-and-schemata}

Un schéma XMP est un ensemble de noms de propriétés défini dans un espace de noms XML commun qui comprend le type des données et des informations descriptives. Un schéma XMP est identifié par l’URI de l’espace de noms XML. L’utilisation des espaces de noms permet d’empêcher tout conflit entre les propriétés dans différents schémas qui portent le même nom, mais ont un sens différent.

Par exemple, la propriété `Creator` dans deux schémas conçus indépendamment peut correspondre à la personne ou à l’application (Adobe Photoshop, par exemple) ayant créé la ressource.

#### Propriétés et valeurs {#properties-and-values}

XMP peut inclure des propriétés de l’un ou de plusieurs des schémas. Par exemple, un sous-ensemble classique utilisé par de nombreuses applications Adobe peut comprendre les éléments suivants :

* Schéma Dublin Core : `dc:title`, `dc:creator`, `dc:subject`, `dc:format`, `dc:rights`.
* Schéma de base XMP : `xmp:CreateDate`, `xmp:CreatorTool`, `xmp:ModifyDate`, `xmp:metadataDate`
* Schéma de gestion des droits XMP : `xmpRights:WebStatement`, `xmpRights:Marked`
* Schéma de gestion des médias XMP : `xmpMM:DocumentID`

#### Variantes linguistiques {#language-alternatives}

XMP vous offre la possibilité d’ajouter une propriété `xml:lang` aux propriétés de texte pour spécifier la langue du texte.

## Utilisation de métadonnées IPTC {#support-for-iptc-metadata}

Découvrez comment [!DNL Adobe Experience Manager Assets] prend en charge les métadonnées IPTC, les évaluations des créations et les mots-clés ajoutés aux ressources par [!DNL Adobe Bridge] et par d’autres applications [!DNL Adobe Creative Cloud].

[!DNL Adobe Experience Manager Assets] prend en charge la norme de métadonnées IPTC qui est couramment utilisée pour décrire des ressources. Cela permet à [!DNL Assets] de bénéficier d’une plus large acceptation de ses images auprès des différents intervenants, y compris les photographes, les agences de création, les bibliothèques, les musées, etc.

Le schéma de métadonnées par défaut des ressources intègre désormais les schémas de métadonnées IPTC Core et IPTC Extension afin de définir des propriétés de métadonnées complètes qui permettent aux utilisateurs et aux utilisatrices d’ajouter des données précises et fiables sur les personnes, les emplacements et les produits affichés dans une image. Il prend également en charge les dates, les noms et les identifiants concernant la création de l’image, ainsi qu’une manière flexible d’exprimer les informations sur les droits.

La page Propriétés des ressources comprend désormais des onglets distincts pour afficher les métadonnées IPTC Core et IPTC Extension dans les champs modifiables.

1. Sélectionnez une image dans l’interface utilisateur d’[!DNL Assets].
1. Cliquez sur **[!UICONTROL Propriétés]** dans la barre d’outils.
1. Cliquez sur l’onglet **[!UICONTROL IPTC]** pour afficher les métadonnées IPTC de la ressource.
1. Modifiez les propriétés de métadonnées IPTC, si vous le souhaitez.

   ![iptc_tab](assets/keywords-in-iptc-tab.png)

1. Cliquez sur l’onglet **[!UICONTROL Extension IPTC]** pour afficher les métadonnées d’extension IPTC de la ressource.
1. Modifiez les propriétés de métadonnées d’extension IPTC, selon vos besoins.
1. Cliquez sur **[!UICONTROL Enregistrer et fermer]** pour enregistrer les modifications.

### Prise en charge de l’évaluation de la création {#creative-rating-support}

Outre les évaluations individuelles et cumulées, la page Propriétés affiche désormais les évaluations affectées à des ressources par le biais d’Adobe Bridge et d’autres applications Creative.

Ces évaluations sont disponibles dans la section **[!UICONTROL Évaluation de la création]** de l’onglet **[!UICONTROL Avancé]**.

Cette évaluation est une propriété en lecture seule et se situe entre 1 et 5. Vous pouvez rechercher des ressources en fonction de leur évaluation créative dans le panneau de recherche.

Toutefois, cette propriété n’est actuellement pas indexée pour éviter tout conflit avec les modifications personnalisées effectuées par les utilisateurs ou utilisatrices.

### Prise en charge des mots-clés {#keyword-support}

L’onglet **[!UICONTROL IPTC]** de la page [!UICONTROL Propriétés] affiche également les mots-clés ajoutés aux ressources au moyen d’Adobe Bridge et d’autres applications Adobe Creative Cloud. Vous pouvez aussi modifier ces mots-clés et en ajouter d’autres à partir de l’onglet **[!UICONTROL IPTC]**.

![mots-clés](assets/keywords-in-iptc-tab.png)
