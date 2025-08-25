---
title: Questions techniques fréquentes
description: Questions techniques fréquentes sur AEM 6.5 LTS.
solution: Experience Manager
feature: Release Information
role: User,Admin,Architect,Developer
exl-id: 051244f1-cc67-4222-bd45-0c135c28bb15
source-git-commit: f983fc1edc613feaa070c4e82a92aabab9d50cbb
workflow-type: tm+mt
source-wordcount: '247'
ht-degree: 99%

---

# Questions techniques fréquentes sur AEM 6.5 LTS {#technical-faq}

Cette page est destinée à répondre à des questions techniques fréquentes sur AEM 6.5 LTS.

## Questions fréquentes techniques

### Le point d’entrée `/systemalive` n’est plus disponible dans AEM 6.5 LTS.

Le lot de système prêt à l’emploi Felix, configuré pour fournir le point d’entrée `/systemalive`, a été abandonné et remplacé par les contrôles d’intégrité Apache Felix. Ce lot n’est plus inclus dans AEM 6.5 LTS.

Le nouveau point d’entrée du contrôle d’intégrité est disponible à l’adresse `/system/health` et est implémenté à l’aide des contrôles d’intégrité Apache Felix.

Pour obtenir une documentation détaillée sur le framework de contrôle d’intégrité Felix, reportez-vous à la [documentation Felix](https://github.com/apache/felix-dev/blob/master/healthcheck/README.md).

### Prise en charge de la console AEM Groovy

La version de la console AEM Groovy utilisée dans AEM 6.5 peut ne pas fonctionner dans AEM 6.5 LTS en raison de l’absence de dépendances Guava. La nouvelle version prise en charge de la console AEM Groovy est la [19.0.8](https://github.com/orbinson/aem-groovy-console/releases/download/19.0.8/aem-groovy-console-all-19.0.8.zip).

### AEM 6.5 LTS prend-il en charge la synchronisation des utilisateurs et utilisatrices ?

Oui, AEM 6.5 LTS prend en charge la synchronisation des utilisateurs et utilisatrices. La fonctionnalité de synchronisation des utilisateurs et utilisatrices d’AEM 6.5 et 6.5 LTS est identique.

### Le fichier Uber JAR sur Maven Central semble être corrompu. Quel est le problème ?

Vérifiez que vous utilisez le fichier Uber JAR avec le classificateur `apis`. Notez que la structure de création de package d’Uber JAR a été modifiée dans AEM 6.5 LTS. Pour plus d’informations, consultez [Mettre à jour la version AEM Uber Jar](/help/sites-deploying/upgrading-code-and-customizations.md#update-the-aem-uber-jar-version).

## Obtention d’aide supplémentaire

Si vous rencontrez des problèmes qui ne sont pas abordés ici :
* Consultez les [notes de mise à jour](/help/release-notes/release-notes.md) des problèmes connus.
* Pour obtenir de l’aide, contactez l’assistance Adobe.
