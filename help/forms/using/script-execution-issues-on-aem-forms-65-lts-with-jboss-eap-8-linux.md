---
title: Échec de l’exécution du script sur AEM Forms 6.5 LTS avec JBoss EAP 8 (Linux)
description: La configuration de JBoss EAP 8.0 dans un environnement Linux peut entraîner certaines erreurs lors de l’exécution de scripts shell ou de fichiers de démarrage
solution: Experience Manager
feature: Deploying
role: User,Admin,Developer
exl-id: 4dfaa625-47fa-4681-9e2f-a3bbdca95276
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 2e690827bfa8f3d8227860de4efb802758ae0095
workflow-type: tm+mt
source-wordcount: '240'
ht-degree: 1%
---
# Échec de l’exécution du script sur AEM Forms 6.5 LTS avec JBoss EAP 8 (Linux)

## Problème

Lors de la configuration de **JBoss EAP 8.0 (AEM Forms 6.5.1 LTS)** dans un environnement **Linux**, vous pouvez rencontrer l’une des erreurs suivantes lors de l’exécution de scripts shell ou de fichiers de démarrage :

```text
/bin/sh^M: bad interpreter
$'\r': command not found
```

Ces erreurs se produisent lorsque des scripts shell ou des fichiers de configuration ont été créés ou modifiés sur un système **Windows** et contiennent des terminaisons de ligne **retour chariot + saut de ligne)**.
Les systèmes Linux ne prennent en charge que les terminaisons de ligne **LF (Line Feed)** et les terminaisons de ligne de style Windows provoquent des échecs d’exécution de script.

## Application

* **JBoss EAP 8.0**
* **Systèmes d’exploitation Linux/UNIX**

## Étapes de dépannage

1. **Identifiez le fichier concerné**

   * Consultez la sortie d’erreur pour identifier le script `.sh` ou le fichier de configuration à l’origine de l’échec.

2. **Convertir le fichier au format Unix**

   * Utilisez l&#39;utilitaire `dos2unix` pour convertir les terminaisons de ligne de style Windows au format Unix :

     ```bash
     dos2unix <file_name>
     ```

   * Remplacez `<file_name>` par le script ou le fichier de configuration qui renvoie l’erreur.

3. **Répétez l’opération si nécessaire**

   * Si plusieurs scripts sont affectés, répétez la conversion pour tous les fichiers `.sh` pertinents (par exemple, les scripts de programme d’installation, de LCM ou de démarrage de JBoss).

4. **Réexécutez le script**

   * Après la conversion, exécutez à nouveau le script pour confirmer que le problème est résolu.

Après avoir converti les fichiers en terminaisons de ligne Unix (LF), les erreurs `/bin/sh^M` et `$'\r': command not found` sont résolues et les scripts JBoss s’exécutent correctement sous Linux.
