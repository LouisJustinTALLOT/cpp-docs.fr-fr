---
title: _udiv64
ms.date: 04/17/2019
f1_keywords:
- _udiv64
helpviewer_keywords:
- _udiv64 intrinsic
ms.openlocfilehash: 73a29b180eeda49a9a25e9e568d25c7563234fad
ms.sourcegitcommit: 2ce88de75e7681220ae09a0ab13056f22f357a46
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2019
ms.locfileid: "59982448"
---
# <a name="udiv64"></a>_udiv64

Le `_udiv64` intrinsèque divise un entier non signé 64 bits en un entier non signé 32 bits. La valeur de retour conserve le quotient, et la fonction intrinsèque retourne le reste à un paramètre de pointeur. `_udiv64` est **spécifique à Microsoft**.

## <a name="syntax"></a>Syntaxe

```C
unsigned int _udiv64(
   unsigned __int64 dividend,
   unsigned int divisor,
   unsigned int* remainder
);
```

### <a name="parameters"></a>Paramètres

*dividend*<br/>
[in] L’entier non signé 64 bits à diviser.

*divisor*<br/>
[in] L’entier non signé de 32 bits à diviser par.

*remainder*<br/>
[out] Le reste de l’entier non signé 32 bits.

## <a name="return-value"></a>Valeur de retour

Les 32 bits du quotient.

## <a name="remarks"></a>Notes

Le `_udiv64` divise intrinsèque *dividende* par *diviseur*. Il stocke le reste de l’entier non signé 32 bits vers lequel pointé *reste*et retourne les 32 bits du quotient.

Le `_udiv64` intrinsèque est disponible à partir de Visual Studio 2019 RTM.

## <a name="requirements"></a>Configuration requise

|Intrinsèque|Architecture|Header|
|---------------|------------------|------------|
|`_udiv64`|x86, x64|\<immintrin.h>|

## <a name="see-also"></a>Voir aussi

[_div64](div64.md) \
[Intrinsèques du compilateur](compiler-intrinsics.md)
