---
title: _mm_cvtsi64x_ss
ms.date: 11/04/2016
f1_keywords:
- _mm_cvtsi64x_ss
helpviewer_keywords:
- cvtsi2ss instruction
- _mm_cvtsi64x_ss intrinsic
ms.assetid: 01e5d321-c18a-46fd-a6f6-324364514e1f
ms.openlocfilehash: 3ba9dc56cbb027e8cf9f31d293b3f96908aff5e4
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59039778"
---
# <a name="mmcvtsi64xss"></a>_mm_cvtsi64x_ss

**Section spécifique à Microsoft**

Génère le x64 étendu version du convertir en entier 64 bits en à valeur scalaire en nombres à virgule flottante simple précision (`cvtsi2ss`) instruction.

## <a name="syntax"></a>Syntaxe

```
__m128 _mm_cvtsi64x_ss(
   __m128 a,
   __int64 b
);
```

#### <a name="parameters"></a>Paramètres

*a*<br/>
[in] Un `__m128` structure contenant quatre valeurs à virgule flottante simple précision.

*b*<br/>
[in] Un entier 64 bits à convertir en valeur à virgule flottante.

## <a name="return-value"></a>Valeur de retour

Un `__m128` structure dont la première valeur à virgule flottante est le résultat de la conversion. Les trois autres valeurs sont copiées sans modification à partir de `a`.

## <a name="requirements"></a>Configuration requise

|Intrinsèque|Architecture|
|---------------|------------------|
|`_mm_cvtsi64x_ss`|X64|

**Fichier d’en-tête** \<intrin.h >

## <a name="remarks"></a>Notes

Le `__m128` structure représente un registre XMM, donc cette intrinsèque autorise une valeur `b` de la mémoire système à déplacer vers un XMM inscrire.

Cette routine est disponible uniquement en tant qu'intrinsèque.

## <a name="example"></a>Exemple

```
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

[__m128](../cpp/m128.md)<br/>
[compilateur, fonctions intrinsèques](../intrinsics/compiler-intrinsics.md)