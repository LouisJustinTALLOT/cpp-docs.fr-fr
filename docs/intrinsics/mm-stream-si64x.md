---
title: _mm_stream_si64x
ms.date: 09/02/2019
f1_keywords:
- _mm_stream_si64x
helpviewer_keywords:
- movnti instruction
- _mm_stream_si64x intrinsic
ms.assetid: 114c2cd0-085f-41aa-846e-87bdd56c9ee7
ms.openlocfilehash: f6ed0f2482ecbcdaa4d50034e0d08381768847a2
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/03/2019
ms.locfileid: "70221750"
---
# <a name="_mm_stream_si64x"></a>_mm_stream_si64x

**Section spécifique à Microsoft**

Génère l’instruction MOVNTI. Écrit les données dans la *source* dans un emplacement de mémoire spécifié par *destination*, sans polluer les caches.

## <a name="syntax"></a>Syntaxe

```C
void _mm_stream_si64x(
   __int64 * Destination,
   __int64 Source
);
```

### <a name="parameters"></a>Paramètres

*Destination*\
à Pointeur vers l’emplacement où écrire les données sources.

*Source*\
dans Données à écrire.

## <a name="requirements"></a>Configuration requise

|Intrinsèque|Architecture|
|---------------|------------------|
|`_mm_stream_si64x`|X64|

**Fichier d’en-tête** \<> Intro. h

## <a name="remarks"></a>Notes

Cette routine est disponible uniquement en tant qu'intrinsèque.

## <a name="example"></a>Exemple

```C
// _mm_stream_si64x.c
// processor: x64

#include <stdio.h>
#include <intrin.h>

#pragma intrinsic(_mm_stream_si64x)

int main()
{
    __int64 val = 0xFFFFFFFFFFFFI64;
    __int64 a[10];

    memset(a, 0, sizeof(a));
    _mm_stream_si64x(a+1, val);
    printf_s( "%I64x %I64x %I64x %I64x", a[0], a[1], a[2], a[3]);
}
```

```Output
0 ffffffffffff 0 0
```

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Intrinsèques du compilateur](../intrinsics/compiler-intrinsics.md)
