---
title: Erreur des outils Éditeur de liens LNK1277
ms.date: 11/04/2016
f1_keywords:
- LNK1277
helpviewer_keywords:
- LNK1277
ms.assetid: afca3de0-50cc-4140-af7a-13493a170835
ms.openlocfilehash: 137aa15dd9dad4b08d52af55da60a9cdf8b58055
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50662070"
---
# <a name="linker-tools-error-lnk1277"></a>Erreur des outils Éditeur de liens LNK1277

enregistrement objet introuvable dans pgd (NomFichier)

Lorsque vous utilisez [/LTCG : PGOPTIMZE](../../build/reference/ltcg-link-time-code-generation.md), le chemin d’accès d’un des fichiers d’entrée .lib, def ou .obj était différent du chemin d’accès sur lequel ils ont été trouvés lors/LTCG : PGINSTRUMENT. Cela peut s’expliquer par une modification dans la variable d’environnement LIB après/LTCG : PGINSTRUMENT. Le chemin d’accès complet aux fichiers d’entrée est stockée dans le fichier .pgd.

/ LTCG : PGOPTIMIZE exige que les entrées soit identique à la phase / LTCG : PGINSTRUMENT.

Pour résoudre cet avertissement, effectuez l’une des opérations suivantes :

- Exécutez/LTCG : PGINSTRUMENT, restauration par progression de toutes les séries de tests et exécutez/LTCG : PGOPTIMIZE.

- Modifier la variable d’environnement LIB pour qu’il avait lors de l’exécution / LTCG : PGINSTRUMENT.

Il est déconseillé de contourner LNK1277 à l’aide de/LTCG : PGUPDATE.