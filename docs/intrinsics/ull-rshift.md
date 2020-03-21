---
title: __ull_rshift
ms.date: 09/02/2019
f1_keywords:
- __ull_rshift
helpviewer_keywords:
- ull_rshift intrinsic
- __ull_rshift intrinsic
ms.assetid: b7ff5254-3540-4e6e-b57c-a6c4beb7dca2
ms.openlocfilehash: bf9fe7775cee1c774c097a1b6bd371721c9fa34f
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/21/2020
ms.locfileid: "80074989"
---
# <a name="__ull_rshift"></a>__ull_rshift

**Section spécifique de Microsoft**

sur x64, décale une valeur 64 bits spécifiée par le premier paramètre à droite d’un nombre de bits spécifié par le deuxième paramètre.

## <a name="syntax"></a>Syntaxe

```C
unsigned __int64 __ull_rshift(
   unsigned __int64 mask,
   int nBit
);
```

### <a name="parameters"></a>Paramètres

*masque*\
dans Valeur entière 64 bits à décaler vers la droite.

*nBit*\
dans Nombre de bits à décaler, Modulo 32 sur x86 et Modulo 64 sur x64.

## <a name="return-value"></a>Valeur retournée

Masque décalé par `nBit` bits.

## <a name="requirements"></a>Spécifications

|Intrinsic|Architecture|
|---------------|------------------|
|`__ull_rshift`|x86, x64|

**Fichier d’en-tête** \<Intro. h >

## <a name="remarks"></a>Notes

Si le deuxième paramètre est supérieur à 31 sur x86 (63 sur x64), ce nombre est réalisé en modulo 32 (64 sur x64) pour déterminer le nombre de bits à décaler. Le `ull` dans le nom indique `unsigned long long (unsigned __int64)`.

## <a name="example"></a>Exemple

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

**Fin de la section spécifique de Microsoft**

## <a name="see-also"></a>Voir aussi

[__ll_lshift](../intrinsics/ll-lshift.md)\
[__ll_rshift](../intrinsics/ll-rshift.md)\
[Intrinsèques du compilateur](../intrinsics/compiler-intrinsics.md)
