---
title: Concurrency::fast_math, fonctions de l’espace de noms
ms.date: 11/04/2016
f1_keywords:
- amp_math/Concurrency::fast_math::acos
- amp_math/Concurrency::fast_math::asin
- amp_math/Concurrency::fast_math::asinf
- amp_math/Concurrency::fast_math::atan2
- amp_math/Concurrency::fast_math::atan2f
- amp_math/Concurrency::fast_math::ceil
- amp_math/Concurrency::fast_math::ceilf
- amp_math/Concurrency::fast_math::cosf
- amp_math/Concurrency::fast_math::cosh
- amp_math/Concurrency::fast_math::exp
- amp_math/Concurrency::fast_math::exp2
- amp_math/Concurrency::fast_math::expf
- amp_math/Concurrency::fast_math::fabs
- amp_math/Concurrency::fast_math::floor
- amp_math/Concurrency::fast_math::floorf
- amp_math/Concurrency::fast_math::fmaxf
- amp_math/Concurrency::fast_math::fmin
- amp_math/Concurrency::fast_math::fmod
- amp_math/Concurrency::fast_math::fmodf
- amp_math/Concurrency::fast_math::frexpf
- amp_math/Concurrency::fast_math::isfinite
- amp_math/Concurrency::fast_math::isnan
- amp_math/Concurrency::fast_math::ldexp
- amp_math/Concurrency::fast_math::log
- amp_math/Concurrency::fast_math::log10
- amp_math/Concurrency::fast_math::log2
- amp_math/Concurrency::fast_math::log2f
- amp_math/Concurrency::fast_math::modf
- amp_math/Concurrency::fast_math::modff
- amp_math/Concurrency::fast_math::powf
- amp_math/Concurrency::fast_math::round
- amp_math/Concurrency::fast_math::rsqrt
- amp_math/Concurrency::fast_math::rsqrtf
- amp_math/Concurrency::fast_math::signbitf
- amp_math/Concurrency::fast_math::sin
- amp_math/Concurrency::fast_math::sincosf
- amp_math/Concurrency::fast_math::sinf
- amp_math/Concurrency::fast_math::sinhf
- amp_math/Concurrency::fast_math::sqrt
- amp_math/Concurrency::fast_math::tan
- amp_math/Concurrency::fast_math::tanf
- amp_math/Concurrency::fast_math::tanhf
- amp_math/Concurrency::fast_math::trunc
ms.assetid: f5763d62-795b-4de6-a7a5-c7115f158708
ms.openlocfilehash: cd0882b072cfe26cd83e63024ae6837dc962ebf9
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376397"
---
# <a name="concurrencyfast_math-namespace-functions"></a>Concurrency::fast_math, fonctions de l’espace de noms

