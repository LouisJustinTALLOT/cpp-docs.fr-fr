---
title: _mm_cvtsi64x_ss
ms.date: 09/02/2019
f1_keywords:
- _mm_cvtsi64x_ss
helpviewer_keywords:
- cvtsi2ss instruction
- _mm_cvtsi64x_ss intrinsic
ms.assetid: 01e5d321-c18a-46fd-a6f6-324364514e1f
ms.openlocfilehash: 0e9bacc56f212e804467d1c6e0159a1749235976
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/03/2019
ms.locfileid: "70217457"
---
# <a name="_mm_cvtsi64x_ss"></a>_mm_cvtsi64x_ss

**Section spécifique à Microsoft**

Génère la version étendue x64 de l’entier de conversion 64 bits en une instruction de valeur à virgule flottante simple`cvtsi2ss`précision scalaire ().

## <a name="syntax"></a>Syntaxe

```C
__m128 _mm_cvtsi64x_ss(
   __m128 a,
   __int64 b
);
```

### <a name="parameters"></a>Paramètres

*un*\
dans `__m128` Structure contenant quatre valeurs à virgule flottante simple précision.

*p*\
dans Entier 64 bits à convertir en valeur à virgule flottante.

## <a name="return-value"></a>Valeur de retour

`__m128` Structure dont la première valeur à virgule flottante est le résultat de la conversion. Les trois autres valeurs sont copiées sans modification àpartir de.

## <a name="requirements"></a>Configuration requise

|Intrinsèque|Architecture|
|---------------|------------------|
|`_mm_cvtsi64x_ss`|X64|

**Fichier d’en-tête** \<> Intro. h

## <a name="remarks"></a>Notes

La `__m128` structure représente un registre XMM, de sorte que l’intrinsèque autorise le déplacement de la valeur *b* de la mémoire système vers un registre XMM.

Cette routine est disponible uniquement en tant qu'intrinsèque.

## <a name="example"></a>Exemples

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

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[__m128](../cpp/m128.md)\
[Intrinsèques du compilateur](../intrinsics/compiler-intrinsics.md)
