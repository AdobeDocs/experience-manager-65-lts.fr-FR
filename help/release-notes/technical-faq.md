---
title: Questions techniques fréquentes
description: Questions techniques fréquentes sur AEM 6.5 LTS.
solution: Experience Manager
feature: Release Information
role: User,Admin,Developer
exl-id: 051244f1-cc67-4222-bd45-0c135c28bb15
source-git-commit: f994a8712a403083de1edc62579846ba99bd3afd
workflow-type: tm+mt
source-wordcount: '392'
ht-degree: 59%

---

# Questions techniques fréquentes sur AEM 6.5 LTS {#technical-faq}

Cette page est destinée à répondre à des questions techniques fréquentes sur AEM 6.5 LTS.

## Questions fréquentes techniques

### Le point d’entrée `/systemalive` n’est plus disponible dans AEM 6.5 LTS.

Le lot de système prêt à l’emploi Felix, configuré pour fournir le point d’entrée `/systemalive`, a été abandonné et remplacé par les contrôles d’intégrité Apache Felix. Ce lot n’est plus inclus dans AEM 6.5 LTS.

Le nouveau point d’entrée du contrôle d’intégrité est disponible à l’adresse `/system/health` et est implémenté à l’aide des contrôles d’intégrité Apache Felix.

Pour obtenir une documentation détaillée sur le framework de contrôle d’intégrité Felix, reportez-vous à la [documentation Felix](https://github.com/apache/felix-dev/blob/master/healthcheck/README.md).

### Prise en charge d’AEM Groovy Console

La version de la console AEM Groovy utilisée dans AEM 6.5 peut ne pas fonctionner dans AEM 6.5 LTS en raison de l’absence de dépendances guava. La nouvelle version prise en charge de la console AEM Groovy est la [19.0.8](https://github.com/orbinson/aem-groovy-console/releases/download/19.0.8/aem-groovy-console-all-19.0.8.zip).

#### Configuration supplémentaire requise pour la console AEM Groovy

Si vous utilisez la console AEM Groovy, vous devez ajouter explicitement la configuration OSGi suivante pour `com.adobe.granite.apicontroller.FilterResolverHookFactory`. Ajoutez des `aem-groovy-console-bundle` à la liste des lots autorisés pour la clé `org.apache.sling.distribution.api`, en étendant les valeurs par défaut de la plateforme :

```
"org.apache.sling.distribution.api": "com.adobe.*,com.day.*,org.apache.sling.*,aem-groovy-console-bundle"
```

### AEM 6.5 LTS prend-il en charge la synchronisation des utilisateurs et utilisatrices ?

Oui, AEM 6.5 LTS prend en charge la synchronisation des utilisateurs et utilisatrices. La fonctionnalité de synchronisation des utilisateurs et utilisatrices d’AEM 6.5 et 6.5 LTS est identique.

### Le fichier Uber JAR sur Maven Central semble être corrompu. Quel est le problème ?

Vérifiez que vous utilisez le fichier Uber JAR avec le classificateur `apis`. Notez que la structure de création de package d’Uber JAR a été modifiée dans AEM 6.5 LTS. Pour plus d’informations, consultez [Mettre à jour la version AEM Uber Jar](/help/sites-deploying/upgrading-code-and-customizations.md#update-the-aem-uber-jar-version).

### Le LTS AEM 6.5 prend-il en charge les espaces de noms de package `jakarta.*` (par exemple, `jakarta.annotation`) ?

Nombre AEM 6.5 LTS ne prend pas en charge les artefacts Sling migrés vers les espaces de noms de package `jakarta.*`. Utilisez les équivalents `javax.*` dans votre code et vos dépendances, par exemple, `javax.annotation.PostConstruct` plutôt que `jakarta.annotation.PostConstruct` dans les modèles Sling. L’implémentation des modèles Sling dans AEM 6.5 LTS ne reconnaît que les annotations `javax.*`. Par conséquent, `jakarta.*` annotations sont silencieusement ignorées lors de l’initialisation.

Pour plus d’informations, consultez l’article de la base de connaissances [Les modèles Sling avec `jakarta.annotation.PostConstruct` échouent sur AEM 6.5 LTS](https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-30339).

## Obtention d’aide supplémentaire

Si vous rencontrez des problèmes qui ne sont pas abordés ici :
* Consultez les [notes de mise à jour](/help/release-notes/release-notes.md) des problèmes connus.
* Pour obtenir de l’aide, contactez l’assistance Adobe.
