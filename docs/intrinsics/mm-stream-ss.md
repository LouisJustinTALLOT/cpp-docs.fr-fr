---
description: 'En savoir plus sur : _mm_stream_ss'
title: _mm_stream_ss
ms.date: 09/02/2019
f1_keywords:
- _mm_stream_ss
helpviewer_keywords:
- movntss instruction
- _mm_stream_ss intrinsic
ms.assetid: c53dffe9-0dfe-4063-85d3-e8987b870fce
ms.openlocfilehash: 3af79ee38c09f08ab8e1e5300800846c866972a3
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97133205"
---
# <a name="_mm_stream_ss"></a>_mm_stream_ss

**Spécifique à Microsoft**

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

*Code*\
dans Nombre 128 bits qui contient la **`float`** valeur à écrire dans ses 32 derniers bits de poids fort.

## <a name="return-value"></a>Valeur retournée

Aucun.

## <a name="requirements"></a>Spécifications

|Intrinsic|Architecture|
|---------------|------------------|
|`_mm_stream_ss`|SSE4a|

**Fichier d’en-tête** \<intrin.h>

## <a name="remarks"></a>Notes

L’intrinsèque génère l' `movntss` instruction. Pour déterminer la prise en charge matérielle pour cette instruction, appelez l' `__cpuid` intrinsèque avec `InfoType=0x80000001` et vérifiez le bit 6 de `CPUInfo[2] (ECX)` . Ce bit est égal à 1 lorsque l’instruction est prise en charge et 0 dans le cas contraire.

Si vous exécutez du code qui utilise l' `_mm_stream_ss` intrinsèque sur du matériel qui ne prend pas en charge l' `movntss` instruction, les résultats sont imprévisibles.

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

**FIN spécifique à Microsoft**

Parties Copyright 2007 par Advanced Micro Devices, Inc. Tous droits réservés. Reproduit avec l’autorisation de Advanced Micro Devices, Inc.

## <a name="see-also"></a>Voir aussi

[_mm_stream_sd](../intrinsics/mm-stream-sd.md)\
[_mm_stream_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_stream_ps)\
[_mm_store_ss](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_store_ss)\
[_mm_sfence](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_sfence)\
[Intrinsèques du compilateur](../intrinsics/compiler-intrinsics.md)
