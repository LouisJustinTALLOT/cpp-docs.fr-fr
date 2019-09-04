---
title: __nop
ms.date: 09/02/2019
f1_keywords:
- __nop
helpviewer_keywords:
- nop instruction
- __nop intrinsic
ms.assetid: 7a2a938b-87e0-476d-a348-03ea7635b6b9
ms.openlocfilehash: 4561bcb84063f3707825c8ca164867d41500e2db
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/03/2019
ms.locfileid: "70221671"
---
# <a name="__nop"></a>__nop

**Section spécifique à Microsoft**

Génère du code machine spécifique à la plateforme qui n’effectue aucune opération.

## <a name="syntax"></a>Syntaxe

```C
void __nop();
```

## <a name="requirements"></a>Configuration requise

|Intrinsèque|Architecture|
|---------------|------------------|
|`__nop`|x86, ARM, x64, ARM64|

**Fichier d’en-tête** \<> Intro. h

**FIN de la section spécifique à Microsoft**

## <a name="remarks"></a>Notes

La fonction `__nop` est équivalente à l’instruction machine `NOP` . Pour plus d’informations sur x86 et x64, recherchez le document «Guide du développeur de logiciels d’architecture Intel, volume 2: Référence du jeu d’instructions, sur le site [Intel Corporation](https://software.intel.com/articles/intel-sdm) .

## <a name="see-also"></a>Voir aussi

[Intrinsèques du compilateur](../intrinsics/compiler-intrinsics.md)\
[__noop](../intrinsics/noop.md)
