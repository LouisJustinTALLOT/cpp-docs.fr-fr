---
title: _InterlockedAddLargeStatistic
ms.date: 11/04/2016
f1_keywords:
- _InterlockedAddLargeStatistic
- _InterlockedAddLargeStatistic_cpp
helpviewer_keywords:
- _InterlockedAddLargeStatistic intrinsic
- InterlockedAddLargeStatistic intrinsic
ms.assetid: 2802e74b-bcee-46e4-b562-894908d44409
ms.openlocfilehash: 6f9d599a8d7668c6c8a37846275e8338002589d1
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/05/2019
ms.locfileid: "59033412"
---
# <a name="interlockedaddlargestatistic"></a>_InterlockedAddLargeStatistic

**Section spécifique à Microsoft**

Effectue une addition verrouillée dans laquelle le premier opérande est une valeur 64 bits.

## <a name="syntax"></a>Syntaxe

```
long _InterlockedAddLargeStatistic(
   __int64 volatile * Addend,
   long Value
);
```

#### <a name="parameters"></a>Paramètres

*Terme*<br/>
[in, out] Pointeur vers le premier opérande pour l’opération d’ajout. La valeur indiquée est remplacée par le résultat de l’addition.

*Value*<br/>
[in] Le deuxième opérande ; valeur à ajouter à la première opérande.

## <a name="return-value"></a>Valeur de retour

La valeur du second opérande.

## <a name="requirements"></a>Configuration requise

|Intrinsèque|Architecture|
|---------------|------------------|
|`_InterlockedAddLargeStatistic`|x86|

**Fichier d’en-tête** \<intrin.h >

## <a name="remarks"></a>Notes

Cet intrinsèque n’est pas atomique, car il est implémenté comme deux distinctes des instructions verrouillées. Une lecture 64 bits atomique qui se produit sur un autre thread pendant l’exécution de cette intrinsèque peut entraîner une valeur incohérente en cours de lecture.

Cette fonction se comporte comme une barrière en lecture-écriture. Pour plus d’informations, consultez [l’intrinsèque _ReadWriteBarrier](../intrinsics/readwritebarrier.md).

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[compilateur, intrinsèques](../intrinsics/compiler-intrinsics.md)<br/>
[Conflits avec le compilateur x86](../build/x64-software-conventions.md#conflicts-with-the-x86-compiler)