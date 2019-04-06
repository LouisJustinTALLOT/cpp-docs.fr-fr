---
title: _interlockedbittestandset, fonctions intrinsèques
ms.date: 12/17/2018
f1_keywords:
- _interlockedbittestandset_cpp
- _interlockedbittestandset_HLEAcquire
- _interlockedbittestandset64
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
ms.openlocfilehash: 3da533b3cf2ab8f396e4ba284cc0bf921a5c80b5
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/05/2019
ms.locfileid: "59023202"
---
# <a name="interlockedbittestandset-intrinsic-functions"></a>_interlockedbittestandset, fonctions intrinsèques

**Section spécifique à Microsoft**

Générer une instruction qui examine le bit `b` de l'adresse `a` et retourne sa valeur actuelle avant de lui affecter la valeur 1.

## <a name="syntax"></a>Syntaxe

```
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
unsigned char _interlockedbittestandset64_HLEAcquire(
   __int64 *a,
   __int64 b
);
unsigned char _interlockedbittestandset64_HLERelease(
   __int64 *a,
   __int64 b
);
```

#### <a name="parameters"></a>Paramètres

*a*<br/>
[in] Pointeur vers la mémoire à examiner.

*b*<br/>
[in] La position de bit à tester.

## <a name="return-value"></a>Valeur de retour

Valeur du bit à la position `b` avant qu'il ne soit défini.

## <a name="requirements"></a>Configuration requise

|Intrinsèque|Architecture|Header|
|---------------|------------------|------------|
|`_interlockedbittestandset`|x86, ARM, x64|\<intrin.h>|
|`_interlockedbittestandset_acq`, `_interlockedbittestandset_nf`, `_interlockedbittestandset_rel`|ARM|\<intrin.h>|
|`_interlockedbittestandset_HLEAcquire`, `_interlockedbittestandset_HLERelease`|x86, x64|\<immintrin.h>|
|`_interlockedbittestandset64`|X64|\<intrin.h>|
|`_interlockedbittestandset64_HLEAcquire`, `_interlockedbittestandset64_HLERelease`|X64|\<immintrin.h>|

## <a name="remarks"></a>Notes

Sur les processeurs x86 et x64, ces fonctions intrinsèques utilisent le `lock bts` instruction pour lire et définir le bit spécifié sur 1. L'opération est atomique.

Sur les processeurs ARM, utilisez les intrinsèques avec les suffixes `_acq` et `_rel` pour les sémantiques Acquire et Release, par exemple au début et à la fin d’une section critique. Les fonctions intrinsèques ARM avec un suffixe `_nf` (pour « no fence », « pas de délimitation ») n'agissent pas comme une barrière mémoire.

Sur les processeurs Intel qui prennent en charge les instructions HLE (Hardware Lock Elision), les intrinsèques ayant les suffixes `_HLEAcquire` et `_HLERelease` incluent une indication pour le processeur. Celle-ci permet d'accélérer les performances en éliminant une étape d'écriture de verrou dans le matériel. Si ces intrinsèques sont appelés pour des processeurs qui ne prennent pas en charge les instructions HLE, l'indication est ignorée.

Ces routines sont disponibles seulement comme fonctions intrinsèques.

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[compilateur, intrinsèques](../intrinsics/compiler-intrinsics.md)<br/>
[Conflits avec le compilateur x86](../build/x64-software-conventions.md#conflicts-with-the-x86-compiler)