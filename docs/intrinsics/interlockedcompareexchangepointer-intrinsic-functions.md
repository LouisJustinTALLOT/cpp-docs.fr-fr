---
description: 'En savoir plus sur : fonctions intrinsèques de _InterlockedCompareExchangePointer'
title: _InterlockedCompareExchangePointer fonctions intrinsèques
ms.date: 09/02/2019
f1_keywords:
- _InterlockedCompareExchangePointer_HLERelease
- _InterlockedCompareExchangePointer_rel
- _InterlockedCompareExchangePointer_acq_cpp
- _InterlockedCompareExchangePointer
- _InterlockedCompareExchangePointer_cpp
- _InterlockedCompareExchangePointer_np
- _InterlockedCompareExchangePointer_rel_cpp
- _InterlockedCompareExchangePointer_HLEAcquire
- _InterlockedCompareExchangePointer_acq
- _InterlockedCompareExchangePointer_nf
helpviewer_keywords:
- InterlockedCompareExchangePointer_acq intrinsic
- _InterlockedCompareExchangePointer_rel intrinsic
- _InterlockedCompareExchangePointer_acq intrinsic
- InterlockedCompareExchangePointer_rel intrinsic
- InterlockedCompareExchangePointer intrinsic
- _InterlockedCompareExchangePointer_HLERelease intrinsic
- _InterlockedCompareExchangePointer_HLEAcquire intrinsic
- _InterlockedCompareExchangePointer intrinsic
- _InterlockedCompareExchangePointer_nf intrinsic
- _InterlockedCompareExchangePointer_np intrinsic
ms.assetid: 97fde59d-2bf9-42aa-a0fe-a5b6befdd44b
ms.openlocfilehash: cd8d42c6a7036a6c779af6fc32a7176b7e48a73c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97168057"
---
# <a name="_interlockedcompareexchangepointer-intrinsic-functions"></a>_InterlockedCompareExchangePointer fonctions intrinsèques

**Spécifique à Microsoft**

Effectue une opération atomique qui stocke l'adresse `Exchange` dans l'adresse `Destination` si les adresses `Comparand` et `Destination` sont égales.

## <a name="syntax"></a>Syntaxe

```C
void * _InterlockedCompareExchangePointer (
   void * volatile * Destination,
   void * Exchange,
   void * Comparand
);
void * _InterlockedCompareExchangePointer_acq (
   void * volatile * Destination,
   void * Exchange,
   void * Comparand
);
void * _InterlockedCompareExchangePointer_HLEAcquire (
   void * volatile * Destination,
   void * Exchange,
   void * Comparand
);
void * _InterlockedCompareExchangePointer_HLERelease (
   void * volatile * Destination,
   void * Exchange,
   void * Comparand
);
void * _InterlockedCompareExchangePointer_nf (
   void * volatile * Destination,
   void * Exchange,
   void * Comparand
);
void * _InterlockedCompareExchangePointer_np (
   void * volatile * Destination,
   void * Exchange,
   void * Comparand
);
long _InterlockedCompareExchangePointer_rel (
   void * volatile * Destination,
   void * Exchange,
   void * Comparand
);
```

### <a name="parameters"></a>Paramètres

*Destination*\
[in, out] Pointeur vers un pointeur vers la valeur de destination. Le signe est ignoré.

*Exchange*\
dans Pointeur Exchange. Le signe est ignoré.

*Comparateur*\
dans Pointeur à comparer à la destination. Le signe est ignoré.

## <a name="return-value"></a>Valeur retournée

La valeur de retour est la valeur initiale de la destination.

## <a name="requirements"></a>Spécifications

|Intrinsic|Architecture|En-tête|
|---------------|------------------|------------|
|`_InterlockedCompareExchangePointer`|x86, ARM, x64, ARM64|\<intrin.h>|
|`_InterlockedCompareExchangePointer_acq`, `_InterlockedCompareExchangePointer_nf`, `_InterlockedCompareExchangePointer_rel`|ARM, ARM64|\<iiintrin.h>|
|`_InterlockedCompareExchangePointer_HLEAcquire`, `_InterlockedCompareExchangePointer_HLERelease`|x86, x64|\<immintrin.h>|

## <a name="remarks"></a>Notes

`_InterlockedCompareExchangePointer` effectue une comparaison atomique de l'adresse `Destination` à l'adresse `Comparand`. Si l'adresse `Destination` est égale à l'adresse `Comparand`, l'adresse `Exchange` est stockée dans l'adresse spécifiée par `Destination`. Dans le cas contraire, aucune opération n'est effectuée.

`_InterlockedCompareExchangePointer` fournit la prise en charge intrinsèque du compilateur pour la fonction Win32 SDK Windows [InterlockedCompareExchangePointer](/windows-hardware/drivers/ddi/content/wdm/nf-wdm-interlockedcompareexchangepointer) .

Pour obtenir un exemple d’utilisation de `_InterlockedCompareExchangePointer` , consultez [_InterlockedDecrement](../intrinsics/interlockeddecrement-intrinsic-functions.md).

Sur les plateformes ARM, utilisez les fonctions intrinsèques avec des suffixes `_acq` et `_rel` si vous devez acquérir et libérer des éléments de la sémantique, comme le début et la fin d’une section critique. Les intrinsèques ARM avec un `_nf` suffixe (« no cloture ») n’agissent pas comme une barrière de mémoire.

Les fonctions intrinsèques avec un suffixe `_np` (pour « no prefetch », « pas de prérécupération ») empêchent l'insertion par le compilateur d'une possible opération de prérécupération.

Sur les plateformes Intel qui prennent en charge les instructions HLE (Hardware Lock Elision), les fonctions intrinsèques avec les suffixes `_HLEAcquire` et `_HLERelease` comprennent une indication pour le processeur qui peut accélérer les performances en éliminant une étape d'écriture de verrou dans le matériel. Si ces fonctions intrinsèques sont appelées sur des plateformes qui ne prennent pas en charge HLE, l’indicateur est ignoré.

Ces routines sont disponibles seulement comme fonctions intrinsèques.

**FIN spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Intrinsèques du compilateur](../intrinsics/compiler-intrinsics.md)\
[Mots clés](../cpp/keywords-cpp.md)