||||
|-|-|-|
|[Acos](#acos)|[acosf](#acosf)|[Asin](#asin)|
|[asinf](#asinf)|[Atan](#atan)|[atan2](#atan2)|
|[atan2f](#atan2f)|[atanf](#atanf)|[ceil](#ceil)|
|[ceilf](#ceilf)|[Cos](#cos)|[cosf](#cosf)|
|[cosh](#cosh)|[coshf](#coshf)|[Exp](#exp)|
|[exp2](#exp2)|[exp2f](#exp2f)|[expf](#expf)|
|[fabs](#fabs)|[fabsf](#fabsf)|[Étage](#floor)|
|[floorf](#floorf)|[fmax](#fmax)|[fmaxf](#fmaxf)|
|[fmin](#fmin)|[fminf](#fminf)|[fmod](#fmod)|
|[fmodf](#fmodf)|[frexp](#frexp)|[frexpf frexpf](#frexpf)|
|[isfinite](#isfinite)|[isinf](#isinf)|[isnan (isnan)](#isnan)|
|[ldexp](#ldexp)|[ldexpf (ldexpf)](#ldexpf)|[rapport](#log)|
|[journal10](#log10)|[log10f](#log10f)|[log2](#log2)|
|[log2f](#log2f)|[logf](#logf)|[modf](#modf)|
|[modff](#modff)|[Pow](#pow)|[powf](#powf)|
|[Rond](#round)|[roundf](#roundf)|[rsqrt](#rsqrt)|
|[rsqrtf](#rsqrtf)|[signbit](#signbit)|[signbitf](#signbitf)|
|[Péché](#sin)|[sincos](#sincos)|[sincosf](#sincosf)|
|[sinf](#sinf)|[sinh](#sinh)|[sinhf](#sinhf)|
|[Sqrt](#sqrt)|[sqrtf](#sqrtf)|[Tan](#tan)|
|[tanf](#tanf)|[tanh tanh](#tanh)|[tanhf](#tanhf)|
|[Trunc](#trunc)|[truncf](#truncf)|

## <a name="acos"></a><a name="acos"></a>Acos

Calcule l’arccosine de l’argument

```cpp
inline float acos(float _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne la valeur arccosine de l’argument

## <a name="acosf"></a><a name="acosf"></a>acosf

Calcule l’arccosine de l’argument

```cpp
inline float acosf(float _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne la valeur arccosine de l’argument

## <a name="asin"></a><a name="asin"></a>Asin

Calcule l’arcsine de l’argument

```cpp
inline float asin(float _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne la valeur arcsine de l’argument

## <a name="asinf"></a><a name="asinf"></a>asinf

Calcule l’arcsine de l’argument

```cpp
inline float asinf(float _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne la valeur arcsine de l’argument

## <a name="atan"></a><a name="atan"></a>Atan

Calcule l'arc tangente de l'argument.

```cpp
inline float atan(float _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne la valeur arctangente de l’argument

## <a name="atan2"></a><a name="atan2"></a>atan2

Calcule l’arctangent de _Y/_X

```cpp
inline float atan2(
    float _Y,
    float _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_Y*<br/>
Valeur à virgule flottante

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne la valeur arctangente de _Y/_X

## <a name="atan2f"></a><a name="atan2f"></a>atan2f

Calcule l’arctangent de _Y/_X

```cpp
inline float atan2f(
    float _Y,
    float _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_Y*<br/>
Valeur à virgule flottante

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne la valeur arctangente de _Y/_X

## <a name="atanf"></a><a name="atanf"></a>atanf

Calcule l'arc tangente de l'argument.

```cpp
inline float atanf(float _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne la valeur arctangente de l’argument

## <a name="ceil"></a><a name="ceil"></a>Ceil

Calcule le plafond de l’argument

```cpp
inline float ceil(float _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne le plafond de l’argument

## <a name="ceilf"></a><a name="ceilf"></a>ceilf

Calcule le plafond de l’argument

```cpp
inline float ceilf(float _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne le plafond de l’argument

## <a name="cosf"></a><a name="cosf"></a>cosf (cosf)

Calcule le cosinus de l'argument.

```cpp
inline float cosf(float _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne la valeur cosine de l’argument

## <a name="coshf"></a><a name="coshf"></a>coshf (coshf)

Calcule la valeur cosine hyperbolique de l’argument

```cpp
inline float coshf(float _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne la valeur cosine hyperbolique de l’argument

## <a name="cos"></a><a name="cos"></a>Cos

Calcule le cosinus de l'argument.

```cpp
inline float cos(float _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne la valeur cosine de l’argument

## <a name="cosh"></a><a name="cosh"></a>Cosh

Calcule la valeur cosine hyperbolique de l’argument

```cpp
inline float cosh(float _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne la valeur cosine hyperbolique de l’argument

## <a name="exp"></a><a name="exp"></a>Exp

Calcule l’exponentiel de base-e de l’argument

```cpp
inline float exp(float _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne l’exponentiel de base-e de l’argument

## <a name="exp2"></a><a name="exp2"></a>exp2

Calcule l’exponentielle de base-2 de l’argument

```cpp
inline float exp2(float _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne l'exponentielle de base 2 de l'argument.

## <a name="exp2f"></a><a name="exp2f"></a>exp2f exp2f

Calcule l’exponentielle de base-2 de l’argument

```cpp
inline float exp2f(float _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne l'exponentielle de base 2 de l'argument.

## <a name="expf"></a><a name="expf"></a>expf expf

Calcule l’exponentiel de base-e de l’argument

```cpp
inline float expf(float _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne l’exponentiel de base-e de l’argument

## <a name="fabs"></a><a name="fabs"></a>fabs

Retourne la valeur absolue de l’argument

```cpp
inline float fabs(float _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur entière

### <a name="return-value"></a>Valeur de retour

Retourne la valeur absolue de l’argument

## <a name="fabsf"></a><a name="fabsf"></a>fabsf

Retourne la valeur absolue de l’argument

```cpp
inline float fabsf(float _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne la valeur absolue de l’argument

## <a name="floor"></a><a name="floor"></a>Étage

Calcule le plancher de l’argument

```cpp
inline float floor(float _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne le plancher de l’argument

## <a name="floorf"></a><a name="floorf"></a>plancher

Calcule le plancher de l’argument

```cpp
inline float floorf(float _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne le plancher de l’argument

## <a name="fmax"></a><a name="fmax"></a>Fmax

Déterminer la valeur numérique maximale des arguments

```cpp
inline float max(
    float _X,
    float _Y) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur entière

*_Y*<br/>
Valeur entière

### <a name="return-value"></a>Valeur de retour

Retourner la valeur numérique maximale des arguments

## <a name="fmaxf"></a><a name="fmaxf"></a>fmaxf (fmaxf)

Déterminer la valeur numérique maximale des arguments

```cpp
inline float fmaxf(
    float _X,
    float _Y) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

*_Y*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourner la valeur numérique maximale des arguments

## <a name="fmin"></a><a name="fmin"></a>fmin fmin

Déterminer la valeur numérique minimale des arguments

```cpp
inline float min(
    float _X,
    float _Y) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur entière

*_Y*<br/>
Valeur entière

### <a name="return-value"></a>Valeur de retour

Retourner la valeur numérique minimale des arguments

## <a name="fminf"></a><a name="fminf"></a>fminf

Déterminer la valeur numérique minimale des arguments

```cpp
inline float fminf(
    float _X,
    float _Y) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

*_Y*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourner la valeur numérique minimale des arguments

## <a name="fmod"></a><a name="fmod"></a>fmod

Calcule le reste du point flottant de _X/_Y

```cpp
inline float fmod(
    float _X,
    float _Y) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

*_Y*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne le reste du point flottant de _X/_Y

## <a name="fmodf"></a><a name="fmodf"></a>fmodf

Calcule le reste du point flottant de _X/_Y.

```cpp
inline float fmodf(
    float _X,
    float _Y) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

*_Y*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne le reste du point flottant de _X/_Y

## <a name="frexp"></a><a name="frexp"></a>frexp frexp

Obtient la mantissa et l’exposant de _X

```cpp
inline float frexp(
    float _X,
    _Out_ int* _Exp) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

*_Exp*<br/>
Retourne l’exposant integer de _X en valeur de point flottant

### <a name="return-value"></a>Valeur de retour

Retourne la mantissa _X

## <a name="frexpf"></a><a name="frexpf"></a>frexpf frexpf

Obtient la mantissa et l’exposant de _X

```cpp
inline float frexpf(
    float _X,
    _Out_ int* _Exp) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

*_Exp*<br/>
Retourne l’exposant integer de _X en valeur de point flottant

### <a name="return-value"></a>Valeur de retour

Retourne la mantissa _X

## <a name="isfinite"></a><a name="isfinite"></a>isfinite

Détermine si l’argument a une valeur limitée

```cpp
inline int isfinite(float _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne une valeur non zéro si et seulement si l’argument a une valeur finie

## <a name="isinf"></a><a name="isinf"></a>isinf

Détermine si l’argument est une infinité

```cpp
inline int isinf(float _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne une valeur non zéro si et seulement si l’argument a une valeur infinie

## <a name="isnan"></a><a name="isnan"></a>isnan (isnan)

Détermine si l’argument est un NaN

```cpp
inline int isnan(float _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne une valeur non zéro si et seulement si l’argument a une valeur NaN

## <a name="ldexp"></a><a name="ldexp"></a>ldexp

Calcule un nombre réel de la mantissa et exposant

```cpp
inline float ldexp(
    float _X,
    int _Exp) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur de point flottant, mentissa

*_Exp*<br/>
Exposant Integer

### <a name="return-value"></a>Valeur de retour

Retours _X \* 2 _Exp

## <a name="ldexpf"></a><a name="ldexpf"></a>ldexpf (ldexpf)

Calcule un nombre réel de la mantissa et exposant

```cpp
inline float ldexpf(
    float _X,
    int _Exp) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur de point flottant, mentissa

*_Exp*<br/>
Exposant Integer

### <a name="return-value"></a>Valeur de retour

Retours _X \* 2 _Exp

## <a name="log"></a><a name="log"></a>rapport

Calcule le logarithme de base-e de l’argument

```cpp
inline float log(float _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne le logarithme de base-e de l’argument

## <a name="log10"></a><a name="log10"></a>journal10

Calcule le logarithme de base-10 de l’argument

```cpp
inline float log10(float _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne le logarithme de base-10 de l’argument

## <a name="log10f"></a><a name="log10f"></a>log10f

Calcule le logarithme de base-10 de l’argument

```cpp
inline float log10f(float _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne le logarithme de base-10 de l’argument

## <a name="log2"></a><a name="log2"></a>log2

Calcule le logarithme de base-2 de l’argument

```cpp
inline float log2(float _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne le logarithme de base-2 de l’argument

## <a name="log2f"></a><a name="log2f"></a>log2f

Calcule le logarithme de base-2 de l’argument

```cpp
inline float log2f(float _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne le logarithme de base-10 de l’argument

## <a name="logf"></a><a name="logf"></a>logf

Calcule le logarithme de base-e de l’argument

```cpp
inline float logf(float _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne le logarithme de base-e de l’argument

## <a name="modf"></a><a name="modf"></a>modf

Divise _X en pièces fractionnées et integer.

```cpp
inline float modf(
    float _X,
    float* _Ip) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

*_Ip*<br/>
Reçoit une partie de la valeur de l’intégrant

### <a name="return-value"></a>Valeur de retour

Retourne la partie fractionnée signée de _X

## <a name="modff"></a><a name="modff"></a>modff (modff)

Divise _X en pièces fractionnées et integer.

```cpp
inline float modff(
    float _X,
    float* _Ip) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

*_Ip*<br/>
Reçoit une partie de la valeur de l’intégrant

### <a name="return-value"></a>Valeur de retour

Retourne la partie fractionnée signée de _X

## <a name="pow"></a><a name="pow"></a>Pow

Calcule _X portés à la puissance de _Y

```cpp
inline float pow(
    float _X,
    float _Y) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur de point flottant, base

*_Y*<br/>
Valeur à point flottant, exposant

### <a name="return-value"></a>Valeur de retour

Retourne la valeur de _X porté au pouvoir de _Y

## <a name="powf"></a><a name="powf"></a>powf powf

Calcule _X portés à la puissance de _Y

```cpp
inline float powf(
    float _X,
    float _Y) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur de point flottant, base

*_Y*<br/>
Valeur à point flottant, exposant

### <a name="return-value"></a>Valeur de retour

## <a name="round"></a><a name="round"></a>Rond

Les rondes _X à l’intégrant le plus proche

```cpp
inline float round(float _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne l’intégrant le plus proche de _X

## <a name="roundf"></a><a name="roundf"></a>roundf (en)

Les rondes _X à l’intégrant le plus proche

```cpp
inline float roundf(float _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne l’intégrant le plus proche de _X

## <a name="rsqrt"></a><a name="rsqrt"></a>rsqrt

Retourne la réciprocité de la racine carrée de l’argument

```cpp
inline float rsqrt(float _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne la réciprocité de la racine carrée de l’argument

## <a name="rsqrtf"></a><a name="rsqrtf"></a>rsqrtf

Retourne la réciprocité de la racine carrée de l’argument

```cpp
inline float rsqrtf(float _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne la réciprocité de la racine carrée de l’argument

## <a name="signbit"></a><a name="signbit"></a>signbit

Détermine si le signe de _X est négatif

```cpp
inline int signbit(float _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne une valeur non zéro si et seulement si le signe de _X est négatif

## <a name="signbitf"></a><a name="signbitf"></a>signbitf

Détermine si le signe de _X est négatif

```cpp
inline int signbitf(float _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne une valeur non zéro si et seulement si le signe de _X est négatif

## <a name="sin"></a><a name="sin"></a>Péché

Calcule la valeur sinusoïdale de l’argument

```cpp
inline float sin(float _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne la valeur sinusoïne de l’argument

## <a name="sinf"></a><a name="sinf"></a>sinf sinf

Calcule la valeur sinusoïdale de l’argument

```cpp
inline float sinf(float _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne la valeur sinusoïne de l’argument

## <a name="sincos"></a><a name="sincos"></a>sincos

Calcule la valeur sine et cosine de _X

```cpp
inline void sincos(
    float _X,
    float* _S,
    float* _C) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

*_S*<br/>
Retourne la valeur sinusoïale de _X

*_C*<br/>
Retourne la valeur cosine de _X

## <a name="sincosf"></a><a name="sincosf"></a>sincosf

Calcule la valeur sine et cosine de _X

```cpp
inline void sincosf(
    float _X,
    float* _S,
    float* _C) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

*_S*<br/>
Retourne la valeur sinusoïale de _X

*_C*<br/>
Retourne la valeur cosine de _X

## <a name="sinh"></a><a name="sinh"></a>Sinh

Calcule la valeur sine hyperbolique de l’argument

```cpp
inline float sinh(float _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne la valeur sine hyperbolique de l’argument

## <a name="sinhf"></a><a name="sinhf"></a>sinhf

Calcule la valeur sine hyperbolique de l’argument

```cpp
inline float sinhf(float _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne la valeur sine hyperbolique de l’argument

## <a name="sqrt"></a><a name="sqrt"></a>Sqrt

Calcule la racine squre de l’argument

```cpp
inline float sqrt(float _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne la racine de squre de l’argument

## <a name="sqrtf"></a><a name="sqrtf"></a>sqrtf

Calcule la racine squre de l’argument

```cpp
inline float sqrtf(float _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne la racine de squre de l’argument

## <a name="tan"></a><a name="tan"></a>Tan

Calcule la valeur tangente de l’argument

```cpp
inline float tan(float _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne la valeur tangente de l’argument

## <a name="tanf"></a><a name="tanf"></a>Tanf

Calcule la valeur tangente de l’argument

```cpp
inline float tanf(float _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne la valeur tangente de l’argument

## <a name="tanh"></a><a name="tanh"></a>tanh tanh

Calcule la valeur tangente hyperbolique de l’argument

```cpp
inline float tanh(float _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne la valeur tangente hyperbolique de l’argument

## <a name="tanhf"></a><a name="tanhf"></a>tanhf

Calcule la valeur tangente hyperbolique de l’argument

```cpp
inline float tanhf(float _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne la valeur tangente hyperbolique de l’argument

## <a name="trunc"></a><a name="trunc"></a>Trunc

Tronque l’argument à la composante integer

```cpp
inline float trunc(float _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne la composante integer de l’argument

## <a name="truncf"></a><a name="truncf"></a>truncf

Tronque l’argument à la composante integer

```cpp
inline float truncf(float _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne la composante integer de l’argument

## <a name="requirements"></a>Spécifications

**En-tête:** amp_math.h **Namespace:** Concurrency::fast_math

## <a name="see-also"></a>Voir aussi

[Concurrency::fast_math, espace de noms](concurrency-fast-math-namespace.md)
