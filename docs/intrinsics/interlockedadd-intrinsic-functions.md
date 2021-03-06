---
description: 'En savoir plus sur : fonctions intrinsèques de _InterlockedAdd'
title: _InterlockedAdd fonctions intrinsèques
ms.date: 09/02/2019
f1_keywords:
- _InterlockedAdd64_acq_cpp
- _InterlockedAdd64_acq
- _InterlockedAdd_acq
- _InterlockedAdd_nf
- _InterlockedAdd64_rel
- _InterlockedAdd64
- _InterlockedAdd_cpp
- _InterlockedAdd_rel_cpp
- _InterlockedAdd_rel
- _InterlockedAdd64_rel_cpp
- _InterlockedAdd64_cpp
- _InterlockedAdd_acq_cpp
- _InterlockedAdd64_nf
- _InterlockedAdd
helpviewer_keywords:
- _InterlockedAdd_nf intrinsic
- _InterlockedAdd_rel intrinsic
- _InterlockedAdd intrinsic
- _InterlockedAdd64 intrinsic
- _InterlockedAdd64_acq intrinsic
- _InterlockedAdd64_nf intrinsic
- _InterlockedAdd_acq intrinsic
- _InterlockedAdd64_rel intrinsic
ms.assetid: 3d319603-ea9c-4fdd-ae61-e52430ccc3b1
ms.openlocfilehash: b467cc855e674a50899999c6e945321390735b00
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97336892"
---
# <a name="_interlockedadd-intrinsic-functions"></a>_InterlockedAdd fonctions intrinsèques

**Spécifique à Microsoft**

Ces fonctions effectuent un ajout atomique, ce qui garantit que l’opération se termine correctement lorsque plusieurs threads ont accès à une variable partagée.

## <a name="syntax"></a>Syntaxe

```C
long _InterlockedAdd(
   long volatile * Addend,
   long Value
);
long _InterlockedAdd_acq(
   long volatile * Addend,
   long Value
);
long _InterlockedAdd_nf(
   long volatile * Addend,
   long Value
);
long _InterlockedAdd_rel(
   long volatile * Addend,
   long Value
);
__int64 _InterlockedAdd64(
   __int64 volatile * Addend,
   __int64 Value
);
__int64 _InterlockedAdd64_acq(
   __int64 volatile * Addend,
   __int64 Value
);
__int64 _InterlockedAdd64_nf (
   __int64 volatile * Addend,
   __int64 Value
);
__int64 _InterlockedAdd64_rel(
   __int64 volatile * Addend,
   __int64 Value
);
```

### <a name="parameters"></a>Paramètres

*Addend*\
[in, out] Pointeur vers l’entier à ajouter à ; remplacé par le résultat de l’addition.

*Value*\
dans Valeur à ajouter.

## <a name="return-value"></a>Valeur retournée

Ces deux fonctions renvoient le résultat de l'addition.

## <a name="requirements"></a>Spécifications

|Intrinsic|Architecture|
|---------------|------------------|
|`_InterlockedAdd`|ARM, ARM64|
|`_InterlockedAdd_acq`|ARM, ARM64|
|`_InterlockedAdd_nf`|ARM, ARM64|
|`_InterlockedAdd_rel`|ARM, ARM64|
|`_InterlockedAdd64`|ARM, ARM64|
|`_InterlockedAdd64_acq`|ARM, ARM64|
|`_InterlockedAdd64_nf`|ARM, ARM64|
|`_InterlockedAdd64_rel`|ARM, ARM64|

**Fichier d’en-tête** \<intrin.h>

## <a name="remarks"></a>Notes

Les versions de ces fonctions avec le suffixe `_acq` ou `_rel` effectuent une addition verrouillée respectant la sémantique acquire ou release. L’acquisition de la *sémantique* signifie que le résultat de l’opération est rendu visible par tous les threads et processeurs avant les lectures et écritures de mémoire ultérieures. Elle est utile lors de l'entrée d'une section critique. La *sémantique Release* signifie que toutes les lectures et écritures en mémoire sont forcées à être rendues visibles à tous les threads et les processeurs avant que le résultat de l’opération soit rendu visible. Elle est utile quand vous quittez une section critique. Les intrinsèques avec un `_nf` suffixe (« no cloture ») n’agissent pas comme une barrière de mémoire.

Ces routines sont disponibles seulement comme fonctions intrinsèques.

## <a name="example-_interlockedadd"></a>Exemple : `_InterlockedAdd`

```cpp
// interlockedadd.cpp
// Compile with: /Oi /EHsc
// processor: ARM
#include <stdio.h>
#include <intrin.h>

#pragma intrinsic(_InterlockedAdd)

int main()
{
        long data1 = 0xFF00FF00;
        long data2 = 0x00FF0000;
        long retval;
        retval = _InterlockedAdd(&data1, data2);
        printf("0x%x 0x%x 0x%x", data1, data2, retval);
}
```

## <a name="output-_interlockedadd"></a>Sortie `_InterlockedAdd`

```Output
0xffffff00 0xff0000 0xffffff00
```

## <a name="example-_interlockedadd64"></a>Exemple : `_InterlockedAdd64`

```cpp
// interlockedadd64.cpp
// compile with: /Oi /EHsc
// processor: ARM
#include <iostream>
#include <intrin.h>
using namespace std;

#pragma intrinsic(_InterlockedAdd64)

int main()
{
        __int64 data1 = 0x0000FF0000000000;
        __int64 data2 = 0x00FF0000FFFFFFFF;
        __int64 retval;
        cout << hex << data1 << " + " << data2 << " = " ;
        retval = _InterlockedAdd64(&data1, data2);
        cout << data1 << endl;
        cout << "Return value: " << retval << endl;
}
```

## <a name="output-_interlockedadd64"></a>Sortie `_InterlockedAdd64`

```Output
ff0000000000 + ff0000ffffffff = ffff00ffffffff
Return value: ffff00ffffffff
```

**FIN spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Intrinsèques du compilateur](../intrinsics/compiler-intrinsics.md)\
[Conflits avec le compilateur x86](../build/x64-software-conventions.md#conflicts-with-the-x86-compiler)
