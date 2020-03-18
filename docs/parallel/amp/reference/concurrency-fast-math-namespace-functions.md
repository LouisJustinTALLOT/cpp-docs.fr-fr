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
ms.openlocfilehash: 3652e02d9f3ff7b09ee7334dba20188e40344cb5
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/16/2020
ms.locfileid: "79419272"
---
# <a name="concurrencyfast_math-namespace-functions"></a>Concurrency::fast_math, fonctions de l’espace de noms

||||
|-|-|-|
|[acos](#acos)|[acosf](#acosf)|[asin](#asin)|
|[asinf](#asinf)|[atan](#atan)|[atan2](#atan2)|
|[atan2f](#atan2f)|[atanf](#atanf)|[ceil](#ceil)|
|[ceilf](#ceilf)|[cos](#cos)|[cosf](#cosf)|
|[cosh](#cosh)|[coshf](#coshf)|[exp](#exp)|
|[exp2](#exp2)|[exp2f](#exp2f)|[expf](#expf)|
|[fabs](#fabs)|[fabsf](#fabsf)|[floor](#floor)|
|[floorf](#floorf)|[fmax](#fmax)|[fmaxf](#fmaxf)|
|[fmin](#fmin)|[fminf](#fminf)|[fmod](#fmod)|
|[fmodf](#fmodf)|[frexp](#frexp)|[frexpf,](#frexpf)|
|[isFinite,](#isfinite)|[isinf](#isinf)|[isnan](#isnan)|
|[ldexp](#ldexp)|[ldexpf,](#ldexpf)|[log](#log)|
|[log10](#log10)|[log10f](#log10f)|[log2](#log2)|
|[log2f](#log2f)|[logf](#logf)|[modf](#modf)|
|[modff](#modff)|[pow](#pow)|[powf](#powf)|
|[round](#round)|[roundf](#roundf)|[rsqrt,](#rsqrt)|
|[rsqrtf,](#rsqrtf)|[signbit](#signbit)|[signbitf,](#signbitf)|
|[sin](#sin)|[SinCos,](#sincos)|[sincosf,](#sincosf)|
|[sinf](#sinf)|[sinh](#sinh)|[sinhf](#sinhf)|
|[sqrt](#sqrt)|[sqrtf](#sqrtf)|[tan](#tan)|
|[tanf](#tanf)|[tanh](#tanh)|[tanhf](#tanhf)|
|[trunc](#trunc)|[truncf](#truncf)|

## <a name="acos"></a>  acos

Calcule l’arc cosinus de l’argument

```cpp
inline float acos(float _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne la valeur de l’arc cosinus de l’argument

## <a name="acosf"></a>acosf

Calcule l’arc cosinus de l’argument

```cpp
inline float acosf(float _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne la valeur de l’arc cosinus de l’argument

## <a name="asin"></a>  asin

Calcule l’arc sinus de l’argument

```cpp
inline float asin(float _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne la valeur de l’arc sinus de l’argument

## <a name="asinf"></a>ASInf,

Calcule l’arc sinus de l’argument

```cpp
inline float asinf(float _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne la valeur de l’arc sinus de l’argument

## <a name="atan"></a>  atan

Calcule l'arc tangente de l'argument.

```cpp
inline float atan(float _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne la valeur d’arc tangente de l’argument.

## <a name="atan2"></a>  atan2

Calcule l’arc tangente de _Y/_X

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

Retourne la valeur d’arc tangente de _Y/_X

## <a name="atan2f"></a>atan2f,

Calcule l’arc tangente de _Y/_X

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

Retourne la valeur d’arc tangente de _Y/_X

## <a name="atanf"></a>atanf,

Calcule l'arc tangente de l'argument.

```cpp
inline float atanf(float _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne la valeur d’arc tangente de l’argument.

## <a name="ceil"></a>ceil

Calcule le plafond de l’argument

```cpp
inline float ceil(float _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne le plafond de l’argument.

## <a name="ceilf"></a>ceilf,

Calcule le plafond de l’argument

```cpp
inline float ceilf(float _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne le plafond de l’argument.

## <a name="cosf"></a>cosf,

Calcule le cosinus de l'argument.

```cpp
inline float cosf(float _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne la valeur cosinus de l’argument

## <a name="coshf"></a>coshf,

Calcule la valeur du cosinus hyperbolique de l’argument.

```cpp
inline float coshf(float _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne la valeur du cosinus hyperbolique de l’argument.

## <a name="cos"></a>  cos

Calcule le cosinus de l'argument.

```cpp
inline float cos(float _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne la valeur cosinus de l’argument

## <a name="cosh"></a>  cosh

Calcule la valeur du cosinus hyperbolique de l’argument.

```cpp
inline float cosh(float _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne la valeur du cosinus hyperbolique de l’argument.

## <a name="exp"></a>  exp

Calcule la valeur exponentielle de base e de l’argument.

```cpp
inline float exp(float _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne l’exponentiel de base e de l’argument

## <a name="exp2"></a>EXP2

Calcule la valeur exponentielle de base 2 de l’argument.

```cpp
inline float exp2(float _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne l'exponentielle de base 2 de l'argument.

## <a name="exp2f"></a>exp2f,

Calcule la valeur exponentielle de base 2 de l’argument.

```cpp
inline float exp2f(float _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne l'exponentielle de base 2 de l'argument.

## <a name="expf"></a>expf,

Calcule la valeur exponentielle de base e de l’argument.

```cpp
inline float expf(float _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne l’exponentiel de base e de l’argument

## <a name="fabs"></a>FABS

Retourne la valeur absolue de l’argument.

```cpp
inline float fabs(float _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur entière

### <a name="return-value"></a>Valeur de retour

Retourne la valeur absolue de l’argument.

## <a name="fabsf"></a>fabsf

Retourne la valeur absolue de l’argument.

```cpp
inline float fabsf(float _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne la valeur absolue de l’argument.

## <a name="floor"></a>Floor

Calcule le plancher de l’argument

```cpp
inline float floor(float _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne le plancher de l’argument.

## <a name="floorf"></a>floorf,

Calcule le plancher de l’argument

```cpp
inline float floorf(float _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne le plancher de l’argument.

## <a name="fmax"></a>Fmax

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

Retourne la valeur numérique maximale des arguments

## <a name="fmaxf"></a>fmaxf,

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

Retourne la valeur numérique maximale des arguments

## <a name="fmin"></a>fmin,

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

Retourne la valeur numérique minimale des arguments

## <a name="fminf"></a>fminf,

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

Retourne la valeur numérique minimale des arguments

## <a name="fmod"></a>fmod

Calcule le reste à virgule flottante de _X/_Y

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

Retourne le reste à virgule flottante de _X/_Y

## <a name="fmodf"></a>fmodf,

Calcule le reste à virgule flottante de _X/_Y.

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

Retourne le reste à virgule flottante de _X/_Y

## <a name="frexp"></a>frexp

Obtient la mantisse et l’exposant de _X

```cpp
inline float frexp(
    float _X,
    _Out_ int* _Exp) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

*_Exp*<br/>
Retourne l’exposant entier de _X dans une valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne la mantisse _X

## <a name="frexpf"></a>frexpf,

Obtient la mantisse et l’exposant de _X

```cpp
inline float frexpf(
    float _X,
    _Out_ int* _Exp) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

*_Exp*<br/>
Retourne l’exposant entier de _X dans une valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne la mantisse _X

## <a name="isfinite"></a>isFinite,

Détermine si l’argument a une valeur finie

```cpp
inline int isfinite(float _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne une valeur différente de zéro si et seulement si l’argument a une valeur finie

## <a name="isinf"></a>isinf,

Détermine si l’argument est un infini

```cpp
inline int isinf(float _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne une valeur différente de zéro si et seulement si l’argument a une valeur infinie

## <a name="isnan"></a>isNaN

Détermine si l’argument est une valeur NaN

```cpp
inline int isnan(float _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne une valeur différente de zéro si et seulement si l’argument a une valeur NaN

## <a name="ldexp"></a>ldexp

Calcule un nombre réel à partir de la mantisse et de l’exposant

```cpp
inline float ldexp(
    float _X,
    int _Exp) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante, mentissa

*_Exp*<br/>
Exposant entier

### <a name="return-value"></a>Valeur de retour

Retourne _X \* 2 ^ _Exp

## <a name="ldexpf"></a>ldexpf,

Calcule un nombre réel à partir de la mantisse et de l’exposant

```cpp
inline float ldexpf(
    float _X,
    int _Exp) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante, mentissa

*_Exp*<br/>
Exposant entier

### <a name="return-value"></a>Valeur de retour

Retourne _X \* 2 ^ _Exp

## <a name="log"></a>  log

Calcule le logarithme de base e de l’argument

```cpp
inline float log(float _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne le logarithme de base e de l’argument

## <a name="log10"></a>  log10

Calcule le logarithme en base 10 de l’argument.

```cpp
inline float log10(float _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne le logarithme en base 10 de l’argument.

## <a name="log10f"></a>log10f,

Calcule le logarithme en base 10 de l’argument.

```cpp
inline float log10f(float _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne le logarithme en base 10 de l’argument.

## <a name="log2"></a>Log2

Calcule le logarithme de base 2 de l’argument.

```cpp
inline float log2(float _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne le logarithme de base 2 de l’argument.

## <a name="log2f"></a>log2f,

Calcule le logarithme de base 2 de l’argument.

```cpp
inline float log2f(float _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne le logarithme en base 10 de l’argument.

## <a name="logf"></a>LogF,

Calcule le logarithme de base e de l’argument

```cpp
inline float logf(float _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne le logarithme de base e de l’argument

## <a name="modf"></a>modf,

Divise _X en parties fractionnaires et entières.

```cpp
inline float modf(
    float _X,
    float* _Ip) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

*_Ip*<br/>
Reçoit une partie entière de la valeur

### <a name="return-value"></a>Valeur de retour

Retourne la partie fractionnaire signée de _X

## <a name="modff"></a>modff,

Divise _X en parties fractionnaires et entières.

```cpp
inline float modff(
    float _X,
    float* _Ip) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

*_Ip*<br/>
Reçoit une partie entière de la valeur

### <a name="return-value"></a>Valeur de retour

Retourne la partie fractionnaire signée de _X

## <a name="pow"></a>  pow

Calcule _X élevé à la puissance de _Y

```cpp
inline float pow(
    float _X,
    float _Y) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante, base

*_Y*<br/>
Valeur à virgule flottante, exposant

### <a name="return-value"></a>Valeur de retour

Retourne la valeur de _X élevée à la puissance de _Y

## <a name="powf"></a>powf,

Calcule _X élevé à la puissance de _Y

```cpp
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

## <a name="round"></a>Round

Arrondit _X à l’entier le plus proche.

```cpp
inline float round(float _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne l’entier le plus proche de _X

## <a name="roundf"></a>roundf,

Arrondit _X à l’entier le plus proche.

```cpp
inline float roundf(float _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne l’entier le plus proche de _X

## <a name="rsqrt"></a>rsqrt,

Retourne la réciproque de la racine carrée de l’argument

```cpp
inline float rsqrt(float _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne la réciproque de la racine carrée de l’argument

## <a name="rsqrtf"></a>rsqrtf,

Retourne la réciproque de la racine carrée de l’argument

```cpp
inline float rsqrtf(float _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne la réciproque de la racine carrée de l’argument

## <a name="signbit"></a>signbit,

Détermine si le signe de _X est négatif

```cpp
inline int signbit(float _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne une valeur différente de zéro si et seulement si le signe de _X est négatif

## <a name="signbitf"></a>signbitf,

Détermine si le signe de _X est négatif

```cpp
inline int signbitf(float _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne une valeur différente de zéro si et seulement si le signe de _X est négatif

## <a name="sin"></a>  sin

Calcule la valeur du sinus de l’argument

```cpp
inline float sin(float _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne la valeur sinus de l’argument.

## <a name="sinf"></a>sinf

Calcule la valeur du sinus de l’argument

```cpp
inline float sinf(float _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne la valeur sinus de l’argument.

## <a name="sincos"></a>SinCos,

Calcule la valeur du sinus et du cosinus de _X

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
Retourne la valeur de sinus de _X

*_C*<br/>
Retourne la valeur cosinus de _X

## <a name="sincosf"></a>sincosf,

Calcule la valeur du sinus et du cosinus de _X

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
Retourne la valeur de sinus de _X

*_C*<br/>
Retourne la valeur cosinus de _X

## <a name="sinh"></a>  sinh

Calcule la valeur du sinus hyperbolique de l’argument.

```cpp
inline float sinh(float _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne la valeur du sinus hyperbolique de l’argument.

## <a name="sinhf"></a>sinhf,

Calcule la valeur du sinus hyperbolique de l’argument.

```cpp
inline float sinhf(float _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne la valeur du sinus hyperbolique de l’argument.

## <a name="sqrt"></a>  sqrt

Calcule la racine Squre de l’argument

```cpp
inline float sqrt(float _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne la racine Squre de l’argument

## <a name="sqrtf"></a>sqrtf,

Calcule la racine Squre de l’argument

```cpp
inline float sqrtf(float _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne la racine Squre de l’argument

## <a name="tan"></a>  tan

Calcule la valeur de tangente de l’argument

```cpp
inline float tan(float _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne la valeur de tangente de l’argument

## <a name="tanf"></a>Tanf,

Calcule la valeur de tangente de l’argument

```cpp
inline float tanf(float _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne la valeur de tangente de l’argument

## <a name="tanh"></a>  tanh

Calcule la valeur tangente hyperbolique de l’argument.

```cpp
inline float tanh(float _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne la valeur tangente hyperbolique de l’argument.

## <a name="tanhf"></a>tanhf,

Calcule la valeur tangente hyperbolique de l’argument.

```cpp
inline float tanhf(float _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne la valeur tangente hyperbolique de l’argument.

## <a name="trunc"></a>trunc

Tronque l’argument du composant entier

```cpp
inline float trunc(float _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne le composant entier de l’argument.

## <a name="truncf"></a>truncf,

Tronque l’argument du composant entier

```cpp
inline float truncf(float _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne le composant entier de l’argument.

## <a name="requirements"></a>Spécifications

**En-tête :** amp_math. h **espace de noms :** concurrency :: fast_math

## <a name="see-also"></a>Voir aussi

[Concurrency::fast_math, espace de noms](concurrency-fast-math-namespace.md)
