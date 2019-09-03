---
title: __rdtsc
ms.date: 09/02/2019
f1_keywords:
- __rdtsc
helpviewer_keywords:
- __rdtsc intrinsic
- rdtsc instruction
- Read Time Stamp Counter instruction
ms.assetid: e31d0e51-c9bb-42ca-bbe9-a81ffe662387
ms.openlocfilehash: 837b68ca6ac63587cd43a7e8828777221c677e3c
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/03/2019
ms.locfileid: "70217149"
---
# <a name="__rdtsc"></a>__rdtsc

**Section spécifique à Microsoft**

Génère l' `rdtsc` instruction, qui retourne l’horodatage du processeur. Le datage du processeur enregistre le nombre de cycles d’horloge depuis la dernière réinitialisation.

## <a name="syntax"></a>Syntaxe

```C
unsigned __int64 __rdtsc();
```

## <a name="return-value"></a>Valeur de retour

Entier non signé 64 bits représentant un nombre de cycles.

## <a name="requirements"></a>Configuration requise

|Intrinsèque|Architecture|
|---------------|------------------|
|`__rdtsc`|x86, x64|

**Fichier d’en-tête** \<> Intro. h

## <a name="remarks"></a>Notes

Cette routine est disponible uniquement comme intrinsèque.

L’interprétation de la valeur TSC dans les générations ultérieures de matériel diffère de celle des versions antérieures de x64. Pour plus d’informations, consultez les manuels du matériel.

## <a name="example"></a>Exemples

```cpp
// rdtsc.cpp
// processor: x86, x64
#include <stdio.h>
#include <intrin.h>

#pragma intrinsic(__rdtsc)

int main()
{
    unsigned __int64 i;
    i = __rdtsc();
    printf_s("%I64d ticks\n", i);
}
```

```Output
3363423610155519 ticks
```

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Intrinsèques du compilateur](../intrinsics/compiler-intrinsics.md)
