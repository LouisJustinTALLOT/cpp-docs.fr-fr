---
description: 'En savoir plus sur : _udiv128'
title: _udiv128
ms.date: 04/17/2019
f1_keywords:
- _udiv128
helpviewer_keywords:
- _udiv128 intrinsic
ms.openlocfilehash: f88546a179106f4291fcaeb865f1aad9e67c4045
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97333654"
---
# <a name="_udiv128"></a>_udiv128

L' `_udiv128` intrinsèque divise un entier non signé 128 bits par un entier non signé 64 bits. La valeur de retour contient le quotient et l’intrinsèque retourne le reste à l’aide d’un paramètre de pointeur. `_udiv128` est **spécifique à Microsoft**.

## <a name="syntax"></a>Syntaxe

```C
unsigned __int64 _udiv128(
   unsigned __int64 highDividend,
   unsigned __int64 lowDividend,
   unsigned __int64 divisor,
   unsigned __int64 *remainder
);
```

### <a name="parameters"></a>Paramètres

*highDividend* \
dans 64 bits de poids fort du dividende.

*lowDividend* \
dans 64 bits de poids faible du dividende.

*divisor* \
dans Entier 64 bits à diviser par.

*sections* \
à Bits d’entier 64 bits du reste.

## <a name="return-value"></a>Valeur retournée

64 bits du quotient.

## <a name="remarks"></a>Notes

Transmettez les 64 bits supérieurs du dividende 128 bits dans *highDividend* et les 64 bits inférieurs dans *lowDividend*. L’intrinsèque divise cette valeur par *diviseur*. Elle stocke le reste dans l’entier non signé 64 bits vers le *reste*, et retourne les 64 bits du quotient.

Le `_udiv128` intrinsèque est disponible à partir de Visual Studio 2019 RTM.

## <a name="requirements"></a>Spécifications

|Intrinsic|Architecture|En-tête|
|---------------|------------------|------------|
|`_udiv128`|x64|\<immintrin.h>|

## <a name="see-also"></a>Voir aussi

[_div128](div128.md) \
[Intrinsèques du compilateur](compiler-intrinsics.md)
