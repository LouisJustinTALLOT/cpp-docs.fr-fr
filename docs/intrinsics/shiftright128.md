---
description: 'En savoir plus sur : __shiftright128'
title: __shiftright128
ms.date: 09/02/2019
f1_keywords:
- __shiftright128
helpviewer_keywords:
- __shiftright128 intrinsic
ms.assetid: 5419a6c4-0de1-43fb-b314-4faa5b2d051f
ms.openlocfilehash: 71f8a0d9b740ebfef5e930715e07d1ec31950269
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97306974"
---
# <a name="__shiftright128"></a>__shiftright128

**Spécifique à Microsoft**

Décale une quantité de 128 bits, représentée par deux quantités de 64 bits `LowPart` et `HighPart`, vers la droite d'un nombre de bits spécifié par `Shift` et retourne les 64 bits de poids faible du résultat.

## <a name="syntax"></a>Syntaxe

```C
unsigned __int64 __shiftright128(
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

64 bits de poids faible du résultat.

## <a name="requirements"></a>Spécifications

|Intrinsic|Architecture|
|---------------|------------------|
|`__shiftright128`|x64|

**Fichier d’en-tête** \<intrin.h>

## <a name="remarks"></a>Notes

La valeur `Shift` est toujours modulo 64 pour que, par exemple, si vous appelez `__shiftright128(0, 1, 64)`, la fonction décale les `0` bits de la partie supérieure vers la droite et renvoie une partie faible de `0` et non `1` comme on pourrait s'y attendre.

## <a name="example"></a>Exemple

Pour obtenir un exemple, consultez [__shiftleft128](../intrinsics/shiftleft128.md).

**FIN spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[__shiftleft128](../intrinsics/shiftleft128.md)\
[Intrinsèques du compilateur](../intrinsics/compiler-intrinsics.md)
