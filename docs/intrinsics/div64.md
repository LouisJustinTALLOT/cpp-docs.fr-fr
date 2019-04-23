---
title: _div64
ms.date: 04/17/2019
f1_keywords:
- _div64
helpviewer_keywords:
- _div64 intrinsic
ms.openlocfilehash: a221cc7cf0655a41873c6777aecd8a9b27131b74
ms.sourcegitcommit: 2ce88de75e7681220ae09a0ab13056f22f357a46
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2019
ms.locfileid: "59982418"
---
# <a name="div64"></a>_div64

Le `_div64` intrinsèque divise un entier 64 bits par un entier 32 bits. La valeur de retour conserve le quotient, et la fonction intrinsèque retourne le reste à un paramètre de pointeur. `_div64` est **spécifique à Microsoft**.

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
[in] Entier 64 bits à diviser.

*divisor* \
[in] Entier 32 bits à diviser par.

*remainder* \
[out] Les bits d’entier 32 bits du reste.

## <a name="return-value"></a>Valeur de retour

Les 32 bits du quotient.

## <a name="remarks"></a>Notes

Le `_div64` divise intrinsèque *dividende* par *diviseur*. Il stocke le reste de l’entier 32 bits vers lequel pointé *reste*et retourne les 32 bits du quotient.

Le `_div64` intrinsèque est disponible à partir de Visual Studio 2019 RTM.

## <a name="requirements"></a>Configuration requise

|Intrinsèque|Architecture|Header|
|---------------|------------------|------------|
|`_div64`|x86, x64|\<immintrin.h>|

## <a name="see-also"></a>Voir aussi

[_udiv64](udiv64.md) \
[Intrinsèques du compilateur](compiler-intrinsics.md)
