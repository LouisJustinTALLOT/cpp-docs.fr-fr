---
title: _InterlockedIncrement fonctions intrinsèques
description: Fonctions intrinsèques du compilateur Microsoft C/C++ pour l’incrément de verrouillage.
ms.date: 09/03/2020
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
ms.openlocfilehash: 2148ae31f3eb03e398372db3bf15fc64e4857dd1
ms.sourcegitcommit: 4ed2d68634eb2fb77e18110a2d26bc0008be369c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89556319"
---
# <a name="_interlockedincrement-intrinsic-functions"></a>`_InterlockedIncrement` fonctions intrinsèques

Fournit la prise en charge intrinsèque du compilateur pour la fonction Win32 SDK Windows [InterlockedIncrement](/windows/win32/api/winnt/nf-winnt-interlockedincrement) . Les `_InterlockedIncrement` fonctions intrinsèques sont **spécifiques à Microsoft**.

## <a name="syntax"></a>Syntaxe

```C
long _InterlockedIncrement(
   long volatile * lpAddend
);
long _InterlockedIncrement_acq(
   long volatile * lpAddend
);
long _InterlockedIncrement_rel(
   long volatile * lpAddend
);
long _InterlockedIncrement_nf(
   long volatile * lpAddend
);
short _InterlockedIncrement16(
   short volatile * lpAddend
);
short _InterlockedIncrement16_acq(
   short volatile * lpAddend
);
short _InterlockedIncrement16_rel(
   short volatile * lpAddend
);
short _InterlockedIncrement16_nf (
   short volatile * lpAddend
);
__int64 _InterlockedIncrement64(
   __int64 volatile * lpAddend
);
__int64 _InterlockedIncrement64_acq(
   __int64 volatile * lpAddend
);
__int64 _InterlockedIncrement64_rel(
   __int64 volatile * lpAddend
);
__int64 _InterlockedIncrement64_nf(
   __int64 volatile * lpAddend
);
```

### <a name="parameters"></a>Paramètres

*lpAddend*\
[in, out] Pointeur vers la variable à incrémenter.

## <a name="return-value"></a>Valeur renvoyée

La valeur de retour est la valeur incrémentée résultante.

## <a name="requirements"></a>Spécifications

|Intrinsic|Architecture|En-tête|
|---------------|------------------|------------|
|`_InterlockedIncrement`, `_InterlockedIncrement16`|x86, ARM, x64, ARM64|\<intrin.h>|
|`_InterlockedIncrement64`|ARM, x64, ARM64|\<intrin.h>|
|`_InterlockedIncrement_acq`, `_InterlockedIncrement_rel`, `_InterlockedIncrement_nf`, `_InterlockedIncrement16_acq`, `_InterlockedIncrement16_rel`, `_InterlockedIncrement16_nf`, `_InterlockedIncrement64_acq`, `_InterlockedIncrement64_rel`, `_InterlockedIncrement64_nf`|ARM, ARM64|\<intrin.h>|

## <a name="remarks"></a>Notes

Il existe plusieurs variantes de `_InterlockedIncrement` qui varient selon les types de données qu’elles impliquent et l’utilisation d’une sémantique acquire ou release spécifique au processeur.

La fonction `_InterlockedIncrement` opère sur des valeurs entières de 32 bits, `_InterlockedIncrement16` sur des valeurs entières de 16 bits et `_InterlockedIncrement64` sur des valeurs entières de 64 bits.

Sur les plateformes ARM, utilisez les fonctions intrinsèques avec des suffixes `_acq` et `_rel` si vous devez acquérir et libérer des éléments de la sémantique, comme le début et la fin d’une section critique. L’intrinsèque avec un `_nf` suffixe (« no barrière ») n’agit pas comme une barrière de mémoire.

La variable vers laquelle pointe le paramètre `lpAddend` doit être alignée sur une limite de 32 bits. Dans le cas contraire, cette fonction échoue sur les systèmes x86 multiprocesseurs et les systèmes autres que x86. Pour plus d’informations, consultez [Aligner](../cpp/align-cpp.md).

La fonction Win32 est déclarée dans `Wdm.h` ou `Ntddk.h`.

Ces routines sont disponibles seulement comme fonctions intrinsèques.

## <a name="example"></a>Exemple

Pour obtenir un exemple d’utilisation de `_InterlockedIncrement` , consultez [_InterlockedDecrement](../intrinsics/interlockeddecrement-intrinsic-functions.md).

## <a name="see-also"></a>Voir aussi

[Intrinsèques du compilateur](../intrinsics/compiler-intrinsics.md)\
[Mot](../cpp/keywords-cpp.md)\
[Conflits avec le compilateur x86](../build/x64-software-conventions.md#conflicts-with-the-x86-compiler)
