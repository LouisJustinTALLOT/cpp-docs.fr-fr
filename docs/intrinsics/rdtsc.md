---
title: __rdtsc
ms.date: 11/04/2016
f1_keywords:
- __rdtsc
helpviewer_keywords:
- __rdtsc intrinsic
- rdtsc instruction
- Read Time Stamp Counter instruction
ms.assetid: e31d0e51-c9bb-42ca-bbe9-a81ffe662387
ms.openlocfilehash: 6f30be3340ae1be237bb2f8a008a8cb60c7351f0
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62396572"
---
# <a name="rdtsc"></a>__rdtsc

**Section spécifique à Microsoft**

Génère le `rdtsc` instruction, qui retourne l’horodatage du processeur. L’horodatage de processeur enregistre le nombre de cycles d’horloge depuis la dernière réinitialisation.

## <a name="syntax"></a>Syntaxe

```
unsigned __int64 __rdtsc();
```

## <a name="return-value"></a>Valeur de retour

Entier non signé 64 bits représentant le nombre de cycles.

## <a name="requirements"></a>Configuration requise

|Intrinsèque|Architecture|
|---------------|------------------|
|`__rdtsc`|x86, x64|

**Fichier d’en-tête** \<intrin.h >

## <a name="remarks"></a>Notes

Cette routine est disponible uniquement comme intrinsèque.

L’interprétation de la valeur TSC dans cette génération de matériel diffère de celui des versions précédentes de x64. Consultez les manuels de matériel pour plus d’informations.

## <a name="example"></a>Exemple

```
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

[compilateur, fonctions intrinsèques](../intrinsics/compiler-intrinsics.md)