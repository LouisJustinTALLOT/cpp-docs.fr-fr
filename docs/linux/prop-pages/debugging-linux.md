---
title: Débogage, propriétés (Linux C++) | Microsoft Docs
ms.date: 06/07/2019
ms.assetid: 0c1c0fcc-a49b-451c-a5cb-ce9711fac064
ms.openlocfilehash: 2b55a0db001c98be72ac88c17c62b21e98ec4888
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/29/2020
ms.locfileid: "92924515"
---
# <a name="c-debugging-properties-linux-c"></a>Débogage C++, propriétés (Linux C++)

::: moniker range="msvc-140"

La prise en charge Linux est disponible dans Visual Studio 2017 et ultérieur.

::: moniker-end

::: moniker range=">=msvc-150"

| Propriété | Description | Choices |
|--|--|--|
| Machine de débogage distante | **Visual Studio 2019 version 16,1** : spécifie l’ordinateur sur lequel le programme doit être débogué. Peut être différente de la machine de build distante spécifiée dans la page [Général](general-linux.md). Vous pouvez ajouter ou modifier une connexion à un ordinateur cible à l’aide des options **Outils**  >  **Options**  >  Gestionnaire de **Cross Platform**  >  **connexions** multiplateforme. |
| Commande de prélancement | Commande exécutée dans l’interpréteur de commandes avant le démarrage du débogueur, qui peut être utilisée pour changer l’environnement de débogage. |
| Programme | Chemin complet sur le système distant du programme à déboguer. S’il reste vide ou s’il n’est pas changé, il renvoie par défaut à la sortie du projet actuel. |
| Arguments de programme | Arguments de ligne de commande à passer au programme en cours de débogage. |
| Répertoire de travail | Répertoire de travail de l’application distante. Par défaut, il s’agit du répertoire de base de l’utilisateur. |
| Commandes de débogueur supplémentaires | Commandes `gdb` supplémentaires que le débogueur doit exécuter avant le démarrage du débogage. |
| Numéro de port du débogueur | Numéro de port utilisé pour la communication du débogueur avec le débogueur distant. Le port ne doit pas être en cours d’utilisation sur le système local. Cette valeur doit être positive et comprise entre 1 et 65535. Si elle n’est pas indiquée, un numéro de port libre est utilisé. |
| Numéro de port du débogueur distant | Numéro de port sur lequel le serveur de débogueur distant `gdbserver` est à l’écoute sur le système distant. Le port ne doit pas être en cours d’utilisation sur le système distant. Cette valeur doit être positive et comprise entre 1 et 65535. Si elle n’est pas indiquée, un numéro de port libre (à partir du numéro 4444) est utilisé. |
| Mode de débogage | Spécifie la façon dont le débogueur interagit avec `gdb`. En *mode gdb* , le débogueur exécute `gdb` via l’interpréteur de commandes sur le système distant. En *mode gdbserver* , `gdb` s’exécute localement et se connecte à l' `gdbserver` exécution à distance. | **gdbserver**<br/>**gdb** |
| Autres chemins de recherche des symboles | Chemin de recherche supplémentaire pour les symboles de débogage (solib-search-path). |
| Déboguer les processus enfants | Spécifie s’il faut activer le débogage des processus enfants. |
| Activer la mise en forme Python | Permet d’afficher les valeurs d’expression selon une mise en forme élégante. Uniquement pris en charge en mode de débogage gdb. |
| Fichier de visualisation | Fichier de visualisation natif par défaut (.natvis) contenant les directives de visualisation des types SLT. Les autres fichiers .natvis associés à la solution actuelle sont chargés automatiquement. |
| Mappage de chemins de fichiers sources supplémentaires | Équivalences de chemins supplémentaires que le débogueur utilise pour mapper les noms de fichiers sources Windows aux noms de fichiers sources Linux. Le format est « \<windows-path> = \<linux-path> ;... ». Un nom de fichier source sous le chemin Windows est référencé comme s’il s’agissait d’un nom de fichier situé à la même position relative sous le chemin Linux. Les fichiers qui se trouvent dans le projet local ne nécessitent pas de mappage supplémentaire. |

::: moniker-end
