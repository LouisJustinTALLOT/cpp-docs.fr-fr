---
title: Calcul des valeurs nécessaires
ms.date: 11/04/2016
helpviewer_keywords:
- helper functions, calculating necessary values
ms.assetid: 4f037d0f-881a-4a48-a9d2-9f8872dfccb7
ms.openlocfilehash: 80c028a315669fb0032628bb86a834d429935f50
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50513865"
---
# <a name="calculating-necessary-values"></a>Calcul des valeurs nécessaires

Deux informations essentielles doivent être calculées par la routine d’assistance de délai. À cette fin, il existe deux fonctions inline dans delayhlp.cpp pour le calcul de ces informations.

- La première calcule l’index de l’importation en cours dans les trois tables (import address table (IAT), importation liées BIAT (address table) et (UIAT) indépendant import address table).

- Le deuxième compte le nombre d’importations dans une table IAT valide.

```cpp
// utility function for calculating the index of the current import
// for all the tables (INT, BIAT, UIAT, and IAT).
__inline unsigned
IndexFromPImgThunkData(PCImgThunkData pitdCur, PCImgThunkData pitdBase) {
    return pitdCur - pitdBase;
    }

// utility function for calculating the count of imports given the base
// of the IAT. NB: this only works on a valid IAT!
__inline unsigned
CountOfImports(PCImgThunkData pitdBase) {
    unsigned        cRet = 0;
    PCImgThunkData  pitd = pitdBase;
    while (pitd->u1.Function) {
        pitd++;
        cRet++;
        }
    return cRet;
    }
```

## <a name="see-also"></a>Voir aussi

[Présentation de la fonction d’assistance](understanding-the-helper-function.md)