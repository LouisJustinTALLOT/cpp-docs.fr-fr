---
title: _interlockedbittestandset fonctions intrinsèques
ms.date: 09/02/2019
f1_keywords:
- _interlockedbittestandset_cpp
- _interlockedbittestandset_HLEAcquire
- _interlockedbittestandset64
- _interlockedbittestandset64_acq
- _interlockedbittestandset64_nf
- _interlockedbittestandset64_rel
- _interlockedbittestandset
- _interlockedbittestandset_rel
- _interlockedbittestandset64_HLEAcquire
- _interlockedbittestandset_HLERelease
- _interlockedbittestandset_acq
- _interlockedbittestandset_nf
- _interlockedbittestandset64_cpp
- _interlockedbittestandset64_HLERelease
helpviewer_keywords:
- _interlockedbittestandset intrinsic
- _interlockedbittestandset64 intrinsic
- lock_bts instruction
ms.assetid: b1b7e334-53ea-48cf-ba60-5fa3ef51a1fc
ms.openlocfilehash: 9679abf674b5ef366818e73504c3c8c80c5d8ed7
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/03/2019
ms.locfileid: "70217760"
---
# <a name="_interlockedbittestandset-intrinsic-functions"></a>_interlockedbittestandset fonctions intrinsèques

**Section spécifique à Microsoft**

Générez une instruction pour examiner `b` le bit de `a` l’adresse et retourner sa valeur actuelle avant de lui affecter la valeur 1.

## <a name="syntax"></a>Syntaxe

```C
unsigned char _interlockedbittestandset(
   long *a,
   long b
);
unsigned char _interlockedbittestandset_acq(
   long *a,
   long b
);
unsigned char _interlockedbittestandset_HLEAcquire(
   long *a,
   long b
);
unsigned char _interlockedbittestandset_HLERelease(
   long *a,
   long b
);
unsigned char _interlockedbittestandset_nf(
   long *a,
   long b
);
unsigned char _interlockedbittestandset_rel(
   long *a,
   long b
);
unsigned char _interlockedbittestandset64(
   __int64 *a,
   __int64 b
);
unsigned char _interlockedbittestandset64_acq(
   __int64 *a,
   __int64 b
);
unsigned char _interlockedbittestandset64_nf(
   __int64 *a,
   __int64 b
);
unsigned char _interlockedbittestandset64_rel(
   __int64 *a,
   __int64 b
);
unsigned char _interlockedbittestandset64_HLEAcquire(
   __int64 *a,
   __int64 b
);
unsigned char _interlockedbittestandset64_HLERelease(
   __int64 *a,
   __int64 b
);
```

### <a name="parameters"></a>Paramètres

*un*\
dans Pointeur vers la mémoire à examiner.

*p*\
dans Position de bit à tester.

## <a name="return-value"></a>Valeur de retour

Valeur du bit à la position `b` avant qu’il ne soit défini.

## <a name="requirements"></a>Configuration requise

|Intrinsèque|Architecture|Header|
|---------------|------------------|------------|
|`_interlockedbittestandset`|x86, ARM, x64, ARM64|\<intrin.h>|
|`_interlockedbittestandset_acq`, `_interlockedbittestandset_nf`, `_interlockedbittestandset_rel`|ARM, ARM64|\<intrin.h>|
|`_interlockedbittestandset64_acq`, `_interlockedbittestandset64_nf`, `_interlockedbittestandset64_rel`|ARM64|\<intrin.h>|
|`_interlockedbittestandset_HLEAcquire`, `_interlockedbittestandset_HLERelease`|x86, x64|\<immintrin.h>|
|`_interlockedbittestandset64`|x64, ARM64|\<intrin.h>|
|`_interlockedbittestandset64_HLEAcquire`, `_interlockedbittestandset64_HLERelease`|X64|\<immintrin.h>|

## <a name="remarks"></a>Notes

Sur les processeurs x86 et x64, ces fonctions intrinsèques utilisent l' `lock bts` instruction pour lire et définir le bit spécifié sur 1. L'opération est atomique.

Sur les processeurs ARM et ARM64, utilisez les intrinsèques `_rel` avec `_acq` les suffixes et pour les sémantiques Acquire et Release, par exemple au début et à la fin d’une section critique. Les intrinsèques ARM avec un `_nf` suffixe («no cloture») n’agissent pas comme une barrière de mémoire.

Sur les processeurs Intel qui prennent en charge les instructions HLE (Hardware Lock Elision), les intrinsèques ayant les suffixes `_HLEAcquire` et `_HLERelease` incluent une indication pour le processeur. Celle-ci permet d'accélérer les performances en éliminant une étape d'écriture de verrou dans le matériel. Si ces fonctions intrinsèques sont appelées sur des processeurs qui ne prennent pas en charge HLE, l’indicateur est ignoré.

Ces routines sont disponibles seulement comme fonctions intrinsèques.

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Intrinsèques du compilateur](../intrinsics/compiler-intrinsics.md)\
[Conflits avec le compilateur x86](../build/x64-software-conventions.md#conflicts-with-the-x86-compiler)
