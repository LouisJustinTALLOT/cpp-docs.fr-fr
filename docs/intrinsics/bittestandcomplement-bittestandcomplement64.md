---
description: 'En savoir plus sur : _bittestandcomplement, _bittestandcomplement64'
title: _bittestandcomplement, _bittestandcomplement64
ms.date: 09/02/2019
f1_keywords:
- _bittestandcomplement64
- _bittestandcomplement64_cpp
- _bittestandcomplement_cpp
- _bittestandcomplement
helpviewer_keywords:
- btc instruction
- _bittestandcomplement intrinsic
- _bittestandcomplement64 intrinsic
ms.assetid: 53fa12dd-835e-4e5d-baec-a431c8678806
ms.openlocfilehash: 8a701b2a38dcfa2e6efe3044b63a78533a7a6efa
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97337187"
---
# <a name="_bittestandcomplement-_bittestandcomplement64"></a>_bittestandcomplement, _bittestandcomplement64

**Spécifique à Microsoft**

Générer une instruction qui examine le bit `b` de l'adresse `a`, retourne sa valeur actuelle et définit le bit sur son complément.

## <a name="syntax"></a>Syntaxe

```C
unsigned char _bittestandcomplement(
   long *a,
   long b
);
unsigned char _bittestandcomplement64(
   __int64 *a,
   __int64 b
);
```

### <a name="parameters"></a>Paramètres

*un*\
[in, out] Pointeur vers la mémoire à examiner.

*p*\
dans Position de bit à tester.

## <a name="return-value"></a>Valeur retournée

Bit à la position spécifiée.

## <a name="requirements"></a>Spécifications

|Intrinsic|Architecture|
|---------------|------------------|
|`_bittestandcomplement`|x86, ARM, x64, ARM64|
|`_bittestandcomplement64`|x64, ARM64|

**Fichier d’en-tête** \<intrin.h>

## <a name="remarks"></a>Notes

Cette routine est disponible uniquement en tant qu'intrinsèque.

## <a name="example"></a>Exemple

```cpp
// bittestandcomplement.cpp
// processor: x86, IPF, x64
#include <stdio.h>
#include <intrin.h>

#pragma intrinsic(_bittestandcomplement)
#ifdef _M_AMD64
#pragma intrinsic(_bittestandcomplement64)
#endif

int main()
{
   long i = 1;
   __int64 i64 = 0x1I64;
   unsigned char result;
   printf("Initial value: %d\n", i);
   printf("Testing bit 1\n");
   result = _bittestandcomplement(&i, 1);
   printf("Value changed to %d, Result: %d\n", i, result);
#ifdef _M_AMD64
   printf("Testing bit 0\n");
   result = _bittestandcomplement64(&i64, 0);
   printf("Value changed to %I64d, Result: %d\n", i64, result);
#endif
}
```

```Output
Initial value: 1
Testing bit 1
Value changed to 3, Result: 0
Testing bit 0
Value changed to 0, Result: 1
```

**FIN spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Intrinsèques du compilateur](../intrinsics/compiler-intrinsics.md)
