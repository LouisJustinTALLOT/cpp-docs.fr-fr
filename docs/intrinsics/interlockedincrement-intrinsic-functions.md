---
title: _InterlockedIncrement, fonctions intrinsèques
ms.date: 12/17/2018
f1_keywords:
- _InterlockedIncrement_acq
- _InterlockedIncrement16_rel_cpp
- _InterlockedIncrement16_cpp
- _InterlockedIncrement64_rel
- _InterlockedIncrement_rel
- _InterlockedIncrement64_nf
- _InterlockedIncrement16_acq_cpp
- _InterlockedIncrement_rel_cpp
- _InterlockedIncrement64
- _InterlockedIncrement64_rel_cpp
- _InterlockedIncrement16_nf
- _InterlockedIncrement16_rel
- _InterlockedIncrement16_acq
- _InterlockedIncrement_nf
- _InterlockedIncrement_acq_cpp
- _InterlockedIncrement64_cpp
- _InterlockedIncrement64_acq_cpp
- _InterlockedIncrement
- _InterlockedIncrement_cpp
- _InterlockedIncrement64_acq
- _InterlockedIncrement16
helpviewer_keywords:
- _InterlockedIncrement64_rel intrinsic
- _InterlockedIncrement16_rel intrinsic
- InterlockedIncrement64_acq intrinsic
- _InterlockedIncrement16 intrinsic
- _InterlockedIncrement16_acq intrinsic
- _InterlockedIncrement_nf intrinsic
- _InterlockedIncrement_rel intrinsic
- _InterlockedIncrement64_nf intrinsic
- InterlockedIncrement_rel intrinsic
- InterlockedIncrement_acq intrinsic
- _InterlockedIncrement64_acq intrinsic
- _InterlockedIncrement16_nf intrinsic
- _InterlockedIncrement intrinsic
- _InterlockedIncrement64 intrinsic
- InterlockedIncrement64_rel intrinsic
- InterlockedIncrement64 intrinsic
- InterlockedIncrement16 intrinsic
- _InterlockedIncrement_acq intrinsic
- InterlockedIncrement intrinsic
ms.assetid: 37700615-f372-438b-bcef-d76e11839482
ms.openlocfilehash: 58c71c577e3d87ca72836134a4f895f32170fe7f
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69509356"
---
# <a name="_interlockedincrement-intrinsic-functions"></a>_InterlockedIncrement, fonctions intrinsèques

**Section spécifique à Microsoft**

Fournit la prise en charge intrinsèque du compilateur pour la fonction Win32 SDK Windows [InterlockedIncrement](/windows/win32/api/winnt/nf-winnt-interlockedincrement) .

## <a name="syntax"></a>Syntaxe

```
long _InterlockedIncrement(
   long * lpAddend
);
long _InterlockedIncrement_acq(
   long * lpAddend
);
long _InterlockedIncrement_rel(
   long * lpAddend
);
long _InterlockedIncrement_nf(
   long * lpAddend
);
short _InterlockedIncrement16(
   short * lpAddend
);
short _InterlockedIncrement16_acq(
   short * lpAddend
);
short _InterlockedIncrement16_rel(
   short * lpAddend
);
short _InterlockedIncrement16_nf (
   short * lpAddend
);
__int64 _InterlockedIncrement64(
   __int64 * lpAddend
);
__int64 _InterlockedIncrement64_acq(
   __int64 * lpAddend
);
__int64 _InterlockedIncrement64_rel(
   __int64 * lpAddend
);
__int64 _InterlockedIncrement64_nf(
   __int64 * lpAddend
);
```

#### <a name="parameters"></a>Paramètres

*lpAddend*<br/>
[in, out] Pointeur vers la variable à incrémenter.

## <a name="return-value"></a>Valeur de retour

La valeur de retour est la valeur incrémentée résultante.

## <a name="requirements"></a>Configuration requise

|Intrinsèque|Architecture|Header|
|---------------|------------------|------------|
|`_InterlockedIncrement`, `_InterlockedIncrement16`, `_InterlockedIncrement64`|x86, ARM, x64|\<intrin.h>|
|`_InterlockedIncrement_acq`, `_InterlockedIncrement_rel`, `_InterlockedIncrement_nf`, `_InterlockedIncrement16_acq`, `_InterlockedIncrement16_rel`, `_InterlockedIncrement16_nf`, `_InterlockedIncrement64_acq`, `_InterlockedIncrement64_rel`, `_InterlockedIncrement64_nf`|ARM|\<intrin.h>|

## <a name="remarks"></a>Notes

Il existe plusieurs variantes de `_InterlockedIncrement` qui varient selon les types de données qu’elles impliquent et l’utilisation d’une sémantique acquire ou release spécifique au processeur.

La fonction `_InterlockedIncrement` opère sur des valeurs entières de 32 bits, `_InterlockedIncrement16` sur des valeurs entières de 16 bits et `_InterlockedIncrement64` sur des valeurs entières de 64 bits.

Sur les plateformes ARM, utilisez les fonctions intrinsèques avec des suffixes `_acq` et `_rel` si vous devez acquérir et libérer des éléments de la sémantique, comme le début et la fin d’une section critique. La fonction intrinsèque avec un suffixe `_nf` (pour « no fence », « pas de délimitation ») n'agit pas comme une barrière mémoire.

La variable vers laquelle pointe le paramètre `lpAddend` doit être alignée sur une limite de 32 bits. Dans le cas contraire, cette fonction échoue sur les systèmes x86 multiprocesseurs et les systèmes autres que x86. Pour plus d’informations, consultez [Aligner](../cpp/align-cpp.md).

La fonction Win32 est déclarée dans `Wdm.h` ou `Ntddk.h`.

Ces routines sont disponibles seulement comme fonctions intrinsèques.

## <a name="example"></a>Exemple

Pour obtenir un exemple d’utilisation `_InterlockedIncrement`de, consultez [_InterlockedDecrement](../intrinsics/interlockeddecrement-intrinsic-functions.md).

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[compilateur, fonctions intrinsèques](../intrinsics/compiler-intrinsics.md)<br/>
[Mots clés](../cpp/keywords-cpp.md)<br/>
[Conflits avec le compilateur x86](../build/x64-software-conventions.md#conflicts-with-the-x86-compiler)