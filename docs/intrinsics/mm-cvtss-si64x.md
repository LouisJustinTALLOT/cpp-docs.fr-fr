---
title: _mm_cvtss_si64x
ms.date: 11/04/2016
f1_keywords:
- _mm_cvtss_si64x
helpviewer_keywords:
- cvtss2si intrinsic
- _mm_cvtss_si64x intrinsic
ms.assetid: c279aff2-ee29-4271-8829-3ec691bf7718
ms.openlocfilehash: a3b7ece325d975045046e865e6b090f3f6729558
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62263332"
---
# <a name="mmcvtsssi64x"></a>_mm_cvtss_si64x

**Section spécifique à Microsoft**

Génère le x64 étendu version de la convertir scalaire unique précision nombre à virgule flottante en entier 64 bits (`cvtss2si`) instruction.

## <a name="syntax"></a>Syntaxe

```
__int64 _mm_cvtss_si64x(
   __m128 value
);
```

#### <a name="parameters"></a>Paramètres

*value*<br/>
[in] Un `__m128` structure contenant les valeurs à virgule flottante-.

## <a name="return-value"></a>Valeur de retour

Un entier 64 bits, le résultat de la conversion de la première valeur à virgule flottante en entier.

## <a name="requirements"></a>Configuration requise

|Intrinsèque|Architecture|
|---------------|------------------|
|`_mm_cvtss_si64x`|X64|

**Fichier d’en-tête** \<intrin.h >

## <a name="remarks"></a>Notes

Le premier élément de la valeur de la structure est converti en un entier et retourné. Les bits de contrôle arrondi dans MXCSR servent à déterminer le comportement d’arrondi. La valeur par défaut de mode d’arrondi est arrondi à la plus proche, arrondi au nombre pair si la partie décimale est égale à 0,5. Étant donné que le `__m128` structure représente un registre XMM, cette intrinsèque prend une valeur du registre XMM et l’écrit dans la mémoire système.

Cette routine est disponible uniquement en tant qu'intrinsèque.

## <a name="example"></a>Exemple

```
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

[__m128d](../cpp/m128d.md)<br/>
[compilateur, fonctions intrinsèques](../intrinsics/compiler-intrinsics.md)