---
description: 'En savoir plus sur : fonctions intrinsèques de _interlockedbittestandreset'
title: _interlockedbittestandreset fonctions intrinsèques
ms.date: 09/02/2019
f1_keywords:
- _interlockedbittestandreset_rel
- _interlockedbittestandreset64
- _interlockedbittestandreset64_acq
- _interlockedbittestandreset64_nf
- _interlockedbittestandreset64_rel
- _interlockedbittestandreset64_HLERelease
- _interlockedbittestandreset_HLERelease
- _interlockedbittestandreset_HLEAcquire
- _interlockedbittestandreset_acq
- _interlockedbittestandreset_cpp
- _interlockedbittestandreset_nf
- _interlockedbittestandreset64_cpp
- _interlockedbittestandreset64_HLEAcquire
- _interlockedbittestandreset
helpviewer_keywords:
- lock_btr instruction
- _interlockedbittestandreset64 intrinsic
- _interlockedbittestandreset intrinsic
ms.assetid: 9bbb1442-f2e9-4dc2-b0da-97f3de3493b9
ms.openlocfilehash: 10bd636fb25d0f4025530f0bd7a8c3f877cc1556
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97168213"
---
# <a name="_interlockedbittestandreset-intrinsic-functions"></a>_interlockedbittestandreset fonctions intrinsèques

**Spécifique à Microsoft**

Génère une instruction pour définir `b` le bit de l’adresse `a` à zéro et retourner sa valeur d’origine.

## <a name="syntax"></a>Syntaxe

```C
unsigned char _interlockedbittestandreset(
   long *a,
   long b
);
unsigned char _interlockedbittestandreset_acq(
   long *a,
   long b
);
unsigned char _interlockedbittestandreset_HLEAcquire(
   long *a,
   long b
);
unsigned char _interlockedbittestandreset_HLERelease(
   long *a,
   long b
);
unsigned char _interlockedbittestandreset_nf(
   long *a,
   long b
);
unsigned char _interlockedbittestandreset_rel(
   long *a,
   long b
);
unsigned char _interlockedbittestandreset64(
   __int64 *a,
   __int64 b
);
unsigned char _interlockedbittestandreset64_acq(
   __int64 *a,
   __int64 b
);
unsigned char _interlockedbittestandreset64_nf(
   __int64 *a,
   __int64 b
);
unsigned char _interlockedbittestandreset64_rel(
   __int64 *a,
   __int64 b
);
unsigned char _interlockedbittestandreset64_HLEAcquire(
   __int64 *a,
   __int64 b
);
unsigned char _interlockedbittestandreset64_HLERelease(
   __int64 *a,
   __int64 b
);
```

### <a name="parameters"></a>Paramètres

*un*\
dans Pointeur vers la mémoire à examiner.

*p*\
dans Position de bit à tester.

## <a name="return-value"></a>Valeur retournée

Valeur d'origine du bit à la position spécifiée par `b`.

## <a name="requirements"></a>Spécifications

|Intrinsic|Architecture|En-tête|
|---------------|------------------|------------|
|`_interlockedbittestandreset`|x86, ARM, x64, ARM64|\<intrin.h>|
|`_interlockedbittestandreset_acq`, `_interlockedbittestandreset_nf`, `_interlockedbittestandreset_rel`|ARM, ARM64|\<intrin.h>|
|`_interlockedbittestandreset64_acq`, `_interlockedbittestandreset64_nf`, `_interlockedbittestandreset64_rel`|ARM64|\<intrin.h>|
|`_interlockedbittestandreset_HLEAcquire`, `_interlockedbittestandreset_HLERelease`|x86, x64|\<immintrin.h>|
|`_interlockedbittestandreset64`|x64, ARM64|\<intrin.h>|
|`_interlockedbittestandreset64_HLEAcquire`, `_interlockedbittestandreset64_HLERelease`|x64|\<immintrin.h>|

## <a name="remarks"></a>Notes

Sur les processeurs x86 et x64, ces fonctions intrinsèques utilisent l' `lock btr` instruction, qui lit et définit le bit spécifié à zéro dans une opération atomique.

Sur les processeurs ARM, utilisez les intrinsèques avec les suffixes `_acq` et `_rel` pour les sémantiques Acquire et Release, par exemple au début et à la fin d’une section critique. Les intrinsèques ARM avec un `_nf` suffixe (« no cloture ») n’agissent pas comme une barrière de mémoire.

Sur les processeurs Intel qui prennent en charge les instructions HLE (Hardware Lock Elision), les intrinsèques ayant les suffixes `_HLEAcquire` et `_HLERelease` incluent une indication pour le processeur. Celle-ci permet d'accélérer les performances en éliminant une étape d'écriture de verrou dans le matériel. Si ces fonctions intrinsèques sont appelées sur des processeurs qui ne prennent pas en charge HLE, l’indicateur est ignoré.

Ces routines sont disponibles seulement comme fonctions intrinsèques.

**FIN spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Intrinsèques du compilateur](../intrinsics/compiler-intrinsics.md)\
[Conflits avec le compilateur x86](../build/x64-software-conventions.md#conflicts-with-the-x86-compiler)
