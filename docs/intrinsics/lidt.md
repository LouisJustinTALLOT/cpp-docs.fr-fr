---
description: 'En savoir plus sur : __lidt'
title: __lidt
ms.date: 09/02/2019
f1_keywords:
- __lidt
- __lidt_cpp
helpviewer_keywords:
- LIDT instruction
- __lidt intrinsic
ms.assetid: 8298d25d-a19e-4900-828d-6b3b09841882
ms.openlocfilehash: 9b9f4bc51bab07a578671932c16548a0a49d155b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97167771"
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
