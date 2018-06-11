---
title: Général, propriétés (projet Makefile Linux C++) | Microsoft Docs
ms.custom: ''
ms.date: 9/26/2017
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: Linux
ms.topic: conceptual
ms.assetid: 3dec6853-43f6-412b-9806-9bfad333a204
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- linux
ms.openlocfilehash: 6fb23d2c7275788b05fe4450613770c268ca6c64
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34705697"
---
# <a name="makefile-project-properties-linux-c"></a>Projet Makefile, propriétés (Linux C++)

Il s’agit d’une liste partielle des propriétés disponibles dans un projet Makefile Linux. Beaucoup de propriétés de projet Makefile sont identiques aux propriétés de projet d’application de console C++ Linux.

## <a name="general"></a>Général

Propriété | Description | Options
--- | ---| ---
Répertoire de sortie | Spécifie un chemin relatif vers le répertoire de fichiers de sortie ; peut inclure des variables d’environnement.
Répertoire intermédiaire | Spécifie un chemin relatif vers le répertoire de fichiers intermédiaire ; peut inclure des variables d’environnement.
Fichier journal de génération | Spécifie le fichier journal de génération à utiliser quand la journalisation de la génération est activée.
Type de configuration | Spécifie le type de sortie générée par cette configuration. | **Bibliothèque dynamique (.so)**  : bibliothèque dynamique (.so)<br>**Bibliothèque statique (.a)**  : bibliothèque statique (.a)<br>**Application (.out)**  : application (.out)<br>**Makefile** : fichier makefile<br>
Machine de build distante | Machine ou appareil cible à utiliser pour la génération, le déploiement et le débogage à distance.
Répertoire racine de build distant | Spécifie le chemin d’un répertoire sur la machine ou l’appareil distant.
Répertoire de projet de build distant | Spécifie le chemin d’un répertoire sur la machine ou l’appareil distant du projet.

## <a name="debugging"></a>Débogage

Consultez [Débogage, propriétés (Linux C++)](debugging-linux.md)

## <a name="copy-sources"></a>Copier les sources

Consultez [Copier les sources, propriétés de projet (Linux C++)](copy-sources-project.md).

## <a name="build-events"></a>Événements de build

### <a name="pre-build-event"></a>Événement prébuild

Propriété | Description
--- | ---
Ligne de commande | Spécifie une ligne de commande pour l’outil d’événement prébuild à exécuter.
Description | Spécifie une description de l’outil d’événement prébuild à afficher.
Utilisation dans la génération | Spécifie si cet événement de build est exclu de la génération pour la configuration actuelle.
Fichiers supplémentaires à copier | Spécifie les fichiers supplémentaires à copier sur le système distant. Vous pouvez éventuellement fournir la liste sous forme de paires de mappage entre l’emplacement local et l’emplacement distant en utilisant la syntaxe suivante : fulllocalpath1:=fullremotepath1;fulllocalpath2:=fullremotepath2, où un fichier local peut être copié vers l’emplacement distant spécifié sur le système distant.

### <a name="post-build-event"></a>Événement post-build

Propriété | Description
--- | ---
Ligne de commande | Spécifie une ligne de commande pour l’outil d’événement postbuild à exécuter.
Description | Spécifie une description de l’outil d’événement post-build à afficher.
Utilisation dans la génération | Spécifie si cet événement de build est exclu de la génération pour la configuration actuelle.
Fichiers supplémentaires à copier | Spécifie les fichiers supplémentaires à copier sur le système distant. Vous pouvez éventuellement fournir la liste sous forme de paires de mappage entre l’emplacement local et l’emplacement distant en utilisant la syntaxe suivante : fulllocalpath1:=fullremotepath1;fulllocalpath2:=fullremotepath2, où un fichier local peut être copié vers l’emplacement distant spécifié sur le système distant.

### <a name="remote-pre-build-event"></a>Événement prébuild distant

Propriété | Description
--- | ---
Ligne de commande | Spécifie une ligne de commande pour l’outil d’événement prébuild à exécuter sur le système distant.
Description | Spécifie une description de l’outil d’événement prébuild à afficher.
Utilisation dans la génération | Spécifie si cet événement de build est exclu de la génération pour la configuration actuelle.
Fichiers supplémentaires à copier | Spécifie les fichiers supplémentaires à copier à partir du système distant. Vous pouvez éventuellement fournir la liste sous forme de paires de mappage entre l’emplacement distant et l’emplacement local en utilisant la syntaxe suivante : fullremotepath1:=fulllocalpath1;fullremotepath2:=fulllocalpath2, où un fichier distant peut être copié vers l’emplacement spécifié sur la machine locale.

### <a name="remote-post-build-event"></a>Événement post-build distant

Propriété | Description
--- | ---
Ligne de commande | Spécifie une ligne de commande pour l’outil d’événement post-build à exécuter sur le système distant.
Description | Spécifie une description de l’outil d’événement post-build à afficher.
Utilisation dans la génération | Spécifie si cet événement de build est exclu de la génération pour la configuration actuelle.
Fichiers supplémentaires à copier | Spécifie les fichiers supplémentaires à copier à partir du système distant. Vous pouvez éventuellement fournir la liste sous forme de paires de mappage entre l’emplacement distant et l’emplacement local en utilisant la syntaxe suivante : fullremotepath1:=fulllocalpath1;fullremotepath2:=fulllocalpath2, où un fichier distant peut être copié vers l’emplacement spécifié sur la machine locale.

## <a name="cc"></a>C/C++

### <a name="intellisense"></a>IntelliSense

Les propriétés IntelliSense peuvent être définies au niveau du projet ou du fichier pour fournir des indications au moteur IntelliSense. Elles n’impactent pas la compilation.

Propriété | Description
--- | ---
Chemin de recherche Include | Spécifie le chemin de recherche Include pour résoudre les fichiers Include.
Fichiers Include forcés | Spécifie les fichiers Include forcés.
Définitions de préprocesseur | Spécifie les définitions du préprocesseur utilisées par les fichiers sources.
Annuler la définition de définitions de préprocesseur | Spécifie l’annulation de la définition d’une ou de plusieurs définitions du préprocesseur.     (/U[macro])
Options supplémentaires | Spécifie les commutateurs supplémentaires du compilateur utilisés par IntelliSense lors de l’analyse des fichiers C++.

### <a name="build"></a>Générer

Propriété | Description
--- | ---
Ligne de commande Build | Spécifie la ligne de commande à exécuter pour la commande 'Build'.
Ligne de commande Rebuild All | Spécifie la ligne de commande à exécuter pour la commande 'Rebuild All'.
Ligne de commande Clean | Spécifie la ligne de commande à exécuter pour la commande 'Clean'.

### <a name="remote-build"></a>Build distante

Propriété | Description
--- | ---
Ligne de commande Build | Spécifie la ligne de commande à exécuter pour la commande 'Build'. Cette commande est exécutée sur le système distant.
Ligne de commande Rebuild All | Spécifie la ligne de commande à exécuter pour la commande 'Rebuild All'. Cette commande est exécutée sur le système distant.
Ligne de commande Clean | Spécifie la ligne de commande à exécuter pour la commande 'Clean'. Cette commande est exécutée sur le système distant.
Sorties | Spécifie les sorties générées par la build distante sur le système distant.
