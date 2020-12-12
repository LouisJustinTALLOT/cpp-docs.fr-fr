---
description: 'En savoir plus sur : fonctions intrinsèques de _InterlockedExchangeAdd'
title: _InterlockedExchangeAdd fonctions intrinsèques
ms.date: 09/02/2019
f1_keywords:
- _InterlockedExchangeAdd64_nf
- _InterlockedExchangeAdd64_rel
- _InterlockedExchangeAdd16_rel
- _InterlockedExchangeAdd_acq
- _InterlockedExchangeAdd_nf
- _InterlockedExchangeAdd_rel
- _InterlockedExchangeAdd8_acq
- _InterlockedExchangeAdd16_nf
- _InterlockedExchangeAdd_acq_cpp
- _InterlockedExchangeAdd64_acq_cpp
- _InterlockedExchangeAdd16_acq
- _InterlockedExchangeAdd_HLERelease
- _InterlockedExchangeAdd64_cpp
- _InterlockedExchangeAdd64_HLERelease
- _InterlockedExchangeAdd64_acq
- _InterlockedExchangeAdd8
- _InterlockedExchangeAdd64
- _InterlockedExchangeAdd8_nf
- _InterlockedExchangeAdd16
- _InterlockedExchangeAdd64_rel_cpp
- _InterlockedExchangeAdd_cpp
- _InterlockedExchangeAdd8_rel
- _InterlockedExchangeAdd_HLEAcquire
- _InterlockedExchangeAdd64_HLEAcquire
- _InterlockedExchangeAdd
helpviewer_keywords:
- _InterlockedExchangeAdd8_nf intrinsic
- InterlockedExchangeAdd64_acq intrinsic
- _InterlockedExchangeAdd8_acq intrinsic
- _InterlockedExchangeAdd64 intrinsic
- _InterlockedExchangeAdd intrinsic
- _InterlockedExchangeAdd8_rel intrinsic
- _InterlockedExchangeAdd_acq intrinsic
- _InterlockedExchangeAdd_HLEAcquire intrinsic
- _InterlockedExchangeAdd8 intrinsic
- _InterlockedExchangeAdd_rel intrinsic
- _InterlockedExchangeAdd64_HLERelease intrinsic
- _InterlockedExchangeAdd64_nf intrinsic
- InterlockedExchangeAdd_rel intrinsic
- InterlockedExchangeAdd intrinsic
- _InterlockedExchangeAdd_nf intrinsic
- _InterlockedExchangeAdd16_rel intrinsic
- InterlockedExchangeAdd_acq intrinsic
- _InterlockedExchangeAdd64_HLEAcquire intrinsic
- _InterlockedExchangeAdd16 intrinsic
- _InterlockedExchangeAdd64_acq intrinsic
- InterlockedExchangeAdd64_rel intrinsic
- _InterlockedExchangeAdd16_acq intrinsic
- InterlockedExchangeAdd64 intrinsic
- _InterlockedExchangeAdd_HLERelease intrinsic
- _InterlockedExchangeAdd16_nf intrinsic
- _InterlockedExchangeAdd64_rel intrinsic
ms.assetid: 25809e1f-9c60-4492-9f7c-0fb59c8d13d2
ms.openlocfilehash: fa1403889aec15ba8cdaae135db2b7563636c21e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97168018"
---
# <a name="_interlockedexchangeadd-intrinsic-functions"></a>_InterlockedExchangeAdd fonctions intrinsèques

**Spécifique à Microsoft**

Fournit la prise en charge intrinsèque du compilateur pour la fonction Win32 SDK Windows [_InterlockedExchangeAdd fonctions intrinsèques](../intrinsics/interlockedexchangeadd-intrinsic-functions.md) .

## <a name="syntax"></a>Syntaxe

```C
long _InterlockedExchangeAdd(
   long volatile * Addend,
   long Value
);
long _InterlockedExchangeAdd_acq(
   long volatile * Addend,
   long Value
);
long _InterlockedExchangeAdd_rel(
   long volatile * Addend,
   long Value
);
long _InterlockedExchangeAdd_nf(
   long volatile * Addend,
   long Value
);
long _InterlockedExchangeAdd_HLEAcquire(
   long volatile * Addend,
   long Value
);
long _InterlockedExchangeAdd_HLERelease(
   long volatile * Addend,
   long Value
);
char _InterlockedExchangeAdd8(
   char volatile * Addend,
   char Value
);
char _InterlockedExchangeAdd8_acq(
   char volatile * Addend,
   char Value
);
char _InterlockedExchangeAdd8_rel(
   char volatile * Addend,
   char Value
);
char _InterlockedExchangeAdd8_nf(
   char volatile * Addend,
   char Value
);
short _InterlockedExchangeAdd16(
   short volatile * Addend,
   short Value
);
short _InterlockedExchangeAdd16_acq(
   short volatile * Addend,
   short Value
);
short _InterlockedExchangeAdd16_rel(
   short volatile * Addend,
   short Value
);
short _InterlockedExchangeAdd16_nf(
   short volatile * Addend,
   short Value
);
__int64 _InterlockedExchangeAdd64(
   __int64 volatile * Addend,
   __int64 Value
);
__int64 _InterlockedExchangeAdd64_acq(
   __int64 volatile * Addend,
   __int64 Value
);
__int64 _InterlockedExchangeAdd64_rel(
   __int64 volatile * Addend,
   __int64 Value
);
__int64 _InterlockedExchangeAdd64_nf(
   __int64 volatile * Addend,
   __int64 Value
);
__int64 _InterlockedExchangeAdd64_HLEAcquire(
   __int64 volatile * Addend,
   __int64 Value
);
__int64 _InterlockedExchangeAdd64_HLERelease(
   __int64 volatile * Addend,
   __int64 Value
);
```

