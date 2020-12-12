---
description: 'En savoir plus sur : __shiftleft128'
title: __shiftleft128
ms.date: 09/02/2019
f1_keywords:
- __shiftleft128
helpviewer_keywords:
- __shiftleft128 intrinsic
ms.assetid: 557b846a-8fb0-469d-91ac-1b1fad80dc2a
ms.openlocfilehash: e0e1402660c2ddb6f5993e5186302ff489ed864f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97306987"
---
# <a name="__shiftleft128"></a>__shiftleft128

**Spécifique à Microsoft**

Décale une quantité de 128 bits, représentée par deux quantités de 64 bits `LowPart` et `HighPart`, vers la gauche d'un nombre de bits spécifié par `Shift` et retourne les 64 bits de poids fort du résultat.

## <a name="syntax"></a>Syntaxe

```C
unsigned __int64 __shiftleft128(
   unsigned __int64 LowPart,
   unsigned __int64 HighPart,
   unsigned char Shift
);
```

### <a name="parameters"></a>Paramètres

*LowPart*\
dans 64 bits de poids faible de la quantité 128 bits à décaler.

*HighPart*\
dans 64 bits de poids fort de la quantité 128 bits à décaler.

*Majuscule*\
dans Nombre de bits à décaler.

## <a name="return-value"></a>Valeur retournée

64 bits de poids fort du résultat.

## <a name="requirements"></a>Spécifications

|Intrinsic|Architecture|
|---------------|------------------|
|`__shiftleft128`|x64|

**Fichier d’en-tête** \<intrin.h>

## <a name="remarks"></a>Notes

La valeur de *décalage* est toujours modulo 64 afin que, par exemple, si vous appelez `__shiftleft128(1, 0, 64)` , la fonction décale les bits de la partie inférieure vers la `0` gauche et retourne une partie haute de `0` et non `1` comme cela peut être prévu.

## <a name="example"></a>Exemple

```C
// shiftleft128.c
// processor: IPF, x64
#include <stdio.h>
#include <intrin.h>

#pragma intrinsic (__shiftleft128, __shiftright128)

int main()
{
    unsigned __int64 i = 0x1I64;
    unsigned __int64 j = 0x10I64;
    unsigned __int64 ResultLowPart;
    unsigned __int64 ResultHighPart;

    ResultLowPart = i << 1;
    ResultHighPart = __shiftleft128(i, j, 1);

    // concatenate the low and high parts padded with 0's
    // to display correct hexadecimal 128 bit values
    printf_s("0x%02I64x%016I64x << 1 = 0x%02I64x%016I64x\n",
             j, i, ResultHighPart, ResultLowPart);

    ResultHighPart = j >> 1;
    ResultLowPart = __shiftright128(i, j, 1);

    printf_s("0x%02I64x%016I64x >> 1 = 0x%02I64x%016I64x\n",
             j, i, ResultHighPart, ResultLowPart);
}
```

```Output
0x100000000000000001 << 1 = 0x200000000000000002
0x100000000000000001 >> 1 = 0x080000000000000000
```

**FIN spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[__shiftright128](../intrinsics/shiftright128.md)\
[Intrinsèques du compilateur](../intrinsics/compiler-intrinsics.md)
