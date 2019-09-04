---
title: _mm_stream_ss
ms.date: 09/02/2019
f1_keywords:
- _mm_stream_ss
helpviewer_keywords:
- movntss instruction
- _mm_stream_ss intrinsic
ms.assetid: c53dffe9-0dfe-4063-85d3-e8987b870fce
ms.openlocfilehash: 005f4f697d64f6ea68b35dc32daf1217be463a2a
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/03/2019
ms.locfileid: "70217356"
---
# <a name="_mm_stream_ss"></a>_mm_stream_ss

**Section spécifique à Microsoft**

Écrit des données 32 bits dans un emplacement de mémoire sans polluer les caches.

## <a name="syntax"></a>Syntaxe

```C
void _mm_stream_ss(
   float * Destination,
   __m128 Source
);
```

### <a name="parameters"></a>Paramètres

*Destination*\
à Pointeur vers l’emplacement où les données sources sont écrites.

*Source*\
dans Nombre 128 bits qui contient la `float` valeur à écrire dans ses 32 derniers bits de poids fort.

## <a name="return-value"></a>Valeur de retour

Aucune.

## <a name="requirements"></a>Configuration requise

|Intrinsèque|Architecture|
|---------------|------------------|
|`_mm_stream_ss`|SSE4a|

**Fichier d’en-tête** \<> Intro. h

## <a name="remarks"></a>Notes

L’intrinsèque génère l' `movntss` instruction. Pour déterminer la prise en charge matérielle pour cette instruction `__cpuid` , appelez `InfoType=0x80000001` l’intrinsèque avec et vérifiez `CPUInfo[2] (ECX)`le bit 6 de. Ce bit est égal à 1 lorsque l’instruction est prise en charge et 0 dans le cas contraire.

Si vous exécutez du code qui utilise `_mm_stream_ss` l’intrinsèque sur du matériel qui ne `movntss` prend pas en charge l’instruction, les résultats sont imprévisibles.

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

Parties Copyright 2007 par Advanced Micro Devices, Inc. Tous droits réservés. Reproduit avec l’autorisation de Advanced Micro Devices, Inc.

## <a name="see-also"></a>Voir aussi

[_mm_stream_sd](../intrinsics/mm-stream-sd.md)\
[_mm_stream_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_stream_ps)\
[_mm_store_ss](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_store_ss)\
[_mm_sfence](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_sfence)\
[Intrinsèques du compilateur](../intrinsics/compiler-intrinsics.md)
