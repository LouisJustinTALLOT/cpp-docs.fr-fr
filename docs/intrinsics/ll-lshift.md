---
title: __ll_lshift
ms.date: 11/04/2016
f1_keywords:
- __ll_lshift_cpp
- __ll_lshift
helpviewer_keywords:
- ll_lshift intrinsic
- __ll_lshift intrinsic
ms.assetid: fe98f733-426d-44b3-8f24-5d0d6d44bd94
ms.openlocfilehash: 5a91ce5db46b19be570f8d48a584a2caeabcc163
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62263384"
---
# <a name="lllshift"></a>__ll_lshift

**Section spécifique à Microsoft**

Décale la valeur fournie de 64 bits vers la gauche du nombre spécifié de bits.

## <a name="syntax"></a>Syntaxe

```
unsigned __int64 __ll_lshift(
   unsigned __int64 Mask,
   int nBit
);
```

#### <a name="parameters"></a>Paramètres

*Masque*<br/>
[in] La valeur d’entier 64 bits à déplacer vers la gauche.

*nBit*<br/>
[in] Le nombre de bits de décalage.

## <a name="return-value"></a>Valeur de retour

Le masque décalée vers la gauche par `nBit` bits.

## <a name="requirements"></a>Configuration requise

|Intrinsèque|Architecture|
|---------------|------------------|
|`__ll_lshift`|x86, x64|

**Fichier d’en-tête** \<intrin.h >

## <a name="remarks"></a>Notes

Si vous compilez votre programme à l’aide de l’architecture 64 bits et `nBit` est supérieur à 63, le nombre de bits de décalage est `nBit` modulo 64. Si vous compilez votre programme à l’aide de l’architecture 32 bits et `nBit` est supérieur à 31, le nombre de bits de décalage est `nBit` modulo 32.

Le `ll` dans le nom indique que cette opération se fait sur `long long` (`__int64`).

## <a name="example"></a>Exemple

```
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

```
10000
```

**Remarque** il n’existe aucune version non signée de l’opération de décalage vers la gauche. Il s’agit, car `__ll_lshift` utilise déjà un paramètre d’entrée non signé. Contrairement au décalage vers la droite, il n’existe aucune dépendance vis-à-vis de l’authentification pour le décalage vers la gauche, car le bit le moins significatif dans le résultat est toujours défini sur zéro, quel que soit le signe de la valeur décalée vers la.

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[__ll_rshift](../intrinsics/ll-rshift.md)<br/>
[__ull_rshift](../intrinsics/ull-rshift.md)<br/>
[compilateur, fonctions intrinsèques](../intrinsics/compiler-intrinsics.md)