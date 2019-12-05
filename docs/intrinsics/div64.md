---
title: _div64
ms.date: 09/02/2019
f1_keywords:
- _div64
helpviewer_keywords:
- _div64 intrinsic
ms.openlocfilehash: 59c5eae66f9e93cb88f9512e405376f2ef5f1ceb
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74858020"
---
# <a name="_div64"></a>_div64

L’intrinsèque `_div64` divise un entier 64 bits par un entier 32 bits. La valeur de retour contient le quotient et l’intrinsèque retourne le reste à l’aide d’un paramètre de pointeur. `_div64` est **spécifique à Microsoft**.

## <a name="syntax"></a>Syntaxe

```C
int _div64(
   __int64 dividend,
   int divisor,
   int* remainder
);
```

### <a name="parameters"></a>Parameters

*dividend* \
dans Entier 64 bits à diviser.

 \ *diviseur*
dans Entier 32 bits à diviser par.

*reste* \
à Bits d’entier 32 bits du reste.

## <a name="return-value"></a>Valeur de retour

32 bits du quotient.

## <a name="remarks"></a>Notes

Le `_div64` intrinsèque divise le *dividende* par *diviseur*. Elle stocke le reste dans l’entier 32 bits désigné par le *reste*, et retourne les 32 bits du quotient.

Le `_div64` intrinsèque est disponible à partir de Visual Studio 2019 RTM.

## <a name="requirements"></a>Configuration requise pour

|Intrinsèque|Architecture|Header|
|---------------|------------------|------------|
|`_div64`|x86, x64|\<immintrin.h>|

## <a name="see-also"></a>Voir aussi

[_udiv64](udiv64.md) \
[Intrinsèques du compilateur](compiler-intrinsics.md)
