---
title: _InterlockedCompareExchange128 fonctions intrinsèques
ms.date: 09/02/2019
f1_keywords:
- _InterlockedCompareExchange128_cpp
- _InterlockedCompareExchange128
- _InterlockedCompareExchange128_acq
- _InterlockedCompareExchange128_nf
- _InterlockedCompareExchange128_np
- _InterlockedCompareExchange128_rel
helpviewer_keywords:
- cmpxchg16b instruction
- _InterlockedCompareExchange128 intrinsic
ms.assetid: f05918fc-716a-4f6d-b746-1456d6b96c56
ms.openlocfilehash: 525b0fd77323789eed05c47c944794ff389bfac5
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/03/2019
ms.locfileid: "70217686"
---
# <a name="_interlockedcompareexchange128-intrinsic-functions"></a>_InterlockedCompareExchange128 fonctions intrinsèques

**Section spécifique à Microsoft**

Effectue une comparaison et un échange interverrouillés 128 bits.

## <a name="syntax"></a>Syntaxe

```C
unsigned char _InterlockedCompareExchange128(
   __int64 volatile * Destination,
   __int64 ExchangeHigh,
   __int64 ExchangeLow,
   __int64 * ComparandResult
);
unsigned char _InterlockedCompareExchange128_acq(
   __int64 volatile * Destination,
   __int64 ExchangeHigh,
   __int64 ExchangeLow,
   __int64 * ComparandResult
);
unsigned char _InterlockedCompareExchange128_nf(
   __int64 volatile * Destination,
   __int64 ExchangeHigh,
   __int64 ExchangeLow,
   __int64 * ComparandResult
);
unsigned char _InterlockedCompareExchange128_np(
   __int64 volatile * Destination,
   __int64 ExchangeHigh,
   __int64 ExchangeLow,
   __int64 * ComparandResult
);
unsigned char _InterlockedCompareExchange128_rel(
   __int64 volatile * Destination,
   __int64 ExchangeHigh,
   __int64 ExchangeLow,
   __int64 * ComparandResult
);
```

### <a name="parameters"></a>Paramètres

*Destination*\
[in, out] Pointeur vers la destination, qui est un tableau d’entiers 2 64 bits considéré comme un champ de 128 bits. Les données de destination doivent être alignées sur 16 octets pour éviter une erreur de protection générale.

*ExchangeHigh*\
dans Entier 64 bits qui peut être échangé avec la partie haute de la destination.

*ExchangeLow*\
dans Entier 64 bits qui peut être échangé avec la partie inférieure de la destination.

*ComparandResult*\
[in, out] Pointeur vers un tableau d’entiers 2 64 bits (considéré comme un champ de 128 bits) à comparer avec la destination.  En sortie, ce tableau est remplacé par la valeur d’origine de la destination.

## <a name="return-value"></a>Valeur de retour

1 si la valeur de 128 bits comparand est égale à la valeur d’origine de la destination. `ExchangeHigh`et `ExchangeLow` remplacent la destination 128 bits.

0 si comparand n’est pas égal à la valeur d’origine de la destination. La valeur de la destination est inchangée et la valeur de comparand est remplacée par la valeur de la destination.

## <a name="requirements"></a>Configuration requise

|Intrinsèque|Architecture|
|---------------|------------------|
|`_InterlockedCompareExchange128`|x64, ARM64|
|`_InterlockedCompareExchange128_acq`, `_InterlockedCompareExchange128_nf`, `_InterlockedCompareExchange128_rel`|ARM64|
|`_InterlockedCompareExchange128_np`|X64|

**Fichier d’en-tête** \<> Intro. h

## <a name="remarks"></a>Notes

L' `_InterlockedCompareExchange128` intrinsèque génère l' `cmpxchg16b` instruction (avec le `lock` préfixe) pour effectuer une comparaison et un échange verrouillés 128 bits. Les versions antérieures du matériel AMD 64 bits ne prennent pas en charge cette instruction. Pour vérifier la prise en charge matérielle `cmpxchg16b` de l’instruction, `__cpuid` appelez l' `InfoType=0x00000001 (standard function 1)`intrinsèque avec. Le bit 13 `CPUInfo[2]` de (ECX) est 1 si l’instruction est prise en charge.

