---
description: 'En savoir plus sur : _mm_cvtsi64x_ss'
title: _mm_cvtsi64x_ss
ms.date: 09/02/2019
f1_keywords:
- _mm_cvtsi64x_ss
helpviewer_keywords:
- cvtsi2ss instruction
- _mm_cvtsi64x_ss intrinsic
ms.assetid: 01e5d321-c18a-46fd-a6f6-324364514e1f
ms.openlocfilehash: 81a1af04d4c66cefd9815471baeb3a6095403ddf
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97167719"
---
# <a name="_mm_cvtsi64x_ss"></a>_mm_cvtsi64x_ss

**Spécifique à Microsoft**

Génère la version étendue x64 de l’entier Convert 64 bits en scalaire Single-Precision Floating-Point instruction value ( `cvtsi2ss` ).

## <a name="syntax"></a>Syntaxe

```C
__m128 _mm_cvtsi64x_ss(
   __m128 a,
   __int64 b
);
```

### <a name="parameters"></a>Paramètres

*un*\
dans **`__m128`** Structure contenant quatre valeurs à virgule flottante simple précision.

*p*\
dans Entier 64 bits à convertir en valeur à virgule flottante.

## <a name="return-value"></a>Valeur retournée

**`__m128`** Structure dont la première valeur à virgule flottante est le résultat de la conversion. Les trois autres valeurs sont copiées sans *modification à partir de.*

## <a name="requirements"></a>Spécifications

|Intrinsic|Architecture|
|---------------|------------------|
|`_mm_cvtsi64x_ss`|x64|

**Fichier d’en-tête** \<intrin.h>

## <a name="remarks"></a>Notes

La **`__m128`** structure représente un registre XMM, de sorte que l’intrinsèque autorise le déplacement de la valeur *b* de la mémoire système vers un registre XMM.

Cette routine est disponible uniquement en tant qu'intrinsèque.

## <a name="example"></a>Exemple

```cpp
// _mm_cvtsi64x_ss.cpp
// processor: x64

#include <intrin.h>
#include <stdio.h>

#pragma intrinsic(_mm_cvtsi64x_ss)

int main()
{
    __m128 a;
    __int64 b = 54;

    a.m128_f32[0] = 0;
    a.m128_f32[1] = 0;
    a.m128_f32[2] = 0;
    a.m128_f32[3] = 0;
    a = _mm_cvtsi64x_ss(a, b);

    printf_s( "%lf %lf %lf %lf\n",
              a.m128_f32[0], a.m128_f32[1],
              a.m128_f32[2], a.m128_f32[3] );
}
```

```Output
54.000000 0.000000 0.000000 0.000000
```

**FIN spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[__m128](../cpp/m128.md)\
[Intrinsèques du compilateur](../intrinsics/compiler-intrinsics.md)
