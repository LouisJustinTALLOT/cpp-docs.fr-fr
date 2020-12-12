---
description: 'En savoir plus sur : __mulh'
title: __mulh
ms.date: 09/02/2019
f1_keywords:
- __mulh
helpviewer_keywords:
- __mulh intrinsic
ms.assetid: cd2ab093-9ef6-404d-ac34-0bee033882f3
ms.openlocfilehash: 0cee31b6a9e1088d76200cd46482fd4aaf80474b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97118938"
---
# <a name="__mulh"></a>__mulh

**Spécifique à Microsoft**

Retourne les 64 bits de poids fort du produit des entiers 2 64 bits signés.

## <a name="syntax"></a>Syntaxe

```C
__int64 __mulh(
   __int64 a,
   __int64 b
);
```

### <a name="parameters"></a>Paramètres

*un*\
[in] Premier nombre à multiplier.

*p*\
[in] Second nombre à multiplier.

## <a name="return-value"></a>Valeur retournée

64 bits de poids fort du résultat 128 bits de la multiplication.

## <a name="requirements"></a>Spécifications

|Intrinsic|Architecture|
|---------------|------------------|
|`__mulh`|x64|

**Fichier d’en-tête** \<intrin.h>

## <a name="remarks"></a>Notes

Cette routine est disponible uniquement en tant qu'intrinsèque.

## <a name="example"></a>Exemple

```cpp
// mulh.cpp
// processor: x64
#include <stdio.h>
#include <intrin.h>

#pragma intrinsic (__mulh)

int main()
{
    __int64 a = 0x0fffffffffffffffI64;
    __int64 b = 0xf0000000I64;

    __int64 result = __mulh(a, b); // the high 64 bits
    __int64 result2 = a * b; // the low 64 bits

    printf_s(" %#I64x * %#I64x = %#I64x%I64x\n",
             a, b, result, result2);
}
```

```Output
0xfffffffffffffff * 0xf0000000 = 0xeffffffffffffff10000000
```

**FIN spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Intrinsèques du compilateur](../intrinsics/compiler-intrinsics.md)
