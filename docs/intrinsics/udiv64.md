---
title: _udiv64
ms.date: 09/02/2019
f1_keywords:
- _udiv64
helpviewer_keywords:
- _udiv64 intrinsic
ms.openlocfilehash: ddb46f33b0fccc1cedc2a704265b096ba715b506
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857994"
---
# <a name="_udiv64"></a>_udiv64

L’intrinsèque `_udiv64` divise un entier non signé 64 bits par un entier non signé 32 bits. La valeur de retour contient le quotient et l’intrinsèque retourne le reste à l’aide d’un paramètre de pointeur. `_udiv64` est **spécifique à Microsoft**.

## <a name="syntax"></a>Syntaxe

```C
unsigned int _udiv64(
   unsigned __int64 dividend,
   unsigned int divisor,
   unsigned int* remainder
);
```

### <a name="parameters"></a>Parameters

*dividend*\
dans Entier non signé 64 bits à diviser.

\ *diviseur*
dans Entier non signé 32 bits à diviser par.

*reste*\
à Reste de l’entier non signé 32 bits.

## <a name="return-value"></a>Valeur de retour

32 bits du quotient.

## <a name="remarks"></a>Notes

Le `_udiv64` intrinsèque divise le *dividende* par *diviseur*. Elle stocke le reste dans l’entier non signé 32 bits vers le *reste*, et retourne les 32 bits du quotient.

Le `_udiv64` intrinsèque est disponible à partir de Visual Studio 2019 RTM.

## <a name="requirements"></a>Configuration requise pour

|Intrinsèque|Architecture|Header|
|---------------|------------------|------------|
|`_udiv64`|x86, x64|\<immintrin.h>|

## <a name="see-also"></a>Voir aussi

[_div64](div64.md) \
[Intrinsèques du compilateur](compiler-intrinsics.md)
