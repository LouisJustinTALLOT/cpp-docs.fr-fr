---
description: 'En savoir plus sur : _InterlockedAddLargeStatistic'
title: _InterlockedAddLargeStatistic
ms.date: 09/02/2019
f1_keywords:
- _InterlockedAddLargeStatistic
- _InterlockedAddLargeStatistic_cpp
helpviewer_keywords:
- _InterlockedAddLargeStatistic intrinsic
- InterlockedAddLargeStatistic intrinsic
ms.assetid: 2802e74b-bcee-46e4-b562-894908d44409
ms.openlocfilehash: 52ca32d0f9b08d638a66923f8f0204eb515b447e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97336869"
---
# <a name="_interlockedaddlargestatistic"></a>_InterlockedAddLargeStatistic

**Spécifique à Microsoft**

Effectue une addition verrouillée dans laquelle le premier opérande est une valeur 64 bits.

## <a name="syntax"></a>Syntaxe

```C
long _InterlockedAddLargeStatistic(
   __int64 volatile * Addend,
   long Value
);
```

### <a name="parameters"></a>Paramètres

*Addend*\
[in, out] Pointeur vers le premier opérande de l’opération d’ajout. La valeur vers laquelle pointe est remplacée par le résultat de l’addition.

*Value*\
dans Deuxième opérande ; valeur à ajouter au premier opérande.

## <a name="return-value"></a>Valeur retournée

Valeur du second opérande.

## <a name="requirements"></a>Spécifications

|Intrinsic|Architecture|
|---------------|------------------|
|`_InterlockedAddLargeStatistic`|x86|

**Fichier d’en-tête** \<intrin.h>

## <a name="remarks"></a>Notes

L' `_InterlockedAddLargeStatistic` intrinsèque n’est pas atomique, car il est implémenté comme deux instructions verrouillées distinctes. Une lecture atomique 64 bits qui se produit sur un autre thread pendant l’exécution de l’intrinsèque peut entraîner la lecture d’une valeur incohérente.

`_InterlockedAddLargeStatistic` se comporte comme une barrière de lecture-écriture. Pour plus d’informations, consultez [_ReadWriteBarrier](../intrinsics/readwritebarrier.md).

**FIN spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Intrinsèques du compilateur](../intrinsics/compiler-intrinsics.md)\
[Conflits avec le compilateur x86](../build/x64-software-conventions.md#conflicts-with-the-x86-compiler)
