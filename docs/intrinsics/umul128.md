---
title: _umul128
ms.date: 09/02/2019
f1_keywords:
- __umul128
helpviewer_keywords:
- __umul128 intrinsic
ms.assetid: 13684df3-3ac7-467c-b258-a0e93bc490b5
ms.openlocfilehash: 205f0f7f9046ede624bb09e18d8ede32fadbc3de
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/03/2019
ms.locfileid: "70219692"
---
# <a name="_umul128"></a>_umul128

**Section spécifique à Microsoft**

Multiplie deux entiers non signés 64 bits passés comme les deux premiers arguments, place les 64 bits de poids fort du produit dans l’entier non signé 64 bits vers lequel pointe `HighProduct` et retourne les 64 bits de poids faible du produit.

## <a name="syntax"></a>Syntaxe

```C
unsigned __int64 _umul128(
   unsigned __int64 Multiplier,
   unsigned __int64 Multiplicand,
   unsigned __int64 *HighProduct
);
```

### <a name="parameters"></a>Paramètres

*Multiple*\
dans Premier entier 64 bits à multiplier.

*Multiplicande*\
dans Deuxième entier 64 bits à multiplier.

*HighProduct*\
à 64 bits de poids fort du produit.

## <a name="return-value"></a>Valeur de retour

64 bits de poids faible du produit.

## <a name="requirements"></a>Configuration requise

|Intrinsèque|Architecture|Header|
|---------------|------------------|------------|
|`_umul128`|X64|\<intrin.h>|

## <a name="example"></a>Exemple

```C
// umul128.c
// processor: x64

#include <stdio.h>
#include <intrin.h>

#pragma intrinsic(_umul128)

int main()
{
    unsigned __int64 a = 0x0fffffffffffffffI64;
    unsigned __int64 b = 0xf0000000I64;
    unsigned __int64 c, d;

    d = _umul128(a, b, &c);

    printf_s("%#I64x * %#I64x = %#I64x%I64x\n", a, b, c, d);
}
```

```Output
0xfffffffffffffff * 0xf0000000 = 0xeffffffffffffff10000000
```

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Intrinsèques du compilateur](../intrinsics/compiler-intrinsics.md)
