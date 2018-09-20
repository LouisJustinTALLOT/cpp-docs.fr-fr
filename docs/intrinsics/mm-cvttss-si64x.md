---
title: _mm_cvttss_si64x | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- _mm_cvttss_si64x
dev_langs:
- C++
helpviewer_keywords:
- _mm_cvttss_si64x intrinsic
- cvttss2si instruction
ms.assetid: f9a3fd07-5bd8-4758-8744-6315c082cf87
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6f8d863a485f6b3fa9648b74e8a438dcf5ef37be
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46381360"
---
# <a name="mmcvttsssi64x"></a>_mm_cvttss_si64x

**Section spécifique à Microsoft**

Émet le x64 étendu version de la convertir avec le nombre de nombres à virgule flottante simple précision de troncation en entier 64 bits (`cvttss2si`) instruction.

## <a name="syntax"></a>Syntaxe

```
__int64 _mm_cvttss_si64x( 
   __m128 value 
);
```

#### <a name="parameters"></a>Paramètres

*valeur*<br/>
[in] Un `__m128` structure contenant les valeurs à virgule flottante simple précision.

## <a name="return-value"></a>Valeur de retour

Le résultat de la conversion de la première valeur à virgule flottante en un entier 64 bits.

## <a name="requirements"></a>Configuration requise

|Intrinsèque|Architecture|
|---------------|------------------|
|`_mm_cvttss_si64x`|X64|

**Fichier d’en-tête** \<intrin.h >

## <a name="remarks"></a>Notes

La fonction intrinsèque diffère `_mm_cvtss_si64x` uniquement par l’inexactes conversions sont tronquées vers zéro. Étant donné que le `__m128` structure représente un registre XMM, l’instruction générée déplace les données à partir d’un registre XMM dans la mémoire système.

Cette routine est disponible uniquement en tant qu'intrinsèque.

## <a name="example"></a>Exemple

```
// _mm_cvttss_si64x.cpp
// processor: x64
#include <intrin.h>
#include <stdio.h>

#pragma intrinsic(_mm_cvttss_si64x)

int main()
{
    __m128 a;
    __int64 b = 54;

    // _mm_load_ps requires an aligned buffer.
    __declspec(align(16)) float af[4] = { 101.5, 200.75,
                                          300.5, 400.5 };

    // Load a with the floating point values.
    // The values will be copied to the XMM registers.
    a = _mm_load_ps(af);

    // Extract the first element of a and convert to an integer
    b = _mm_cvttss_si64x(a);

    printf_s("%I64d\n", b);
}
```

```Output
101
```

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[__m128](../cpp/m128.md)<br/>
[compilateur, fonctions intrinsèques](../intrinsics/compiler-intrinsics.md)