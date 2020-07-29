---
title: _mm_cvttss_si64x
ms.date: 09/02/2019
f1_keywords:
- _mm_cvttss_si64x
helpviewer_keywords:
- _mm_cvttss_si64x intrinsic
- cvttss2si instruction
ms.assetid: f9a3fd07-5bd8-4758-8744-6315c082cf87
ms.openlocfilehash: 6d920a5c59cacb23c7fb155c7ac8e813a9b0e8d0
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87217985"
---
# <a name="_mm_cvttss_si64x"></a>_mm_cvttss_si64x

**Spécifique à Microsoft**

Émet la version étendue x64 du convertir avec un nombre à virgule flottante simple précision de troncation en une instruction de type entier 64 bits ( `cvttss2si` ).

## <a name="syntax"></a>Syntaxe

```C
__int64 _mm_cvttss_si64x(
   __m128 value
);
```

### <a name="parameters"></a>Paramètres

*ajoutée*\
dans **`__m128`** Structure contenant des valeurs à virgule flottante simple précision.

## <a name="return-value"></a>Valeur retournée

Résultat de la conversion de la première valeur à virgule flottante en entier 64 bits.

## <a name="requirements"></a>Spécifications

|Intrinsic|Architecture|
|---------------|------------------|
|`_mm_cvttss_si64x`|x64|

**Fichier d’en-tête** \<intrin.h>

## <a name="remarks"></a>Notes

L’intrinsèque diffère `_mm_cvtss_si64x` uniquement de en ce que les conversions inexactes sont tronquées vers zéro. Étant donné que la **`__m128`** structure représente un registre XMM, l’instruction générée déplace les données d’un registre XMM dans la mémoire système.

Cette routine est disponible uniquement en tant qu'intrinsèque.

## <a name="example"></a>Exemple

```cpp
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

**FIN spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[__m128](../cpp/m128.md)\
[Intrinsèques du compilateur](../intrinsics/compiler-intrinsics.md)
