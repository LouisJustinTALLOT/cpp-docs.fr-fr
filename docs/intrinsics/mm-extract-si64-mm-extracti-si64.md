---
description: 'En savoir plus sur : _mm_extract_si64, _mm_extracti_si64'
title: _mm_extract_si64, _mm_extracti_si64
ms.date: 09/02/2019
f1_keywords:
- _mm_extracti_si64
- _mm_extract_si64
helpviewer_keywords:
- extrq instruction
- _mm_extracti_si64 intrinsic
- _mm_extract_si64 intrinsic
ms.assetid: 459fdd72-cc54-4ee5-bbd5-d2c6067a88e7
ms.openlocfilehash: 39a07c7310727de8d752c060c3d38481469ff1a7
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97322865"
---
# <a name="_mm_extract_si64-_mm_extracti_si64"></a>_mm_extract_si64, _mm_extracti_si64

**Spécifique à Microsoft**

Génère l' `extrq` instruction pour extraire les bits spécifiés à partir des 64 bits de poids faible de son premier argument.

## <a name="syntax"></a>Syntaxe

```C
__m128i _mm_extract_si64(
   __m128i Source,
   __m128i Descriptor
);
__m128i _mm_extracti_si64(
   __m128i Source,
   int Length,
   int Index
);
```

### <a name="parameters"></a>Paramètres

*Code*\
dans Champ de 128 bits avec données d’entrée dans ses 64 bits inférieurs.

*Description*\
dans Champ de 128 bits qui décrit le champ de bits à extraire.

*Base*\
dans Entier qui spécifie la longueur du champ à extraire.

*Index*\
dans Entier qui spécifie l’index du champ à extraire

## <a name="return-value"></a>Valeur retournée

Champ de 128 bits avec le champ extrait dans ses bits les moins significatifs.

## <a name="requirements"></a>Spécifications

|Intrinsic|Architecture|
|---------------|------------------|
|`_mm_extract_si64`|SSE4a|
|`_mm_extracti_si64`|SSE4a|

**Fichier d’en-tête** \<intrin.h>

## <a name="remarks"></a>Notes

Ces fonctions intrinsèques génèrent l' `extrq` instruction pour extraire les bits de la *source*. Il existe deux versions : `_mm_extracti_si64` est la version immédiate et `_mm_extract_si64` est la version non immédiate. Chaque version extrait de la *source* un champ de bits défini par sa longueur et l’index de son bit le moins significatif. Les valeurs de la longueur et de l’index sont prises en mod 64, donc les deux-1 et 127 sont interprétées comme 63. Si la somme de l’index (réduit) et de la longueur de champ (réduite) est supérieure à 64, les résultats ne sont pas définis. La valeur zéro pour la longueur du champ est interprétée comme 64. Si la longueur de champ et l’index de bits sont tous deux nuls, bits 63:0 de la *source* sont extraits. Si la longueur du champ est égale à zéro, mais que l’index binaire est différent de zéro, les résultats ne sont pas définis.

Dans un appel à `_mm_extract_si64` , le *descripteur* contient l’index en bits 13:8 et la longueur de champ des données à extraire dans bits 5:0.

Si vous appelez `_mm_extracti_si64` avec des arguments que le compilateur ne peut pas déterminer comme constantes entières, le compilateur génère du code pour empaqueter ces valeurs dans un registre XMM (*descripteur*) et pour appeler `_mm_extract_si64` .

Pour déterminer la prise en charge matérielle de l' `extrq` instruction, appelez l' `__cpuid` intrinsèque avec `InfoType=0x80000001` et vérifiez le bit 6 de `CPUInfo[2] (ECX)` . Ce bit aura la valeur 1 si l’instruction est prise en charge, et 0 dans le cas contraire. Si vous exécutez du code qui utilise ce matériel intrinsèque qui ne prend pas en charge l' `extrq` instruction, les résultats sont imprévisibles.

## <a name="example"></a>Exemple

```cpp
// Compile this sample with: /EHsc
#include <iostream>
#include <intrin.h>
using namespace std;

union {
    __m128i m;
    unsigned __int64 ui64[2];
} source, descriptor, result1, result2, result3;

int
main()
{
    source.ui64[0] =     0xfedcba9876543210ll;
    descriptor.ui64[0] = 0x0000000000000b1bll;

    result1.m = _mm_extract_si64 (source.m, descriptor.m);
    result2.m = _mm_extracti_si64(source.m, 27, 11);
    result3.ui64[0] = (source.ui64[0] >> 11) & 0x7ffffff;

    cout << hex << "result1 = 0x" << result1.ui64[0] << endl;
    cout << "result2 = 0x" << result2.ui64[0] << endl;
    cout << "result3 = 0x" << result3.ui64[0] << endl;
}
```

```Output
result1 = 0x30eca86
result2 = 0x30eca86
result3 = 0x30eca86
```

**FIN spécifique à Microsoft**

Parties Copyright 2007 par Advanced Micro Devices, Inc. Tous droits réservés. Reproduit avec l’autorisation de Advanced Micro Devices, Inc.

## <a name="see-also"></a>Voir aussi

[_mm_insert_si64, _mm_inserti_si64](../intrinsics/mm-insert-si64-mm-inserti-si64.md)\
[Intrinsèques du compilateur](../intrinsics/compiler-intrinsics.md)
