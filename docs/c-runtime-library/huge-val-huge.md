---
title: HUGE_VAL, _HUGE
ms.date: 11/04/2016
apiname:
- _HUGE
apilocation:
- msvcrt.dll
apitype: DLLExport
f1_keywords:
- _HUGE
- HUGE_VAL
helpviewer_keywords:
- _HUGE constant
- HUGE_VAL constant
- double value
ms.assetid: 3f044b45-02cd-46b2-b1de-87fd0441dd6a
ms.openlocfilehash: b1d9b099684d9671a60dd1afb1e6692e3c0d2a65
ms.sourcegitcommit: a1fad0a266b20b313364a74b16c9ac45d089b1e9
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/11/2019
ms.locfileid: "54220476"
---
# <a name="hugeval-huge"></a>HUGE_VAL, _HUGE

## <a name="syntax"></a>Syntaxe

```
#include <math.h>
```

## <a name="remarks"></a>Notes

`HUGE_VAL` est la plus grande valeur double représentable. Cette valeur est retournée par de nombreuses fonctions mathématiques d’exécution quand une erreur se produit. Pour certaines fonctions, -`HUGE_VAL` est retourné. `HUGE_VAL` est défini en tant que `_HUGE`, mais les fonctions mathématiques d’exécution retournent `HUGE_VAL`. Vous devez également utiliser `HUGE_VAL` dans votre code à des fins de cohérence.

## <a name="see-also"></a>Voir aussi

[Constantes globales](../c-runtime-library/global-constants.md)
