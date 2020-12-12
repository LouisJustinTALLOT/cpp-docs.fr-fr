---
description: 'En savoir plus sur : calcul des valeurs nécessaires'
title: Calcul des valeurs nécessaires
ms.date: 11/04/2016
helpviewer_keywords:
- helper functions, calculating necessary values
ms.assetid: 4f037d0f-881a-4a48-a9d2-9f8872dfccb7
ms.openlocfilehash: 92d8462be2db55dbc10375629b133d9286560878
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97179341"
---
# <a name="calculating-necessary-values"></a>Calcul des valeurs nécessaires

Deux informations importantes doivent être calculées par la routine d’assistance Delay. À cette fin, il existe deux fonctions inline dans delayhlp. cpp pour le calcul de ces informations.

- La première calcule l’index de l’importation actuelle dans les trois tables différentes (table d’adresses d’importation (IAT), table d’adresses d’importation (BIAT) et table d’adresses d’importation (UIAT) indépendante).

- La seconde compte le nombre d’importations dans une IAT valide.

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

[Fonctionnement de la fonction d’assistance](understanding-the-helper-function.md)
