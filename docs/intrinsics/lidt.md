---
title: __lidt
ms.date: 09/02/2019
f1_keywords:
- __lidt
- __lidt_cpp
helpviewer_keywords:
- LIDT instruction
- __lidt intrinsic
ms.assetid: 8298d25d-a19e-4900-828d-6b3b09841882
ms.openlocfilehash: 87a49643e7cd11ae57dc01130f250895cf012065
ms.sourcegitcommit: 1839405b97036891b6e4d37c99def044d6f37eff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/18/2020
ms.locfileid: "88562491"
---
# <a name="__lidt"></a>__lidt

**Spécifique à Microsoft**

Charge le registre de la table du descripteur d’interruption (IDTR) avec la valeur dans l’emplacement de mémoire spécifié.

## <a name="syntax"></a>Syntaxe

```C
void __lidt(void * Source);
```

### <a name="parameters"></a>Paramètres

*Code*\
dans Pointeur vers la valeur à copier dans IDTR.

## <a name="requirements"></a>Spécifications

|Intrinsic|Architecture|
|---------------|------------------|
|`__lidt`|x86, x64|

**Fichier d’en-tête** \<intrin.h>

## <a name="remarks"></a>Notes

La `__lidt` fonction est équivalente à l' `LIDT` instruction machine et est disponible uniquement en mode noyau. Pour plus d’informations, recherchez le document « Guide du développeur de logiciels d’architecture Intel, volume 2 : référence de jeu d’instructions » sur le site [Intel Corporation](https://software.intel.com/articles/intel-sdm) .

**FIN spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Intrinsèques du compilateur](../intrinsics/compiler-intrinsics.md)\
[__sidt](../intrinsics/sidt.md)
