---
title: _mm_cvtss_si64x
ms.date: 09/02/2019
f1_keywords:
- _mm_cvtss_si64x
helpviewer_keywords:
- cvtss2si intrinsic
- _mm_cvtss_si64x intrinsic
ms.assetid: c279aff2-ee29-4271-8829-3ec691bf7718
ms.openlocfilehash: 6079ed7846a35ff16355f0341d63430f9846057f
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/03/2019
ms.locfileid: "70217435"
---
# <a name="_mm_cvtss_si64x"></a>_mm_cvtss_si64x

**Section spécifique à Microsoft**

Génère la version étendue x64 du nombre à virgule flottante simple précision de conversion en une instruction entière 64`cvtss2si`bits ().

## <a name="syntax"></a>Syntaxe

```C
__int64 _mm_cvtss_si64x(
   __m128 value
);
```

### <a name="parameters"></a>Paramètres

*value*\
dans `__m128` Structure contenant des valeurs à virgule flottante.

## <a name="return-value"></a>Valeur de retour

Entier 64 bits, résultat de la conversion de la première valeur à virgule flottante en entier.

## <a name="requirements"></a>Configuration requise

|Intrinsèque|Architecture|
|---------------|------------------|
|`_mm_cvtss_si64x`|X64|

**Fichier d’en-tête** \<> Intro. h

## <a name="remarks"></a>Notes

Le premier élément de la valeur de structure est converti en entier et retourné. Les bits de contrôle d’arrondi dans MXCSR sont utilisés pour déterminer le comportement d’arrondi. Le mode d’arrondi par défaut est arrondi au plus proche, en arrondissant au nombre pair si la partie décimale est 0,5. Étant donné `__m128` que la structure représente un registre XMM, l’intrinsèque prend une valeur du Registre XMM et l’écrit dans la mémoire système.

Cette routine est disponible uniquement en tant qu'intrinsèque.

## <a name="example"></a>Exemple

```cpp
// _mm_cvtss_si64x.cpp
// processor: x64
#include <intrin.h>
#include <stdio.h>

#pragma intrinsic(_mm_cvtss_si64x)

int main()
{
    __m128 a;
    __int64 b = 54;

    // _mm_load_ps requires an aligned buffer.
    __declspec(align(16)) float af[4] =
                           { 101.25, 200.75, 300.5, 400.5 };

    // Load a with the floating point values.
    // The values will be copied to the XMM registers.
    a = _mm_load_ps(af);

    // Extract the first element of a and convert to an integer
    b = _mm_cvtss_si64x(a);

    printf_s("%I64d\n", b);
}
```

```Output
101
```

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[__m128d](../cpp/m128d.md)\
[Intrinsèques du compilateur](../intrinsics/compiler-intrinsics.md)
