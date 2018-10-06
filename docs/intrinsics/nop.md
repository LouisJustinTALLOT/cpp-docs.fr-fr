---
title: __nop | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __nop
dev_langs:
- C++
helpviewer_keywords:
- nop instruction
- __nop intrinsic
ms.assetid: 7a2a938b-87e0-476d-a348-03ea7635b6b9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bc5dab4ba2c23f60eb4407548cea5c15106c1401
ms.sourcegitcommit: a738519aa491a493a8f213971354356c0e6a5f3a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/05/2018
ms.locfileid: "48820501"
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
|`__nop`|x86, x64|

**Fichier d’en-tête** \<intrin.h >

**FIN de la section spécifique à Microsoft**

## <a name="remarks"></a>Notes

Le `__nop` fonction est équivalente à la `NOP` instruction machine. Pour plus d’informations, recherchez dans le document, « manuel du développeur de logiciels Architecture Intel, Volume 2 : référence de jeu d’instructions, » à la [Intel Corporation](https://software.intel.com/articles/intel-sdm) site.

## <a name="see-also"></a>Voir aussi

[compilateur, fonctions intrinsèques](../intrinsics/compiler-intrinsics.md)<br/>
[__noop](../intrinsics/noop.md)