> [!NOTE]
> La valeur de `ComparandResult` est toujours remplacée. Après l' `lock` instruction, cette intrinsèque copie immédiatement la valeur initiale de `Destination` dans `ComparandResult`. Pour cette raison, `ComparandResult` et `Destination` doit pointer vers des emplacements de mémoire distincts pour éviter un comportement inattendu.

Bien que vous puissiez `_InterlockedCompareExchange128` utiliser pour la synchronisation de threads de bas niveau, vous n’avez pas besoin de synchroniser plus de 128 bits si vous pouvez utiliser `_InterlockedCompareExchange` des fonctions de synchronisation plus petites (telles que les autres intrinsèques) à la place. Utilisez `_InterlockedCompareExchange128` si vous souhaitez un accès atomique à une valeur 128 bits dans la mémoire.

Si vous exécutez du code qui utilise l’intrinsèque sur du matériel qui ne `cmpxchg16b` prend pas en charge l’instruction, les résultats sont imprévisibles.

Sur les plateformes ARM, utilisez les intrinsèques avec les suffixes `_acq` et `_rel` pour la sémantique Acquire et Release, comme au début et à la fin d'une section critique. Les intrinsèques ARM avec un `_nf` suffixe («no cloture») n’agissent pas comme une barrière de mémoire.

Les fonctions intrinsèques avec un suffixe `_np` (pour « no prefetch », « pas de prérécupération ») empêchent l'insertion par le compilateur d'une possible opération de prérécupération.

Cette routine est disponible uniquement comme intrinsèque.

## <a name="example"></a>Exemple

Cet exemple utilise `_InterlockedCompareExchange128` pour remplacer le mot de poids fort d’un tableau d’entiers 2 64 bits par la somme de ses mots hauts et bas et pour incrémenter le mot de poids faible. L’accès au `BigInt.Int` tableau est atomique, mais cet exemple utilise un thread unique et ignore le verrouillage pour plus de simplicité.

```cpp
// cmpxchg16b.c
// processor: x64
// compile with: /EHsc /O2
#include <stdio.h>
#include <intrin.h>

typedef struct _LARGE_INTEGER_128 {
    __int64 Int[2];
} LARGE_INTEGER_128, *PLARGE_INTEGER_128;

volatile LARGE_INTEGER_128 BigInt;

// This AtomicOp() function atomically performs:
//   BigInt.Int[1] += BigInt.Int[0]
//   BigInt.Int[0] += 1
void AtomicOp ()
{
    LARGE_INTEGER_128 Comparand;
    Comparand.Int[0] = BigInt.Int[0];
    Comparand.Int[1] = BigInt.Int[1];
    do {
        ; // nothing
    } while (_InterlockedCompareExchange128(BigInt.Int,
                                            Comparand.Int[0] + Comparand.Int[1],
                                            Comparand.Int[0] + 1,
                                            Comparand.Int) == 0);
}

// In a real application, several threads contend for the value
// of BigInt.
// Here we focus on the compare and exchange for simplicity.
int main(void)
{
   BigInt.Int[1] = 23;
   BigInt.Int[0] = 11;
   AtomicOp();
   printf("BigInt.Int[1] = %d, BigInt.Int[0] = %d\n",
      BigInt.Int[1],BigInt.Int[0]);
}
```

```Output
BigInt.Int[1] = 34, BigInt.Int[0] = 12
```

**FIN de la section spécifique à Microsoft**


## <a name="see-also"></a>Voir aussi

[Intrinsèques du compilateur](../intrinsics/compiler-intrinsics.md)\
[_InterlockedCompareExchange fonctions intrinsèques](../intrinsics/interlockedcompareexchange-intrinsic-functions.md)\
[Conflits avec le compilateur x86](../build/x64-software-conventions.md#conflicts-with-the-x86-compiler)
