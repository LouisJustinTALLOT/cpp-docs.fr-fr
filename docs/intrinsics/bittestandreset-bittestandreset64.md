---
title: _bittestandreset, _bittestandreset64
ms.date: 11/04/2016
f1_keywords:
- _bittestandreset64_cpp
- _bittestandreset
- _bittestandreset_cpp
- _bittestandreset64
helpviewer_keywords:
- btr instruction
- _bittestandreset intrinsic
- _bittestandreset64 intrinsic
ms.assetid: 8dad63bb-a051-4cd7-a793-3357537dfeaf
ms.openlocfilehash: d8c4675e7efe9e1de8ce6f133d1c361481f1b544
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50557663"
---
# <a name="bittestandreset-bittestandreset64"></a>_bittestandreset, _bittestandreset64

**Section spécifique à Microsoft**

Générer l'instruction qui examine le bit `b` de l'adresse `a`, retourne sa valeur actuelle et réinitialise le bit à la valeur 0.

## <a name="syntax"></a>Syntaxe

```
unsigned char _bittestandreset(
   long *a,
   long b
);
unsigned char _bittestandreset64(
   __int64 *a,
   __int64 b
);
```

#### <a name="parameters"></a>Paramètres

*a*<br/>
[in, out] Pointeur vers la mémoire à examiner.

*b*<br/>
[in] La position de bit à tester.

## <a name="return-value"></a>Valeur de retour

Bit à la position spécifiée.

## <a name="requirements"></a>Configuration requise

|Intrinsèque|Architecture|
|---------------|------------------|
|`_bittestandreset`|x86, ARM, x64|
|`_bittestandreset64`|X64|

**Fichier d’en-tête** \<intrin.h >

## <a name="remarks"></a>Notes

Cette routine est disponible uniquement en tant qu'intrinsèque.

## <a name="example"></a>Exemple

```
// bittestandreset.cpp
// processor: x86, IPF, x64
#include <stdio.h>
#include <limits.h>
#include <intrin.h>

#pragma intrinsic(_bittestandreset)

// Check the sign bit and reset to 0 (taking the absolute value)
// Returns 0 if the number is positive or zero
// Returns 1 if the number is negative
unsigned char absolute_value(long* p)
{
   const int SIGN_BIT = 31;
   return _bittestandreset(p, SIGN_BIT);
}

int main()
{
    long i = -112;
    unsigned char result;

    // Check the sign bit and reset to 0 (taking the absolute value)

    result = absolute_value(&i);
    if (result == 1)
        printf_s("The number was negative.\n");
}
```

```Output
The number was negative.
```

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[compilateur, fonctions intrinsèques](../intrinsics/compiler-intrinsics.md)