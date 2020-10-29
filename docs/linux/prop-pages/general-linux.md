---
title: Propriétés générales (projet Linux C++)
description: Décrit les propriétés de projet Linux que vous pouvez définir dans Visual Studio sur la page Propriétés générales.
ms.date: 10/14/2020
ms.assetid: 56c800a9-3df9-4196-87b2-81adb00e4767
ms.openlocfilehash: 188e73f20eccc0e61278e154dd26e34e8613e1e9
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/29/2020
ms.locfileid: "92924492"
---
# <a name="general-properties-linux-c"></a>Propriétés générales (Linux C++)

::: moniker range="msvc-140"

La prise en charge Linux est disponible dans Visual Studio 2017 et ultérieur.

::: moniker-end

::: moniker range=">=msvc-150"

| Propriété | Description |
|--|--|
| Répertoire de sortie | Spécifie un chemin d’accès relatif au répertoire de fichiers de sortie. Il peut inclure des variables d'environnement. |
| Répertoire intermédiaire | Spécifie un chemin d'accès relatif au répertoire des fichiers intermédiaires. Il peut inclure des variables d'environnement. |
| Nom de la cible | Spécifie le nom de fichier généré par ce projet. |
| Extension de la cible | Spécifie l’extension de fichier (par exemple, `.a` ) générée par ce projet. |
| Extensions à supprimer lors du nettoyage | Spécification de caractères génériques délimités par des points-virgules pour les fichiers du répertoire intermédiaire à supprimer lors du nettoyage ou de la régénération. |
| Fichier journal de génération | Spécifie le fichier journal de génération à utiliser quand la journalisation de la génération est activée. |
| Ensemble d'outils de plateforme | Spécifie l’ensemble d’outils utilisé pour générer la configuration actuelle. S’il n’est pas défini, l’ensemble d’outils par défaut est utilisé. |
| WSL *. exe-chemin d’accès complet | **Visual Studio 2019 version 16,1** Chemin d’accès complet au fichier exécutable Windows sous-système pour Linux (WSL) utilisé pour la génération et le débogage. |
| Machine de build distante | Affiche l’ordinateur ou le périphérique cible à utiliser pour la génération, le déploiement et le débogage à distance. Vous pouvez ajouter ou modifier une connexion à un ordinateur cible à l’aide des options **Outils**  >  **Options**  >  Gestionnaire de **Cross Platform**  >  **connexions** multiplateforme.<br /> **Visual Studio 2019 version 16,1** Vous pouvez spécifier un autre ordinateur pour le débogage sur la page [débogage](debugging-linux.md) . |
| Répertoire racine de build distant | Spécifie le chemin d’un répertoire sur la machine ou l’appareil distant. |
| Répertoire de projet de build distant | Spécifie le chemin d’un répertoire sur la machine ou l’appareil distant du projet. |
| Répertoire de déploiement distant | **Visual Studio 2019 version 16,1** Spécifie le chemin d’accès au répertoire sur l’ordinateur ou l’appareil distant pour déployer le projet. |
| Activer la build incrémentielle | **Visual Studio 2019 version 16,7** Spécifie s’il faut effectuer des builds incrémentielles à l’aide du système de génération [Ninja](https://ninja-build.org/) . Les builds sont généralement plus rapides pour la plupart des projets avec ce paramètre activé. |
| Répertoires Include de la copie distante | **Visual Studio 2019 version 16,5**  Liste des répertoires à copier de manière récursive à partir de la cible Linux. Cette propriété affecte la copie d’en-tête distant pour IntelliSense, mais pas la Build. Il peut être utilisé quand **IntelliSense utilise les valeurs par défaut du compilateur** a la valeur false. Utilisez **des répertoires Include supplémentaires** sous l’onglet général C/C++ pour spécifier des répertoires Include supplémentaires à utiliser à la fois pour IntelliSense et pour la génération. |
| Répertoires d’exclusion de la copie distante | **Visual Studio 2019 version 16,5** Liste de répertoires à *ne pas* copier à partir de la cible Linux. En règle générale, cette propriété est utilisée pour supprimer les sous-répertoires des répertoires Include. |
| IntelliSense utilise les valeurs par défaut du compilateur | **Visual Studio 2019 version 16,5** Indique s’il faut interroger le compilateur référencé par ce projet pour obtenir la liste par défaut des emplacements include. Ces emplacements sont automatiquement ajoutés à la liste des répertoires distants à copier. Affectez uniquement la valeur false à cette propriété si le compilateur ne prend pas en charge les paramètres de type GCC. Les compilateurs GCC et Clang prennent en charge les requêtes pour les répertoires Include (par exemple, `g++ -x c++ -E -v -std=c++11` ). |
| Type de configuration | Spécifie le type de sortie généré par cette configuration, par exemple : **bibliothèque dynamique (. so)** , **bibliothèque statique (. a)** , **application (. out)** et **Makefile** |
| Utilisation de STL | Spécifie la bibliothèque C++ standard à utiliser pour cette configuration, par exemple : **bibliothèque C++ GNU standard partagée** ou **bibliothèque C++ standard GNU statique (-static)** |

::: moniker-end
