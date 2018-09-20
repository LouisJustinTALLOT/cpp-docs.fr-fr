---
title: _InterlockedAddLargeStatistic | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- _InterlockedAddLargeStatistic
- _InterlockedAddLargeStatistic_cpp
dev_langs:
- C++
helpviewer_keywords:
- _InterlockedAddLargeStatistic intrinsic
- InterlockedAddLargeStatistic intrinsic
ms.assetid: 2802e74b-bcee-46e4-b562-894908d44409
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6698a58ec2a5363700f7751565f1dde8e25c2bcf
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46415978"
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

*Valeur*<br/>
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

[compilateur, fonctions intrinsèques](../intrinsics/compiler-intrinsics.md)<br/>
[Conflits avec le compilateur x86](../build/conflicts-with-the-x86-compiler.md)