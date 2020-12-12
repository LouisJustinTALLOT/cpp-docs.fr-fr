---
description: 'En savoir plus sur : __ll_rshift'
title: __ll_rshift
ms.date: 09/02/2019
f1_keywords:
- __ll_rshift_cpp
- __ll_rshift
helpviewer_keywords:
- __ll_rshift intrinsic
- ll_rshift intrinsic
ms.assetid: ef13b732-d122-44a0-add9-f5544a2c4ab2
ms.openlocfilehash: 567228431104bdde34cc0a5c5f41f0217515a337
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97167745"
---
# <a name="__ll_rshift"></a>__ll_rshift

**Spécifique à Microsoft**

Décale une valeur 64 bits spécifiée par le premier paramètre à droite, par un nombre de bits spécifié par le deuxième paramètre.

## <a name="syntax"></a>Syntaxe

```C
__int64 __ll_rshift(
   __int64 Mask,
   int nBit
);
```

### <a name="parameters"></a>Paramètres

*Filtrage*\
dans Valeur entière 64 bits à décaler vers la droite.

*nBit*\
dans Nombre de bits à décaler, Modulo 64 sur x64 et Modulo 32 sur x86.

## <a name="return-value"></a>Valeur retournée

Masque décalé par `nBit` bits.

## <a name="requirements"></a>Spécifications

|Intrinsic|Architecture|
|---------------|------------------|
|`__ll_rshift`|x86, x64|

**Fichier d’en-tête** \<intrin.h>

## <a name="remarks"></a>Notes

Si le deuxième paramètre est supérieur à 64 sur x64 (32 sur x86), ce nombre est réalisé en modulo 64 (32 sur x86) pour déterminer le nombre de bits à décaler. Le `ll` préfixe indique qu’il s’agit d’une opération sur **`long long`** , un autre nom pour **`__int64`** , le type intégral signé 64 bits.

## <a name="example"></a>Exemple

```cpp
// ll_rshift.cpp
// compile with: /EHsc
// processor: x86, x64
#include <iostream>
#include <intrin.h>
using namespace std;

#pragma intrinsic(__ll_rshift)

int main()
{
   __int64 Mask = - 0x100;
   int nBit = 4;
   cout << hex << Mask << endl;
   cout << " - " << (- Mask) << endl;
   Mask = __ll_rshift(Mask, nBit);
   cout << hex << Mask << endl;
   cout << " - " << (- Mask) << endl;
}
```

## <a name="output"></a>Output

```Output
ffffffffffffff00
- 100
fffffffffffffff0
- 10
```

> [!NOTE]
> Si `_ull_rshift` a été utilisé, le MSB de la valeur décalée vers la droite aurait été zéro, donc le résultat souhaité n’aurait pas été obtenu dans le cas d’une valeur négative.

**FIN spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Intrinsèques du compilateur](../intrinsics/compiler-intrinsics.md)\
[__ll_lshift](../intrinsics/ll-lshift.md)\
[__ull_rshift](../intrinsics/ull-rshift.md)
