---
title: Questions techniques fréquentes
description: Questions techniques fréquentes sur AEM 6.5 LTS.
solution: Experience Manager
feature: Release Information
role: User,Admin,Architect,Developer
exl-id: 051244f1-cc67-4222-bd45-0c135c28bb15
source-git-commit: ec722773ce3acff1d0de861523db8ff7df552c4b
workflow-type: tm+mt
source-wordcount: '247'
ht-degree: 2%

---

# FAQ technique sur AEM 6.5 LTS {#technical-faq}

Cette page est destinée à répondre à des questions techniques fréquentes sur AEM 6.5 LTS.

## Questions fréquentes techniques

### Le point d’entrée `/systemalive` n’est plus disponible dans AEM 6.5 LTS.

Le lot Felix System Ready , configuré pour fournir le point d’entrée `/systemalive`, a été abandonné et remplacé par les contrôles d’intégrité Apache Felix. Ce lot n’est plus inclus dans AEM 6.5 LTS.

Le nouveau point d’entrée du contrôle d’intégrité est disponible à l’adresse `/system/health` et est implémenté à l’aide des contrôles d’intégrité Apache Felix.

Pour obtenir une documentation détaillée sur le framework de contrôle d’intégrité Felix, reportez-vous à la [documentation Felix](https://github.com/apache/felix-dev/blob/master/healthcheck/README.md).

### Prise en charge de la console AEM Groovy

La version de la console AEM Groovy utilisée dans AEM 6.5 peut ne pas fonctionner dans AEM 6.5 LTS en raison de l’absence de dépendances guava. La nouvelle version prise en charge de la console AEM Groovy est la [19.0.8](https://mvnrepository.com/artifact/be.orbinson.aem/aem-groovy-console/19.0.8).

### AEM 6.5 LTS prend-il en charge la synchronisation des utilisateurs ?

Oui, AEM 6.5 LTS prend en charge la synchronisation des utilisateurs. La fonctionnalité de synchronisation des utilisateurs entre AEM 6.5 et 6.5 LTS n’a pas changé.

### Le fichier Uber JAR sur Maven Central semble être corrompu. Quel est le problème ?

Vérifiez que vous utilisez Uber JAR avec le classificateur `apis`. Notez que la structure de création de package d’Uber JAR a changé dans AEM 6.5 LTS. Pour plus d’informations, voir [Mise à jour de la version AEM Uber Jar](/help/sites-deploying/upgrading-code-and-customizations.md#update-the-aem-uber-jar-version).

## Obtention d’aide supplémentaire

Si vous rencontrez des problèmes qui ne sont pas abordés ici :
* Consultez les [notes de mise à jour](/help/release-notes/release-notes.md) pour connaître les problèmes connus.
* Pour obtenir de l’aide, contactez l’assistance Adobe.
