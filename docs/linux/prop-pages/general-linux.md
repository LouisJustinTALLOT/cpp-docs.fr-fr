---
title: Propriétés générales (Projet Linux CMD)
description: Décrit les propriétés du projet Linux que vous pouvez définir dans Visual Studio sur la page propriétés générales.
ms.date: 01/14/2020
ms.assetid: 56c800a9-3df9-4196-87b2-81adb00e4767
ms.openlocfilehash: 832f10ca2c95e40ff7ece23462105fa49014aa5d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "79446167"
---
# <a name="general-properties-linux-c"></a>Propriétés générales (Linux CMD)

::: moniker range="vs-2015"

La prise en charge Linux est disponible dans Visual Studio 2017 et ultérieur.

::: moniker-end

::: moniker range=">=vs-2017"

| Propriété | Description | Choices |
|--|--|--|
| Répertoire de sortie | Spécifie un chemin relatif vers l’annuaire des fichiers de sortie. Il peut inclure des variables d'environnement. |
| Répertoire intermédiaire | Spécifie un chemin d'accès relatif au répertoire des fichiers intermédiaires. Il peut inclure des variables d'environnement. |
| Nom de la cible | Spécifie le nom de fichier que ce projet génère. |
| Extension de la cible | Spécifie l’extension `.a`de fichiers (par exemple) que ce projet génère. |
| Extensions à supprimer lors du nettoyage | Spécification de wildcard semi-colon-délimité pour quels fichiers dans l’annuaire intermédiaire à supprimer sur propre ou reconstruire. |
| Fichier journal de génération | Spécifie le fichier journal de génération à utiliser quand la journalisation de la génération est activée. |
| Ensemble d'outils de plateforme | Spécifie le sertier d’outils utilisé pour la construction de la configuration actuelle. Si elle n’est pas définie, l’ensemble d’outils par défaut est utilisé. |
| Machine de build distante | Affiche la machine ou l’appareil cible à utiliser pour la construction à distance, le déploiement et le débogé. Vous pouvez ajouter ou modifier une connexion machine cible en utilisant **Tools** > **Options** > **Cross Platform** > **Connection Manager**.<br /> **Visual Studio 2019 version 16.1** Vous pouvez spécifier une autre machine pour débogage sur la page [Debugging.](debugging-linux.md) |
| Répertoire racine de build distant | Spécifie le chemin d’un répertoire sur la machine ou l’appareil distant. |
| Répertoire de projet de build distant | Spécifie le chemin d’un répertoire sur la machine ou l’appareil distant du projet. |
| Répertoire de déploiement à distance | **Visual Studio 2019 version 16.1** Spécifie le parcours de la machine à distance ou de l’appareil pour déployer le projet. |
| Copie à distance Inclure des répertoires | **Visual Studio 2019 version 16.5**  Une liste d’annuaires à copier de façon récursive de la cible Linux. Cette propriété affecte la copie d’en-tête à distance pour IntelliSense, mais pas la construction. Il peut être utilisé lorsque **IntelliSense Utilise Compiler Defaults** est mis à faux. Utilisez **d’autres répertoires inclus** dans l’onglet C/C-General pour spécifier d’autres répertoires à utiliser pour IntelliSense et construire. |
| La copie à distance exclut les répertoires | **Visual Studio 2019 version 16.5** Une liste d’annuaires à *ne pas* copier à partir de la cible Linux. Habituellement, cette propriété est utilisée pour supprimer les sous-directeurs des répertoires inclus. |
| IntelliSense utilise Compiler Par défaut | **Visual Studio 2019 version 16.5** Que ce soit pour interroger le compilateur référencé par ce projet pour sa liste par défaut d’inclure des emplacements. Ces emplacements sont automatiquement ajoutés à la liste des répertoires distants à copier. Ne définissez cette propriété à faux que si le compilateur ne prend pas en charge les paramètres de gcc. Les compilateurs de gcc et de clang soutiennent les `g++ -x c++ -E -v -std=c++11`requêtes pour les répertoires incluent (par exemple, ). |
| Type de configuration | Spécifie le type de sortie généré par cette configuration. | **Bibliothèque dynamique (.so)**<br/><br/>**Bibliothèque statique (.a)**<br/><br/>**Application (.out)**<br/><br/>**Makefile** |
| Utilisation de STL | Spécifie la bibliothèque C++ standard à utiliser pour cette configuration. | **Bibliothèque standard C++ GNU partagée**<br/><br/>**Bibliothèque standard C++ GNU statique (-static)** |

::: moniker-end
