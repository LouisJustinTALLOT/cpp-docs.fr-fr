---
title: _enable
ms.date: 09/02/2019
f1_keywords:
- _enable
- _enable_cpp
helpviewer_keywords:
- enable intrinsic
- _enable intrinsic
- ssm instruction
ms.assetid: 8bee669b-6bd8-4e25-9383-bb7d57295b4d
ms.openlocfilehash: 7adcd4eac807b8d0937efbbe6d89f8ad6dcb157c
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/03/2019
ms.locfileid: "70217872"
---
# <a name="_enable"></a>_enable

**Section spécifique à Microsoft**

Active les interruptions.

## <a name="syntax"></a>Syntaxe

```C
void _enable(void);
```

## <a name="requirements"></a>Configuration requise

|Intrinsèque|Architecture|
|---------------|------------------|
|`_enable`|x86, ARM, x64, ARM64|

**Fichier d’en-tête** \<> Intro. h

## <a name="remarks"></a>Notes

`_enable` fait en sorte que le processeur définisse l'indicateur d'interruption. Sur les systèmes x86, cette fonction génère l'instruction de définition de l'indicateur d'interruption (`sti`).

Cette fonction est disponible uniquement en mode noyau. Si vous l'utilisez en mode utilisateur, une exception Instruction privilégiée est levée.

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Intrinsèques du compilateur](../intrinsics/compiler-intrinsics.md)
