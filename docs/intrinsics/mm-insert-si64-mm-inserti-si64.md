---
title: _mm_insert_si64, _mm_inserti_si64 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- _mm_inserti_si64
- _mm_insert_si64
dev_langs:
- C++
helpviewer_keywords:
- insertq instruction
- _mm_insert_si64 intrinsic
- _mm_inserti_si64 intrinsic
ms.assetid: 897a4b36-8b08-4b00-a18f-7850f5732d7d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f859b461a2072afabbe48126eba94e0a3ed470a3
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46403862"
---
# <a name="mminsertsi64-mminsertisi64"></a>_mm_insert_si64, _mm_inserti_si64

**Section spécifique à Microsoft**

Génère le `insertq` instruction pour insérer des bits à partir de son second opérande dans son premier opérande.

## <a name="syntax"></a>Syntaxe

```
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

#### <a name="parameters"></a>Paramètres

*Source1*<br/>
[in] Un champ de 128 bits avec des données d’entrée dans son 64 bits inférieurs dans lequel un champ sera inséré.

*Source2*<br/>
[in] Un champ de 128 bits avec les données à insérer dans ses bits de poids faibles.  Pour `_mm_insert_si64`, contient également un descripteur de champ dans ses bits de poids fort.

*Longueur*<br/>
[in] Une constante entière qui spécifie la longueur du champ à insérer.

*Index*<br/>
[in] Une constante entière qui spécifie l’index du bit moins significatif du champ dans lequel les données seront insérées.

## <a name="return-value"></a>Valeur de retour

Un champ de 128 bits dont 64 bits inférieurs contiennent d’origine 64 bits de poids faibles de `Source1` avec le champ de bits spécifié remplacé par les bits de poids faibles `Source2`. Les 64 bits supérieures de la valeur de retour ne sont pas définis.

## <a name="requirements"></a>Configuration requise

|Intrinsèque|Architecture|
|---------------|------------------|
|`_mm_insert_si64`|SSE4a|
|`_mm_inserti_si64`|SSE4a|

**Fichier d’en-tête** \<intrin.h >

## <a name="remarks"></a>Notes

Cet intrinsèque génère le `insertq` instruction pour insérer des bits de `Source2` dans `Source1`. Il existe deux versions de cette intrinsèques : `_mm_inserti_si64`, est la version immédiate, et `_mm_insert_si64` est celui non immédiat.  Chaque version extrait un champ de bits d’une longueur donnée Source2 et l’insère dans Source1.  Les extraits sont les bits les moins significatifs de Source2.  Le Source1 de champ dans lequel ces bits seront insérés est défini par la longueur et l’index de son bit le moins significatif.  Les valeurs de la longueur et les index sont effectuées mod 64, par conséquent, -1 et 127 sont interprétés en tant que 63. Si la somme des index de bits (réduit) et la longueur de champ (réduit) est supérieure à 64, les résultats sont indéfinis. Une valeur égale à zéro pour la longueur de champ est interprétée en tant que 64.  Si l’index de longueur et les bits du champ est les deux zéro, 63:0 de bits de `Source2` sont insérées dans `Source1`.  Si la longueur de champ est égal à zéro, mais l’index de bits est différente de zéro, les résultats sont indéfinis.

Dans un appel à _mm_insert_si64, la longueur de champ est contenue dans 77:72 de bits de Source2 et l’index dans 69:64 de bits.

Si vous appelez `_mm_inserti_si64` avec les arguments que le compilateur ne peut pas déterminer être des constantes entières, le compilateur génère du code pour regrouper ces valeurs dans un registre XMM et appeler `_mm_insert_si64`.

Pour déterminer la prise en charge matérielle pour le `insertq` appel le `__cpuid` intrinsèque avec `InfoType=0x80000001` et vérifiez le bit 6 de `CPUInfo[2] (ECX)`. Ce bit sera égale à 1 si l’instruction est pris en charge et 0 dans le cas contraire. Si vous exécutez le code qui utilise cet intrinsèque sur du matériel qui ne prend pas en charge la `insertq` instruction, les résultats sont imprévisibles.

## <a name="example"></a>Exemple

```
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

Copyright 2007 par avancées Micro Devices, Inc. Tous droits réservés. Reproduit avec l’autorisation d’Advanced Micro Devices, Inc.

## <a name="see-also"></a>Voir aussi

[_mm_extract_si64, _mm_extracti_si64](../intrinsics/mm-extract-si64-mm-extracti-si64.md)<br/>
[compilateur, fonctions intrinsèques](../intrinsics/compiler-intrinsics.md)