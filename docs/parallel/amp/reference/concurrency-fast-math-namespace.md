---
description: 'En savoir plus sur : accès concurrentiel :: fast_math espace de noms'
title: Concurrency::fast_math, espace de noms
ms.date: 11/04/2016
f1_keywords:
- amp_math/Concurrency::fast_math
ms.assetid: 54fed939-9902-49db-9f29-e98fd9821508
ms.openlocfilehash: 99638e3d8b0a452774d1e92d408ce3edddfa861c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97122367"
---
# <a name="concurrencyfast_math-namespace"></a>Concurrency::fast_math, espace de noms

Les fonctions de l' `fast_math` espace de noms ont une précision inférieure, ne prennent en charge que la simple précision ( **`float`** ) et appellent les intrinsèques DirectX. Il existe deux versions de chaque fonction, par exemple `cos` et `cosf` . Les deux versions prennent et retournent un **`float`** , mais chacune appelle le même intrinsèque DirectX.

## <a name="syntax"></a>Syntaxe

```cpp
namespace fast_math;
```

## <a name="members"></a>Membres

### <a name="functions"></a>Fonctions

|Nom|Description|
|----------|-----------------|
|[COS](concurrency-fast-math-namespace-functions.md#cos)|Calcule l’arc cosinus de l’argument|
|[cosf](concurrency-fast-math-namespace-functions.md#cosf)|Calcule l’arc cosinus de l’argument|
|[ASIN](concurrency-fast-math-namespace-functions.md#asin)|Calcule l’arc sinus de l’argument|
|[asinf](concurrency-fast-math-namespace-functions.md#asinf)|Calcule l’arc sinus de l’argument|
|[atan](concurrency-fast-math-namespace-functions.md#atan)|Calcule l'arc tangente de l'argument.|
|[atan2](concurrency-fast-math-namespace-functions.md#atan2)|Calcule l’arc tangente de _Y/_X|
|[atan2f](concurrency-fast-math-namespace-functions.md#atan2f)|Calcule l’arc tangente de _Y/_X|
|[atanf](concurrency-fast-math-namespace-functions.md#atanf)|Calcule l'arc tangente de l'argument.|
|[ceil](concurrency-fast-math-namespace-functions.md#ceil)|Calcule le plafond de l’argument|
|[ceilf](concurrency-fast-math-namespace-functions.md#ceilf)|Calcule le plafond de l’argument|
|[COS](concurrency-fast-math-namespace-functions.md#cos)|Calcule le cosinus de l'argument.|
|[cosf](concurrency-fast-math-namespace-functions.md#cosf)|Calcule le cosinus de l'argument.|
|[cosh](concurrency-fast-math-namespace-functions.md#cosh)|Calcule la valeur du cosinus hyperbolique de l’argument.|
|[coshf](concurrency-fast-math-namespace-functions.md#coshf)|Calcule la valeur du cosinus hyperbolique de l’argument.|
|[exp](concurrency-fast-math-namespace-functions.md#exp)|Calcule la valeur exponentielle de base e de l’argument.|
|[EXP2](concurrency-fast-math-namespace-functions.md#exp2)|Calcule la valeur exponentielle de base 2 de l’argument.|
|[exp2f](concurrency-fast-math-namespace-functions.md#exp2f)|Calcule la valeur exponentielle de base 2 de l’argument.|
|[expf](concurrency-fast-math-namespace-functions.md#expf)|Calcule la valeur exponentielle de base e de l’argument.|
|[fabs](concurrency-fast-math-namespace-functions.md#fabs)|Retourne la valeur absolue de l’argument.|
|[fabsf](concurrency-fast-math-namespace-functions.md#fabsf)|Retourne la valeur absolue de l’argument.|
|[floor](concurrency-fast-math-namespace-functions.md#floor)|Calcule le plancher de l’argument|
|[floorf](concurrency-fast-math-namespace-functions.md#floorf)|Calcule le plancher de l’argument|
|[fmax](concurrency-fast-math-namespace-functions.md#fmax)|Déterminer la valeur numérique maximale des arguments|
|[fmaxf](concurrency-fast-math-namespace-functions.md#fmaxf)|Déterminer la valeur numérique maximale des arguments|
|[fmin](concurrency-fast-math-namespace-functions.md#fmin)|Déterminer la valeur numérique minimale des arguments|
|[fminf](concurrency-fast-math-namespace-functions.md#fminf)|Déterminer la valeur numérique minimale des arguments|
|[fmod](concurrency-fast-math-namespace-functions.md#fmod)|Calcule le reste à virgule flottante de _X/_Y|
|[fmodf](concurrency-fast-math-namespace-functions.md#fmodf)|Calcule le reste à virgule flottante de _X/_Y|
|[frexp](concurrency-fast-math-namespace-functions.md#frexp)|Obtient la mantisse et l’exposant de _X|
|[frexpf,](concurrency-fast-math-namespace-functions.md#frexpf)|Obtient la mantisse et l’exposant de _X|
|[isFinite,](concurrency-fast-math-namespace-functions.md#isfinite)|Détermine si l’argument a une valeur finie|
|[isinf,](concurrency-fast-math-namespace-functions.md#isinf)|Détermine si l’argument est un infini|
|[isNaN](concurrency-fast-math-namespace-functions.md#isnan)|Détermine si l’argument est une valeur NaN|
|[ldexp](concurrency-fast-math-namespace-functions.md#ldexp)|Calcule un nombre réel à partir de la mantisse et de l’exposant|
|[ldexpf,](concurrency-fast-math-namespace-functions.md#ldexpf)|Calcule un nombre réel à partir de la mantisse et de l’exposant|
|[Sign](concurrency-fast-math-namespace-functions.md#log)|Calcule le logarithme de base e de l’argument|
|[log10](concurrency-fast-math-namespace-functions.md#log10)|Calcule le logarithme en base 10 de l’argument.|
|[log10f](concurrency-fast-math-namespace-functions.md#log10f)|Calcule le logarithme en base 10 de l’argument.|
|[Log2](concurrency-fast-math-namespace-functions.md#log2)|Calcule le logarithme de base 2 de l’argument.|
|[log2f](concurrency-fast-math-namespace-functions.md#log2f)|Calcule le logarithme de base 2 de l’argument.|
|[logf](concurrency-fast-math-namespace-functions.md#logf)|Calcule le logarithme de base e de l’argument|
|[modf](concurrency-fast-math-namespace-functions.md#modf)|Divise _X en parties fractionnaires et entières.|
|[modff](concurrency-fast-math-namespace-functions.md#modff)|Divise _X en parties fractionnaires et entières.|
|[Poe](concurrency-fast-math-namespace-functions.md#pow)|Calcule _X élevé à la puissance de _Y|
|[powf](concurrency-fast-math-namespace-functions.md#powf)|Calcule _X élevé à la puissance de _Y|
|[Round](concurrency-fast-math-namespace-functions.md#round)|Arrondit _X à l’entier le plus proche.|
|[roundf](concurrency-fast-math-namespace-functions.md#roundf)|Arrondit _X à l’entier le plus proche.|
|[rsqrt,](concurrency-fast-math-namespace-functions.md#rsqrt)|Retourne la réciproque de la racine carrée de l’argument|
|[rsqrtf,](concurrency-fast-math-namespace-functions.md#rsqrtf)|Retourne la réciproque de la racine carrée de l’argument|
|[signbit](concurrency-fast-math-namespace-functions.md#signbit)|Retourne le signe de l’argument.|
|[signbitf,](concurrency-fast-math-namespace-functions.md#signbitf)|Retourne le signe de l’argument.|
|[Sin](concurrency-fast-math-namespace-functions.md#sin)|Calcule la valeur du sinus de l’argument|
|[SinCos,](concurrency-fast-math-namespace-functions.md#sincos)|Calcule la valeur du sinus et du cosinus de _X|
|[sincosf,](concurrency-fast-math-namespace-functions.md#sincosf)|Calcule la valeur du sinus et du cosinus de _X|
|[sinf](concurrency-fast-math-namespace-functions.md#sinf)|Calcule la valeur du sinus de l’argument|
|[Sinh](concurrency-fast-math-namespace-functions.md#sinh)|Calcule la valeur du sinus hyperbolique de l’argument.|
|[sinhf](concurrency-fast-math-namespace-functions.md#sinhf)|Calcule la valeur du sinus hyperbolique de l’argument.|
|[racine](concurrency-fast-math-namespace-functions.md#sqrt)|Calcule la racine carrée de l’argument|
|[sqrtf](concurrency-fast-math-namespace-functions.md#sqrtf)|Calcule la racine carrée de l’argument|
|[Tan](concurrency-fast-math-namespace-functions.md#tan)|Calcule la valeur de tangente de l’argument|
|[tanf](concurrency-fast-math-namespace-functions.md#tanf)|Calcule la valeur de tangente de l’argument|
|[Tanh](concurrency-fast-math-namespace-functions.md#tanh)|Calcule la valeur tangente hyperbolique de l’argument.|
|[tanhf](concurrency-fast-math-namespace-functions.md#tanhf)|Calcule la valeur tangente hyperbolique de l’argument.|
|[trunc](concurrency-fast-math-namespace-functions.md#trunc)|Tronque l’argument du composant entier|
|[truncf](concurrency-fast-math-namespace-functions.md#truncf)|Tronque l’argument du composant entier|

## <a name="requirements"></a>Spécifications

**En-tête :** amp_math. h

**Espace de noms :** Concurrence :: fast_math

## <a name="see-also"></a>Voir aussi

[Concurrence de l’espace de noms (C++ AMP)](concurrency-namespace-cpp-amp.md)
