---
title: Débogage, propriétés (Linux C++) | Microsoft Docs
ms.custom: ''
ms.date: 9/26/2017
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: Linux
ms.topic: conceptual
ms.assetid: 0c1c0fcc-a49b-451c-a5cb-ce9711fac064
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- linux
ms.openlocfilehash: df57a884186fe33d91de78647cc225f3a63a6f9f
ms.sourcegitcommit: e9ce38decc9f986edab5543de3464b11ebccb123
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/13/2018
ms.locfileid: "42578337"
---
# <a name="c-debugging-properties-linux-c"></a>Débogage C++, propriétés (Linux C++)

Property | Description | Options
--- | ---| ---
Commande de prélancement | Commande exécutée dans l’interpréteur de commandes avant le début du débogage et avant l’exécution du débogueur. Elle peut être utilisée pour changer l’environnement de débogage.
Programme | Chemin complet du programme à déboguer sur le système distant. Il s’agit d’un chemin sur le système distant. S’il reste vide ou s’il n’est pas changé, il renvoie par défaut à la sortie du projet actuel.
Arguments de programme | Arguments de ligne de commande à passer au programme en cours de débogage.
Répertoire de travail | Répertoire de travail de l’application distante. Par défaut, il s’agit du répertoire de base de l’utilisateur.
Commandes de débogueur supplémentaires | Commandes gdb supplémentaires que le débogueur doit exécuter avant le démarrage du débogage.
Numéro de port du débogueur | Numéro de port utilisé pour la communication du débogueur avec le débogueur distant. Le port ne doit pas être en cours d’utilisation sur le système local. Cette valeur doit être positive et comprise entre 1 et 65535. Si elle n’est pas indiquée, un numéro de port libre est utilisé.
Numéro de port du débogueur distant | Numéro de port sur lequel le serveur de débogueur distant (gdbserver) est à l’écoute sur le système distant. Le port ne doit pas être en cours d’utilisation sur le système distant. Cette valeur doit être positive et comprise entre 1 et 65535. Si elle n’est pas indiquée, un numéro de port libre (à partir du numéro 4444) est utilisé.
Mode de débogage | Spécifie la façon dont le débogueur interagit avec gdb. En mode gdb, le débogueur exécute gdb via l’interpréteur de commandes sur le système distant. En mode gdbserver, gdb s’exécute localement et se connecte à gdbserver, qui s’exécute à distance. | **gdbserver**<br>**gdb**<br>
Autres chemins de recherche des symboles | Chemin de recherche supplémentaire pour les symboles de débogage (solib-search-path).
Déboguer les processus enfants | Spécifie s’il faut activer le débogage des processus enfants.
Activer la mise en forme Python | Permet d’afficher les valeurs d’expression selon une mise en forme élégante. Uniquement pris en charge en mode de débogage gdb.
Fichier de visualisation | Fichier de visualisation natif par défaut (.natvis) contenant les directives de visualisation des types SLT. Les autres fichiers .natvis associés à la solution actuelle sont chargés automatiquement.
Mappage de chemins de fichiers sources supplémentaires | Équivalences de chemins supplémentaires que le débogueur utilise pour mapper les noms de fichiers sources Windows aux noms de fichiers sources Linux. Le format est « \<windows-path>=\<linux-path>;... ». Un nom de fichier source sous le chemin Windows est référencé comme s’il s’agissait d’un nom de fichier situé à la même position relative sous le chemin Linux. Les fichiers qui se trouvent dans le projet local ne nécessitent pas de mappage supplémentaire.
