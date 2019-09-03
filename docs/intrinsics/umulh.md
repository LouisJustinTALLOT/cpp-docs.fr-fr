---
title: __umulh
ms.date: 09/02/2019
f1_keywords:
- __umulh
helpviewer_keywords:
- __umulh intrinsic
ms.assetid: d241b53a-e6f7-4af1-9f6e-84e149158f03
ms.openlocfilehash: bf098657d1bd5b7ef8a4ffc21f487d2ce619a04e
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/03/2019
ms.locfileid: "70219663"
---
# <a name="__umulh"></a>__umulh

**Section spécifique à Microsoft**

Retourner les 64 bits de poids fort du produit de deux entiers non signés 64 bits.

## <a name="syntax"></a>Syntaxe

```C
unsigned __int64 __umulh(
   unsigned __int64 a,
   unsigned __int64 b
);
```

### <a name="parameters"></a>Paramètres

*un*\
[in] Premier nombre à multiplier.

*p*\
[in] Second nombre à multiplier.

## <a name="return-value"></a>Valeur de retour

64 bits de poids fort du résultat 128 bits de la multiplication.

## <a name="requirements"></a>Configuration requise

|Intrinsèque|Architecture|
|---------------|------------------|
|`__umulh`|X64|

**Fichier d’en-tête** \<> Intro. h

## <a name="remarks"></a>Notes

Ces routines sont disponibles seulement comme fonctions intrinsèques.

## <a name="example"></a>Exemple

```cpp
// umulh.cpp
// processor: X64
#include <cstdio>
#include <intrin.h>

int main()
{
    unsigned __int64 i = 0x10;
    unsigned __int64 j = 0xFEDCBA9876543210;
    unsigned __int64 k = i * j; // k has the low 64 bits
                                // of the product.
    unsigned __int64 result;
    result = __umulh(i, j); // result has the high 64 bits
                            // of the product.
    printf_s("0x%I64x * 0x%I64x = 0x%I64x%I64x \n", i, j, result, k);
    return 0;
}
```

```Output
0x10 * 0xfedcba9876543210 = 0xfedcba98765432100
```

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Intrinsèques du compilateur](../intrinsics/compiler-intrinsics.md)
