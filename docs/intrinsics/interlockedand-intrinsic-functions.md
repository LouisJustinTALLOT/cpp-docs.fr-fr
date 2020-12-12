---
description: 'En savoir plus sur : fonctions intrinsèques de _InterlockedAnd'
title: _InterlockedAnd fonctions intrinsèques
ms.date: 09/02/2019
f1_keywords:
- _InterlockedAnd_rel
- _InterlockedAnd_cpp
- _InterlockedAnd8_nf
- _InterlockedAnd
- _InterlockedAnd_HLERelease
- _InterlockedAnd8_np
- _InterlockedAnd16_rel
- _InterlockedAnd64_np
- _InterlockedAnd_np
- _InterlockedAnd64_HLERelease
- _InterlockedAnd64
- _InterlockedAnd64_nf
- _InterlockedAnd64_HLEAcquire
- _InterlockedAnd16
- _InterlockedAnd16_nf
- _InterlockedAnd8
- _InterlockedAnd_HLEAcquire
- _InterlockedAnd_acq
- _InterlockedAnd16_np
- _InterlockedAnd64_cpp
- _InterlockedAnd64_acq
- _InterlockedAnd16_acq
- _InterlockedAnd8_acq
- _InterlockedAnd64_rel
- _InterlockedAnd_nf
- _InterlockedAnd8_rel
helpviewer_keywords:
- _InterlockedAnd64_np intrinsic
- _InterlockedAnd intrinsic
- _InterlockedAnd64 intrinsic
- _InterlockedAnd8_rel intrinsic
- InterlockedAnd64 intrinsic
- _InterlockedAnd16_np intrinsic
- _InterlockedAnd64_nf intrinsic
- _InterlockedAnd_nf intrinsic
- _InterlockedAnd_np intrinsic
- _InterlockedAnd64_HLERelease intrinsic
- _InterlockedAnd16_rel intrinsic
- _InterlockedAnd_HLERelease intrinsic
- _InterlockedAnd64_acq intrinsic
- _InterlockedAnd16 intrinsic
- _InterlockedAnd8_nf intrinsic
- _InterlockedAnd64_rel intrinsic
- _InterlockedAnd8_np intrinsic
- _InterlockedAnd_rel intrinsic
- InterlockedAnd intrinsic
- _InterlockedAnd8_acq intrinsic
- _InterlockedAnd_acq intrinsic
- _InterlockedAnd64_HLEAcquire intrinsic
- _InterlockedAnd16_acq intrinsic
- _InterlockedAnd16_nf intrinsic
- _InterlockedAnd8 intrinsic
- _InterlockedAnd_HLEAcquire intrinsic
ms.assetid: ad271dc3-42cd-47d0-9f65-30d5cfeb66fc
ms.openlocfilehash: f5e00b997eced482a8adc8881e9a1b6a3231bb72
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97168252"
---
# <a name="_interlockedand-intrinsic-functions"></a>_InterlockedAnd fonctions intrinsèques

**Spécifique à Microsoft**

Sert à exécuter une opération AND atomique au niveau du bit sur une variable partagée par plusieurs threads.

## <a name="syntax"></a>Syntaxe

```C
long _InterlockedAnd(
   long volatile * value,
   long mask
);
long _InterlockedAnd_acq(
   long volatile * value,
   long mask
);
long _InterlockedAnd_HLEAcquire(
   long volatile * value,
   long mask
);
long _InterlockedAnd_HLERelease(
   long volatile * value,
   long mask
);
long _InterlockedAnd_nf(
   long volatile * value,
   long mask
);
long _InterlockedAnd_np(
   long volatile * value,
   long mask
);
long _InterlockedAnd_rel(
   long volatile * value,
   long mask
);
char _InterlockedAnd8(
   char volatile * value,
   char mask
);
char _InterlockedAnd8_acq(
   char volatile * value,
   char mask
);
char _InterlockedAnd8_nf(
   char volatile * value,
   char mask
);
char _InterlockedAnd8_np(
   char volatile * value,
   char mask
);
char _InterlockedAnd8_rel(
   char volatile * value,
   char mask
);
short _InterlockedAnd16(
   short volatile * value,
   short mask
);
short _InterlockedAnd16_acq(
   short volatile * value,
   short mask
);
short _InterlockedAnd16_nf(
   short volatile * value,
   short mask
);
short _InterlockedAnd16_np(
   short volatile * value,
   short mask
);
short _InterlockedAnd16_rel(
   short volatile * value,
   short mask
);
__int64 _InterlockedAnd64(
   __int64 volatile* value,
   __int64 mask
);
__int64 _InterlockedAnd64_acq(
   __int64 volatile* value,
   __int64 mask
);
__int64 _InterlockedAnd64_HLEAcquire(
   __int64 volatile* value,
   __int64 mask
);
__int64 _InterlockedAnd64_HLERelease(
   __int64 volatile* value,
   __int64 mask
);
__int64 _InterlockedAnd64_nf(
   __int64 volatile* value,
   __int64 mask
);
__int64 _InterlockedAnd64_np(
   __int64 volatile* value,
   __int64 mask
);
__int64 _InterlockedAnd64_rel(
   __int64 volatile* value,
   __int64 mask
);
```

