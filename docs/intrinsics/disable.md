---
description: 'En savoir plus sur : _disable'
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
ms.openlocfilehash: c118315a4fea2dad401cc5c6f3621a8ec3b1794c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97337096"
---
# <a name="_disable"></a>_disable

**Spécifique à Microsoft**

Désactive les interruptions.

## <a name="syntax"></a>Syntaxe

```C
void _disable(void);
```

## <a name="requirements"></a>Spécifications

|Intrinsic|Architecture|
|---------------|------------------|
|`_disable`|x86, ARM, x64, ARM64|

**Fichier d’en-tête** \<intrin.h>

## <a name="remarks"></a>Notes

`_disable` fait en sorte que le processeur efface l'indicateur d'interruption. Sur les systèmes x86, cette fonction génère l'instruction d'effacement de l'indicateur d'interruption (`cli`).

Cette fonction est disponible uniquement en mode noyau. Si vous l'utilisez en mode utilisateur, une exception Instruction privilégiée est levée au moment de l'exécution.

Sur les plateformes ARM et ARM64, cette routine est uniquement disponible en tant qu’intrinsèque.

**FIN spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Intrinsèques du compilateur](../intrinsics/compiler-intrinsics.md)
