---
title: Primitives à virgule flottante
ms.date: 4/2/2020
api_name:
- _dclass
- _ldclass
- _fdclass
- _dsign
- _ldsign
- _fdsign
- _dpcomp
- _ldpcomp
- _fdpcomp
- _dtest
- _ldtest
- _fdtest
- _d_int
- _ld_int
- _fd_int
- _dscale
- _ldscale
- _fdscale
- _dunscale
- _ldunscale
- _fdunscale
- _dexp
- _ldexp
- _fdexp
- _dnorm
- _fdnorm
- _dpoly
- _ldpoly
- _fdpoly
- _dlog
- _ldlog
- _fdlog
- _dsin
- _ldsin
- _fdsin
- _o__d_int
- _o__dclass
- _o__dlog
- _o__dnorm
- _o__dpcomp
- _o__dpoly
- _o__dscale
- _o__dsign
- _o__dsin
- _o__dtest
- _o__dunscale
- _o__fd_int
- _o__fdclass
- _o__fdexp
- _o__fdlog
- _o__fdpcomp
- _o__fdpoly
- _o__fdscale
- _o__fdsign
- _o__fdsin
- _o__ld_int
- _o__ldclass
- _o__ldexp
- _o__ldlog
- _o__ldpcomp
- _o__ldpoly
- _o__ldscale
- _o__ldsign
- _o__ldsin
- _o__ldtest
- _o__ldunscale
api_location:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-math-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _dclass
- _ldclass
- _fdclass
- _dsign
- _ldsign
- _fdsign
- _dpcomp
- _ldpcomp
- _fdpcomp
- _dtest
- _ldtest
- _fdtest
- _d_int
- _ld_int
- _fd_int
- _dscale
- _ldscale
- _fdscale
- _dunscale
- _ldunscale
- _fdunscale
- _dexp
- _ldexp
- _fdexp
- _dnorm
- _fdnorm
- _dpoly
- _ldpoly
- _fdpoly
- _dlog
- _ldlog
- _fdlog
- _dsin
- _ldsin
- _fdsin
helpviewer_keywords:
- _dclass
- _ldclass
- _fdclass
- _dsign
- _ldsign
- _fdsign
- _dpcomp
- _ldpcomp
- _fdpcomp
- _dtest
- _ldtest
- _fdtest
- _d_int
- _ld_int
- _fd_int
- _dscale
- _ldscale
- _fdscale
- _dunscale
- _ldunscale
- _fdunscale
- _dexp
- _ldexp
- _fdexp
- _dnorm
- _fdnorm
- _dpoly
- _ldpoly
- _fdpoly
- _dlog
- _ldlog
- _fdlog
- _dsin
- _ldsin
- _fdsin
ms.openlocfilehash: d861fbf2b71d557354a60f65b8a76dc24ca1dd13
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81346709"
---
# <a name="floating-point-primitives"></a>Primitives à virgule flottante

Fonctions primitives spécifiques à Microsoft qui sont utilisées pour implémenter certaines fonctions standard de la bibliothèque C runtime (CRT). Ils sont documentés ici pour l’exhaustivité, mais ne sont pas recommandés pour une utilisation. Certaines de ces fonctions sont notées comme inutilisées, parce qu’elles sont connues pour avoir des problèmes de précision, de manipulation des exceptions et de conformité au comportement de l’IEEE-754. Ils n’existent dans la bibliothèque que pour la compatibilité vers l’arrière. Pour un comportement correct, la portabilité et le respect des normes, préférez les fonctions standard de point flottant sur ces fonctions.

Par défaut, l’état global de cette fonction est étendue à l’application. Pour changer cela, voir [Global State dans le CRT](../global-state.md).

## <a name="_dclass-_ldclass-_fdclass"></a>_dclass, _ldclass, _fdclass

### <a name="syntax"></a>Syntaxe

```C
short __cdecl _dclass(double x);
short __cdecl _ldclass(long double x);
short __cdecl _fdclass(float x);
```

### <a name="parameters"></a>Paramètres

*X*<br/>
Argument de fonction flottant-point.

### <a name="remarks"></a>Notes

Ces primitifs à point flottant implémentent les versions C de la macro [fpclassify](fpclassify.md) CRT pour les types de points flottants. La classification de l’argument *x* est retournée comme l’une de ces constantes, définies en math.h:

