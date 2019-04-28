---
title: _mm_extract_si64, _mm_extracti_si64
ms.date: 11/04/2016
f1_keywords:
- _mm_extracti_si64
- _mm_extract_si64
helpviewer_keywords:
- extrq instruction
- _mm_extracti_si64 intrinsic
- _mm_extract_si64 intrinsic
ms.assetid: 459fdd72-cc54-4ee5-bbd5-d2c6067a88e7
ms.openlocfilehash: e77ca5589ed50a4199921603afec1d9888c6cca5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62263696"
---
# <a name="mmextractsi64-mmextractisi64"></a>_mm_extract_si64, _mm_extracti_si64

**Section spécifique à Microsoft**

Génère le `extrq` instruction d’extraction de bits spécifiée à partir de 64 bits de poids faibles de son premier argument.

## <a name="syntax"></a>Syntaxe

```
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

#### <a name="parameters"></a>Paramètres

*Source*<br/>
[in] Un champ de 128 bits avec des données d’entrée dans son 64 bits de poids faible.

*Descriptor*<br/>
[in] Un champ de 128 bits qui décrit le champ de bits pour extraire.

*Longueur*<br/>
[in] Entier qui spécifie la longueur du champ à extraire.

*Index*<br/>
[in] Entier qui spécifie l’index du champ à extraire

## <a name="return-value"></a>Valeur de retour

Un champ de 128 bits avec le champ extrait dans ses bits les moins significatifs.

## <a name="requirements"></a>Configuration requise

|Intrinsèque|Architecture|
|---------------|------------------|
|`_mm_extract_si64`|SSE4a|
|`_mm_extracti_si64`|SSE4a|

**Fichier d’en-tête** \<intrin.h >

## <a name="remarks"></a>Notes

Cet intrinsèque génère le `extrq` instruction d’extraction des bits de `Source`. Il existe deux versions de cette intrinsèques : `_mm_extracti_si64` est la version immédiate, et `_mm_extract_si64` est celui non immédiat.  L’extrait de chaque version `Source` un champ de bits défini par sa longueur et l’index de son bit le moins significatif. Les valeurs de la longueur et les index sont effectuées mod 64, par conséquent, -1 et 127 sont interprétés en tant que 63. Si la somme des index (réduit) et la longueur de champ (réduit) est supérieure à 64, les résultats sont indéfinis. Une valeur égale à zéro pour la longueur de champ est interprétée en tant que 64. Si l’index de longueur et les bits du champ est les deux zéro, 63:0 de bits de `Source` sont extraits. Si la longueur de champ est égal à zéro, mais l’index de bits est différente de zéro, les résultats sont indéfinis.

Dans un appel à _mm_extract_si64, le `Descriptor` contient l’index dans les bits 13:8 et la longueur de champ des données à extraire dans bits 5:0...

Si vous appelez `_mm_extracti_si64` avec les arguments que le compilateur ne peut pas déterminer être des constantes entières le compilateur génère du code pour regrouper ces valeurs dans un registre XMM (`Descriptor`) et d’appeler `_mm_extract_si64`.

Pour déterminer la prise en charge matérielle pour le `extrq` instruction, appelez le `__cpuid` intrinsèque avec `InfoType=0x80000001` et vérifiez le bit 6 de `CPUInfo[2] (ECX)`. Ce bit sera égale à 1 si l’instruction est pris en charge et 0 dans le cas contraire. Si vous exécutez du code qui utilise ce matériel intrinsèque qui ne prend pas en charge la `extrq` instruction, les résultats sont imprévisibles.

## <a name="example"></a>Exemple

```
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

**FIN de la section spécifique à Microsoft**

Copyright 2007 par avancées Micro Devices, Inc. Tous droits réservés. Reproduit avec l’autorisation d’Advanced Micro Devices, Inc.

## <a name="see-also"></a>Voir aussi

[_mm_insert_si64, _mm_inserti_si64](../intrinsics/mm-insert-si64-mm-inserti-si64.md)<br/>
[compilateur, fonctions intrinsèques](../intrinsics/compiler-intrinsics.md)