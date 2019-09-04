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
ms.openlocfilehash: 158ecbf39320d70b51f1f498a0b689ba58fec363
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/03/2019
ms.locfileid: "70221810"
---
# <a name="__ll_lshift"></a>__ll_lshift

**Section spécifique à Microsoft**

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

## <a name="return-value"></a>Valeur de retour

Masque déplacé vers la gauche par `nBit` bits.

## <a name="requirements"></a>Configuration requise

|Intrinsèque|Architecture|
|---------------|------------------|
|`__ll_lshift`|x86, x64|

**Fichier d’en-tête** \<> Intro. h

## <a name="remarks"></a>Notes

Si vous compilez votre programme pour l’architecture 64 bits et `nBit` que est supérieur à 63, le nombre de bits à décaler est `nBit` modulo 64. Si vous compilez votre programme pour l’architecture 32 bits et `nBit` que est supérieur à 31, le nombre de bits à décaler est `nBit` modulo 32.

Le `ll` dans le nom indique qu’il s’agit d’une `long long` opération`__int64`sur ().

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

## <a name="output"></a>Sortie

```Output
10000
```

> [!NOTE]
> Il n’existe aucune version non signée de l’opération de décalage vers la gauche. Cela est dû `__ll_lshift` au fait que utilise déjà un paramètre d’entrée non signé. Contrairement au décalage vers la droite, il n’existe aucune dépendance de signe pour le décalage vers la gauche, car le bit le moins significatif dans le résultat est toujours défini sur zéro, quel que soit le signe de la valeur décalée.

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[__ll_rshift](../intrinsics/ll-rshift.md)\
[__ull_rshift](../intrinsics/ull-rshift.md)\
[Intrinsèques du compilateur](../intrinsics/compiler-intrinsics.md)
