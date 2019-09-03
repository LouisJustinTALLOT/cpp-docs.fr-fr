---
title: __ull_rshift
ms.date: 09/02/2019
f1_keywords:
- __ull_rshift
helpviewer_keywords:
- ull_rshift intrinsic
- __ull_rshift intrinsic
ms.assetid: b7ff5254-3540-4e6e-b57c-a6c4beb7dca2
ms.openlocfilehash: e914a019877482058c6b2842d3138cda02f1e228
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/03/2019
ms.locfileid: "70219704"
---
# <a name="__ull_rshift"></a>__ull_rshift

**Section spécifique à Microsoft**

sur x64, décale une valeur 64 bits spécifiée par le premier paramètre à droite d’un nombre de bits spécifié par le deuxième paramètre.

## <a name="syntax"></a>Syntaxe

```C
unsigned __int64 __ull_rshift(
   unsigned __int64 mask, 
   int nBit
);
```

### <a name="parameters"></a>Paramètres

*filtrage*\
dans Valeur entière 64 bits à décaler vers la droite.

*nBit*\
dans Nombre de bits à décaler, Modulo 32 sur x86 et Modulo 64 sur x64.

## <a name="return-value"></a>Valeur de retour

Masque décalé par `nBit` bits.

## <a name="requirements"></a>Configuration requise

|Intrinsèque|Architecture|
|---------------|------------------|
|`__ull_rshift`|x86, x64|

**Fichier d’en-tête** \<> Intro. h

## <a name="remarks"></a>Notes

Si le deuxième paramètre est supérieur à 31 sur x86 (63 sur x64), ce nombre est réalisé en modulo 32 (64 sur x64) pour déterminer le nombre de bits à décaler. La `ull` dans le nom indique `unsigned long long (unsigned __int64)`.

## <a name="example"></a>Exemples

```cpp
// ull_rshift.cpp
// compile with: /EHsc
// processor: x86, x64
#include <iostream>
#include <intrin.h>
using namespace std;

#pragma intrinsic(__ull_rshift)

int main()
{
   unsigned __int64 mask = 0x100;
   int nBit = 8;
   mask = __ull_rshift(mask, nBit);
   cout << hex << mask << endl;
}
```

```Output
1
```

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[__ll_lshift](../intrinsics/ll-lshift.md)\
[__ll_rshift](../intrinsics/ll-rshift.md)\
[Intrinsèques du compilateur](../intrinsics/compiler-intrinsics.md)
