---
title: _mm_cvttss_si64x
ms.date: 09/02/2019
f1_keywords:
- _mm_cvttss_si64x
helpviewer_keywords:
- _mm_cvttss_si64x intrinsic
- cvttss2si instruction
ms.assetid: f9a3fd07-5bd8-4758-8744-6315c082cf87
ms.openlocfilehash: 69016a4e23b020b2c4c79c6b97a5a76f2b2dc028
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/03/2019
ms.locfileid: "70217417"
---
# <a name="_mm_cvttss_si64x"></a>_mm_cvttss_si64x

**Section spécifique à Microsoft**

Émet la version étendue x64 du convertir avec un nombre à virgule flottante simple précision de troncation en une instruction de type`cvttss2si`entier 64 bits ().

## <a name="syntax"></a>Syntaxe

```C
__int64 _mm_cvttss_si64x(
   __m128 value
);
```

### <a name="parameters"></a>Paramètres

*value*\
dans `__m128` Structure contenant des valeurs à virgule flottante simple précision.

## <a name="return-value"></a>Valeur de retour

Résultat de la conversion de la première valeur à virgule flottante en entier 64 bits.

## <a name="requirements"></a>Configuration requise

|Intrinsèque|Architecture|
|---------------|------------------|
|`_mm_cvttss_si64x`|X64|

**Fichier d’en-tête** \<> Intro. h

## <a name="remarks"></a>Notes

L’intrinsèque diffère uniquement `_mm_cvtss_si64x` de en ce que les conversions inexactes sont tronquées vers zéro. Étant donné `__m128` que la structure représente un registre XMM, l’instruction générée déplace les données d’un registre XMM dans la mémoire système.

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

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[__m128](../cpp/m128.md)\
[Intrinsèques du compilateur](../intrinsics/compiler-intrinsics.md)
