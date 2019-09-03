---
title: _udiv64
ms.date: 09/02/2019
f1_keywords:
- _udiv64
helpviewer_keywords:
- _udiv64 intrinsic
ms.openlocfilehash: 6dabbc94260ef578eb1a58a1b289b4a4654decdd
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/03/2019
ms.locfileid: "70219681"
---
# <a name="_udiv64"></a>_udiv64

L' `_udiv64` intrinsèque divise un entier non signé 64 bits par un entier non signé 32 bits. La valeur de retour contient le quotient et l’intrinsèque retourne le reste à l’aide d’un paramètre de pointeur. `_udiv64`est **spécifique à Microsoft**.

## <a name="syntax"></a>Syntaxe

```C
unsigned int _udiv64(
   unsigned __int64 dividend,
   unsigned int divisor,
   unsigned int* remainder
);
```

### <a name="parameters"></a>Paramètres

*dividend*\
dans Entier non signé 64 bits à diviser.

*Division*\
dans Entier non signé 32 bits à diviser par.

*sections*\
à Reste de l’entier non signé 32 bits.

## <a name="return-value"></a>Valeur de retour

32 bits du quotient.

## <a name="remarks"></a>Notes

L' `_udiv64` intrinsèque divise le dividendepar diviseur. Elle stocke le reste dans l’entier non signé 32 bits vers le *reste*, et retourne les 32 bits du quotient.

Le `_udiv64` intrinsèque est disponible à partir de Visual Studio 2019 RTM.

## <a name="requirements"></a>Configuration requise

|Intrinsèque|Architecture|Header|
|---------------|------------------|------------|
|`_udiv64`|x86, x64|\<immintrin.h>|

## <a name="see-also"></a>Voir aussi

[_div64](div64.md) \
[Intrinsèques du compilateur](compiler-intrinsics.md)
