---
title: _disable
ms.date: 09/02/2019
f1_keywords:
- _disable_cpp
- _disable
helpviewer_keywords:
- _disable intrinsic
- rsm instruction
- disable intrinsic
ms.assetid: 52da3df9-815c-4524-9839-6d1742cff5c6
ms.openlocfilehash: 94be850e1d494ff62df84922b46f28481be68314
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/03/2019
ms.locfileid: "70216820"
---
# <a name="_disable"></a>_disable

**Section spécifique à Microsoft**

Désactive les interruptions.

## <a name="syntax"></a>Syntaxe

```C
void _disable(void);
```

## <a name="requirements"></a>Configuration requise

|Intrinsèque|Architecture|
|---------------|------------------|
|`_disable`|x86, ARM, x64, ARM64|

**Fichier d’en-tête** \<> Intro. h

## <a name="remarks"></a>Notes

`_disable` fait en sorte que le processeur efface l'indicateur d'interruption. Sur les systèmes x86, cette fonction génère l'instruction d'effacement de l'indicateur d'interruption (`cli`).

Cette fonction est disponible uniquement en mode noyau. Si vous l'utilisez en mode utilisateur, une exception Instruction privilégiée est levée au moment de l'exécution.

Sur les plateformes ARM et ARM64, cette routine est uniquement disponible en tant qu’intrinsèque.

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Intrinsèques du compilateur](../intrinsics/compiler-intrinsics.md)
