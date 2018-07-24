---
title: Fonctions d’espace de noms Concurrency::fast_math | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
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
dev_langs:
- C++
ms.assetid: f5763d62-795b-4de6-a7a5-c7115f158708
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c4fad0d6f5823a205490038755f9de4eef10eae8
ms.sourcegitcommit: 7eadb968405bcb92ffa505e3ad8ac73483e59685
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2018
ms.locfileid: "39208508"
---
# <a name="concurrencyfastmath-namespace-functions"></a>Fonctions d’espace de noms Concurrency::fast_math
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
|[fmodf](#fmodf)|[frexp](#frexp)|[frexpf](#frexpf)|  
|[isfinite](#isfinite)|[isinf](#isinf)|[isnan](#isnan)|  
|[ldexp](#ldexp)|[ldexpf](#ldexpf)|[log](#log)|  
|[log10](#log10)|[log10f](#log10f)|[log2](#log2)|  
|[log2f](#log2f)|[logf](#logf)|[modf](#modf)|  
|[modff](#modff)|[pow](#pow)|[powf](#powf)|  
|[round](#round)|[roundf](#roundf)|[rsqrt](#rsqrt)|  
|[rsqrtf](#rsqrtf)|[signbit](#signbit)|[signbitf](#signbitf)|  
|[sin](#sin)|[sincos](#sincos)|[sincosf](#sincosf)|  
|[sinf](#sinf)|[sinh](#sinh)|[sinhf](#sinhf)|  
|[sqrt](#sqrt)|[sqrtf](#sqrtf)|[tan](#tan)|  
|[tanf](#tanf)|[tanh](#tanh)|[tanhf](#tanhf)|  
|[trunc](#trunc)|[truncf](#truncf)|  
  
##  <a name="acos"></a>  acos  
 Calcule l’arc cosinus de l’argument  
  
```  
inline float acos(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Paramètres  
 `_X`  
 Valeur à virgule flottante  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne la valeur d’arc cosinus de l’argument  
  
##  <a name="acosf"></a>  acosf  
 Calcule l’arc cosinus de l’argument  
  
```  
inline float acosf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Paramètres  
 `_X`  
 Valeur à virgule flottante  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne la valeur d’arc cosinus de l’argument  
  
##  <a name="asin"></a>  asin  
 Calcule l’arc sinus de l’argument  
  
```  
inline float asin(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Paramètres  
 `_X`  
 Valeur à virgule flottante  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne la valeur d’arc sinus de l’argument  
  
##  <a name="asinf"></a>  asinf  
 Calcule l’arc sinus de l’argument  
  
```  
inline float asinf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Paramètres  
 `_X`  
 Valeur à virgule flottante  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne la valeur d’arc sinus de l’argument  
  
##  <a name="atan"></a>  atan  
 Calcule l’arc tangente de l’argument  
  
```  
inline float atan(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Paramètres  
 `_X`  
 Valeur à virgule flottante  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne la valeur de l’arc tangente de l’argument  
  
##  <a name="atan2"></a>  atan2  
 Calcule l’arc tangente de _Y/_X  
  
```  
inline float atan2(
    float _Y,  
    float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Paramètres  
 `_Y`  
 Valeur à virgule flottante  
  
 `_X`  
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
 `_Y`  
 Valeur à virgule flottante  
  
 `_X`  
 Valeur à virgule flottante  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne la valeur de l’arc tangente de _Y/_X  
  
##  <a name="atanf"></a>  atanf  
 Calcule l’arc tangente de l’argument  
  
```  
inline float atanf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Paramètres  
 `_X`  
 Valeur à virgule flottante  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne la valeur de l’arc tangente de l’argument  
  
##  <a name="ceil"></a>  ceil  
 Calcule le plafond de l’argument  
  
```  
inline float ceil(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Paramètres  
 `_X`  
 Valeur à virgule flottante  
  
### <a name="return-value"></a>Valeur de retour  
 Renvoie la valeur plafond de l’argument  
  
##  <a name="ceilf"></a>  ceilf  
 Calcule le plafond de l’argument  
  
```  
inline float ceilf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Paramètres  
 `_X`  
 Valeur à virgule flottante  
  
### <a name="return-value"></a>Valeur de retour  
 Renvoie la valeur plafond de l’argument  
  
##  <a name="cosf"></a>  cosf  
 Calcule le cosinus de l’argument  
  
```  
inline float cosf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Paramètres  
 `_X`  
 Valeur à virgule flottante  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne la valeur de cosinus de l’argument  
  
##  <a name="coshf"></a>  coshf  
 Calcule la valeur de cosinus hyperbolique de l’argument  
  
```  
inline float coshf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Paramètres  
 `_X`  
 Valeur à virgule flottante  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne la valeur de cosinus hyperbolique de l’argument  
  
##  <a name="cos"></a>  cos  
 Calcule le cosinus de l’argument  
  
```  
inline float cos(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Paramètres  
 `_X`  
 Valeur à virgule flottante  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne la valeur de cosinus de l’argument  
  
##  <a name="cosh"></a>  cosh  
 Calcule la valeur de cosinus hyperbolique de l’argument  
  
```  
inline float cosh(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Paramètres  
 `_X`  
 Valeur à virgule flottante  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne la valeur de cosinus hyperbolique de l’argument  
  
##  <a name="exp"></a>  exp  
 Calcule l’exponentielle de l’argument de base e  
  
```  
inline float exp(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Paramètres  
 `_X`  
 Valeur à virgule flottante  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne la valeur exponentielle de l’argument de base e  
  
##  <a name="exp2"></a>  exp2  
 Calcule la valeur exponentielle de l’argument de base 2  
  
```  
inline float exp2(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Paramètres  
 `_X`  
 Valeur à virgule flottante  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne la valeur exponentielle de l’argument de base 2  
  
##  <a name="exp2f"></a>  exp2f  
 Calcule la valeur exponentielle de l’argument de base 2  
  
```  
inline float exp2f(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Paramètres  
 `_X`  
 Valeur à virgule flottante  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne la valeur exponentielle de l’argument de base 2  
  
##  <a name="expf"></a>  expf  
 Calcule l’exponentielle de l’argument de base e  
  
```  
inline float expf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Paramètres  
 `_X`  
 Valeur à virgule flottante  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne la valeur exponentielle de l’argument de base e  
  
##  <a name="fabs"></a>  fabs  
 Retourne la valeur absolue de l’argument  
  
```  
inline float fabs(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Paramètres  
 `_X`  
 Valeur entière  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne la valeur absolue de l’argument  
  
##  <a name="fabsf"></a>  fabsf  
 Retourne la valeur absolue de l’argument  
  
```  
inline float fabsf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Paramètres  
 `_X`  
 Valeur à virgule flottante  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne la valeur absolue de l’argument  
  
##  <a name="floor"></a>  Floor  
 Calcule le plancher de l’argument  
  
```  
inline float floor(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Paramètres  
 `_X`  
 Valeur à virgule flottante  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne la valeur plancher de l’argument  
  
##  <a name="floorf"></a>  floorf  
 Calcule le plancher de l’argument  
  
```  
inline float floorf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Paramètres  
 `_X`  
 Valeur à virgule flottante  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne la valeur plancher de l’argument  
  
##  <a name="fmax"></a>  fmax  
 Déterminer la valeur numérique maximale des arguments  
  
```  
inline float max(
    float _X,  
    float _Y) restrict(amp);
```  
  
### <a name="parameters"></a>Paramètres  
 `_X`  
 Valeur entière  
  
 `_Y`  
 Valeur entière  
  
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
 `_X`  
 Valeur à virgule flottante  
  
 `_Y`  
 Valeur à virgule flottante  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne la valeur numérique maximale des arguments  
  
##  <a name="fmin"></a>  fmin  
 Déterminer la valeur numérique minimale des arguments  
  
```  
inline float min(
    float _X,  
    float _Y) restrict(amp);
```  
  
### <a name="parameters"></a>Paramètres  
 `_X`  
 Valeur entière  
  
 `_Y`  
 Valeur entière  
  
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
 `_X`  
 Valeur à virgule flottante  
  
 `_Y`  
 Valeur à virgule flottante  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne la valeur numérique minimale des arguments  
  
##  <a name="fmod"></a>  fmod  
 Calcule le reste à virgule flottante de _X/_Y.  
  
```  
inline float fmod(
    float _X,  
    float _Y) restrict(amp);
```  
  
### <a name="parameters"></a>Paramètres  
 `_X`  
 Valeur à virgule flottante  
  
 `_Y`  
 Valeur à virgule flottante  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne le reste à virgule flottante de _X/_Y.  
  
##  <a name="fmodf"></a>  fmodf  
 Calcule le reste à virgule flottante de _X/_Y.  
  
```  
inline float fmodf(
    float _X,  
    float _Y) restrict(amp);
```  
  
### <a name="parameters"></a>Paramètres  
 `_X`  
 Valeur à virgule flottante  
  
 `_Y`  
 Valeur à virgule flottante  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne le reste à virgule flottante de _X/_Y.  
  
##  <a name="frexp"></a>  frexp  
 Obtient la mantisse et l’exposant de _X  
  
```  
inline float frexp(
    float _X,  
    _Out_ int* _Exp) restrict(amp);
```  
  
### <a name="parameters"></a>Paramètres  
 `_X`  
 Valeur à virgule flottante  
  
 `_Exp`  
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
 `_X`  
 Valeur à virgule flottante  
  
 `_Exp`  
 Retourne l’exposant entier de _X dans la valeur à virgule flottante  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne la mantisse _X  
  
##  <a name="isfinite"></a>  isfinite  
 Détermine si l’argument a une valeur finie  
  
```  
inline int isfinite(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Paramètres  
 `_X`  
 Valeur à virgule flottante  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne une valeur différente de zéro si et seulement si l’argument a une valeur finie  
  
##  <a name="isinf"></a>  isinf  
 Détermine si l’argument est un nombre infini  
  
```  
inline int isinf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Paramètres  
 `_X`  
 Valeur à virgule flottante  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne une valeur différente de zéro si et seulement si l’argument a une valeur infinie  
  
##  <a name="isnan"></a>  isNaN  
 Détermine si l’argument est une valeur NaN  
  
```  
inline int isnan(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Paramètres  
 `_X`  
 Valeur à virgule flottante  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne une valeur différente de zéro si et seulement si l’argument a une valeur NaN  
  
##  <a name="ldexp"></a>  ldexp  
 Calcule un nombre réel à partir de la mantisse et l’exposant  
  
```  
inline float ldexp(
    float _X,  
    int _Exp) restrict(amp);
```  
  
### <a name="parameters"></a>Paramètres  
 `_X`  
 Valeur à virgule flottante, mentissa  
  
 `_Exp`  
 Exposant entier  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne _X \* 2 ^ _Exp  
  
##  <a name="ldexpf"></a>  ldexpf  
 Calcule un nombre réel à partir de la mantisse et l’exposant  
  
```  
inline float ldexpf(
    float _X,  
    int _Exp) restrict(amp);
```  
  
### <a name="parameters"></a>Paramètres  
 `_X`  
 Valeur à virgule flottante, mentissa  
  
 `_Exp`  
 Exposant entier  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne _X \* 2 ^ _Exp  
  
##  <a name="log"></a>  log  
 Calcule le logarithme en base e de l’argument  
  
```  
inline float log(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Paramètres  
 `_X`  
 Valeur à virgule flottante  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne le logarithme en base e de l’argument  
  
##  <a name="log10"></a>  log10  
 Calcule le logarithme en base 10 de l’argument  
  
```  
inline float log10(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Paramètres  
 `_X`  
 Valeur à virgule flottante  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne le logarithme en base 10 de l’argument  
  
##  <a name="log10f"></a>  log10f  
 Calcule le logarithme en base 10 de l’argument  
  
```  
inline float log10f(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Paramètres  
 `_X`  
 Valeur à virgule flottante  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne le logarithme en base 10 de l’argument  
  
##  <a name="log2"></a>  log2  
 Calcule le logarithme en base 2 de l’argument  
  
```  
inline float log2(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Paramètres  
 `_X`  
 Valeur à virgule flottante  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne le logarithme base 2 de l’argument  
  
##  <a name="log2f"></a>  log2f  
 Calcule le logarithme en base 2 de l’argument  
  
```  
inline float log2f(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Paramètres  
 `_X`  
 Valeur à virgule flottante  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne le logarithme en base 10 de l’argument  
  
##  <a name="logf"></a>  logf  
 Calcule le logarithme en base e de l’argument  
  
```  
inline float logf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Paramètres  
 `_X`  
 Valeur à virgule flottante  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne le logarithme en base e de l’argument  
  
##  <a name="modf"></a>  modf  
 Fractionne _X en une partie fractionnaire et une partie entière.  
  
```  
inline float modf(
    float _X,  
    float* _Ip) restrict(amp);
```  
  
### <a name="parameters"></a>Paramètres  
 `_X`  
 Valeur à virgule flottante  
  
 `_Ip`  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne la partie fractionnaire signée de _X  
  
##  <a name="modff"></a>  modff  
 Fractionne _X en une partie fractionnaire et une partie entière.  
  
```  
inline float modff(
    float _X,  
    float* _Ip) restrict(amp);
```  
  
### <a name="parameters"></a>Paramètres  
 `_X`  
 Valeur à virgule flottante  
  
 `_Ip`  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne la partie fractionnaire signée de _X  
  
##  <a name="pow"></a>  pow  
 Calcule _X élevé à la puissance _Y  
  
```  
inline float pow(
    float _X,  
    float _Y) restrict(amp);
```  
  
### <a name="parameters"></a>Paramètres  
 `_X`  
 Valeur à virgule flottante, base  
  
 `_Y`  
 Valeur à virgule flottante, exposant  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne la valeur de _X élevé à la puissance de _Y  
  
##  <a name="powf"></a>  powf  
 Calcule _X élevé à la puissance _Y  
  
```  
inline float powf(
    float _X,  
    float _Y) restrict(amp);
```  
  
### <a name="parameters"></a>Paramètres  
 `_X`  
 Valeur à virgule flottante, base  
  
 `_Y`  
 Valeur à virgule flottante, exposant  
  
### <a name="return-value"></a>Valeur de retour  
  
##  <a name="round"></a>  arrondir  
 Arrondit _X à l’entier le plus proche  
  
```  
inline float round(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Paramètres  
 `_X`  
 Valeur à virgule flottante  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne l’entier le plus proche de _X  
  
##  <a name="roundf"></a>  roundf  
 Arrondit _X à l’entier le plus proche  
  
```  
inline float roundf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Paramètres  
 `_X`  
 Valeur à virgule flottante  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne l’entier le plus proche de _X  
  
##  <a name="rsqrt"></a>  rsqrt  
 Retourne la réciproque de la racine carrée de l’argument  
  
```  
inline float rsqrt(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Paramètres  
 `_X`  
 Valeur à virgule flottante  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne la réciproque de la racine carrée de l’argument  
  
##  <a name="rsqrtf"></a>  rsqrtf  
 Retourne la réciproque de la racine carrée de l’argument  
  
```  
inline float rsqrtf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Paramètres  
 `_X`  
 Valeur à virgule flottante  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne la réciproque de la racine carrée de l’argument  
  
##  <a name="signbit"></a>  signbit  
 Détermine si le signe de _X est négatif  
  
```  
inline int signbit(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Paramètres  
 `_X`  
 Valeur à virgule flottante  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne une valeur différente de zéro si et seulement si le signe de _X est négatif  
  
##  <a name="signbitf"></a>  signbitf  
 Détermine si le signe de _X est négatif  
  
```  
inline int signbitf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Paramètres  
 `_X`  
 Valeur à virgule flottante  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne une valeur différente de zéro si et seulement si le signe de _X est négatif  
  
##  <a name="sin"></a>  sin  
 Calcule la valeur du sinus de l’argument  
  
```  
inline float sin(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Paramètres  
 `_X`  
 Valeur à virgule flottante  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne la valeur du sinus de l’argument  
  
##  <a name="sinf"></a>  sinf  
 Calcule la valeur du sinus de l’argument  
  
```  
inline float sinf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Paramètres  
 `_X`  
 Valeur à virgule flottante  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne la valeur du sinus de l’argument  
  
##  <a name="sincos"></a>  sincos  
 Calcule la valeur de sinus et le cosinus de _X  
  
```  
inline void sincos(
    float _X,  
    float* _S,  
    float* _C) restrict(amp);
```  
  
### <a name="parameters"></a>Paramètres  
 `_X`  
 Valeur à virgule flottante  
  
 `_S`  
 Retourne la valeur du sinus de _X  
  
 `_C`  
 Retourne la valeur de cosinus de _X  
  
##  <a name="sincosf"></a>  sincosf  
 Calcule la valeur de sinus et le cosinus de _X  
  
```  
inline void sincosf(
    float _X,  
    float* _S,  
    float* _C) restrict(amp);
```  
  
### <a name="parameters"></a>Paramètres  
 `_X`  
 Valeur à virgule flottante  
  
 `_S`  
 Retourne la valeur du sinus de _X  
  
 `_C`  
 Retourne la valeur de cosinus de _X  
  
##  <a name="sinh"></a>  sinh  
 Calcule la valeur du sinus hyperbolique de l’argument  
  
```  
inline float sinh(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Paramètres  
 `_X`  
 Valeur à virgule flottante  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne la valeur du sinus hyperbolique de l’argument  
  
##  <a name="sinhf"></a>  sinhf  
 Calcule la valeur du sinus hyperbolique de l’argument  
  
```  
inline float sinhf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Paramètres  
 `_X`  
 Valeur à virgule flottante  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne la valeur du sinus hyperbolique de l’argument  
  
##  <a name="sqrt"></a>  sqrt  
 Calcule la racine squre de l’argument  
  
```  
inline float sqrt(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Paramètres  
 `_X`  
 Valeur à virgule flottante  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne la racine squre de l’argument  
  
##  <a name="sqrtf"></a>  sqrtf  
 Calcule la racine squre de l’argument  
  
```  
inline float sqrtf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Paramètres  
 `_X`  
 Valeur à virgule flottante  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne la racine squre de l’argument  
  
##  <a name="tan"></a>  tan  
 Calcule la valeur de la tangente de l’argument  
  
```  
inline float tan(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Paramètres  
 `_X`  
 Valeur à virgule flottante  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne la valeur de la tangente de l’argument  
  
##  <a name="tanf"></a>  tanf  
 Calcule la valeur de la tangente de l’argument  
  
```  
inline float tanf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Paramètres  
 `_X`  
 Valeur à virgule flottante  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne la valeur de la tangente de l’argument  
  
##  <a name="tanh"></a>  tanh  
 Calcule la valeur de la tangente hyperbolique de l’argument  
  
```  
inline float tanh(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Paramètres  
 `_X`  
 Valeur à virgule flottante  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne la valeur de la tangente hyperbolique de l’argument  
  
##  <a name="tanhf"></a>  tanhf  
 Calcule la valeur de la tangente hyperbolique de l’argument  
  
```  
inline float tanhf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Paramètres  
 `_X`  
 Valeur à virgule flottante  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne la valeur de la tangente hyperbolique de l’argument  
  
##  <a name="trunc"></a>  trunc  
 Tronque l’argument à la partie entière  
  
```  
inline float trunc(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Paramètres  
 `_X`  
 Valeur à virgule flottante  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne la partie entière de l’argument  
  
##  <a name="truncf"></a>  truncf  
 Tronque l’argument à la partie entière  
  
```  
inline float truncf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Paramètres  
 `_X`  
 Valeur à virgule flottante  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne la partie entière de l’argument  

## <a name="requirements"></a>Configuration requise
**En-tête :** amp_math.h **Namespace :** Concurrency::fast_math
  
## <a name="see-also"></a>Voir aussi  
 [Concurrency::fast_math, espace de noms](concurrency-fast-math-namespace.md)
