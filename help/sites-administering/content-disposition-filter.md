---
title: Filtre de disposition du contenu
description: Découvrez comment utiliser le filtre de disposition du contenu pour empêcher les attaques XSS.
contentOwner: trushton
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: Security
solution: Experience Manager, Experience Manager Sites
feature: Security
role: Admin
exl-id: 997cb6f3-1ef8-409c-acea-157d5b27a6b2
source-git-commit: c3e9029236734e22f5d266ac26b923eafbe0a459
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Filtre de disposition du contenu {#content-disposition-filter}

Le filtre de disposition de contenu est une fonctionnalité de sécurité contre les attaques XSS sur les fichiers SVG.

Une fois installé, le filtre bloque l’accès à toutes les ressources. Par exemple, il vous a été impossible d’afficher un PDF en ligne. Cette section décrit comment configurer le filtre selon vos besoins.

## Configuration du filtre de disposition du contenu {#configure-content-disposition-filter}

Vous pouvez visualiser le [filtre de disposition de contenu Apache Sling dans GitHub](https://github.com/apache/sling-org-apache-sling-security/blob/master/src/main/java/org/apache/sling/security/impl/ContentDispositionFilterConfiguration.java).

Les options du filtre de disposition du contenu offrent les fonctionnalités suivantes :

* **Chemins de disposition du contenu :** une liste des chemins d’accès pour lesquels le filtre est appliqué, suivie d’une liste de types MIME à exclure sur ce chemin. Ce chemin d’accès doit être un chemin absolu et peut contenir un caractère générique (`*`) à la fin, pour faire correspondre chaque chemin de ressource avec le préfixe de chemin donné. Par exemple : `/content/*:image/jpeg,image/svg+xml` applique le filtre à chaque nœud dans `/content?` à l’exception des images JPG et SVG.

* **Chemins d’accès aux ressources exclues :** une liste de ressources exclues. Chaque chemin doit être absolu et complet. La correspondance des préfixes et les caractères génériques ne sont pas pris en charge.

* **Activer pour tous les chemins d’accès aux ressources :** cet indicateur contrôle l’activation de ce filtre pour tous les chemins, à l’exception des chemins d’accès aux ressources exclues. En définissant cet indicateur sur « true », vous pouvez ignorer les chemins de disposition du contenu. Indépendamment de la configuration, seuls les chemins d’accès aux ressources sont concernés, lesquels contiennent une propriété nommée « `jcr:data` » ou « `jcr:content/jcr:data` ».
