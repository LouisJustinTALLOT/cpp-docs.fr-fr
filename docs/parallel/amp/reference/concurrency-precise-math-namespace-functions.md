---
title: Concurrency::precise_math, fonctions de l’espace de noms
ms.date: 11/04/2016
f1_keywords:
- amp_math/Concurrency::precise_math::acos
- amp_math/Concurrency::precise_math::acosh
- amp_math/Concurrency::precise_math::acoshf
- amp_math/Concurrency::precise_math::asinf
- amp_math/Concurrency::precise_math::asinh
- amp_math/Concurrency::precise_math::atan
- amp_math/Concurrency::precise_math::atan2
- amp_math/Concurrency::precise_math::atanf
- amp_math/Concurrency::precise_math::atanh
- amp_math/Concurrency::precise_math::cbrt
- amp_math/Concurrency::precise_math::cbrtf
- amp_math/Concurrency::precise_math::ceilf
- amp_math/Concurrency::precise_math::copysign
- amp_math/Concurrency::precise_math::cos
- amp_math/Concurrency::precise_math::cosf
- amp_math/Concurrency::precise_math::coshf
- amp_math/Concurrency::precise_math::cospi
- amp_math/Concurrency::precise_math::erf
- amp_math/Concurrency::precise_math::erfc
- amp_math/Concurrency::precise_math::erfcinv
- amp_math/Concurrency::precise_math::erfcinvf
- amp_math/Concurrency::precise_math::erfinv
- amp_math/Concurrency::precise_math::erfinvf
- amp_math/Concurrency::precise_math::exp10
- amp_math/Concurrency::precise_math::exp10f
- amp_math/Concurrency::precise_math::exp2f
- amp_math/Concurrency::precise_math::expf
- amp_math/Concurrency::precise_math::expm1f
- amp_math/Concurrency::precise_math::fabs
- amp_math/Concurrency::precise_math::floor
- amp_math/Concurrency::precise_math::fdim
- amp_math/Concurrency::precise_math::floorf
- amp_math/Concurrency::precise_math::fmaf
- amp_math/Concurrency::precise_math::fmaxf
- amp_math/Concurrency::precise_math::fmin
- amp_math/Concurrency::precise_math::fmod
- amp_math/Concurrency::precise_math::fmodf
- amp_math/Concurrency::precise_math::frexp
- amp_math/Concurrency::precise_math::frexpf
- amp_math/Concurrency::precise_math::hypotf
- amp_math/Concurrency::precise_math::ilogb
- amp_math/Concurrency::precise_math::isfinite
- amp_math/Concurrency::precise_math::isinf
- amp_math/Concurrency::precise_math::isnormal
- amp_math/Concurrency::precise_math::ldexp
- amp_math/Concurrency::precise_math::lgamma
- amp_math/Concurrency::precise_math::lgammaf
- amp_math/Concurrency::precise_math::log10
- amp_math/Concurrency::precise_math::log10f
- amp_math/Concurrency::precise_math::log1pf
- amp_math/Concurrency::precise_math::log2
- amp_math/Concurrency::precise_math::logb
- amp_math/Concurrency::precise_math::logbf
- amp_math/Concurrency::precise_math::modf
- amp_math/Concurrency::precise_math::modff
- amp_math/Concurrency::precise_math::nanf
- amp_math/Concurrency::precise_math::nearbyint
- amp_math/Concurrency::precise_math::nextafter
- amp_math/Concurrency::precise_math::nextafterf
- amp_math/Concurrency::precise_math::phif
- amp_math/Concurrency::precise_math::pow
- amp_math/Concurrency::precise_math::probit
- amp_math/Concurrency::precise_math::probitf
- amp_math/Concurrency::precise_math::rcbrtf
- amp_math/Concurrency::precise_math::remainder
- amp_math/Concurrency::precise_math::remquo
- amp_math/Concurrency::precise_math::remquof
- amp_math/Concurrency::precise_math::roundf
- amp_math/Concurrency::precise_math::rsqrt
- amp_math/Concurrency::precise_math::scalb
- amp_math/Concurrency::precise_math::scalbf
- amp_math/Concurrency::precise_math::scalbnf
- amp_math/Concurrency::precise_math::signbit
- amp_math/Concurrency::precise_math::sin
- amp_math/Concurrency::precise_math::sincos
- amp_math/Concurrency::precise_math::sinf
- amp_math/Concurrency::precise_math::sinh
- amp_math/Concurrency::precise_math::sinpi
- amp_math/Concurrency::precise_math::sinpif
- amp_math/Concurrency::precise_math::sqrtf
- amp_math/Concurrency::precise_math::tan
- amp_math/Concurrency::precise_math::tanh
- amp_math/Concurrency::precise_math::tanhf
- amp_math/Concurrency::precise_math::tanpif
- amp_math/Concurrency::precise_math::tgamma
- amp_math/Concurrency::precise_math::trunc
- amp_math/Concurrency::precise_math::truncf
ms.assetid: fae53ab4-d1c5-45bb-a6a0-a74258e9aea3
ms.openlocfilehash: ee6ab2313fbdc288ebba1b3fdacf192b7b578eb6
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81321853"
---
# <a name="concurrencyprecise_math-namespace-functions"></a>Concurrency::precise_math, fonctions de l’espace de noms

