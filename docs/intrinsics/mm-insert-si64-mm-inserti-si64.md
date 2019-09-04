---
title: _mm_insert_si64, _mm_inserti_si64
ms.date: 09/02/2019
f1_keywords:
- _mm_inserti_si64
- _mm_insert_si64
helpviewer_keywords:
- insertq instruction
- _mm_insert_si64 intrinsic
- _mm_inserti_si64 intrinsic
ms.assetid: 897a4b36-8b08-4b00-a18f-7850f5732d7d
ms.openlocfilehash: 08469ad8049df2a07f0e66d650c1ca3118f8b980
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/03/2019
ms.locfileid: "70221773"
---
# <a name="_mm_insert_si64-_mm_inserti_si64"></a>_mm_insert_si64, _mm_inserti_si64

**Section spécifique à Microsoft**

Génère l' `insertq` instruction pour insérer des bits à partir de son deuxième opérande dans son premier opérande.

## <a name="syntax"></a>Syntaxe

```C
__m128i _mm_insert_si64(
   __m128i Source1,
   __m128i Source2
);
__m128i _mm_inserti_si64(
   __m128i Source1,
   __m128i Source2
   int Length,
   int Index
);
```

### <a name="parameters"></a>Paramètres

*Source1*\
dans Champ de 128 bits qui contient des données d’entrée dans les 64 bits inférieurs, dans lequel un champ sera inséré.

*Source2*\
dans Champ de 128 bits qui contient les données à insérer dans ses bits inférieurs.  Pour `_mm_insert_si64`, contient également un descripteur de champ dans ses bits élevés.

*Base*\
dans Constante entière qui spécifie la longueur du champ à insérer.

*Évaluer*\
dans Constante entière qui spécifie l’index du bit le moins significatif du champ dans lequel les données seront insérées.

## <a name="return-value"></a>Valeur de retour

Un champ de 128 bits, dont les 64 inférieurs contiennent les 64 bits de poids faible d’origine de *Source1*, le champ de bits spécifié étant remplacé par les bits de poids faible de *source2*. Les 64 bits supérieurs de la valeur de retour ne sont pas définis.

## <a name="requirements"></a>Configuration requise

|Intrinsèque|Architecture|
|---------------|------------------|
|`_mm_insert_si64`|SSE4a|
|`_mm_inserti_si64`|SSE4a|

**Fichier d’en-tête** \<> Intro. h

## <a name="remarks"></a>Notes

Ces fonctions intrinsèques génèrent l' `insertq` instruction pour insérer des bits de *source2* dans *Source1*. Il existe deux versions: `_mm_inserti_si64`, est la version immédiate et `_mm_insert_si64` est la version non immédiate. Chaque version extrait un champ de bits d’une longueur donnée de source2 et l’insère dans source1.  Les bits extraits sont les bits les moins significatifs de source2.  Le champ source1 dans lequel ces bits seront insérés est défini par la longueur et l’index de son bit le moins significatif.  Les valeurs de la longueur et de l’index sont prises en mod 64, donc les deux-1 et 127 sont interprétées comme 63. Si la somme de l’index binaire (réduit) et de la longueur de champ (réduite) est supérieure à 64, les résultats ne sont pas définis. La valeur zéro pour la longueur du champ est interprétée comme 64. Si la longueur de champ et l’index de bits sont tous deux nuls, bits 63:0 de *source2* sont insérés dans *Source1*. Si la longueur du champ est égale à zéro, mais que l’index binaire est différent de zéro, les résultats ne sont pas définis.

Dans un appel à _mm_insert_si64, la longueur de champ est contenue dans bits 77:72 de source2 et l’index dans bits 69:64.

Si vous appelez `_mm_inserti_si64` avec des arguments que le compilateur ne peut pas déterminer comme constantes entières, le compilateur génère du code pour empaqueter ces valeurs dans `_mm_insert_si64`un registre XMM et appeler.

Pour déterminer la prise en charge `insertq` matérielle de l’instruction `__cpuid` , appelez `InfoType=0x80000001` l’intrinsèque avec et vérifiez `CPUInfo[2] (ECX)`le bit 6 de. Ce bit est égal à 1 si l’instruction est prise en charge et 0 dans le cas contraire. Si vous exécutez du code qui utilise l’intrinsèque sur du matériel qui ne `insertq` prend pas en charge l’instruction, les résultats sont imprévisibles.

## <a name="example"></a>Exemple

```cpp
// Compile this sample with: /EHsc
#include <iostream>
#include <intrin.h>
using namespace std;

union {
    __m128i m;
    unsigned __int64 ui64[2];
} source1, source2, source3, result1, result2, result3;

int
main()
{

    __int64 mask;

    source1.ui64[0] = 0xffffffffffffffffll;
    source2.ui64[0] = 0xfedcba9876543210ll;
    source2.ui64[1] = 0xc10;
    source3.ui64[0] = source2.ui64[0];

    result1.m = _mm_insert_si64 (source1.m, source2.m);
    result2.m = _mm_inserti_si64(source1.m, source3.m, 16, 12);
    mask = 0xffff << 12;
    mask = ~mask;
    result3.ui64[0] = (source1.ui64[0] & mask) |
                      ((source2.ui64[0] & 0xffff) << 12);

    cout << hex << "result1 = 0x" << result1.ui64[0] << endl;
    cout << "result2 = 0x" << result2.ui64[0] << endl;
    cout << "result3 = 0x" << result3.ui64[0] << endl;

}
```

```Output
result1 = 0xfffffffff3210fff
result2 = 0xfffffffff3210fff
result3 = 0xfffffffff3210fff
```

**FIN de la section spécifique à Microsoft**

Parties Copyright 2007 par Advanced Micro Devices, Inc. Tous droits réservés. Reproduit avec l’autorisation de Advanced Micro Devices, Inc.

## <a name="see-also"></a>Voir aussi

[_mm_extract_si64, _mm_extracti_si64](../intrinsics/mm-extract-si64-mm-extracti-si64.md)\
[Intrinsèques du compilateur](../intrinsics/compiler-intrinsics.md)
