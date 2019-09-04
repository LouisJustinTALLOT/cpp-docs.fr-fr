---
title: _mm_stream_sd
ms.date: 09/02/2019
f1_keywords:
- _mm_stream_sd
helpviewer_keywords:
- _mm_stream_sd intrinsic
- movntsd instruction
ms.assetid: 2b4bea5e-e64e-45fa-9afc-88a2e4b82cfc
ms.openlocfilehash: 7f0c6457cc0806a0f1764300cffa1c9878b8a600
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/03/2019
ms.locfileid: "70217362"
---
# <a name="_mm_stream_sd"></a>_mm_stream_sd

**Section spécifique à Microsoft**

Écrit des données 64 bits dans un emplacement de mémoire sans polluer les caches.

## <a name="syntax"></a>Syntaxe

```C
void _mm_stream_sd(
   double * Dest,
   __m128d Source
);
```

### <a name="parameters"></a>Paramètres

*Dest*\
à Pointeur vers l’emplacement où les données sources seront écrites.

*Source*\
dans Valeur 128 bits contenant la `double` valeur à écrire dans ses 64 derniers bits inférieurs.

## <a name="return-value"></a>Valeur de retour

Aucune.

## <a name="requirements"></a>Configuration requise

|Intrinsèque|Architecture|
|---------------|------------------|
|`_mm_stream_sd`|SSE4a|

**Fichier d’en-tête** \<> Intro. h

## <a name="remarks"></a>Notes

L’intrinsèque génère l' `movntsd` instruction. Pour déterminer la prise en charge matérielle pour cette instruction `__cpuid` , appelez `InfoType=0x80000001` l’intrinsèque avec et vérifiez `CPUInfo[2] (ECX)`le bit 6 de. Ce bit est égal à 1 si le matériel prend en charge cette instruction, et 0 dans le cas contraire.

Si vous exécutez du code qui utilise `_mm_stream_sd` l’intrinsèque sur du matériel qui ne `movntsd` prend pas en charge l’instruction, les résultats sont imprévisibles.

## <a name="example"></a>Exemple

```cpp
// Compile this sample with: /EHsc
#include <iostream>
#include <intrin.h>
using namespace std;

int main()
{
    __m128d vals;
    double d[2];

    d[0] = -1.;
    d[1] = -2.;
    vals.m128d_f64[0] = 0.;
    vals.m128d_f64[1] = 1.;
    _mm_stream_sd(&d[1], vals);
    cout << "d[0] = " << d[0] << ", d[1] = " << d[1] << endl;
}
```

```Output
d[0] = -1, d[1] = 1
```

**FIN de la section spécifique à Microsoft**

Parties Copyright 2007 par Advanced Micro Devices, Inc. Tous droits réservés. Reproduit avec l’autorisation de Advanced Micro Devices, Inc.

## <a name="see-also"></a>Voir aussi

[_mm_stream_ss](../intrinsics/mm-stream-ss.md)\
[_mm_store_sd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_store_sd)\
[_mm_sfence](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_sfence)\
[Intrinsèques du compilateur](../intrinsics/compiler-intrinsics.md)
