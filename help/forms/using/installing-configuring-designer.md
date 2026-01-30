---
title: Installation et configuration de Designer
description: Designer est disponible sous la forme d’un programme autonome et est également fourni avec Workbench. Découvrez comment installer un Designer autonome.
role: Admin, User, Developer
feature: Forms Designer,Designer
solution: Experience Manager, Experience Manager Forms
exl-id: 526bbc59-62c3-4e6d-a938-e368d07fe6b0
source-git-commit: eb6f6b994fdd3b2b01e77700d2deb7bd2830ac8f
workflow-type: tm+mt
source-wordcount: '801'
ht-degree: 65%

---

# Installation et configuration de Designer{#installing-and-configuring-designer}

## Prérequis {#pre-requisites}

+++ Pour AEM Forms Designer 64 bits (recommandé)

* Installez une version 64 bits de [Redistribuable Visual C++ 2019 (x64)](https://learn.microsoft.com/fr-fr/cpp/windows/latest-supported-vc-redist?view=msvc-170). Assurez-vous que les packages d’exécution redistribuables susmentionnés sont installés avant de démarrer l’installation.
* Un utilisateur ou une utilisatrice disposant des droits d’administration pour installer ou désinstaller AEM Forms Designer.

+++

+++ Pour AEM Forms Designer 32 bits

* Installez une version 32 bits de [Redistribuable Visual C++ 2019 (x64)](https://learn.microsoft.com/fr-fr/cpp/windows/latest-supported-vc-redist?view=msvc-170). Assurez-vous que les packages d’exécution redistribuables susmentionnés sont installés avant de démarrer l’installation.
* Un utilisateur ou une utilisatrice disposant des droits d’administration pour installer ou désinstaller AEM Forms Designer.

+++

>[!NOTE]
>
>* La version 64 bits de Designer a été introduite avec le pack de services 19 (6.5.19.0) d’AEM 6.5 Forms.
>* La version 32 bits de Designer est obsolète depuis la publication du [Service Pack AEM Forms 21 (6.5.21.0)](https://experienceleague.adobe.com/fr/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases).
> * Les plateformes prises en charge pour Forms Designer s’alignent sur les plateformes prises en charge par AEM Forms. Pour en savoir plus sur les plateformes prises en charge pour Forms Designer, [cliquez ici](/help/sites-deploying/technical-requirements.md)

Pour plus d’informations sur l’installation de Forms Designer, voir [Questions fréquentes](#fandq).

## Installer AEM Forms Designer {#install-designer}

Designer est disponible sous la forme d’un programme autonome et est également fourni avec Workbench. Si vous utilisez un programme d’installation autonome pour AEM Forms Designer, procédez comme suit :

1. Désinstallez la version précédente d’AEM Forms Designer, si elle est déjà installée.
1. Téléchargez AEM Forms Designer 64 bits (recommandé) ou AEM Forms Designer 32 bits en fonction de vos besoins.

   >[!NOTE]
   > 
   >* Forms Designer 32 bits devrait devenir obsolète avec la version 6.5 d’AEM Forms, pack de services 20 (6.5.20.0). Adobe vous recommande d’effectuer une mise à niveau vers Forms Designer 64 bits.
   >* Forms Designer 64 bits est disponible uniquement pour AEM Forms 6.5, pack de services 19 (6.5.19.0) ou versions ultérieures.
   >* À compter de la version d’Adobe Experience Manager 6.5 Forms, pack de services 15 (6.5.15.0), la version Forms Designer inclut également la version du Service Pack. Par exemple, pour le pack de services 15, le numéro de version est 6.5.15.20221112.1.0. Dans cet exemple, 6.5.15 est la version du pack de services .

1. Lancez le programme d’installation d’AEM Forms Designer en cliquant deux fois sur setup.exe.
1. Continuez et fournissez vos détails ainsi que le numéro de série sur l’écran Personnalisation.

   >[!NOTE]
   >
   >* Obtenez votre clé de licence Forms Designer auprès du site Web de licences [Adobe](https://licensing.adobe.com/).

1. Si vous acceptez les termes du contrat de licence, cliquez sur Suivant pour continuer.
1. (Facultatif) Modifiez le chemin d’installation par défaut, si vous voulez installer Designer à l’emplacement de votre choix. Cliquez sur Suivant.
1. Cliquez sur Précédent pour modifier les préférences. Pour installer Designer, cliquez sur Installer.
1. Cliquez sur Terminer à la fin de l’installation.

Vous pouvez également installer AEM Forms Designer par le biais de la ligne de commande en mode passif ou silencieux.

* Installation en ligne de commande passive : le programme d’installation affiche une barre de progression qui indique que l’installation est en cours mais aucun message d’erreur ou d’invite ne s’affiche. Une fois l’installation lancée, vous ne pouvez pas l’annuler.

```shell
msiexec /i "<absolute path>\Designer.msi" /passive SERIALNUMBER=****-****-****-****-****-****
```

* Installation en ligne de commande silencieuse : le programme d’installation exécute l’installation sans afficher d’interface utilisateur. Aucun message, invite ou boîte de dialogue ne s’affiche. Une fois l’installation lancée, vous ne pouvez pas l’annuler.

```shell
msiexec /i "<absolute path>\Designer.msi" /quiet SERIALNUMBER=****-****-****-****-****-****
```

## Mettre à jour AEM Forms Designer {#update-forms-designer}

Il existe deux cas lors de la mise à jour de la dernière version d’AEM Forms Designer 6.5.6.5.16.0 :

* **Cas 1** : lorsque l’utilisateur ou l’utilisatrice dispose d’une version d’AEM Forms Designer antérieure à la version 6.5.15.0.
* **Cas 2** : lorsque l’utilisateur ou l’utilisatrice dispose de la version6.5.15.0 d’AEM Forms Designer.

+++**Lorsque l’utilisateur ou l’utilisatrice dispose d’une version d’AEM Forms Designer antérieure à la version 6.5.15.0.**

Si vous utilisez un programme d’installation autonome pour AEM Forms Designer, procédez comme suit :

1. Avant l’installation d’**AEM Forms Designer 6.5.16.0**, les utilisateurs et les utilisatrices doivent désinstaller toutes les versions précédentes.
1. Téléchargez et installez [AEM Forms Designer 6.5.15.0](https://experienceleague.adobe.com/en/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases#) à partir de la page Versions d’AEM Forms.
1. Après une installation réussie d’**AEM Forms Designer 6.5.15.0**, téléchargez et installez [AEM Forms Designer 6.5.16.0](https://experienceleague.adobe.com/en/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases#) en double-cliquant sur le fichier d’installation téléchargé.

+++

+++**Lorsque l’utilisateur ou l’utilisatrice dispose de la version 6.5.15.0 d’AEM Forms Designer**

Si vous utilisez un programme d’installation autonome pour AEM Forms Designer, procédez comme suit :

1. Téléchargez la dernière version d’AEM Forms Designer à partir du [Portail de distribution logicielle](https://experienceleague.adobe.com/en/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases#).
1. Installez la dernière version d’AEM Forms Designer en double-cliquant sur le fichier d’installation téléchargé.

+++

## Questions fréquentes {#fandq}

* **Un utilisateur peut-il directement mettre à niveau ou installer Designer 64 bits ?**
   * Oui, les utilisateurs peuvent directement mettre à niveau ou installer Designer 64 bits. Pour effectuer la mise à niveau, installez le programme d’installation complet de Designer [SP19](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/servicepack/fd/Designer-Patch/sp19_x64/aemforms_designer_6_5_0_wwe_win.zip) et appliquez-y la version de correctif Designer suivante.

     >[!NOTE]
     > Avant d’effectuer la mise à niveau vers Designer 64 bits, commencez par désinstaller Designer 32 bits s’il existe.

* **Est-il possible pour les utilisateurs et utilisatrices de conserver les deux versions 32 et 64 bits installées sur leur système ?**
   * Nombre Une installation 32 bits et 64 bits ne fonctionne pas sur le même ordinateur. L’utilisateur peut disposer d’un Designer 32 bits ou d’un Designer 64 bits.

* **Comment vérifier si un utilisateur utilise Designer 64 bits ou Designer 32 bits ?**
   * Il y a deux façons de vérifier la version de Forms Designer :

      1. Ouvrez Designer.
      1. Cliquez sur **Aide** > **À propos de Designer** pour afficher les informations de version et de fréquence de Designer.
Par exemple, la chaîne de version se termine par **64 bits** comme illustré dans l’exemple suivant :
         `6.5.21.20240522.1.161 | 64 bit`
      1. Ouvrez Designer. Dans le coin supérieur gauche, une icône d’image de marque contenant des informations 64 bits avec le nom du produit s’affiche.
