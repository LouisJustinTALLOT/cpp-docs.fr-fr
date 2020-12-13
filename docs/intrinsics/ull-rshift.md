---
description: 'En savoir plus sur : __ull_rshift'
title: __ull_rshift
ms.date: 09/02/2019
f1_keywords:
- __ull_rshift
helpviewer_keywords:
- ull_rshift intrinsic
- __ull_rshift intrinsic
ms.assetid: b7ff5254-3540-4e6e-b57c-a6c4beb7dca2
ms.openlocfilehash: 5b819e4a1df8db7b7562023c6acc9dbbd94f7f76
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97333628"
---
# <a name="__ull_rshift"></a>__ull_rshift

**Spécifique à Microsoft**

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

## <a name="return-value"></a>Valeur retournée

Masque décalé par `nBit` bits.

## <a name="requirements"></a>Spécifications

|Intrinsic|Architecture|
|---------------|------------------|
|`__ull_rshift`|x86, x64|

**Fichier d’en-tête** \<intrin.h>

## <a name="remarks"></a>Notes

Si le deuxième paramètre est supérieur à 31 sur x86 (63 sur x64), ce nombre est réalisé en modulo 32 (64 sur x64) pour déterminer le nombre de bits à décaler. La `ull` dans le nom indique `unsigned long long (unsigned __int64)` .

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

**FIN spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[__ll_lshift](../intrinsics/ll-lshift.md)\
[__ll_rshift](../intrinsics/ll-rshift.md)\
[Intrinsèques du compilateur](../intrinsics/compiler-intrinsics.md)
