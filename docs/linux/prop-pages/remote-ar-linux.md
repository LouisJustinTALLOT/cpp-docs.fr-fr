---
title: Archive distante, propriétés (Linux C++)
ms.date: 06/07/2019
ms.assetid: 5ee1e44c-8337-4c3a-b2f3-35e4be954f9f
f1_keywords: []
ms.openlocfilehash: 3b6f71d9cceccf0b0221be46bacb1294d84533cd
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364300"
---
# <a name="remote-archive-properties-c-linux"></a>Archive distante, propriétés (Linux C++)

::: moniker range="vs-2015"

La prise en charge Linux est disponible dans Visual Studio 2017 et ultérieur.

::: moniker-end

::: moniker range=">=vs-2017"

| Propriété | Description |
|--|--|
| Créer un index d’archive | Crée un index d’archive (comme le fait ranlib). Cette option contribue à accélérer l’édition des liens et à réduire la dépendance au sein de sa propre bibliothèque. |
| Créer une archive fine | Crée une archive fine.  Une archive fine n’incorpore pas les objets, mais contient leurs chemins relatifs.  Le passage entre les modes Fin et Normal nécessite la suppression de la bibliothèque existante. |
| Aucun avertissement à la création | N’affiche pas d’avertissement si ou quand la bibliothèque est créée. |
| Tronquer l’horodatage | Utilise zéro pour les horodatages et les UID/GID. |
| Supprimer la bannière de démarrage | N’affiche pas le numéro de version. |
| Commentaires | Commentaires |
| Options supplémentaires | Options supplémentaires. |
| Fichier de sortie | L’option /OUT substitue le nom et l’emplacement par défaut du programme créé par lib. |
| Programme d’archivage | Spécifie le programme à appeler durant l’édition des liens d’objets statiques, ou le chemin du programme d’archivage sur le système distant. |
| Délai d’attente du programme d’archivage | Délai d’attente du programme d’archivage distant, en millisecondes. |
| Copier la sortie | Indique s’il faut copier le fichier de sortie de build du système distant sur la machine locale. |

::: moniker-end
