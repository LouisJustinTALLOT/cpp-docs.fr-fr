---
title: __shiftright128
ms.date: 09/02/2019
f1_keywords:
- __shiftright128
helpviewer_keywords:
- __shiftright128 intrinsic
ms.assetid: 5419a6c4-0de1-43fb-b314-4faa5b2d051f
ms.openlocfilehash: a18a9958a51f291e4997c23e87ee48f739562416
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/03/2019
ms.locfileid: "70220017"
---
# <a name="__shiftright128"></a>__shiftright128

**Section spécifique à Microsoft**

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

## <a name="return-value"></a>Valeur de retour

64 bits de poids faible du résultat.

## <a name="requirements"></a>Configuration requise

|Intrinsèque|Architecture|
|---------------|------------------|
|`__shiftright128`|X64|

**Fichier d’en-tête** \<> Intro. h

## <a name="remarks"></a>Notes

La valeur `Shift` est toujours modulo 64 pour que, par exemple, si vous appelez `__shiftright128(0, 1, 64)`, la fonction décale les `0` bits de la partie supérieure vers la droite et renvoie une partie faible de `0` et non `1` comme on pourrait s'y attendre.

## <a name="example"></a>Exemple

Pour obtenir un exemple, consultez [shiftleft128](../intrinsics/shiftleft128.md).

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[__shiftleft128](../intrinsics/shiftleft128.md)\
[Intrinsèques du compilateur](../intrinsics/compiler-intrinsics.md)
