---
title: __umulh
ms.date: 11/04/2016
f1_keywords:
- __umulh
helpviewer_keywords:
- __umulh intrinsic
ms.assetid: d241b53a-e6f7-4af1-9f6e-84e149158f03
ms.openlocfilehash: b116de7cd91d26463858fb03e5f319e2a2da1cde
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50524798"
---
# <a name="umulh"></a>__umulh

**Section spécifique à Microsoft**

Retourner les 64 bits de poids fort du produit de deux entiers non signés 64 bits.

## <a name="syntax"></a>Syntaxe

```
unsigned __int64 __umulh( 
   unsigned __int64 a, 
   unsigned __int64 b 
);
```

#### <a name="parameters"></a>Paramètres

*a*<br/>
[in] Le premier nombre à multiplier.

*b*<br/>
[in] Le second nombre à multiplier.

## <a name="return-value"></a>Valeur de retour

64 bits de poids fort du résultat 128 bits de la multiplication.

## <a name="requirements"></a>Configuration requise

|Intrinsèque|Architecture|
|---------------|------------------|
|`__umulh`|X64|

**Fichier d’en-tête** \<intrin.h >

## <a name="remarks"></a>Notes

Ces routines sont disponibles seulement comme fonctions intrinsèques.

## <a name="example"></a>Exemple

```
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

[compilateur, fonctions intrinsèques](../intrinsics/compiler-intrinsics.md)