|Valeur|Description|
|-----------|-----------------|
| **FP_NAN** | NaN silencieux, signalant ou indéterminé |
| **FP_INFINITE** | Infini positif ou négatif |
| **FP_NORMAL** | Valeur non nulle normalisée positive ou négative |
| **FP_SUBNORMAL** | Une valeur sous-normale (dénormalisée) positive ou négative |
| **FP_ZERO** | Valeur nulle positive ou négative |

Pour plus de détails, vous pouvez utiliser les [fonctions _fpclass, _fpclassf](fpclass-fpclassf.md) spécifiques à Microsoft. Utilisez la macro ou la fonction [fpclassify](fpclassify.md) pour la portabilité.

## <a name="_dsign-_ldsign-_fdsign"></a>_dsign, _ldsign, _fdsign

### <a name="syntax"></a>Syntaxe

```C
int __cdecl _dsign(double x);
int __cdecl _ldsign(long double x);
int __cdecl _fdsign(float x);
```

### <a name="parameters"></a>Paramètres

*X*<br/>
Argument de fonction flottant-point.

### <a name="remarks"></a>Notes

Ces primitifs à point flottant implémentent la macro ou la fonction [signbit](signbit.md) dans le CRT. Ils retournent une valeur non-zéro si le bit de signe est placé dans le significand (mantissa) de l’argument *x*, et 0 si le bit de signe n’est pas réglé.

## <a name="_dpcomp-_ldpcomp-_fdpcomp"></a>_dpcomp, _ldpcomp, _fdpcomp

### <a name="syntax"></a>Syntaxe

```C
int __cdecl _dpcomp(double x, double y);
int __cdecl _ldpcomp(long double x, long double y);
int __cdecl _fdpcomp(float x, float y);
```

### <a name="parameters"></a>Paramètres

*x*, *y*<br/>
Arguments de fonction de point flottant.

### <a name="remarks"></a>Notes

Ces primitifs flottants prennent deux arguments, *x* et *y,* et retournent une valeur qui montre leur relation de commande, exprimée comme le bitwise ou de ces constantes, définies en math.h :

| Valeur | Description |
|------------|-----------------|
| **_FP_LT** | *x* peut être considéré comme moins que *y* |
| **_FP_EQ** | *x* peut être considéré comme égal à *y* |
| **_FP_GT** | *x* peut être considéré comme plus grand que *y* |

Ces primitifs mettent en œuvre [l’isgreater, l’isgreaterequal, l’instérable, l’islesse, l’islessgreater, et les](floating-point-ordering.md) macros et les fonctions ordonnées dans le CRT.

## <a name="_dtest-_ldtest-_fdtest"></a>_dtest, _ldtest, _fdtest

### <a name="syntax"></a>Syntaxe

```C
short __cdecl _dtest(double* px);
short __cdecl _ldtest(long double* px);
short __cdecl _fdtest(float* px);
```

### <a name="parameters"></a>Paramètres

*Px*<br/>
Pointeur à un argument de point flottant.

### <a name="remarks"></a>Notes

Ces primitifs à point flottant implémentent les versions CMD de la fonction CRT [fpclassify](fpclassify.md) pour les types de points flottants. L’argument *x* est évalué et la classification est retournée comme l’une de ces constantes, définies en math.h:

|Valeur|Description|
|-----------|-----------------|
| **FP_NAN** | NaN silencieux, signalant ou indéterminé |
| **FP_INFINITE** | Infini positif ou négatif |
| **FP_NORMAL** | Valeur non nulle normalisée positive ou négative |
| **FP_SUBNORMAL** | Une valeur sous-normale (dénormalisée) positive ou négative |
| **FP_ZERO** | Valeur nulle positive ou négative |

Pour plus de détails, vous pouvez utiliser les [fonctions _fpclass, _fpclassf](fpclass-fpclassf.md) spécifiques à Microsoft. Utilisez la fonction [fpclassify](fpclassify.md) pour la portabilité.

## <a name="_d_int-_ld_int-_fd_int"></a>_d_int, _ld_int, _fd_int

### <a name="syntax"></a>Syntaxe

```C
short __cdecl _d_int(double* px, short exp);
short __cdecl _ld_int(long double* px, short exp);
short __cdecl _fd_int(float* px, short exp);
```

### <a name="parameters"></a>Paramètres

*Px*<br/>
Pointeur à un argument de point flottant.

*Exp*<br/>
Un exposant comme un type intégral.

### <a name="remarks"></a>Notes

Ces primitifs à point flottant prennent un pointeur à un *px* de valeur flottante-point et une valeur *exp*exposante , et enlèvent la partie fractionnelle de la valeur de point flottant en dessous de l’exposant donné, si possible. La valeur retournée est le résultat de **fpclassify** sur la valeur d’entrée en *px* si c’est un NaN ou à l’infini, et sur la valeur de sortie en *px* autrement.

