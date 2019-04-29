---
title: _enable
ms.date: 11/04/2016
f1_keywords:
- _enable
- _enable_cpp
helpviewer_keywords:
- enable intrinsic
- _enable intrinsic
- ssm instruction
ms.assetid: 8bee669b-6bd8-4e25-9383-bb7d57295b4d
ms.openlocfilehash: e1ece6d6f4040b81b55d8400407d46f165b56b53
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62349028"
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