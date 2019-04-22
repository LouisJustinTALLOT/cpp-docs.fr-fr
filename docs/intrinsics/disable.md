---
title: _disable
ms.date: 11/04/2016
f1_keywords:
- _disable_cpp
- _disable
helpviewer_keywords:
- _disable intrinsic
- rsm instruction
- disable intrinsic
ms.assetid: 52da3df9-815c-4524-9839-6d1742cff5c6
ms.openlocfilehash: 93db063c6b53f0bec739ba134728b83379a21f53
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59024673"
---
# <a name="disable"></a>_disable

**Section spécifique à Microsoft**

Désactive les interruptions.

## <a name="syntax"></a>Syntaxe

```
void _disable(void);
```

## <a name="requirements"></a>Configuration requise

|Intrinsèque|Architecture|
|---------------|------------------|
|`_disable`|x86, ARM, x64|

**Fichier d’en-tête** \<intrin.h >

## <a name="remarks"></a>Notes

`_disable` fait en sorte que le processeur efface l'indicateur d'interruption. Sur les systèmes x86, cette fonction génère l'instruction d'effacement de l'indicateur d'interruption (`cli`).

Cette fonction est disponible uniquement en mode noyau. Si vous l'utilisez en mode utilisateur, une exception Instruction privilégiée est levée au moment de l'exécution.

Sur les plateformes ARM, cette routine est disponible uniquement en tant qu'intrinsèque.

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[compilateur, fonctions intrinsèques](../intrinsics/compiler-intrinsics.md)