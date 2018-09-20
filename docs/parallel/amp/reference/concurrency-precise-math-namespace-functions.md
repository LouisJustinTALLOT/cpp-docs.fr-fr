---
title: Fonctions d’espace de noms Concurrency::precise_math | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
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
dev_langs:
- C++
ms.assetid: fae53ab4-d1c5-45bb-a6a0-a74258e9aea3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: dac840ecb0d3dadd25387eebff9c28ff83213cbe
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46448530"
---
# <a name="concurrencyprecisemath-namespace-functions"></a>Fonctions d’espace de noms Concurrency::precise_math

||||
|-|-|-|
|[acos](#acos)|[acosf](#acosf)|[acosh](#acosh)|
|[acoshf](#acoshf)|[asin](#asin)|[asinf](#asinf)|
|[asinh](#asinh)|[asinhf](#asinhf)|[atan](#atan)|
|[atan2](#atan2)|[atan2f](#atan2f)|[atanf](#atanf)|
|[atanh](#atanh)|[atanhf](#atanhf)|[cbrt](#cbrt)|
|[cbrtf](#cbrtf)|[ceil](#ceil)|[ceilf](#ceilf)|
|[copysign](#copysign)|[copysignf](#copysignf)|[cos](#cos)|
|[cosf](#cosf)|[cosh](#cosh)|[coshf](#coshf)|
|[cospi](#cospi)|[cospif](#cospif)|[erf](#erf)|
|[erfc](#erfc)|[erfcf](#erfcf)|[erfcinv](#erfcinv)|
|[erfcinvf](#erfcinvf)|[erff](#erff)|[erfinv](#erfinv)|
|[erfinvf](#erfinvf)|[exp](#exp)|[exp10](#exp10)|
|[exp10f](#exp10f)|[exp2](#exp2)|[exp2f](#exp2f)|
|[expf](#expf)|[expm1](#expm1)|[expm1f](#expm1f)|
|[fabs](#fabs)|[fabsf](#fabsf)|[floor](#floor)|
|[fdim](#fdim)|[fdimf](#fdimf)||
|[floorf](#floorf)|[fma](#fma)|[fmaf](#fmaf)|
[fmax](#fmax)|[fmaxf](#fmaxf)||
|[fmin](#fmin)|[fminf](#fminf)|[fmod](#fmod)|
|[fmodf](#fmodf)|[fpclassify](#fpclassify)|[frexp](#frexp)|
|[frexpf](#frexpf)|[hypot](#hypot)|[hypotf](#hypotf)|
|[ilogb](#ilogb)|[ilogbf](#ilogbf)|[isfinite](#isfinite)|
|[isinf](#isinf)|[isnan](#isnan)|[isnormal](#isnormal)|
|[ldexp](#ldexp)|[ldexpf](#ldexpf)|[lgamma](#lgamma)|
|[lgammaf](#lgammaf)|[log](#log)|[log10](#log10)|
|[log10f](#log10f)|[log1p](#log1p)|[log1pf](#log1pf)|
|[log2](#log2)|[log2f](#log2f)|[logb](#logb)|
|[logbf](#logbf)|[logf](#logf)|[modf](#modf)|
|[modff](#modff)|[nan](#nan)|[nanf](#nanf)|
|[nearbyint](#nearbyint)|[nearbyintf](#nearbyintf)|[nextafter](#nextafter)|
|[nextafterf](#nextafterf)|[phi](#phi)|[phif](#phif)|
|[pow](#pow)|[powf](#powf)|[probit](#probit)|
|[probitf](#probitf)|[rcbrt](#rcbrt)|[rcbrtf](#rcbrtf)|
|[remainder](#remainder)|[remainderf](#remainderf)|[remquo](#remquo)|
|[remquof](#remquof)|[round](#round)|[roundf](#roundf)|
|[rsqrt](#rsqrt)|[rsqrtf](#rsqrtf)|[scalb](#scalb)|
|[scalbf](#scalbf)|[scalbn](#scalbn)|[scalbnf](#scalbnf)|
|[signbit](#signbit)|[signbitf](#signbitf)|[sin](#sin)|
|[sincos](#sincos)|[sincosf](#sincosf)|[sinf](#sinf)|
|[sinh](#sinh)|[sinhf](#sinhf)|[sinpi](#sinpi)|
|[sinpif](#sinpif)|[sqrt](#sqrt)|[sqrtf](#sqrtf)|
|[tan](#tan)|[tanf](#tanf)|[tanh](#tanh)|
|[tanhf](#tanhf)|[tanpi](#tanpi)|[tanpif](#tanpif)|
|[tgamma](#tgamma)|[tgammaf](#tgammaf)|[trunc](#trunc)|
|[truncf](#truncf)|

##  <a name="acos"></a>  acos

Calcule l’arc cosinus de l’argument

```
inline float acos(float _X) restrict(amp);

inline double acos(double _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne la valeur d’arc cosinus de l’argument

##  <a name="acosf"></a>  acosf

Calcule l’arc cosinus de l’argument

```
inline float acosf(float _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne la valeur d’arc cosinus de l’argument

##  <a name="acosh"></a>  ACOSH

Calcule le cosinus hyperbolique inverse de l’argument

```
inline float acosh(float _X) restrict(amp);

inline double acosh(double _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne la valeur de cosinus hyperbolique inverse de l’argument

##  <a name="acoshf"></a>  acoshf

Calcule le cosinus hyperbolique inverse de l’argument

```
inline float acoshf(float _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne la valeur de cosinus hyperbolique inverse de l’argument

##  <a name="asin"></a>  asin

Calcule l’arc sinus de l’argument

```
inline float asin(float _X) restrict(amp);

inline double asin(double _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne la valeur d’arc sinus de l’argument

##  <a name="asinf"></a>  asinf

Calcule l’arc sinus de l’argument

```
inline float asinf(float _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne la valeur d’arc sinus de l’argument

##  <a name="asinh"></a>  ASINH

Calcule le sinus hyperbolique inverse de l’argument

```
inline float asinh(float _X) restrict(amp);

inline double asinh(double _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne la valeur du sinus hyperbolique inverse de l’argument

##  <a name="asinhf"></a>  asinhf

Calcule le sinus hyperbolique inverse de l’argument

```
inline float asinhf(float _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne la valeur du sinus hyperbolique inverse de l’argument

##  <a name="atan"></a>  atan

Calcule l’arc tangente de l’argument

```
inline float atan(float _X) restrict(amp);

inline double atan(double _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne la valeur de l’arc tangente de l’argument

##  <a name="atan2"></a>  atan2

Calcule l’arc tangente de _Y/_X

```
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

Retourne la valeur de l’arc tangente de _Y/_X

##  <a name="atan2f"></a>  atan2f

Calcule l’arc tangente de _Y/_X

```
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

Retourne la valeur de l’arc tangente de _Y/_X

##  <a name="atanf"></a>  atanf

Calcule l’arc tangente de l’argument

```
inline float atanf(float _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne la valeur de l’arc tangente de l’argument

##  <a name="atanh"></a>  ATANH

Calcule la tangente hyperbolique inverse de l’argument

```
inline float atanh(float _X) restrict(amp);

inline double atanh(double _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne la valeur de tangente hyperbolique inverse de l’argument

##  <a name="atanhf"></a>  atanhf

Calcule la tangente hyperbolique inverse de l’argument

```
inline float atanhf(float _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne la valeur de tangente hyperbolique inverse de l’argument

##  <a name="cbrt"></a>  cbrt

Calcule la racine cubique réelle de l’argument

```
inline float cbrt(float _X) restrict(amp);

inline double cbrt(double _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne la racine cubique réelle de l’argument

##  <a name="cbrtf"></a>  cbrtf

Calcule la racine cubique réelle de l’argument

```
inline float cbrtf(float _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne la racine cubique réelle de l’argument

##  <a name="ceil"></a>  ceil

Calcule le plafond de l’argument

```
inline float ceil(float _X) restrict(amp);

inline double ceil(double _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Renvoie la valeur plafond de l’argument

##  <a name="ceilf"></a>  ceilf

Calcule le plafond de l’argument

```
inline float ceilf(float _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Renvoie la valeur plafond de l’argument

##  <a name="copysign"></a>  copysign

Produit une valeur avec l’ampleur du _X et le signe de _Y

```
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

Retourne une valeur avec l’ampleur du _X et le signe de _Y

##  <a name="copysignf"></a>  copysignf

Produit une valeur avec l’ampleur du _X et le signe de _Y

```
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

Retourne une valeur avec l’ampleur du _X et le signe de _Y

##  <a name="cos"></a>  cos

Calcule le cosinus de l’argument

```
inline float cos(float _X) restrict(amp);

inline double cos(double _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne la valeur de cosinus de l’argument

##  <a name="cosf"></a>  cosf

Calcule le cosinus de l’argument

```
inline float cosf(float _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne la valeur de cosinus de l’argument

##  <a name="cosh"></a>  cosh

Calcule la valeur de cosinus hyperbolique de l’argument

```
inline float cosh(float _X) restrict(amp);

inline double cosh(double _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne la valeur de cosinus hyperbolique de l’argument

##  <a name="coshf"></a>  coshf

Calcule la valeur de cosinus hyperbolique de l’argument

```
inline float coshf(float _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne la valeur de cosinus hyperbolique de l’argument

##  <a name="cospi"></a>  cospi

Calcule la valeur de cosinus de pi \* _X

```
inline float cospi(float _X) restrict(amp);

inline double cospi(double _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne la valeur de cosinus de pi \* _X

##  <a name="cospif"></a>  cospif

Calcule la valeur de cosinus de pi \* _X

```
inline float cospif(float _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne la valeur de cosinus de pi \* _X

##  <a name="erf"></a>  ERF

Calcule la fonction d’erreur de _X

```
inline float erf(float _X) restrict(amp);

inline double erf(double _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne la fonction d’erreur de _X

##  <a name="erfc"></a>  ERFC

Calcule la fonction d’erreur complémentaire de _X

```
inline float erfc(float _X) restrict(amp);

inline double erfc(double _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne la fonction d’erreur complémentaire de _X

##  <a name="erfcf"></a>  erfcf

Calcule la fonction d’erreur complémentaire de _X

```
inline float erfcf(float _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne la fonction d’erreur complémentaire de _X

##  <a name="erfcinv"></a>  erfcinv

Calcule la fonction d’erreur complémentaire inverse de _X

```
inline float erfcinv(float _X) restrict(amp);

inline double erfcinv(double _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne la fonction d’erreur complémentaire inverse de _X

##  <a name="erfcinvf"></a>  erfcinvf

Calcule la fonction d’erreur complémentaire inverse de _X

```
inline float erfcinvf(float _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne la fonction d’erreur complémentaire inverse de _X

##  <a name="erff"></a>  erff

Calcule la fonction d’erreur de _X

```
inline float erff(float _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne la fonction d’erreur de _X

##  <a name="erfinv"></a>  erfinv

Calcule la fonction de l’erreur inverse de _X

```
inline float erfinv(float _X) restrict(amp);

inline double erfinv(double _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne la fonction de l’erreur inverse de _X

##  <a name="erfinvf"></a>  erfinvf

Calcule la fonction de l’erreur inverse de _X

```
inline float erfinvf(float _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne la fonction de l’erreur inverse de _X

##  <a name="exp10"></a>  exp10

Calcule la valeur exponentielle de l’argument de base 10

```
inline float exp10(float _X) restrict(amp);

inline double exp10(double _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne la valeur exponentielle de l’argument de base 10

##  <a name="exp10f"></a>  exp10f

Calcule la valeur exponentielle de l’argument de base 10

```
inline float exp10f(float _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne la valeur exponentielle de l’argument de base 10

##  <a name="expm1"></a>  expm1

Calcule l’exponentielle de base e de l’argument, moins 1

```
inline float expm1(float exponent) restrict(amp);

inline double expm1(double exponent) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*Exposant*<br/>
Le terme exponentiel *n* de l’expression mathématique `e` <sup>n</sup>, où `e` est la base du logarithme népérien.

### <a name="return-value"></a>Valeur de retour

Retourne l’exponentielle de base e de l’argument, moins 1

##  <a name="expm1f"></a>  expm1f

Calcule l’exponentielle de base e de l’argument, moins 1

```
inline float expm1f(float exponent) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*Exposant*<br/>
Le terme exponentiel *n* de l’expression mathématique `e` <sup>n</sup>, où `e` est la base du logarithme népérien.

### <a name="return-value"></a>Valeur de retour

Retourne l’exponentielle de base e de l’argument, moins 1

##  <a name="exp"></a>  exp

Calcule l’exponentielle de l’argument de base e

```
inline float exp(float _X) restrict(amp);

inline double exp(double _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne la valeur exponentielle de l’argument de base e

##  <a name="expf"></a>  expf

Calcule l’exponentielle de l’argument de base e

```
inline float expf(float _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne la valeur exponentielle de l’argument de base e

##  <a name="exp2"></a>  exp2

Calcule la valeur exponentielle de l’argument de base 2

```
inline float exp2(float _X) restrict(amp);

inline double exp2(double _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne la valeur exponentielle de l’argument de base 2

##  <a name="exp2f"></a>  exp2f

Calcule la valeur exponentielle de l’argument de base 2

```
inline float exp2f(float _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne la valeur exponentielle de l’argument de base 2

##  <a name="fabs"></a>  fabs

Retourne la valeur absolue de l’argument

```
inline float fabs(float _X) restrict(amp);

inline double fabs(double _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne la valeur absolue de l’argument

##  <a name="fabsf"></a>  fabsf

Retourne la valeur absolue de l’argument

```
inline float fabsf(float _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne la valeur absolue de l’argument

## <a name="fdim"></a> fdim

Calcule la différence positive entre les arguments.
```
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
Valeur à virgule flottante *_Y*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

La différence entre _X et du _Y si _X est supérieure à _Y ; Sinon, + 0.

## <a name="fdimf"></a> fdimf

Calcule la différence positive entre les arguments.
```
inline float fdimf(
   float _X,
   float _Y
) restrict(amp);
```
### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante *_Y*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

La différence entre _X et du _Y si _X est supérieure à _Y ; Sinon, + 0.

##  <a name="floor"></a>  Floor

Calcule le plancher de l’argument

```
inline float floor(float _X) restrict(amp);

inline double floor(double _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne la valeur plancher de l’argument

##  <a name="floorf"></a>  floorf

Calcule le plancher de l’argument

```
inline float floorf(float _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne la valeur plancher de l’argument

## <a name="a-namefma-fma"></a><a name="fma"> FMA

Calcule le produit des premier et deuxième arguments spécifiés, puis ajoute le troisième argument spécifié au résultat ; le calcul entier est effectué en une seule opération.
```
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
Le premier argument à virgule flottante.
*_Y*<br/>
Le deuxième argument à virgule flottante.
*_Z*<br/>
Le troisième argument à virgule flottante.

### <a name="return-value"></a>Valeur de retour

Le résultat de l’expression (_X \* _Y) + _Z. Le calcul entier est effectué en une seule opération ; Autrement dit, les sous-expressions sont calculées avec une précision infinie, et seul le résultat final est arrondi.

## <a name="fmaf"></a> fmaf

Calcule le produit des premier et deuxième arguments spécifiés, puis ajoute le troisième argument spécifié au résultat ; le calcul entier est effectué en une seule opération.
```
inline float fmaf(
   float _X,
   float _Y,
   float _Z
) restrict(amp);
```
### <a name="parameters"></a>Paramètres

*_X*<br/>
Le premier argument à virgule flottante.
*_Y*<br/>
Le deuxième argument à virgule flottante.
*_Z*<br/>
Le troisième argument à virgule flottante.

### <a name="return-value"></a>Valeur de retour

Le résultat de l’expression (_X \* _Y) + _Z. Le calcul entier est effectué en une seule opération ; Autrement dit, les sous-expressions sont calculées avec une précision infinie, et seul le résultat final est arrondi.

##  <a name="fmax"></a>  fmax

Déterminer la valeur numérique maximale des arguments

```
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

Retourne la valeur numérique maximale des arguments

##  <a name="fmaxf"></a>  fmaxf

Déterminer la valeur numérique maximale des arguments

```
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

Retourne la valeur numérique maximale des arguments

##  <a name="fmin"></a>  fmin

Déterminer la valeur numérique minimale des arguments

```
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

Retourne la valeur numérique minimale des arguments

##  <a name="fminf"></a>  fminf

Déterminer la valeur numérique minimale des arguments

```
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

Retourne la valeur numérique minimale des arguments

##  <a name="fmod"></a>  fmod, fonction (C++ AMP)

Calcule le reste du premier argument spécifié divisé par le deuxième argument spécifié.

```
inline float fmod(
    float _X,
    float _Y) restrict(amp);

inline double fmod(
    double _X,
    double _Y) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Le premier argument à virgule flottante.

*_Y*<br/>
Le deuxième argument à virgule flottante.

### <a name="return-value"></a>Valeur de retour

Le reste de `_X` divisé par `_Y`; autrement dit, la valeur de `_X`  -  `_Y` *n*, où *n* est un entier tel que l’ampleur du `_X`  -  `_Y` *n* est inférieure à la grandeur de `_Y`.

##  <a name="fmodf"></a>  fmodf

Calcule le reste du premier argument spécifié divisé par le deuxième argument spécifié.

```
inline float fmodf(
    float _X,
    float _Y) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Le premier argument à virgule flottante.

*_Y*<br/>
Le deuxième argument à virgule flottante.

### <a name="return-value"></a>Valeur de retour

Le reste de `_X` divisé par `_Y`; autrement dit, la valeur de `_X`  -  `_Y` *n*, où *n* est un entier tel que l’ampleur du `_X`  -  `_Y` *n* est inférieure à la grandeur de `_Y`.

##  <a name="fpclassify"></a>  fpclassify

Classifie la valeur d’argument comme NaN, infinie, normal subnormal, zéro

```
inline int fpclassify(float _X) restrict(amp);

inline int fpclassify(double _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne la valeur de la macro de classification nombre approprié à la valeur de l’argument.

##  <a name="frexp"></a>  frexp

Obtient la mantisse et l’exposant de _X

```
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
Retourne l’exposant entier de _X dans la valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne la mantisse _X

##  <a name="frexpf"></a>  frexpf

Obtient la mantisse et l’exposant de _X

```
inline float frexpf(
    float _X,
    _Out_ int* _Exp) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

*_Exp*<br/>
Retourne l’exposant entier de _X dans la valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne la mantisse _X

##  <a name="hypot"></a>  hypot

Calcule la racine carrée de la somme des carrés de _X et du _Y

```
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

Retourne la racine carrée de la somme des carrés de _X et du _Y

##  <a name="hypotf"></a>  hypotf

Calcule la racine carrée de la somme des carrés de _X et du _Y

```
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

Retourne la racine carrée de la somme des carrés de _X et du _Y

##  <a name="ilogb"></a>  ilogb

Extraire l’exposant de _X comme une valeur int signée

```
inline int ilogb(float _X) restrict(amp);

inline int ilogb(double _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne l’exposant de _X sous la forme d’une valeur int signée

##  <a name="ilogbf"></a>  ilogbf

Extraire l’exposant de _X comme une valeur int signée

```
inline int ilogbf(float _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne l’exposant de _X sous la forme d’une valeur int signée

##  <a name="isfinite"></a>  isfinite

Détermine si l’argument a une valeur finie

```
inline int isfinite(float _X) restrict(amp);

inline int isfinite(double _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne une valeur différente de zéro si et seulement si l’argument a une valeur finie

##  <a name="isinf"></a>  isinf

Détermine si l’argument est un nombre infini

```
inline int isinf(float _X) restrict(amp);

inline int isinf(double _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne une valeur différente de zéro si et seulement si l’argument a une valeur infinie

##  <a name="isnan"></a>  isNaN

Détermine si l’argument est une valeur NaN

```
inline int isnan(float _X) restrict(amp);

inline int isnan(double _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne une valeur différente de zéro si et seulement si l’argument a une valeur NaN

##  <a name="isnormal"></a>  isnormal

Détermine si l’argument est un élément normal

```
inline int isnormal(float _X) restrict(amp);

inline int isnormal(double _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne une valeur différente de zéro si et seulement si l’argument a la valeur normale

##  <a name="ldexp"></a>  ldexp

Calcule un nombre réel à partir de la mantisse spécifié et l’exposant.

```
inline float ldexp(
    float _X,
    int _Exp) restrict(amp);

inline double ldexp(
    double _X,
    double _Exp) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante, mantisse

*_Exp*<br/>
Valeur entière, exposant

### <a name="return-value"></a>Valeur de retour

Retourne _X \* 2 ^ _Exp

##  <a name="ldexpf"></a>  ldexpf

Calcule un nombre réel à partir de la mantisse spécifié et l’exposant.

```
inline float ldexpf(
    float _X,
    int _Exp) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante, mantisse

*_Exp*<br/>
Valeur entière, exposant

### <a name="return-value"></a>Valeur de retour

Retourne _X \* 2 ^ _Exp

##  <a name="lgamma"></a>  lgamma

Calcule le logarithme népérien de la valeur absolue de gamma de l’argument

```
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

*_Se*<br/>
Retourne le signe

### <a name="return-value"></a>Valeur de retour

Retourne le logarithme naturel de la valeur absolue de gamma de l’argument

##  <a name="lgammaf"></a>  lgammaf

Calcule le logarithme népérien de la valeur absolue de gamma de l’argument

```
inline float lgammaf(
    float _X,
    _Out_ int* _Sign) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

*_Se*<br/>
Retourne le signe

### <a name="return-value"></a>Valeur de retour

Retourne le logarithme naturel de la valeur absolue de gamma de l’argument

##  <a name="log"></a>  log

Calcule le logarithme en base e de l’argument

```
inline float log(float _X) restrict(amp);

inline double log(double _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne le logarithme en base e de l’argument

##  <a name="log10"></a>  log10

Calcule le logarithme en base 10 de l’argument

```
inline float log10(float _X) restrict(amp);

inline double log10(double _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne le logarithme en base 10 de l’argument

##  <a name="log10f"></a>  log10f

Calcule le logarithme en base 10 de l’argument

```
inline float log10f(float _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne le logarithme en base 10 de l’argument

##  <a name="log1p"></a>  log1p

Calcule le logarithme en base e de 1 ainsi que l’argument

```
inline float log1p(float _X) restrict(amp);

inline double log1p(double _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne le logarithme en base e de 1 ainsi que l’argument

##  <a name="log1pf"></a>  log1pf

Calcule le logarithme en base e de 1 ainsi que l’argument

```
inline float log1pf(float _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne le logarithme en base e de 1 ainsi que l’argument

##  <a name="log2"></a>  log2

Calcule le logarithme en base 2 de l’argument

```
inline float log2(float _X) restrict(amp);

inline double log2(double _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne le logarithme en base 10 de l’argument

##  <a name="log2f"></a>  log2f

Calcule le logarithme en base 2 de l’argument

```
inline float log2f(float _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne le logarithme en base 10 de l’argument

##  <a name="logb"></a>  logb

Extrait l’exposant de _X, en tant qu’une valeur entière signée dans un format à virgule flottante

```
inline float logb(float _X) restrict(amp);

inline double logb(double _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne l’exposant signé de _X

##  <a name="logbf"></a>  logbf

Extrait l’exposant de _X, en tant qu’une valeur entière signée dans un format à virgule flottante

```
inline float logbf(float _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne l’exposant signé de _X

##  <a name="logf"></a>  logf

Calcule le logarithme en base e de l’argument

```
inline float logf(float _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne le logarithme en base e de l’argument

##  <a name="modf"></a>  modf

Fractionne l’argument spécifié en une partie fractionnaire et une partie entière.

```
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
[out] La partie entière de `_X`, en tant que valeur à virgule flottante.

### <a name="return-value"></a>Valeur de retour

La partie fractionnaire signée de `_X`.

##  <a name="modff"></a>  modff

Fractionne l’argument spécifié en une partie fractionnaire et une partie entière.

```
inline float modff(
    float _X,
    _Out_ float* _Iptr) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

*_Iptr*<br/>
La partie entière de `_X`, en tant que valeur à virgule flottante.

### <a name="return-value"></a>Valeur de retour

Retourne la partie fractionnaire signée de `_X`.

##  <a name="nan"></a>  NaN

Retourne une valeur NaN silencieuse

```
inline double nan(int _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur entière

### <a name="return-value"></a>Valeur de retour

Retourne une valeur NaN silencieuse, s’il est disponible, avec le contenu indiqué dans _X

##  <a name="nanf"></a>  nanf

Retourne une valeur NaN silencieuse

```
inline float nanf(int _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur entière

### <a name="return-value"></a>Valeur de retour

Retourne une valeur NaN silencieuse, s’il est disponible, avec le contenu indiqué dans _X

##  <a name="nearbyint"></a>  nearbyint

Arrondit l’argument à une valeur entière dans un format à virgule flottante, à l’aide de la direction d’arrondi actuelle.

```
inline float nearbyint(float _X) restrict(amp);

inline double nearbyint(double _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne la valeur entière arrondie.

##  <a name="nearbyintf"></a>  nearbyintf

Arrondit l’argument à une valeur entière dans un format à virgule flottante, à l’aide de la direction d’arrondi actuelle.

```
inline float nearbyintf(float _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne la valeur entière arrondie.

##  <a name="nextafter"></a>  nextafter

Déterminer la prochaine valeur représentable dans le type de la fonction, après _X dans la direction de _Y

```
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

Retourne la prochaine valeur représentable, dans le type de la fonction, après _X dans la direction de _Y

##  <a name="nextafterf"></a>  nextafterf

Déterminer la prochaine valeur représentable dans le type de la fonction, après _X dans la direction de _Y

```
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

Retourne la prochaine valeur représentable, dans le type de la fonction, après _X dans la direction de _Y

##  <a name="phi"></a>  phi

Retourne la fonction distribution cumulative de l’argument

```
inline float phi(float _X) restrict(amp);

inline double phi(double _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne la fonction distribution cumulative de l’argument

##  <a name="phif"></a>  phif

Retourne la fonction distribution cumulative de l’argument

```
inline float phif(float _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne la fonction distribution cumulative de l’argument

##  <a name="pow"></a>  pow

Calcule _X élevé à la puissance _Y

```
inline float pow(
    float _X,
    float _Y) restrict(amp);

inline double pow(
    double _X,
    double _Y) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante, base

*_Y*<br/>
Valeur à virgule flottante, exposant

### <a name="return-value"></a>Valeur de retour

##  <a name="powf"></a>  powf

Calcule _X élevé à la puissance _Y

```
inline float powf(
    float _X,
    float _Y) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante, base

*_Y*<br/>
Valeur à virgule flottante, exposant

### <a name="return-value"></a>Valeur de retour

##  <a name="probit"></a>  probit

Retourne la fonction de distribution cumulée inverse de l’argument

```
inline float probit(float _X) restrict(amp);

inline double probit(double _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne la fonction de distribution cumulée inverse de l’argument

##  <a name="probitf"></a>  probitf

Retourne la fonction de distribution cumulée inverse de l’argument

```
inline float probitf(float _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne la fonction de distribution cumulée inverse de l’argument

##  <a name="rcbrt"></a>  rcbrt

Retourne la réciproque de la racine cubique de l’argument

```
inline float rcbrt(float _X) restrict(amp);

inline double rcbrt(double _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne la réciproque de la racine cubique de l’argument

##  <a name="rcbrtf"></a>  rcbrtf

Retourne la réciproque de la racine cubique de l’argument

```
inline float rcbrtf(float _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne la réciproque de la racine cubique de l’argument

##  <a name="remainder"></a>  reste

Calcule le reste : _X REM _Y

```
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

Retourne _X REM _Y

##  <a name="remainderf"></a>  remainderf

Calcule le reste : _X REM _Y

```
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

Retourne _X REM _Y

##  <a name="remquo"></a>  remquo

Calcule le reste du premier argument spécifié divisé par le deuxième argument spécifié. Également calcule le quotient de la mantisse du premier argument spécifié divisé par la mantisse du deuxième argument spécifié et retourne le quotient à l’aide de l’emplacement spécifié dans le troisième argument.

```
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
Le premier argument à virgule flottante.

*_Y*<br/>
Le deuxième argument à virgule flottante.

*_Quo*<br/>
[out] L’adresse d’un entier qui est utilisé pour retourner le quotient des bits fractionnaires de `_X` divisé par bits fractionnaires de `_Y`.

### <a name="return-value"></a>Valeur de retour

Retourne le reste de `_X` divisé par `_Y`.

##  <a name="remquof"></a>  remquof

Calcule le reste du premier argument spécifié divisé par le deuxième argument spécifié. Également calcule le quotient de la mantisse du premier argument spécifié divisé par la mantisse du deuxième argument spécifié et retourne le quotient à l’aide de l’emplacement spécifié dans le troisième argument.

```
inline float remquof(
    float _X,
    float _Y,
    _Out_ int* _Quo) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Le premier argument à virgule flottante.

*_Y*<br/>
Le deuxième argument à virgule flottante.

*_Quo*<br/>
[out] L’adresse d’un entier qui est utilisé pour retourner le quotient des bits fractionnaires de `_X` divisé par bits fractionnaires de `_Y`.

### <a name="return-value"></a>Valeur de retour

Retourne le reste de `_X` divisé par `_Y`.

##  <a name="round"></a>  arrondir

Arrondit _X à l’entier le plus proche

```
inline float round(float _X) restrict(amp);

inline double round(double _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne l’entier le plus proche de _X

##  <a name="roundf"></a>  roundf

Arrondit _X à l’entier le plus proche

```
inline float roundf(float _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne l’entier le plus proche de _X

##  <a name="rsqrt"></a>  rsqrt

Retourne la réciproque de la racine carrée de l’argument

```
inline float rsqrt(float _X) restrict(amp);

inline double rsqrt(double _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne la réciproque de la racine carrée de l’argument

##  <a name="rsqrtf"></a>  rsqrtf

Retourne la réciproque de la racine carrée de l’argument

```
inline float rsqrtf(float _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne la réciproque de la racine carrée de l’argument

##  <a name="scalb"></a>  scalb

Multiplie _X par FLT_RADIX à la puissance _Y

```
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

Retourne _X \* (FLT_RADIX ^ _Y)

##  <a name="scalbf"></a>  scalbf

Multiplie _X par FLT_RADIX à la puissance _Y

```
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

Retourne _X \* (FLT_RADIX ^ _Y)

##  <a name="scalbn"></a>  scalbn

Multiplie _X par FLT_RADIX à la puissance _Y

```
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

Retourne _X \* (FLT_RADIX ^ _Y)

##  <a name="scalbnf"></a>  scalbnf

Multiplie _X par FLT_RADIX à la puissance _Y

```
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

Retourne _X \* (FLT_RADIX ^ _Y)

##  <a name="signbit"></a>  signbit

Détermine si le signe de _X est négatif

```
inline int signbit(float _X) restrict(amp);

inline int signbit(double _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne une valeur différente de zéro si et seulement si le signe de _X est négatif

##  <a name="signbitf"></a>  signbitf

Détermine si le signe de _X est négatif

```
inline int signbitf(float _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne une valeur différente de zéro si et seulement si le signe de _X est négatif

##  <a name="sin"></a>  sin

Calcule la valeur du sinus de l’argument

```
inline float sin(float _X) restrict(amp);

inline double sin(double _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne la valeur du sinus de l’argument

##  <a name="sinf"></a>  sinf

Calcule la valeur du sinus de l’argument

```
inline float sinf(float _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne la valeur du sinus de l’argument

##  <a name="sincos"></a>  sincos

Calcule la valeur de sinus et le cosinus de _X

```
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
Retourne la valeur du sinus de _X

*_C*<br/>
Retourne la valeur de cosinus de _X

##  <a name="sincosf"></a>  sincosf

Calcule la valeur de sinus et le cosinus de _X

```
inline void sincosf(
    float _X,
    _Out_ float* _S,
    _Out_ float* _C) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

*_S*<br/>
Retourne la valeur du sinus de _X

*_C*<br/>
Retourne la valeur de cosinus de _X

##  <a name="sinh"></a>  sinh

Calcule la valeur du sinus hyperbolique de l’argument

```
inline float sinh(float _X) restrict(amp);

inline double sinh(double _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne la valeur du sinus hyperbolique de l’argument

##  <a name="sinhf"></a>  sinhf

Calcule la valeur du sinus hyperbolique de l’argument

```
inline float sinhf(float _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne la valeur du sinus hyperbolique de l’argument

##  <a name="sinpi"></a>  sinpi

Calcule la valeur du sinus de pi \* _X

```
inline float sinpi(float _X) restrict(amp);

inline double sinpi(double _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne la valeur du sinus de pi \* _X

##  <a name="sinpif"></a>  sinpif

Calcule la valeur du sinus de pi \* _X

```
inline float sinpif(float _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne la valeur du sinus de pi \* _X

##  <a name="sqrt"></a>  sqrt

Calcule la racine squre de l’argument

```
inline float sqrt(float _X) restrict(amp);

inline double sqrt(double _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne la racine squre de l’argument

##  <a name="sqrtf"></a>  sqrtf

Calcule la racine squre de l’argument

```
inline float sqrtf(float _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne la racine squre de l’argument

##  <a name="tan"></a>  tan

Calcule la valeur de la tangente de l’argument

```
inline float tan(float _X) restrict(amp);

inline double tan(double _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne la valeur de la tangente de l’argument

##  <a name="tanf"></a>  tanf

Calcule la valeur de la tangente de l’argument

```
inline float tanf(float _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne la valeur de la tangente de l’argument

##  <a name="tanh"></a>  tanh

Calcule la valeur de la tangente hyperbolique de l’argument

```
inline float tanh(float _X) restrict(amp);

inline double tanh(double _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne la valeur de la tangente hyperbolique de l’argument

##  <a name="tanhf"></a>  tanhf

Calcule la valeur de la tangente hyperbolique de l’argument

```
inline float tanhf(float _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne la valeur de la tangente hyperbolique de l’argument

##  <a name="tanpi"></a>  tanpi

Calcule la valeur de la tangente de pi \* _X

```
inline float tanpi(float _X) restrict(amp);

inline double tanpi(double _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne la valeur de la tangente de pi \* _X

##  <a name="tanpif"></a>  tanpif

Calcule la valeur de la tangente de pi \* _X

```
inline float tanpif(float _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne la valeur de la tangente de pi \* _X

##  <a name="tgamma"></a>  tgamma

Calcule la fonction gamma de _X

```
inline float tgamma(float _X) restrict(amp);

inline double tgamma(double _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne le résultat de la fonction gamma de _X

##  <a name="tgammaf"></a>  tgammaf

Calcule la fonction gamma de _X

```
inline float tgammaf(float _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne le résultat de la fonction gamma de _X

##  <a name="trunc"></a>  trunc

Tronque l’argument à la partie entière

```
inline float trunc(float _X) restrict(amp);

inline double trunc(double _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne la partie entière de l’argument

##  <a name="truncf"></a>  truncf

Tronque l’argument à la partie entière

```
inline float truncf(float _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne la partie entière de l’argument

## <a name="see-also"></a>Voir aussi

[Concurrency::precise_math, espace de noms](concurrency-precise-math-namespace.md)
