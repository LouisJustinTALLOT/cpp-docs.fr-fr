---
title: __ll_lshift
ms.date: 09/02/2019
f1_keywords:
- __ll_lshift_cpp
- __ll_lshift
helpviewer_keywords:
- ll_lshift intrinsic
- __ll_lshift intrinsic
ms.assetid: fe98f733-426d-44b3-8f24-5d0d6d44bd94
ms.openlocfilehash: 988284b81c9f04ee5d7f09f8a2f173a689f9fb55
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87230517"
---
# <a name="__ll_lshift"></a>__ll_lshift

**Spécifique à Microsoft**

Déplace la valeur 64 bits fournie à gauche du nombre de bits spécifié.

## <a name="syntax"></a>Syntaxe

```C
unsigned __int64 __ll_lshift(
   unsigned __int64 Mask,
   int nBit
);
```

### <a name="parameters"></a>Paramètres

*Filtrage*\
dans Valeur entière de 64 bits à décaler vers la gauche.

*nBit*\
dans Nombre de bits à décaler.

## <a name="return-value"></a>Valeur retournée

Masque déplacé vers la gauche par `nBit` bits.

## <a name="requirements"></a>Spécifications

|Intrinsic|Architecture|
|---------------|------------------|
|`__ll_lshift`|x86, x64|

**Fichier d’en-tête** \<intrin.h>

## <a name="remarks"></a>Notes

Si vous compilez votre programme pour l’architecture 64 bits et `nBit` que est supérieur à 63, le nombre de bits à décaler est `nBit` modulo 64. Si vous compilez votre programme pour l’architecture 32 bits et `nBit` que est supérieur à 31, le nombre de bits à décaler est `nBit` modulo 32.

Le `ll` dans le nom indique qu’il s’agit d’une opération sur **`long long`** ( **`__int64`** ).

## <a name="example"></a>Exemple

```cpp
// ll_lshift.cpp
// compile with: /EHsc
// processor: x86, x64
#include <iostream>
#include <intrin.h>
using namespace std;

#pragma intrinsic(__ll_lshift)

int main()
{
   unsigned __int64 Mask = 0x100;
   int nBit = 8;
   Mask = __ll_lshift(Mask, nBit);
   cout << hex << Mask << endl;
}
```

## <a name="output"></a>Output

```Output
10000
```

> [!NOTE]
> Il n’existe aucune version non signée de l’opération de décalage vers la gauche. Cela est dû au fait que `__ll_lshift` utilise déjà un paramètre d’entrée non signé. Contrairement au décalage vers la droite, il n’existe aucune dépendance de signe pour le décalage vers la gauche, car le bit le moins significatif dans le résultat est toujours défini sur zéro, quel que soit le signe de la valeur décalée.

**FIN spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[__ll_rshift](../intrinsics/ll-rshift.md)\
[__ull_rshift](../intrinsics/ull-rshift.md)\
[Intrinsèques du compilateur](../intrinsics/compiler-intrinsics.md)