## <a name="_dscale-_ldscale-_fdscale"></a>_dscale, _ldscale, _fdscale

### <a name="syntax"></a>Syntaxe

```C
short __cdecl _dscale(double* px, long exp);
short __cdecl _ldscale(long double* px, long exp);
short __cdecl _fdscale(float* px, long exp);
```

### <a name="parameters"></a>Paramètres

*Px*<br/>
Pointeur à un argument de point flottant.

*Exp*<br/>
Un exposant comme un type intégral.

### <a name="remarks"></a>Notes

Ces primitifs à point flottant prennent un pointeur à un *px* de valeur flottante-point et une valeur *exp*exposante , et l’échelle de la valeur en *px* par 2<sup>*exp*</sup>, si possible. La valeur retournée est le résultat de **fpclassify** sur la valeur d’entrée en *px* si c’est un NaN ou à l’infini, et sur la valeur de sortie en *px* autrement. Pour la portabilité, préférez les fonctions [ldexp, ldexpf et ldexpl.](ldexp.md)

## <a name="_dunscale-_ldunscale-_fdunscale"></a>_dunscale, _ldunscale, _fdunscale

### <a name="syntax"></a>Syntaxe

```C
short __cdecl _dunscale(short* pexp, double* px);
short __cdecl _ldunscale(short* pexp, long double* px);
short __cdecl _fdunscale(short* pexp, float* px);
```

### <a name="parameters"></a>Paramètres

*pexp*<br/>
Un pointeur à un exposant comme un type intégral.

*Px*<br/>
Pointeur à un argument de point flottant.

### <a name="remarks"></a>Notes

Ces primitifs flottants décomposent la valeur de point flottant point point point pointée par *px* dans un significand (mantissa) et un exposant, si possible. Le significand est à l’échelle de telle sorte que la valeur absolue est supérieure ou égale à 0,5 et moins de 1,0. L’exposant est la valeur *n*, où la valeur flottante d’origine est égale à la significand à l’échelle fois 2<sup>*n*</sup>. Cet *exposant* n integer est stocké à l’emplacement indiqué par *pexp*. La valeur retournée est le résultat de **fpclassify** sur la valeur d’entrée en *px* si c’est un NaN ou à l’infini, et sur la valeur de sortie autrement. Pour la portabilité, préférez les [fonctions frexp, frexpf, frexpl.](frexp.md)

## <a name="_dexp-_ldexp-_fdexp"></a>_dexp, _ldexp, _fdexp

### <a name="syntax"></a>Syntaxe

```C
short __cdecl _dexp(double* px, double y, long exp);
short __cdecl _ldexp(long double* px, long double y, long exp);
short __cdecl _fdexp(float* px, float y, long exp);
```

### <a name="parameters"></a>Paramètres

*y*<br/>
Argument de fonction flottant-point.

*Px*<br/>
Pointeur à un argument de point flottant.

*Exp*<br/>
Un exposant comme un type intégral.

### <a name="remarks"></a>Notes

Ces primitifs à point flottant construisent une valeur de point flottant dans l’emplacement pointé par *px* égal à *y* '2<sup>*exp*</sup>. La valeur retournée est le résultat de **fpclassify** sur la valeur d’entrée en *y* si c’est un NaN ou à l’infini, et sur la valeur de sortie en *px* autrement. Pour la portabilité, préférez les fonctions [ldexp, ldexpf et ldexpl.](ldexp.md)

## <a name="_dnorm-_fdnorm"></a>_dnorm, _fdnorm

### <a name="syntax"></a>Syntaxe

```C
short __cdecl _dnorm(unsigned short* ps);
short __cdecl _fdnorm(unsigned short* ps);
```

### <a name="parameters"></a>Paramètres

*Ps*<br/>
Pointeur à la représentation bitwise d’une valeur de point flottant exprimé comme un tableau de **court** **non signé** .

### <a name="remarks"></a>Notes

Ces primitifs à point flottant normalisent la partie fractionnelle d’une valeur de point flottant sous-alimenté et ajustent la *caractéristique,* ou exposant biaisé, pour correspondre. La valeur est passée comme la représentation bitwise du type de point flottant converti `_double_val` `_ldouble_val`en `_float_val` un tableau de **court** **non signé** à travers le , , ou type punning union déclaré dans math.h. La valeur de rendement est le résultat de **fpclassify** sur la valeur flottante de l’entrée si c’est un NaN ou à l’infini, et sur la valeur de sortie autrement.

