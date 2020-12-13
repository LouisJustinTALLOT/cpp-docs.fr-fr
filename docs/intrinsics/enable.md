---
description: 'En savoir plus sur : _enable'
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
ms.openlocfilehash: b9c84a31869dd356d5ee6ebd4eae5bd579cf319e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97337041"
---
# <a name="_enable"></a>_enable

**Spécifique à Microsoft**

Active les interruptions.

## <a name="syntax"></a>Syntaxe

```C
void _enable(void);
```

## <a name="requirements"></a>Spécifications

|Intrinsic|Architecture|
|---------------|------------------|
|`_enable`|x86, ARM, x64, ARM64|

**Fichier d’en-tête** \<intrin.h>

## <a name="remarks"></a>Notes

`_enable` fait en sorte que le processeur définisse l'indicateur d'interruption. Sur les systèmes x86, cette fonction génère l'instruction de définition de l'indicateur d'interruption (`sti`).

Cette fonction est disponible uniquement en mode noyau. Si vous l'utilisez en mode utilisateur, une exception Instruction privilégiée est levée.

**FIN spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Intrinsèques du compilateur](../intrinsics/compiler-intrinsics.md)
