---
title: Copier les sources, propriétés de projet (Linux C++)
ms.date: 9/26/2017
ms.assetid: 1a44230d-5dd8-4d33-93b4-e77e03e00150
ms.openlocfilehash: dd0a26db58265724f0a0e46c31365c97c00ff568
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50477244"
---
# <a name="copy-sources-project-properties-linux-c"></a>Copier les sources, propriétés de projet (Linux C++)

Les propriétés définies dans cette page de propriétés s’appliquent à tous les fichiers contenus dans le projet, à l’exception de ceux pour lesquels des propriétés de niveau fichier sont définies.

Property | Description
--- | ---
Sources à copier | Spécifie les sources devant être copiées sur le système distant. Tout changement apporté à cette liste peut entraîner un décalage ou des répercussions dans la structure des répertoires où sont copiés les fichiers sur le système distant.
Copier les sources | Spécifie si les sources doivent être copiées sur le système distant.
Sources supplémentaires à copier | Spécifie les sources supplémentaires à copier sur le système distant. Vous pouvez éventuellement fournir la liste sous forme de paires de mappage entre l’emplacement local et l’emplacement distant en utilisant la syntaxe suivante : fulllocalpath1:=fullremotepath1;fulllocalpath2:=fullremotepath2, où un fichier local peut être copié vers l’emplacement distant spécifié sur le système distant.
