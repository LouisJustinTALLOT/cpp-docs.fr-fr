---
title: __nop
ms.date: 11/04/2016
f1_keywords:
- __nop
helpviewer_keywords:
- nop instruction
- __nop intrinsic
ms.assetid: 7a2a938b-87e0-476d-a348-03ea7635b6b9
ms.openlocfilehash: 1e76110c1ef0c4b98c295578189eedc99d76eeb9
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/05/2019
ms.locfileid: "59038241"
---
# <a name="nop"></a>__nop

**Section spécifique à Microsoft**

Génère du code machine spécifique à la plateforme qui n’effectue aucune opération.

## <a name="syntax"></a>Syntaxe

```
void __nop();
```

## <a name="requirements"></a>Configuration requise

|Intrinsèque|Architecture|
|---------------|------------------|
|`__nop`|x86, ARM, x64, ARM64|

**Fichier d’en-tête** \<intrin.h >

**FIN de la section spécifique à Microsoft**

## <a name="remarks"></a>Notes

La fonction `__nop` est équivalente à l’instruction machine `NOP` . Pour plus d’informations sur x86 et x64, recherchez le document, « manuel du développeur de logiciels Architecture Intel, Volume 2 : Instruction Set Reference, » à la [Intel Corporation](https://software.intel.com/articles/intel-sdm) site.

## <a name="see-also"></a>Voir aussi

[compilateur, intrinsèques](../intrinsics/compiler-intrinsics.md)<br/>
[__noop](../intrinsics/noop.md)