### <a name="parameters"></a>Paramètres

*ajoutée*\
[in, out] Pointeur vers le premier opérande, à remplacer par le résultat.

*filtrage*\
dans Deuxième opérande.

## <a name="return-value"></a>Valeur retournée

Valeur d’origine du premier opérande.

## <a name="requirements"></a>Spécifications

|Intrinsic|Architecture|En-tête|
|---------------|------------------|------------|
|`_InterlockedAnd`, `_InterlockedAnd8`, `_InterlockedAnd16`|x86, ARM, x64, ARM64|\<intrin.h>|
|`_InterlockedAnd64`|ARM, x64, ARM64|\<intrin.h>|
|`_InterlockedAnd_acq`, `_InterlockedAnd_nf`, `_InterlockedAnd_rel`, `_InterlockedAnd8_acq`, `_InterlockedAnd8_nf`, `_InterlockedAnd8_rel`, `_InterlockedAnd16_acq`, `_InterlockedAnd16_nf`, `_InterlockedAnd16_rel`, `_InterlockedAnd64_acq`, `_InterlockedAnd64_nf`, `_InterlockedAnd64_rel`|ARM, ARM64|\<intrin.h>|
|`_InterlockedAnd_np`, `_InterlockedAnd8_np`, `_InterlockedAnd16_np`, `_InterlockedAnd64_np`|x64|\<intrin.h>|
|`_InterlockedAnd_HLEAcquire`, `_InterlockedAnd_HLERelease`, `_InterlockedAnd64_HLEAcquire`, `_InterlockedAnd64_HLERelease`|x86, x64|\<immintrin.h>|

## <a name="remarks"></a>Notes

Le nombre dans le nom de chaque fonction spécifie la taille en bits des arguments.

Sur les plateformes ARM et ARM64, utilisez les intrinsèques avec les `_acq` `_rel` suffixes et pour les sémantiques Acquire et Release, par exemple au début et à la fin d’une section critique. Les fonctions intrinsèques avec un suffixe `_nf` (pour « no fence », « pas de délimitation ») n'agissent pas comme une barrière mémoire.

Les fonctions intrinsèques avec un suffixe `_np` (pour « no prefetch », « pas de prérécupération ») empêchent l'insertion par le compilateur d'une possible opération de prérécupération.

Sur les plateformes Intel qui prennent en charge les instructions HLE (Hardware Lock Elision), les fonctions intrinsèques avec les suffixes `_HLEAcquire` et `_HLERelease` comprennent une indication pour le processeur qui peut accélérer les performances en éliminant une étape d'écriture de verrou dans le matériel. Si ces fonctions intrinsèques sont appelées sur des plateformes qui ne prennent pas en charge HLE, l'indication est ignorée.

## <a name="example"></a>Exemple

```cpp
// InterlockedAnd.cpp
// Compile with: /Oi
#include <stdio.h>
#include <intrin.h>

#pragma intrinsic(_InterlockedAnd)

int main()
{
        long data1 = 0xFF00FF00;
        long data2 = 0x00FFFF00;
        long retval;
        retval = _InterlockedAnd(&data1, data2);
        printf_s("0x%x 0x%x 0x%x", data1, data2, retval);
}
```

```Output
0xff00 0xffff00 0xff00ff00
```

**FIN spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Intrinsèques du compilateur](../intrinsics/compiler-intrinsics.md)\
[Conflits avec le compilateur x86](../build/x64-software-conventions.md#conflicts-with-the-x86-compiler)