||||
|-|-|-|
|[Acos](#acos)|[acosf](#acosf)|[acosh acosh](#acosh)|
|[acoshf](#acoshf)|[Asin](#asin)|[asinf](#asinf)|
|[asinh](#asinh)|[asinhf](#asinhf)|[Atan](#atan)|
|[atan2](#atan2)|[atan2f](#atan2f)|[atanf](#atanf)|
|[atanh atanh](#atanh)|[atanhf](#atanhf)|[cbrt](#cbrt)|
|[cbrtf](#cbrtf)|[ceil](#ceil)|[ceilf](#ceilf)|
|[copysign](#copysign)|[copysignf](#copysignf)|[Cos](#cos)|
|[cosf](#cosf)|[cosh](#cosh)|[coshf](#coshf)|
|[cospi (cospi)](#cospi)|[cospif](#cospif)|[Erf](#erf)|
|[erfc](#erfc)|[erfcf](#erfcf)|[erfcinv](#erfcinv)|
|[erfcinvf](#erfcinvf)|[erff](#erff)|[erfinv](#erfinv)|
|[erfinvf](#erfinvf)|[Exp](#exp)|[exp10](#exp10)|
|[exp10f](#exp10f)|[exp2](#exp2)|[exp2f](#exp2f)|
|[expf](#expf)|[expm1](#expm1)|[expm1f](#expm1f)|
|[fabs](#fabs)|[fabsf](#fabsf)|[Étage](#floor)|
|[fdim](#fdim)|[fdimf](#fdimf)||
|[floorf](#floorf)|[fma](#fma)|[fmaf](#fmaf)|
[fmax](#fmax)|[fmaxf](#fmaxf)||
|[fmin](#fmin)|[fminf](#fminf)|[fmod](#fmod)|
|[fmodf](#fmodf)|[fpclassify](#fpclassify)|[frexp](#frexp)|
|[frexpf frexpf](#frexpf)|[hypot](#hypot)|[hypotf hypotf](#hypotf)|
|[ilogb](#ilogb)|[ilogbf](#ilogbf)|[isfinite](#isfinite)|
|[isinf](#isinf)|[isnan (isnan)](#isnan)|[isnormal](#isnormal)|
|[ldexp](#ldexp)|[ldexpf (ldexpf)](#ldexpf)|[lgamma](#lgamma)|
|[lgammaf](#lgammaf)|[rapport](#log)|[journal10](#log10)|
|[log10f](#log10f)|[log1p](#log1p)|[log1pf](#log1pf)|
|[log2](#log2)|[log2f](#log2f)|[logb](#logb)|
|[logbf](#logbf)|[logf](#logf)|[modf](#modf)|
|[modff](#modff)|[NaN](#nan)|[nanf](#nanf)|
|[nearbyint](#nearbyint)|[nearbyintf](#nearbyintf)|[nextafter](#nextafter)|
|[nextafterf](#nextafterf)|[Phi](#phi)|[phif](#phif)|
|[Pow](#pow)|[powf](#powf)|[Probit](#probit)|
|[probitf](#probitf)|[rcbrt rcbrt](#rcbrt)|[rcbrtf (rcbrtf)](#rcbrtf)|
|[Reste](#remainder)|[remainderf](#remainderf)|[remquo](#remquo)|
|[remquof](#remquof)|[Rond](#round)|[roundf](#roundf)|
|[rsqrt](#rsqrt)|[rsqrtf](#rsqrtf)|[échauds](#scalb)|
|[scalbf](#scalbf)|[scalbn](#scalbn)|[scalbnf](#scalbnf)|
|[signbit](#signbit)|[signbitf](#signbitf)|[Péché](#sin)|
|[sincos](#sincos)|[sincosf](#sincosf)|[sinf](#sinf)|
|[sinh](#sinh)|[sinhf](#sinhf)|[sinpi](#sinpi)|
|[sinpif sinpif](#sinpif)|[Sqrt](#sqrt)|[sqrtf](#sqrtf)|
|[Tan](#tan)|[tanf](#tanf)|[tanh tanh](#tanh)|
|[tanhf](#tanhf)|[tanpi tanpi](#tanpi)|[tanpif](#tanpif)|
|[tgamma](#tgamma)|[tgammaf](#tgammaf)|[Trunc](#trunc)|
|[truncf](#truncf)|

## <a name="acos"></a><a name="acos"></a>Acos

Calcule l’arccosine de l’argument

```cpp
inline float acos(float _X) restrict(amp);

inline double acos(double _X) restrict(amp);
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

## <a name="acosh"></a><a name="acosh"></a>acosh acosh

Calcule la cosine hyperbolique inverse de l’argument

```cpp
inline float acosh(float _X) restrict(amp);

inline double acosh(double _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne la valeur cosine hyperbolique inverse de l’argument

## <a name="acoshf"></a><a name="acoshf"></a>acoshf

Calcule la cosine hyperbolique inverse de l’argument

```cpp
inline float acoshf(float _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne la valeur cosine hyperbolique inverse de l’argument

## <a name="asin"></a><a name="asin"></a>Asin

Calcule l’arcsine de l’argument

```cpp
inline float asin(float _X) restrict(amp);

inline double asin(double _X) restrict(amp);
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

## <a name="asinh"></a><a name="asinh"></a>asinh

Calcule le sinus hyperbolique inverse de l’argument

```cpp
inline float asinh(float _X) restrict(amp);

inline double asinh(double _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne la valeur sine hyperbolique inverse de l’argument

## <a name="asinhf"></a><a name="asinhf"></a>asinhf

Calcule le sinus hyperbolique inverse de l’argument

```cpp
inline float asinhf(float _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne la valeur sine hyperbolique inverse de l’argument

## <a name="atan"></a><a name="atan"></a>Atan

Calcule l'arc tangente de l'argument.

```cpp
inline float atan(float _X) restrict(amp);

inline double atan(double _X) restrict(amp);
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

inline double atan2(
    double _Y,
    double _X) restrict(amp);
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

## <a name="atanh"></a><a name="atanh"></a>atanh atanh

Calcule la tangente hyperbolique inverse de l’argument

```cpp
inline float atanh(float _X) restrict(amp);

inline double atanh(double _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne la valeur hyperbolique inverse tangente de l’argument

## <a name="atanhf"></a><a name="atanhf"></a>atanhf atanhf

Calcule la tangente hyperbolique inverse de l’argument

```cpp
inline float atanhf(float _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne la valeur hyperbolique inverse tangente de l’argument

## <a name="cbrt"></a><a name="cbrt"></a>Cbrt

Calcule la véritable racine cube de l’argument

```cpp
inline float cbrt(float _X) restrict(amp);

inline double cbrt(double _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne la véritable racine cube de l’argument

## <a name="cbrtf"></a><a name="cbrtf"></a>cbrtf (cbrtf)

Calcule la véritable racine cube de l’argument

```cpp
inline float cbrtf(float _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne la véritable racine cube de l’argument

## <a name="ceil"></a><a name="ceil"></a>Ceil

Calcule le plafond de l’argument

```cpp
inline float ceil(float _X) restrict(amp);

inline double ceil(double _X) restrict(amp);
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

## <a name="copysign"></a><a name="copysign"></a>copysign

Produit une valeur de l’ampleur de _X et le signe de _Y

```cpp
inline float copysign(
    float _X,
    float _Y) restrict(amp);

inline double copysign(
    double _X,
    double _Y) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

*_Y*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne une valeur de l’ampleur de _X et le signe de _Y

## <a name="copysignf"></a><a name="copysignf"></a>copysignf

Produit une valeur de l’ampleur de _X et le signe de _Y

```cpp
inline float copysignf(
    float _X,
    float _Y) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

*_Y*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne une valeur de l’ampleur de _X et le signe de _Y

## <a name="cos"></a><a name="cos"></a>Cos

Calcule le cosinus de l'argument.

```cpp
inline float cos(float _X) restrict(amp);

inline double cos(double _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne la valeur cosine de l’argument

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

## <a name="cosh"></a><a name="cosh"></a>Cosh

Calcule la valeur cosine hyperbolique de l’argument

```cpp
inline float cosh(float _X) restrict(amp);

inline double cosh(double _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne la valeur cosine hyperbolique de l’argument

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

## <a name="cospi"></a><a name="cospi"></a>cospi (cospi)

Calcule la valeur cosine de pi \* _X

```cpp
inline float cospi(float _X) restrict(amp);

inline double cospi(double _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne la valeur cosine de pi \* _X

## <a name="cospif"></a><a name="cospif"></a>cospif

Calcule la valeur cosine de pi \* _X

```cpp
inline float cospif(float _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne la valeur cosine de pi \* _X

## <a name="erf"></a><a name="erf"></a>Erf

Calcule la fonction d’erreur de _X

```cpp
inline float erf(float _X) restrict(amp);

inline double erf(double _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne la fonction d’erreur de _X

## <a name="erfc"></a><a name="erfc"></a>erfc

Calcule la fonction d’erreur complémentaire de _X

```cpp
inline float erfc(float _X) restrict(amp);

inline double erfc(double _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne la fonction d’erreur complémentaire de _X

## <a name="erfcf"></a><a name="erfcf"></a>erfcf

Calcule la fonction d’erreur complémentaire de _X

```cpp
inline float erfcf(float _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne la fonction d’erreur complémentaire de _X

## <a name="erfcinv"></a><a name="erfcinv"></a>erfcinv

Calcule la fonction d’erreur complémentaire inverse de _X

```cpp
inline float erfcinv(float _X) restrict(amp);

inline double erfcinv(double _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne la fonction d’erreur complémentaire inverse de _X

## <a name="erfcinvf"></a><a name="erfcinvf"></a>erfcinvf

Calcule la fonction d’erreur complémentaire inverse de _X

```cpp
inline float erfcinvf(float _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne la fonction d’erreur complémentaire inverse de _X

## <a name="erff"></a><a name="erff"></a>erff

Calcule la fonction d’erreur de _X

```cpp
inline float erff(float _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne la fonction d’erreur de _X

## <a name="erfinv"></a><a name="erfinv"></a>erfinv

Calcule la fonction d’erreur inverse de _X

```cpp
inline float erfinv(float _X) restrict(amp);

inline double erfinv(double _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne la fonction d’erreur inverse de _X

## <a name="erfinvf"></a><a name="erfinvf"></a>erfinvf

Calcule la fonction d’erreur inverse de _X

```cpp
inline float erfinvf(float _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne la fonction d’erreur inverse de _X

## <a name="exp10"></a><a name="exp10"></a>exp10

Calcule l’exponentielle de base-10 de l’argument

```cpp
inline float exp10(float _X) restrict(amp);

inline double exp10(double _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne l’exponentiel de base-10 de l’argument

## <a name="exp10f"></a><a name="exp10f"></a>exp10f

Calcule l’exponentielle de base-10 de l’argument

```cpp
inline float exp10f(float _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne l’exponentiel de base-10 de l’argument

## <a name="expm1"></a><a name="expm1"></a>expm1

Calcule l’exponentielle de base e de l’argument, moins 1

```cpp
inline float expm1(float exponent) restrict(amp);

inline double expm1(double exponent) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*Exposant*<br/>
Le terme *n* exponentiel `e`n de `e` l’expression mathématique <sup>n</sup>, où est la base du logarithme naturel.

### <a name="return-value"></a>Valeur de retour

Retourne l'exponentielle de base e de l'argument, moins 1

## <a name="expm1f"></a><a name="expm1f"></a>expm1f

Calcule l’exponentielle de base e de l’argument, moins 1

```cpp
inline float expm1f(float exponent) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*Exposant*<br/>
Le terme *n* exponentiel `e`n de `e` l’expression mathématique <sup>n</sup>, où est la base du logarithme naturel.

### <a name="return-value"></a>Valeur de retour

Retourne l'exponentielle de base e de l'argument, moins 1

## <a name="exp"></a><a name="exp"></a>Exp

Calcule l’exponentiel de base-e de l’argument

```cpp
inline float exp(float _X) restrict(amp);

inline double exp(double _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne l’exponentiel de base-e de l’argument

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

## <a name="exp2"></a><a name="exp2"></a>exp2

Calcule l’exponentielle de base-2 de l’argument

```cpp
inline float exp2(float _X) restrict(amp);

inline double exp2(double _X) restrict(amp);
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

## <a name="fabs"></a><a name="fabs"></a>fabs

Retourne la valeur absolue de l’argument

```cpp
inline float fabs(float _X) restrict(amp);

inline double fabs(double _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

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

## <a name="fdim"></a><a name="fdim"></a>fdim fdim

Calcule la différence positive entre les arguments.

```cpp
inline float fdim(
   float _X,
   float _Y
) restrict(amp);
inline double fdim(
   double _X,
   double _Y
) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
_Y de valeur *à* point flottant<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

La différence entre _X et _Y si _X est plus grande que _Y; autrement, 0.

## <a name="fdimf"></a><a name="fdimf"></a>fdimf

Calcule la différence positive entre les arguments.

```cpp
inline float fdimf(
   float _X,
   float _Y
) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
_Y de valeur *à* point flottant<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

La différence entre _X et _Y si _X est plus grande que _Y; autrement, 0.

## <a name="floor"></a><a name="floor"></a>Étage

Calcule le plancher de l’argument

```cpp
inline float floor(float _X) restrict(amp);

inline double floor(double _X) restrict(amp);
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

## <a name="a-namefma-fma"></a><a name="fma">Fma

Calcule le produit des premiers et deuxièmes arguments spécifiés, puis ajoute le troisième argument spécifié au résultat; l’ensemble du calcul est effectué en une seule opération.

```cpp
inline float fma(
   float _X,
   float _Y,
   float _Z
) restrict(amp);

inline double fma(
   double _X,
   double _Y,
   double _Z
) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Le premier argument de point flottant.
*_Y*<br/>
Le deuxième argument de point flottant.
*_Z*<br/>
Le troisième argument de point flottant.

### <a name="return-value"></a>Valeur de retour

Le résultat de l’expression \* (_X _Y) _Z. L’ensemble du calcul est effectué en une seule opération; c’est-à-dire que les sous-expressions sont calculées à une précision infinie, et seul le résultat final est arrondi.

## <a name="fmaf"></a><a name="fmaf"></a>fmaf fmaf

Calcule le produit des premiers et deuxièmes arguments spécifiés, puis ajoute le troisième argument spécifié au résultat; l’ensemble du calcul est effectué en une seule opération.

```cpp
inline float fmaf(
   float _X,
   float _Y,
   float _Z
) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Le premier argument de point flottant.
*_Y*<br/>
Le deuxième argument de point flottant.
*_Z*<br/>
Le troisième argument de point flottant.

### <a name="return-value"></a>Valeur de retour

Le résultat de l’expression \* (_X _Y) _Z. L’ensemble du calcul est effectué en une seule opération; c’est-à-dire que les sous-expressions sont calculées à une précision infinie, et seul le résultat final est arrondi.

## <a name="fmax"></a><a name="fmax"></a>Fmax

Déterminer la valeur numérique maximale des arguments

```cpp
inline float fmax(
    float _X,
    float _Y) restrict(amp);

inline double fmax(
    double _X,
    double _Y) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

*_Y*<br/>
Valeur à virgule flottante

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
inline float fmin(
    float _X,
    float _Y) restrict(amp);

inline double fmin(
    double _X,
    double _Y) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

*_Y*<br/>
Valeur à virgule flottante

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

## <a name="fmod-function-c-amp"></a><a name="fmod"></a>fonction fmod (AMP DE C)

Calcule le reste du premier argument spécifié divisé par le deuxième argument spécifié.

```cpp
inline float fmod(
    float _X,
    float _Y) restrict(amp);

inline double fmod(
    double _X,
    double _Y) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Le premier argument de point flottant.

*_Y*<br/>
Le deuxième argument de point flottant.

### <a name="return-value"></a>Valeur de retour

Le reste `_X` de `_Y`divisé par ; `_X`  -  `_Y` `_X`  -  `_Y`c’est-à-dire, la valeur de *n*, où *n* est un tout `_Y`integer de telle sorte que l’ampleur de *n* est inférieure à l’ampleur de .

## <a name="fmodf"></a><a name="fmodf"></a>fmodf

Calcule le reste du premier argument spécifié divisé par le deuxième argument spécifié.

```cpp
inline float fmodf(
    float _X,
    float _Y) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Le premier argument de point flottant.

*_Y*<br/>
Le deuxième argument de point flottant.

### <a name="return-value"></a>Valeur de retour

Le reste `_X` de `_Y`divisé par ; `_X`  -  `_Y` `_X`  -  `_Y`c’est-à-dire, la valeur de *n*, où *n* est un tout `_Y`integer de telle sorte que l’ampleur de *n* est inférieure à l’ampleur de .

## <a name="fpclassify"></a><a name="fpclassify"></a>fpclassify

Classifie la valeur de l’argument comme NaN, infini, normal, subnormal, zéro

```cpp
inline int fpclassify(float _X) restrict(amp);

inline int fpclassify(double _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne la valeur de la classification des nombres macro appropriée à la valeur de l’argument.

## <a name="frexp"></a><a name="frexp"></a>frexp frexp

Obtient la mantissa et l’exposant de _X

```cpp
inline float frexp(
    float _X,
    _Out_ int* _Exp) restrict(amp);

inline double frexp(
    double _X,
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

## <a name="hypot"></a><a name="hypot"></a>hypot

Calcule la racine carrée de la somme des carrés de _X et _Y

```cpp
inline float hypot(
    float _X,
    float _Y) restrict(amp);

inline double hypot(
    double _X,
    double _Y) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

*_Y*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne la racine carrée de la somme des carrés de _X et de _Y

## <a name="hypotf"></a><a name="hypotf"></a>hypotf hypotf

Calcule la racine carrée de la somme des carrés de _X et _Y

```cpp
inline float hypotf(
    float _X,
    float _Y) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

*_Y*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne la racine carrée de la somme des carrés de _X et de _Y

## <a name="ilogb"></a><a name="ilogb"></a>ilogb (ilogb)

Extraire l’exposant de _X comme une valeur int signée

```cpp
inline int ilogb(float _X) restrict(amp);

inline int ilogb(double _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne l’exposant de _X comme une valeur int signé

## <a name="ilogbf"></a><a name="ilogbf"></a>ilogbf

Extraire l’exposant de _X comme une valeur int signée

```cpp
inline int ilogbf(float _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne l’exposant de _X comme une valeur int signé

## <a name="isfinite"></a><a name="isfinite"></a>isfinite

Détermine si l’argument a une valeur limitée

```cpp
inline int isfinite(float _X) restrict(amp);

inline int isfinite(double _X) restrict(amp);
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

inline int isinf(double _X) restrict(amp);
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

inline int isnan(double _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne une valeur non zéro si et seulement si l’argument a une valeur NaN

## <a name="isnormal"></a><a name="isnormal"></a>isnormal

Détermine si l’argument est normal

```cpp
inline int isnormal(float _X) restrict(amp);

inline int isnormal(double _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne une valeur non zéro si et seulement si l’argument a une valeur normale

## <a name="ldexp"></a><a name="ldexp"></a>ldexp

Calcule un nombre réel de la mantissa spécifiée et exposant.

```cpp
inline float ldexp(
    float _X,
    int _Exp) restrict(amp);

inline double ldexp(
    double _X,
    double _Exp) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à point flottant, mantissa

*_Exp*<br/>
Valeur integer, exposant

### <a name="return-value"></a>Valeur de retour

Retours _X \* 2 _Exp

## <a name="ldexpf"></a><a name="ldexpf"></a>ldexpf (ldexpf)

Calcule un nombre réel de la mantissa spécifiée et exposant.

```cpp
inline float ldexpf(
    float _X,
    int _Exp) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à point flottant, mantissa

*_Exp*<br/>
Valeur integer, exposant

### <a name="return-value"></a>Valeur de retour

Retours _X \* 2 _Exp

## <a name="lgamma"></a><a name="lgamma"></a>lgamma lgamma

Calcule le logarithme naturel de la valeur absolue du gamma de l’argument

```cpp
inline float lgamma(
    float _X,
    _Out_ int* _Sign) restrict(amp);

inline double lgamma(
    double _X,
    _Out_ int* _Sign) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

*_Sign*<br/>
Retourne le signe

### <a name="return-value"></a>Valeur de retour

Retourne le logarithme naturel de la valeur absolue du gamma de l’argument

## <a name="lgammaf"></a><a name="lgammaf"></a>lgammaf (lgammaf)

Calcule le logarithme naturel de la valeur absolue du gamma de l’argument

```cpp
inline float lgammaf(
    float _X,
    _Out_ int* _Sign) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

*_Sign*<br/>
Retourne le signe

### <a name="return-value"></a>Valeur de retour

Retourne le logarithme naturel de la valeur absolue du gamma de l’argument

## <a name="log"></a><a name="log"></a>rapport

Calcule le logarithme de base-e de l’argument

```cpp
inline float log(float _X) restrict(amp);

inline double log(double _X) restrict(amp);
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

inline double log10(double _X) restrict(amp);
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

## <a name="log1p"></a><a name="log1p"></a>log1p

Calcule le logarithme de base-e de 1 plus l’argument

```cpp
inline float log1p(float _X) restrict(amp);

inline double log1p(double _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne le logarithme de base-e de 1 plus l’argument

## <a name="log1pf"></a><a name="log1pf"></a>log1pf

Calcule le logarithme de base-e de 1 plus l’argument

```cpp
inline float log1pf(float _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne le logarithme de base-e de 1 plus l’argument

## <a name="log2"></a><a name="log2"></a>log2

Calcule le logarithme de base-2 de l’argument

```cpp
inline float log2(float _X) restrict(amp);

inline double log2(double _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne le logarithme de base-10 de l’argument

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

## <a name="logb"></a><a name="logb"></a>logb

Extrait l’exposant de _X, comme une valeur integer signée dans le format de point flottant

```cpp
inline float logb(float _X) restrict(amp);

inline double logb(double _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne l’exposant signé de _X

## <a name="logbf"></a><a name="logbf"></a>logbf

Extrait l’exposant de _X, comme une valeur integer signée dans le format de point flottant

```cpp
inline float logbf(float _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne l’exposant signé de _X

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

Divise l’argument spécifié en parties fractionnées et integer.

```cpp
inline float modf(
    float _X,
    _Out_ float* _Iptr) restrict(amp);

inline double modf(
    double _X,
    _Out_ double* _Iptr) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

*_Iptr*<br/>
[out] La partie integer de `_X`, comme une valeur de point flottant.

### <a name="return-value"></a>Valeur de retour

La partie fractionnaire `_X`signée de .

## <a name="modff"></a><a name="modff"></a>modff (modff)

Divise l’argument spécifié en parties fractionnées et integer.

```cpp
inline float modff(
    float _X,
    _Out_ float* _Iptr) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

*_Iptr*<br/>
La partie integer de `_X`, comme une valeur de point flottant.

### <a name="return-value"></a>Valeur de retour

Retourne la partie fractionnaire signée de `_X`.

## <a name="nan"></a><a name="nan"></a>Nan

Retourne un NaN tranquille

```cpp
inline double nan(int _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur entière

### <a name="return-value"></a>Valeur de retour

Retourne un NaN silencieux, s’il est disponible, avec le contenu indiqué dans _X

## <a name="nanf"></a><a name="nanf"></a>nanf (nanf)

Retourne un NaN tranquille

```cpp
inline float nanf(int _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur entière

### <a name="return-value"></a>Valeur de retour

Retourne un NaN silencieux, s’il est disponible, avec le contenu indiqué dans _X

## <a name="nearbyint"></a><a name="nearbyint"></a>nearbyint

Arrondit l’argument à une valeur integer dans le format de point flottant, en utilisant la direction arrondie actuelle.

```cpp
inline float nearbyint(float _X) restrict(amp);

inline double nearbyint(double _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne la valeur arrondie de l’intégrant.

## <a name="nearbyintf"></a><a name="nearbyintf"></a>nearbyintf

Arrondit l’argument à une valeur integer dans le format de point flottant, en utilisant la direction arrondie actuelle.

```cpp
inline float nearbyintf(float _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne la valeur arrondie de l’intégrant.

## <a name="nextafter"></a><a name="nextafter"></a>nextafter

Déterminer la valeur représentante suivante, dans le type de la fonction, après _X dans la direction de _Y

```cpp
inline float nextafter(
    float _X,
    float _Y) restrict(amp);

inline double nextafter(
    double _X,
    double _Y) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

*_Y*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne la valeur représentante suivante, dans le type de la fonction, après _X dans la direction de _Y

## <a name="nextafterf"></a><a name="nextafterf"></a>nextafterf

Déterminer la valeur représentante suivante, dans le type de la fonction, après _X dans la direction de _Y

```cpp
inline float nextafterf(
    float _X,
    float _Y) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

*_Y*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne la valeur représentante suivante, dans le type de la fonction, après _X dans la direction de _Y

## <a name="phi"></a><a name="phi"></a>Phi

Retourne la fonction cumulative de distribution de l’argument

```cpp
inline float phi(float _X) restrict(amp);

inline double phi(double _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne la fonction cumulative de distribution de l’argument

## <a name="phif"></a><a name="phif"></a>phif

Retourne la fonction cumulative de distribution de l’argument

```cpp
inline float phif(float _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne la fonction cumulative de distribution de l’argument

## <a name="pow"></a><a name="pow"></a>Pow

Calcule _X portés à la puissance de _Y

```cpp
inline float pow(
    float _X,
    float _Y) restrict(amp);

inline double pow(
    double _X,
    double _Y) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur de point flottant, base

*_Y*<br/>
Valeur à point flottant, exposant

### <a name="return-value"></a>Valeur de retour

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

## <a name="probit"></a><a name="probit"></a>Probit

Retourne la fonction de distribution cumulative inverse de l’argument

```cpp
inline float probit(float _X) restrict(amp);

inline double probit(double _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne la fonction de distribution cumulative inverse de l’argument

## <a name="probitf"></a><a name="probitf"></a>probitf

Retourne la fonction de distribution cumulative inverse de l’argument

```cpp
inline float probitf(float _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne la fonction de distribution cumulative inverse de l’argument

## <a name="rcbrt"></a><a name="rcbrt"></a>rcbrt rcbrt

Retourne la réciprocité de la racine cube de l’argument

```cpp
inline float rcbrt(float _X) restrict(amp);

inline double rcbrt(double _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne la réciprocité de la racine cube de l’argument

## <a name="rcbrtf"></a><a name="rcbrtf"></a>rcbrtf (rcbrtf)

Retourne la réciprocité de la racine cube de l’argument

```cpp
inline float rcbrtf(float _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne la réciprocité de la racine cube de l’argument

## <a name="remainder"></a><a name="remainder"></a>Reste

Calcule le reste: _X REM _Y

```cpp
inline float remainder(
    float _X,
    float _Y) restrict(amp);

inline double remainder(
    double _X,
    double _Y) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

*_Y*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retours _X _Y REM

## <a name="remainderf"></a><a name="remainderf"></a>remainderf

Calcule le reste: _X REM _Y

```cpp
inline float remainderf(
    float _X,
    float _Y) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

*_Y*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retours _X _Y REM

## <a name="remquo"></a><a name="remquo"></a>remquo remquo

Calcule le reste du premier argument spécifié divisé par le deuxième argument spécifié. Calcule également le quotient du significand du premier argument spécifié divisé par le significand du deuxième argument spécifié, et renvoie le quotient à l’aide de l’emplacement spécifié dans le troisième argument.

```cpp
inline float remquo(
    float _X,
    float _Y,
    _Out_ int* _Quo) restrict(amp);

inline double remquo(
    double _X,
    double _Y,
    _Out_ int* _Quo) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Le premier argument de point flottant.

*_Y*<br/>
Le deuxième argument de point flottant.

*_Quo*<br/>
[out] L’adresse d’un intégrant qui est utilisé pour retourner le `_X` quotient des bits `_Y`fractionnels de divisé par les bits fractionnels de .

### <a name="return-value"></a>Valeur de retour

Retourne le `_X` reste `_Y`de divisé par .

## <a name="remquof"></a><a name="remquof"></a>remquof

Calcule le reste du premier argument spécifié divisé par le deuxième argument spécifié. Calcule également le quotient du significand du premier argument spécifié divisé par le significand du deuxième argument spécifié, et renvoie le quotient à l’aide de l’emplacement spécifié dans le troisième argument.

```cpp
inline float remquof(
    float _X,
    float _Y,
    _Out_ int* _Quo) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Le premier argument de point flottant.

*_Y*<br/>
Le deuxième argument de point flottant.

*_Quo*<br/>
[out] L’adresse d’un intégrant qui est utilisé pour retourner le `_X` quotient des bits `_Y`fractionnels de divisé par les bits fractionnels de .

### <a name="return-value"></a>Valeur de retour

Retourne le `_X` reste `_Y`de divisé par .

## <a name="round"></a><a name="round"></a>Rond

Les rondes _X à l’intégrant le plus proche

```cpp
inline float round(float _X) restrict(amp);

inline double round(double _X) restrict(amp);
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

inline double rsqrt(double _X) restrict(amp);
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

## <a name="scalb"></a><a name="scalb"></a>échauds

Multiplie _X en FLT_RADIX à la _Y de puissance

```cpp
inline float scalb(
    float _X,
    float _Y) restrict(amp);

inline double scalb(
    double _X,
    double _Y) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

*_Y*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retours _X \* (FLT_RADIX _Y)

## <a name="scalbf"></a><a name="scalbf"></a>scalbf

Multiplie _X en FLT_RADIX à la _Y de puissance

```cpp
inline float scalbf(
    float _X,
    float _Y) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

*_Y*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retours _X \* (FLT_RADIX _Y)

## <a name="scalbn"></a><a name="scalbn"></a>scalbn

Multiplie _X en FLT_RADIX à la _Y de puissance

```cpp
inline float scalbn(
    float _X,
    int _Y) restrict(amp);

inline double scalbn(
    double _X,
    int _Y) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

*_Y*<br/>
Valeur entière

### <a name="return-value"></a>Valeur de retour

Retours _X \* (FLT_RADIX _Y)

## <a name="scalbnf"></a><a name="scalbnf"></a>scalbnf

Multiplie _X en FLT_RADIX à la _Y de puissance

```cpp
inline float scalbnf(
    float _X,
    int _Y) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

*_Y*<br/>
Valeur entière

### <a name="return-value"></a>Valeur de retour

Retours _X \* (FLT_RADIX _Y)

## <a name="signbit"></a><a name="signbit"></a>signbit

Détermine si le signe de _X est négatif

```cpp
inline int signbit(float _X) restrict(amp);

inline int signbit(double _X) restrict(amp);
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

inline double sin(double _X) restrict(amp);
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
    _Out_ float* _S,
    _Out_ float* _C) restrict(amp);

inline void sincos(
    double _X,
    _Out_ double* _S,
    _Out_ double* _C) restrict(amp);
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
    _Out_ float* _S,
    _Out_ float* _C) restrict(amp);
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

inline double sinh(double _X) restrict(amp);
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

## <a name="sinpi"></a><a name="sinpi"></a>sinpi

Calcule la valeur sinusoïale de pi \* _X

```cpp
inline float sinpi(float _X) restrict(amp);

inline double sinpi(double _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne la valeur sinusoïale de pi \* _X

## <a name="sinpif"></a><a name="sinpif"></a>sinpif sinpif

Calcule la valeur sinusoïale de pi \* _X

```cpp
inline float sinpif(float _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne la valeur sinusoïale de pi \* _X

## <a name="sqrt"></a><a name="sqrt"></a>Sqrt

Calcule la racine squre de l’argument

```cpp
inline float sqrt(float _X) restrict(amp);

inline double sqrt(double _X) restrict(amp);
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

inline double tan(double _X) restrict(amp);
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

inline double tanh(double _X) restrict(amp);
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

## <a name="tanpi"></a><a name="tanpi"></a>tanpi tanpi

Calcule la valeur tangente de pi \* _X

```cpp
inline float tanpi(float _X) restrict(amp);

inline double tanpi(double _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne la valeur tangente de pi \* _X

## <a name="tanpif"></a><a name="tanpif"></a>tanpif

Calcule la valeur tangente de pi \* _X

```cpp
inline float tanpif(float _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne la valeur tangente de pi \* _X

## <a name="tgamma"></a><a name="tgamma"></a>tgamma tgamma

Calcule la fonction gamma de _X

```cpp
inline float tgamma(float _X) restrict(amp);

inline double tgamma(double _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne le résultat de la fonction gamma de _X

## <a name="tgammaf"></a><a name="tgammaf"></a>tgammaf (tgammaf)

Calcule la fonction gamma de _X

```cpp
inline float tgammaf(float _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne le résultat de la fonction gamma de _X

## <a name="trunc"></a><a name="trunc"></a>Trunc

Tronque l’argument à la composante integer

```cpp
inline float trunc(float _X) restrict(amp);

inline double trunc(double _X) restrict(amp);
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

## <a name="see-also"></a>Voir aussi

[Concurrency::precise-math Namespace](concurrency-precise-math-namespace.md)
