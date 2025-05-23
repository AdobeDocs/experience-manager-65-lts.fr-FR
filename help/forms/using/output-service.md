---
title: Service Output
description: Décrit le service Output, qui fait partie d’AEM Document Services.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: document_services
docset: aem65
feature: Document Services,Output Service
solution: Experience Manager, Experience Manager Forms
role: Admin, User, Developer
exl-id: de7b8970-bbac-419b-8e87-8d853b82f44a
source-git-commit: c3e9029236734e22f5d266ac26b923eafbe0a459
workflow-type: tm+mt
source-wordcount: '511'
ht-degree: 100%

---

# Service Output{#output-service}

## Présentation {#overview}

Le service Output est un service OSGi qui fait partie d’AEM Document Services. Le service Output prend en charge divers formats de sortie et fonctions de conception de sortie d’AEM Forms Designer. Le service Output peut convertir des modèles XFA et des données XML pour générer des documents d’impression dans différents formats.

Le service Output permet de créer des applications grâce auxquelles vous pouvez accomplir les actions suivantes :

* Générer des documents de formulaire définitifs en complétant des fichiers de modèle avec des données XML.
* Générer des formulaires de sortie dans différents formats, y compris des flux d’impression PDF non interactifs, PostScript, PCL et ZPL.
* Générer des fichiers PDF d’impression à partir de fichiers PDF de formulaire XFA.
* Générez des documents PDF, PostScript, PCL et ZPL en blocs en fusionnant plusieurs jeux de données avec les modèles fournis.

>[!NOTE]
>
>Le service Output est une application 32 bits. Sous Microsoft Windows, une application 32 bits peut utiliser un maximum de 2 Go de mémoire. La limite s’applique également au service Output.

## Création de documents de formulaire non interactifs {#creating-non-interactive-form-documents}

![usingoutput_modified](assets/usingoutput_modified.png)

En général, vous créez des modèles dans AEM Forms Designer. Les API `generatePDFOutput` et `generatePrintedOutput` du service Output permettent de convertir directement ces modèles en divers formats, y compris au format PDF, PostScript, ZPL et PCL.

L’opération `generatePDFOutput` génère des fichiers PDF, tandis que l’opération `generatePrintedOutput` génère des formats PostScript, ZPL et PCL. Le premier paramètre des deux opérations accepte le nom du fichier du modèle (par exemple `ExpenseClaim.xdp`) ou un objet de document qui contient le modèle. Lorsque vous spécifiez le nom du fichier de modèle, spécifiez également la racine du contenu en tant que chemin d’accès au dossier contenant le modèle. Vous pouvez spécifier la racine du contenu à l’aide du paramètre `PDFOutputOptions` ou `PrintedOutputOptions`. Consultez la documentation Javadoc pour en savoir plus sur les autres options que vous pouvez spécifier à l’aide de ces paramètres.

Le deuxième paramètre accepte un document XML fusionné avec le modèle lors de la génération du document de sortie.

L’opération `generatePDFOutput` peut également accepter un formulaire PDF XFA comme entrée et renvoyer une version non interactive du formulaire PDF en sortie.

## Génération de documents de formulaire non interactifs {#generating-non-interactive-form-documents}

Supposons que vous ayez un ou plusieurs modèles et plusieurs enregistrements de données XML pour chaque modèle.

Utilisez les opérations `generatePDFOutputBatch` et `generatePrintedOutputBatch` du service Output pour générer un document d’impression pour chaque enregistrement.

Vous pouvez également combiner les enregistrements en un seul document. Les deux opérations nécessitent quatre paramètres.

Le premier paramètre est un mappage qui contient une chaîne arbitraire comme clé et le nom du fichier de modèle comme valeur.

Le deuxième paramètre est un autre mappage dont la valeur est un objet de document qui contient des données XML. La clé est la même que celle que vous spécifiez pour le premier paramètre.

Le troisième paramètre pour `generatePDFOutputBatch` ou `generatePrintedOutputBatch` est du type `PDFOutputOptions` ou `PrintedOutputOptions`, respectivement.

Les types de paramètre sont les mêmes que ceux des paramètres pour les opérations `generatePDFOutput` et `generatePrintedOutput` et ont le même effet.

Le quatrième paramètre est du type `BatchOptions`. Vous l’utilisez pour spécifier si un fichier distinct peut être généré pour chaque enregistrement. La valeur par défaut de ce paramètre est « false » (faux).

Les opérations `generatePrintedOutputBatch` et `generatePDFOutputBatch` renvoient une valeur de type `BatchResult`. La valeur contient une liste de documents générés. Elle comporte également un document de métadonnées au format XML qui contient des informations relatives à chaque document généré.
