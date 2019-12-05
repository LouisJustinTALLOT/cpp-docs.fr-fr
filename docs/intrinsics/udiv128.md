---
title: _udiv128
ms.date: 04/17/2019
f1_keywords:
- _udiv128
helpviewer_keywords:
- _udiv128 intrinsic
ms.openlocfilehash: 5e8cc9ca3dbf19a04d07edb1d73df84f2e29a5c3
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857981"
---
# <a name="_udiv128"></a>_udiv128

L’intrinsèque `_udiv128` divise un entier non signé 128 bits par un entier non signé 64 bits. La valeur de retour contient le quotient et l’intrinsèque retourne le reste à l’aide d’un paramètre de pointeur. `_udiv128` est **spécifique à Microsoft**.

## <a name="syntax"></a>Syntaxe

```C
unsigned __int64 _udiv128(
   unsigned __int64 highDividend,
   unsigned __int64 lowDividend,
   unsigned __int64 divisor,
   unsigned __int64 *remainder
);
```

### <a name="parameters"></a>Parameters

*highDividend* \
dans 64 bits de poids fort du dividende.

*lowDividend* \
dans 64 bits de poids faible du dividende.

 \ *diviseur*
dans Entier 64 bits à diviser par.

*reste* \
à Bits d’entier 64 bits du reste.

## <a name="return-value"></a>Valeur de retour

64 bits du quotient.

## <a name="remarks"></a>Notes

Transmettez les 64 bits supérieurs du dividende 128 bits dans *highDividend*et les 64 bits inférieurs dans *lowDividend*. L’intrinsèque divise cette valeur par *diviseur*. Elle stocke le reste dans l’entier non signé 64 bits vers le *reste*, et retourne les 64 bits du quotient.

Le `_udiv128` intrinsèque est disponible à partir de Visual Studio 2019 RTM.

## <a name="requirements"></a>Configuration requise pour

|Intrinsèque|Architecture|Header|
|---------------|------------------|------------|
|`_udiv128`|x64|\<immintrin.h>|

## <a name="see-also"></a>Voir aussi

[_div128](div128.md) \
[Intrinsèques du compilateur](compiler-intrinsics.md)
