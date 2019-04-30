---
title: __shiftright128
ms.date: 11/04/2016
f1_keywords:
- __shiftright128
helpviewer_keywords:
- __shiftright128 intrinsic
ms.assetid: 5419a6c4-0de1-43fb-b314-4faa5b2d051f
ms.openlocfilehash: b721abc9be22709fdc221951e2012300d6b96762
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62390332"
---
# <a name="shiftright128"></a>__shiftright128

**Section spécifique à Microsoft**

Décale une quantité de 128 bits, représentée par deux quantités de 64 bits `LowPart` et `HighPart`, vers la droite d'un nombre de bits spécifié par `Shift` et retourne les 64 bits de poids faible du résultat.

## <a name="syntax"></a>Syntaxe

```
unsigned __int64 __shiftright128(
   unsigned __int64 LowPart,
   unsigned __int64 HighPart,
   unsigned char Shift
);
```

#### <a name="parameters"></a>Paramètres

*LowPart*<br/>
[in] 64 bits de poids faibles de la quantité de 128 bits à décaler.

*HighPart*<br/>
[in] 64 bits de poids fort de la quantité de 128 bits à décaler.

*Maj*<br/>
[in] Le nombre de bits de décalage.

## <a name="return-value"></a>Valeur de retour

64 bits de poids faible du résultat.

## <a name="requirements"></a>Configuration requise

|Intrinsèque|Architecture|
|---------------|------------------|
|`__shiftright128`|X64|

**Fichier d’en-tête** \<intrin.h >

## <a name="remarks"></a>Notes

La valeur `Shift` est toujours modulo 64 pour que, par exemple, si vous appelez `__shiftright128(0, 1, 64)`, la fonction décale les `0` bits de la partie supérieure vers la droite et renvoie une partie faible de `0` et non `1` comme on pourrait s'y attendre.

## <a name="example"></a>Exemple

Pour obtenir un exemple, consultez [__shiftleft128](../intrinsics/shiftleft128.md).

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[__shiftleft128](../intrinsics/shiftleft128.md)<br/>
[compilateur, fonctions intrinsèques](../intrinsics/compiler-intrinsics.md)