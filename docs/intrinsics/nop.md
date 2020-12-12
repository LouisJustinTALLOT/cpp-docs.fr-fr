---
description: 'En savoir plus sur : __nop'
title: __nop
ms.date: 09/02/2019
f1_keywords:
- __nop
helpviewer_keywords:
- nop instruction
- __nop intrinsic
ms.assetid: 7a2a938b-87e0-476d-a348-03ea7635b6b9
ms.openlocfilehash: 55759e8324511b6ddaa2774bdfdc3554c0032c2e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97118925"
---
# <a name="__nop"></a>__nop

**Spécifique à Microsoft**

Génère du code machine spécifique à la plateforme qui n’effectue aucune opération.

## <a name="syntax"></a>Syntaxe

```C
void __nop();
```

## <a name="requirements"></a>Spécifications

|Intrinsic|Architecture|
|---------------|------------------|
|`__nop`|x86, ARM, x64, ARM64|

**Fichier d’en-tête** \<intrin.h>

**FIN spécifique à Microsoft**

## <a name="remarks"></a>Notes

La fonction `__nop` est équivalente à l’instruction machine `NOP` . Pour plus d’informations sur x86 et x64, recherchez le document « Guide du développeur de logiciels d’architecture Intel, volume 2 : référence de jeu d’instructions » sur le site [Intel Corporation](https://software.intel.com/articles/intel-sdm) .

## <a name="see-also"></a>Voir aussi

[Intrinsèques du compilateur](../intrinsics/compiler-intrinsics.md)\
[__noop](../intrinsics/noop.md)
