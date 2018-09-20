---
title: _Activer | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- _enable
- _enable_cpp
dev_langs:
- C++
helpviewer_keywords:
- enable intrinsic
- _enable intrinsic
- ssm instruction
ms.assetid: 8bee669b-6bd8-4e25-9383-bb7d57295b4d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ce3b59bc6665c4622078285a0c3b4b5011bc7d9b
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46433374"
---
# <a name="enable"></a>_enable

**Section spécifique à Microsoft**

Active les interruptions.

## <a name="syntax"></a>Syntaxe

```
void _enable(void);
```

## <a name="requirements"></a>Configuration requise

|Intrinsèque|Architecture|
|---------------|------------------|
|`_enable`|x86, ARM, x64|

**Fichier d’en-tête** \<intrin.h >

## <a name="remarks"></a>Notes

`_enable` fait en sorte que le processeur définisse l'indicateur d'interruption. Sur les systèmes x86, cette fonction génère l'instruction de définition de l'indicateur d'interruption (`sti`).

Cette fonction est disponible uniquement en mode noyau. Si vous l'utilisez en mode utilisateur, une exception Instruction privilégiée est levée.

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[compilateur, fonctions intrinsèques](../intrinsics/compiler-intrinsics.md)