## <a name="_dpoly-_ldpoly-_fdpoly"></a>_dpoly, _ldpoly, _fdpoly

### <a name="syntax"></a>Syntaxe

```C
double __cdecl _dpoly(double x, double const* table, int n);
long double __cdecl _ldpoly(long double x, long double const* table, int n);
float __cdecl _fdpoly(float x, _float const* table, int n);
```

### <a name="parameters"></a>Paramètres

*X*<br/>
Argument de fonction flottant-point.

*table*<br/>
Pointeur vers une table de coefficients constants pour un polynomial.

*n*<br/>
Ordre du polynomial à évaluer.

### <a name="remarks"></a>Notes

Ces primitifs à point flottant renvoient l’évaluation de *x* dans le polynomial de *l’ordre n* dont les coefficients sont représentés par les valeurs constantes correspondantes dans le *tableau.* Par exemple, si *le tableau*\[0] 3,0, *le tableau*\[1] 4,0, *le tableau*\[2, 5,0 et *n* 2, il représente le polynomial 5,0x<sup>2</sup> à 4,0x et 3,0. Si ce polynomial est évalué pour *x* de 2.0, le résultat est 31.0. Ces fonctions ne sont pas utilisées en interne.

## <a name="_dlog-_dlog-_dlog"></a>_dlog, _dlog, _dlog

### <a name="syntax"></a>Syntaxe

```C
double __cdecl _dlog(double x, int base_flag);
long double __cdecl _ldlog(long double x, int base_flag);
float __cdecl _fdlog(float x, int base_flag);
```

### <a name="parameters"></a>Paramètres

*X*<br/>
Argument de fonction flottant-point.

*base_flag*<br/>
Indicateur qui contrôle la base à utiliser, 0 pour la base *e* et non-zéro pour la base 10.

### <a name="remarks"></a>Notes

Ces primitifs à point flottant retournent le journal naturel de *x,* ln *(x)* ou log<sub>*e*</sub>(*x*), quand *base_flag* est de 0. Ils retournent la base de journal 10 de *x*, ou le journal<sub>10</sub>(*x*), quand *base_flag* n’est pas zéro. Ces fonctions ne sont pas utilisées en interne. Pour la portabilité, préférez les fonctions [journal, logf, logl, log10, log10f, et log10l](log-logf-log10-log10f.md).

## <a name="_dsin-_ldsin-_fdsin"></a>_dsin, _ldsin, _fdsin

### <a name="syntax"></a>Syntaxe

```C
double __cdecl _dsin(double x, unsigned int quadrant);
long double __cdecl _ldsin(long double x, unsigned int quadrant);
float __cdecl _fdsin(float x, unsigned int quadrant);
```

### <a name="parameters"></a>Paramètres

*X*<br/>
Argument de fonction flottant-point.

*Quadrant*<br/>
Quadrant décalage de 0, 1, 2, ou `sin` `cos`3 à utiliser pour produire , , , `-sin`et `-cos` les résultats.

### <a name="remarks"></a>Notes

Ces primitifs flottants retournent le sinus de *x* décalé par le *quadrant* modulo 4. En effet, ils retournent le sinus, le cosine, le -sine et le cosine de *x* lorsque le modulo *quadrant* 4 est respectivement 0, 1, 2 ou 3. Ces fonctions ne sont pas utilisées en interne. Pour la portabilité, préférez le [péché, sinf, sinl](sin-sinf-sinl.md), [cos, cosf, et les fonctions cosl.](cos-cosf-cosl.md)

## <a name="requirements"></a>Spécifications

En-tête: \<math.h>

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[Prise en charge de la virgule flottante](../floating-point-support.md)<br/>
[fpclassify](fpclassify.md)<br/>
[_fpclass, _fpclassf](fpclass-fpclassf.md)<br/>
[isfinite, _finite, _finitef](finite-finitef.md)<br/>
[isinf](isinf.md)<br/>
[isnan, _isnan, _isnanf](isnan-isnan-isnanf.md)<br/>
[isnormal](isnormal.md)<br/>
[cos, cosf, cosl](cos-cosf-cosl.md)<br/>
[frexp, frexpf, frexpl](frexp.md)<br/>
[ldexp, ldexpf, et ldexpl](ldexp.md)<br/>
[log, logf, logl, log10, log10f, log10l](log-logf-log10-log10f.md)<br/>
[sin, sinf, sinl](sin-sinf-sinl.md)<br/>
