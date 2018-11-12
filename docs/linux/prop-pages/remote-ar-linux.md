---
title: Archive distante, propriétés (Linux C++)
ms.date: 9/26/2017
ms.assetid: 5ee1e44c-8337-4c3a-b2f3-35e4be954f9f
f1_keywords: []
ms.openlocfilehash: bcd0e0eef16addc60743000b6ed8cba12276e29c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50439222"
---
# <a name="remote-archive-properties-c-linux"></a>Archive distante, propriétés (Linux C++)

Property | Description
--- | ---
Créer un index d’archive | Crée un index d’archive (voir ranlib).  Cette opération contribue à accélérer l’édition des liens et à réduire la dépendance au sein de sa propre bibliothèque.
Créer une archive fine | Crée une archive fine.  Une archive fine n’incorpore pas les objets, mais contient leurs chemins relatifs.  Le passage entre les modes Fin et Normal nécessite la suppression de la bibliothèque existante.
Aucun avertissement à la création | N’affiche pas d’avertissement quand la bibliothèque est créée.
Tronquer l’horodatage | Utilise zéro pour les horodatages et les UID/GID.
Supprimer la bannière de démarrage | Le numéro de version n’est pas affiché.
Verbose | Verbose
Options supplémentaires | Options supplémentaires.
Fichier de sortie | L’option /OUT substitue le nom et l’emplacement par défaut du programme créé par lib.
Programme d’archivage | Spécifie le programme à appeler durant l’édition des liens d’objets statiques, ou le chemin du programme d’archivage sur le système distant.
Délai d’attente du programme d’archivage | Délai d’attente du programme d’archivage distant, en millisecondes.
Copier la sortie | Indique s’il faut copier le fichier de sortie de build du système distant sur la machine locale.
