---
title: _InterlockedExchangePointer fonctions intrinsèques
ms.date: 09/02/2019
f1_keywords:
- _InterlockedExchangePointer_cpp
- _InterlockedExchangePointer_rel
- _InterlockedExchangePointer_nf
- _InterlockedExchangePointer_HLERelease
- _InterlockedExchangePointer_acq
- _InterlockedExchangePointer
- _InterlockedExchangePointer_acq_cpp
- _InterlockedExchangePointer_HLEAcquire
helpviewer_keywords:
- _InterlockedExchangePointer_rel intrinsic
- _InterlockedExchangePointer_HLERelease intrinsic
- _InterlockedExchangePointer intrinsic
- _InterlockedExchangePointer_nf intrinsic
- _InterlockedExchangePointer_acq intrinsic
- _InterlockedExchangePointer_HLEAcquire intrinsic
- InterlockedExchangePointer_acq intrinsic
- InterlockedExchangePointer intrinsic
ms.assetid: 0eaca0b0-d79e-406b-892d-b3b462c50bbb
ms.openlocfilehash: 1402dcf5279658c1364b59a324d988129bc841d8
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/03/2019
ms.locfileid: "70217629"
---
# <a name="_interlockedexchangepointer-intrinsic-functions"></a>_InterlockedExchangePointer fonctions intrinsèques

**Section spécifique à Microsoft**

Effectue une opération d’échange atomique, qui copie l’adresse passée comme deuxième argument dans le premier argument et retourne l’adresse d’origine du premier.

## <a name="syntax"></a>Syntaxe

```C
void * _InterlockedExchangePointer(
   void * volatile * Target,
   void * Value
);
void * _InterlockedExchangePointer_acq(
   void * volatile * Target,
   void * Value
);
void * _InterlockedExchangePointer_rel(
   void * volatile * Target,
   void * Value
);
void * _InterlockedExchangePointer_nf(
   void * volatile * Target,
   void * Value
);
void * _InterlockedExchangePointer_HLEAcquire(
   void * volatile * Target,
   void * Value
);
void * _InterlockedExchangePointer_HLERelease(
   void * volatile * Target,
   void * Value
);
```

### <a name="parameters"></a>Paramètres

*Indicatif*\
[in, out] Pointeur vers le pointeur vers la valeur à échanger. La fonction définit la valeur sur *valeur* et retourne sa valeur précédente.

*Ajoutée*\
dans Valeur à échanger avec la valeur vers laquelle pointe la *cible*.

## <a name="return-value"></a>Valeur de retour

La fonction retourne la valeur initiale vers laquelle pointe la *cible*.

## <a name="requirements"></a>Configuration requise

|Intrinsèque|Architecture|Header|
|---------------|------------------|------------|
|`_InterlockedExchangePointer`|x86, ARM, x64, ARM64|\<intrin.h>|
|`_InterlockedExchangePointer_acq`, `_InterlockedExchangePointer_rel`, `_InterlockedExchangePointer_nf`|ARM, ARM64|\<intrin.h>|
|`_InterlockedExchangePointer_HLEAcquire`, `_InterlockedExchangePointer_HLERelease`|X64|\<immintrin.h>|

Sur l'architecture x86, `_InterlockedExchangePointer` est une macro qui appelle `_InterlockedExchange`.

## <a name="remarks"></a>Notes

Sur un système 64 bits, les paramètres sont 64 bits et doivent être alignés sur des limites de 64 bits. Dans le cas contraire, la fonction échoue. Sur un système 32 bits, les paramètres sont 32 bits et doivent être alignés sur les limites 32 bits. Pour plus d’informations, consultez [Aligner](../cpp/align-cpp.md).

Sur les plateformes ARM, utilisez les fonctions intrinsèques avec des suffixes `_acq` et `_rel` si vous devez acquérir et libérer des éléments de la sémantique, comme le début et la fin d’une section critique. L’intrinsèque avec un `_nf` suffixe («no barrière») n’agit pas comme une barrière de mémoire.

Sur les plateformes Intel qui prennent en charge les instructions HLE (Hardware Lock Elision), les fonctions intrinsèques avec les suffixes `_HLEAcquire` et `_HLERelease` comprennent une indication pour le processeur qui peut accélérer les performances en éliminant une étape d'écriture de verrou dans le matériel. Si ces fonctions intrinsèques sont appelées sur des plateformes qui ne prennent pas en charge HLE, l’indicateur est ignoré.

Ces routines sont disponibles seulement comme fonctions intrinsèques.

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Intrinsèques du compilateur](../intrinsics/compiler-intrinsics.md)\
[Conflits avec le compilateur x86](../build/x64-software-conventions.md#conflicts-with-the-x86-compiler)
