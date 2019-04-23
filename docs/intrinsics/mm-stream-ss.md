---
title: _mm_stream_ss
ms.date: 11/04/2016
f1_keywords:
- _mm_stream_ss
helpviewer_keywords:
- movntss instruction
- _mm_stream_ss intrinsic
ms.assetid: c53dffe9-0dfe-4063-85d3-e8987b870fce
ms.openlocfilehash: 76c6c848351df773b9857b2f83726b64db982d9f
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59031195"
---
# <a name="mmstreamss"></a>_mm_stream_ss

**Section spécifique à Microsoft**

Écrit les données de 32 bits dans un emplacement de mémoire sans polluer les caches.

## <a name="syntax"></a>Syntaxe

```
void _mm_stream_ss(
   float * Dest,
   __m128 Source
);
```

#### <a name="parameters"></a>Paramètres

*Dest*<br/>
[out] Pointeur vers l’emplacement où les données de la source sont écrites.

*Source*<br/>
[in] Un nombre de 128 bits qui contient le `float` valeur à écrire dans sa partie inférieure à 32 bits...

## <a name="return-value"></a>Valeur de retour

Aucun.

## <a name="requirements"></a>Configuration requise

|Intrinsèque|Architecture|
|---------------|------------------|
|`_mm_stream_ss`|SSE4a|

**Fichier d’en-tête** \<intrin.h >

## <a name="remarks"></a>Notes

Cet intrinsèque génère le `movntss` instruction. Pour déterminer la prise en charge matérielle pour cette instruction, appelez le `__cpuid` intrinsèque avec `InfoType=0x80000001` et vérifiez le bit 6 de `CPUInfo[2] (ECX)`. Ce bit est 1 lorsque l’instruction est pris en charge et 0 dans le cas contraire.

Si vous exécutez le code qui utilise le `_mm_stream_ss` intrinsèque sur du matériel qui ne prend pas en charge la `movntss` instruction, les résultats sont imprévisibles.

## <a name="example"></a>Exemple

```cpp
// Compile this sample with: /EHsc
#include <iostream>
#include <intrin.h>
using namespace std;

int main()
{
    __m128 vals;
    float f[4];

    f[0] = -1.;
    f[1] = -2.;
    f[2] = -3.;
    f[3] = -4.;
    vals.m128_f32[0] = 0.;
    vals.m128_f32[1] = 1.;
    vals.m128_f32[2] = 2.;
    vals.m128_f32[3] = 3.;
    _mm_stream_ss(&f[3], vals);
    cout << "f[0] = " << f[0] << ", f[1] = " << f[1] << endl;
    cout << "f[1] = " << f[1] << ", f[3] = " << f[3] << endl;
}
```

```Output
f[0] = -1, f[1] = -2
f[2] = -3, f[3] = 3
```

**FIN de la section spécifique à Microsoft**

Copyright 2007 par avancées Micro Devices, Inc. Tous droits réservés. Reproduit avec l’autorisation d’Advanced Micro Devices, Inc.

## <a name="see-also"></a>Voir aussi

[_mm_stream_sd](../intrinsics/mm-stream-sd.md)<br/>
[_mm_stream_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_stream_ps)<br/>
[_mm_store_ss](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_store_ss)<br/>
[_mm_sfence](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_sfence)<br/>
[compilateur, fonctions intrinsèques](../intrinsics/compiler-intrinsics.md)