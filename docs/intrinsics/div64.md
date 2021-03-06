---
description: 'En savoir plus sur : _div64'
title: _div64
ms.date: 09/02/2019
f1_keywords:
- _div64
helpviewer_keywords:
- _div64 intrinsic
ms.openlocfilehash: 4c9c8f02f7092c12d5734f96346897e2eca9898a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97337069"
---
# <a name="_div64"></a>_div64

L' `_div64` intrinsèque divise un entier 64 bits par un entier 32 bits. La valeur de retour contient le quotient et l’intrinsèque retourne le reste à l’aide d’un paramètre de pointeur. `_div64` est **spécifique à Microsoft**.

## <a name="syntax"></a>Syntaxe

```C
int _div64(
   __int64 dividend,
   int divisor,
   int* remainder
);
```

### <a name="parameters"></a>Paramètres

*dividend* \
dans Entier 64 bits à diviser.

*divisor* \
dans Entier 32 bits à diviser par.

*sections* \
à Bits d’entier 32 bits du reste.

## <a name="return-value"></a>Valeur retournée

32 bits du quotient.

## <a name="remarks"></a>Notes

L' `_div64` intrinsèque divise le *dividende* par *diviseur*. Elle stocke le reste dans l’entier 32 bits désigné par le *reste*, et retourne les 32 bits du quotient.

Le `_div64` intrinsèque est disponible à partir de Visual Studio 2019 RTM.

## <a name="requirements"></a>Spécifications

|Intrinsic|Architecture|En-tête|
|---------------|------------------|------------|
|`_div64`|x86, x64|\<immintrin.h>|

## <a name="see-also"></a>Voir aussi

[_udiv64](udiv64.md) \
[Intrinsèques du compilateur](compiler-intrinsics.md)