### <a name="parameters"></a>Paramètres

*Addend*\
[in, out] Valeur à ajouter à ; remplacé par le résultat de l’addition.

*Value*\
dans Valeur à ajouter.

## <a name="return-value"></a>Valeur retournée

La valeur de retour est la valeur initiale de la variable vers laquelle pointe le paramètre `Addend`.

## <a name="requirements"></a>Spécifications

|Intrinsic|Architecture|En-tête|
|---------------|------------------|------------|
|`_InterlockedExchangeAdd`, `_InterlockedExchangeAdd8`, `_InterlockedExchangeAdd16`|x86, ARM, x64, ARM64|\<intrin.h>|
|`_InterlockedExchangeAdd64`|ARM, x64, ARM64|\<intrin.h>|
|`_InterlockedExchangeAdd_acq`, `_InterlockedExchangeAdd_rel`, `_InterlockedExchangeAdd_nf`, `_InterlockedExchangeAdd8_acq`, `_InterlockedExchangeAdd8_rel`, `_InterlockedExchangeAdd8_nf`,`_InterlockedExchangeAdd16_acq`, `_InterlockedExchangeAdd16_rel`, `_InterlockedExchangeAdd16_nf`, `_InterlockedExchangeAdd64_acq`, `_InterlockedExchangeAdd64_rel`, `_InterlockedExchangeAdd64_nf`|ARM, ARM64|\<intrin.h>|
|`_InterlockedExchangeAdd_HLEAcquire`, `_InterlockedExchangeAdd_HLERelease`|x86, x64|\<immintrin.h>|
|`_InterlockedExchangeAdd64_HLEAcquire`, `_InterlockedExchangeAdd64_HLErelease`|x64|\<immintrin.h>|

## <a name="remarks"></a>Notes

Il existe plusieurs variantes de `_InterlockedExchangeAdd` qui varient selon les types de données qu’elles impliquent et l’utilisation d’une sémantique acquire ou release spécifique au processeur.

La fonction `_InterlockedExchangeAdd` opère sur les valeurs entières de 32 bits, `_InterlockedExchangeAdd8` sur les valeurs entières de 8 bits, `_InterlockedExchangeAdd16` sur les valeurs entières de 16 bits et `_InterlockedExchangeAdd64` sur les valeurs entières de 64 bits.

Sur les plateformes ARM, utilisez les fonctions intrinsèques avec des suffixes `_acq` et `_rel` si vous devez acquérir et libérer des éléments de la sémantique, comme le début et la fin d’une section critique. Les intrinsèques avec un `_nf` suffixe (« no cloture ») n’agissent pas comme une barrière de mémoire.

Sur les plateformes Intel qui prennent en charge les instructions HLE (Hardware Lock Elision), les fonctions intrinsèques avec les suffixes `_HLEAcquire` et `_HLERelease` comprennent une indication pour le processeur qui peut accélérer les performances en éliminant une étape d'écriture de verrou dans le matériel. Si ces fonctions intrinsèques sont appelées sur des plateformes qui ne prennent pas en charge HLE, l’indicateur est ignoré.

Ces routines sont disponibles seulement comme fonctions intrinsèques. Elles sont intrinsèques même lorsque [/OI](../build/reference/oi-generate-intrinsic-functions.md) ou [#pragma intrinsèque](../preprocessor/intrinsic.md) est utilisé. Il n’est pas possible d’utiliser [#pragma fonction](../preprocessor/function-c-cpp.md) sur ces fonctions intrinsèques.

## <a name="example"></a>Exemple

Pour obtenir un exemple d’utilisation de `_InterlockedExchangeAdd` , consultez [_InterlockedDecrement](../intrinsics/interlockeddecrement-intrinsic-functions.md).

**FIN spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Intrinsèques du compilateur](../intrinsics/compiler-intrinsics.md)\
[Mot](../cpp/keywords-cpp.md)\
[Conflits avec le compilateur x86](../build/x64-software-conventions.md#conflicts-with-the-x86-compiler)
