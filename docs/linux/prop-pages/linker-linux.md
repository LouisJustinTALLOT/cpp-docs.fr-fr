---
title: Éditeur de liens, propriétés (Linux C++)
ms.date: 06/07/2019
ms.assetid: a0243a94-8164-425b-b2fe-b84ff363d546
ms.openlocfilehash: d6c6bc44a4d681f442a5a85ca9d5865c4590f884
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/29/2020
ms.locfileid: "92921488"
---
# <a name="linker-properties-linux-c"></a>Éditeur de liens, propriétés (Linux C++)

::: moniker range="msvc-140"

La prise en charge Linux est disponible dans Visual Studio 2017 et ultérieur.

::: moniker-end

::: moniker range=">=msvc-150"

## <a name="general"></a>Général

| Propriété | Description | Choices |
|--|--|--|
| Fichier de sortie | L’option substitue le nom et l’emplacement par défaut du programme créé par l’éditeur de liens. (-o) |
| Afficher la progression | Affiche les messages de progression de l’éditeur de liens. |
| Version | L’option -version indique à l’éditeur de liens de placer un numéro de version dans l’en-tête de l’exécutable. |
| Activer la sortie détaillée | L’option -verbose indique à l’éditeur de liens de générer la sortie des messages détaillés pour le débogage. |
| Trace | L’option --trace indique à l’éditeur de liens de générer la sortie des fichiers d’entrée au fur et à mesure de leur traitement. |
| Symboles de traces | Affiche la liste des fichiers dans lesquels un symbole apparaît. (--trace-symbol=symbol) |
| Afficher le mappage | L’option --print-map indique à l’éditeur de liens de générer la sortie d’un mappage de liens. |
| Signaler les références de symboles non résolus | Quand cette option est activée, les références des symboles non résolus sont signalées. |
| Optimiser pour l’utilisation de la mémoire | Permet d’optimiser l’utilisation de la mémoire, en relisant les tables de symboles selon les besoins. |
| Chemin de recherche de la bibliothèque partagée | Permet à l’utilisateur de remplir le chemin de recherche de la bibliothèque partagée. (-rpath-link=path) |
| Répertoires de bibliothèques supplémentaires | Permet à l’utilisateur de substituer le chemin de la bibliothèque d’environnement. (-L folder). |
| Éditeur de liens | Spécifie le programme à appeler durant l’édition des liens, ou le chemin de l’éditeur de liens sur le système distant. |
| Délai d’attente de l’édition des liens | Délai d’attente de l’édition des liens distante, en millisecondes. |
| Copier la sortie | Indique s’il faut copier le fichier de sortie de build du système distant sur la machine locale. |

## <a name="input"></a>Entrée

| Propriété | Description | Choices |
|--|--|--|
| Bibliothèques par défaut spécifiques ignorées | Spécifie un ou plusieurs noms de bibliothèques par défaut à ignorer. (--exclude-libs lib,lib) |
| Ignorer les bibliothèques par défaut | Ignore les bibliothèques par défaut et recherche uniquement les bibliothèques explicitement spécifiées. |
| Forcer la non-définition des références de symboles | Force l’entrée du symbole dans le fichier de sortie en tant que symbole non défini. (-u symbol --undefined=symbol) |
| Dépendances de bibliothèque | Cette option permet de spécifier des bibliothèques supplémentaires à ajouter à la ligne de commande de l’éditeur de liens. La bibliothèque supplémentaire est ajoutée à la fin de la ligne de commande de l’éditeur de liens, avec le préfixe 'lib' et l’extension '.a'.  (-lFILE) |
| Dépendances supplémentaires | Spécifie les éléments supplémentaires à ajouter à la ligne de commande de l’éditeur de liens. |

## <a name="debugging"></a>Débogage

| Propriété | Description | Choices |
|--|--|--|
| Informations de symboles du débogueur | Informations de symboles du débogueur contenues dans le fichier de sortie. | **Inclure tout**<br>**Omettre les informations de symboles du débogueur uniquement**<br>**Omettre toutes les informations de symbole**<br> |
| Nom de fichier de mappage | L’option Map indique à l’éditeur de liens de créer un fichier de mappage avec le nom spécifié par l’utilisateur. (-Map=) |

## <a name="advanced"></a>Avancé

| Propriété | Description | Choices |
|--|--|--|
| Marquer les variables ReadOnly après le réadressage | Cette option marque les variables en lecture seule après le réadressage. |
| Activer la liaison de fonction immédiate | Cette option marque l’objet pour une liaison de fonction immédiate. |
| Ne pas exiger de pile exécutable | Cette option marque la sortie en indiquant qu’elle ne nécessite pas de pile exécutable. |
| Archive complète | L’archive complète utilise l’ensemble du code des sources et des dépendances supplémentaires. |

::: moniker-end
