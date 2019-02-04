---
title: Primitives à virgule flottante
ms.date: 01/31/2019
apiname:
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
apilocation:
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
apitype: DLLExport
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
ms.openlocfilehash: 230d0def145bcb443437b59303b2b36e348da2bb
ms.sourcegitcommit: e98671a4f741b69d6277da02e6b4c9b1fd3c0ae5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/04/2019
ms.locfileid: "55703439"
---
# <a name="floating-point-primitives"></a>Primitives à virgule flottante

Fonctions primitifs spécifiques à Microsoft sont utilisées pour implémenter certaines standards fonctions runtime C (CRT) de bibliothèque à virgule flottante. Ils sont documentés ici par souci d’exhaustivité, mais ne sont pas recommandées pour une utilisation. Certaines de ces fonctions sont notées comme inutilisé, car elles sont connues à avoir des problèmes de précision, la gestion des exceptions et la conformité aux normes IEEE-754 comportement. Ils existent dans la bibliothèque uniquement pour la compatibilité descendante. Pour le comportement correct, portabilité et de conformité aux normes, préférez les fonctions à virgule flottante standards à ces fonctions.

## <a name="dclass-ldclass-fdclass"></a>_dclass, _ldclass, _fdclass

### <a name="syntax"></a>Syntaxe

```C
short __cdecl _dclass(double x);
short __cdecl _ldclass(long double x);
short __cdecl _fdclass(float x);
```

### <a name="parameters"></a>Paramètres

*x*<br/>
Argument de fonction à virgule flottante.

### <a name="remarks"></a>Notes

Ces primitives à virgule flottante implémentent les versions C de la macro CRT [fpclassify](fpclassify.md) pour les types à virgule flottante. La classification de l’argument *x* est renvoyé comme l’un de ces constantes définies dans math.h :

|Value|Description|
|-----------|-----------------|
| **FP_NAN** | NaN silencieux, signalant ou indéterminé |
| **FP_INFINITE** | Infini positif ou négatif |
| **FP_NORMAL** | Valeur non nulle normalisée positive ou négative |
| **FP_SUBNORMAL** | Une valeur positive ou négative subnormal (dénormalisée) |
| **FP_ZERO** | Valeur nulle positive ou négative |

Pour plus d’informations, vous pouvez utiliser spécifique à Microsoft, [_fpclass, _fpclassf](fpclass-fpclassf.md) fonctions. Utilisez le [fpclassify](fpclassify.md) macro ou une fonction pour la portabilité.

## <a name="dsign-ldsign-fdsign"></a>_dsign, _ldsign, _fdsign

### <a name="syntax"></a>Syntaxe

```C
int __cdecl _dsign(double x);
int __cdecl _ldsign(long double x);
int __cdecl _fdsign(float x);
```

### <a name="parameters"></a>Paramètres

*x*<br/>
Argument de fonction à virgule flottante.

### <a name="remarks"></a>Notes

Implémentent ces primitives à virgule flottante le [signbit](signbit.md) macro ou fonction dans la bibliothèque CRT. Elles retournent une valeur différente de zéro si le bit de signe est défini dans la mantisse (mantisse) de l’argument *x*et 0 si le bit de signe n’est pas défini.

## <a name="dpcomp-ldpcomp-fdpcomp"></a>_dpcomp, _ldpcomp, _fdpcomp

### <a name="syntax"></a>Syntaxe

```C
int __cdecl _dpcomp(double x, double y);
int __cdecl _ldpcomp(long double x, long double y);
int __cdecl _fdpcomp(float x, float y);
```

### <a name="parameters"></a>Paramètres

*x*, *y*<br/>
Arguments de fonction en virgule flottante.

### <a name="remarks"></a>Notes

Ces primitives à virgule flottante prennent deux arguments, *x* et *y*et retournent une valeur qui indique leur relation de classement, exprimée en tant que l’opérateur de bits ou des constantes définies dans math.h :

| Value | Description |
|------------|-----------------|
| **_FP_LT** | *x* peut être considéré comme inférieur à *y* |
| **_FP_EQ** | *x* peut être considéré comme égal à *y* |
| **_FP_GT** | *x* peut être considéré comme supérieur *y* |

Ces primitives implémentent le [isgreater, isgreaterequal, isless, islessequal, islessgreater et isunordered](floating-point-ordering.md) macros et fonctions dans la bibliothèque CRT.

## <a name="dtest-ldtest-fdtest"></a>_dtest, _ldtest, _fdtest

### <a name="syntax"></a>Syntaxe

```C
short __cdecl _dtest(double* px);
short __cdecl _ldtest(long double* px);
short __cdecl _fdtest(float* px);
```

### <a name="parameters"></a>Paramètres

*px*<br/>
Pointeur vers un argument à virgule flottante.

### <a name="remarks"></a>Notes

Ces primitives à virgule flottante implémentent les versions C++ de la fonction CRT [fpclassify](fpclassify.md) pour les types à virgule flottante. L’argument *x* est évaluée et la classification est retournée en tant qu’une des constantes définies dans math.h :

|Value|Description|
|-----------|-----------------|
| **FP_NAN** | NaN silencieux, signalant ou indéterminé |
| **FP_INFINITE** | Infini positif ou négatif |
| **FP_NORMAL** | Valeur non nulle normalisée positive ou négative |
| **FP_SUBNORMAL** | Une valeur positive ou négative subnormal (dénormalisée) |
| **FP_ZERO** | Valeur nulle positive ou négative |

Pour plus d’informations, vous pouvez utiliser spécifique à Microsoft, [_fpclass, _fpclassf](fpclass-fpclassf.md) fonctions. Utilisez le [fpclassify](fpclassify.md) (fonction) pour la portabilité.

## <a name="dint-ldint-fdint"></a>_d_int, _ld_int, _fd_int

### <a name="syntax"></a>Syntaxe

```C
short __cdecl _d_int(double* px, short exp);
short __cdecl _ld_int(long double* px, short exp);
short __cdecl _fd_int(float* px, short exp);
```

### <a name="parameters"></a>Paramètres

*px*<br/>
Pointeur vers un argument à virgule flottante.

*exp*<br/>
Un exposant comme un type intégral.

### <a name="remarks"></a>Notes

Ces primitives à virgule flottante acceptent un pointeur vers une valeur à virgule flottante *px* et une valeur d’exposant *exp*et supprimer la partie fractionnaire de la valeur à virgule flottante ci-dessous l’exposant donné, si possible . La valeur retournée est le résultat de **fpclassify** sur la valeur d’entrée dans *px* s’il s’agit d’une valeur NaN ou l’infini et sur la valeur de sortie dans *px* dans le cas contraire.

## <a name="dscale-ldscale-fdscale"></a>_dscale, _ldscale, _fdscale

### <a name="syntax"></a>Syntaxe

```C
short __cdecl _dscale(double* px, long exp);
short __cdecl _ldscale(long double* px, long exp);
short __cdecl _fdscale(float* px, long exp);
```

### <a name="parameters"></a>Paramètres

*px*<br/>
Pointeur vers un argument à virgule flottante.

*exp*<br/>
Un exposant comme un type intégral.

### <a name="remarks"></a>Notes

Ces primitives à virgule flottante acceptent un pointeur vers une valeur à virgule flottante *px* et une valeur d’exposant *exp*, et mettre à l’échelle de la valeur dans *px* par 2<sup> *exp*</sup>, si possible. La valeur retournée est le résultat de **fpclassify** sur la valeur d’entrée dans *px* s’il s’agit d’une valeur NaN ou l’infini et sur la valeur de sortie dans *px* dans le cas contraire. Pour une portabilité, préférez la [ldexp, ldexpf et ldexpl](ldexp.md) fonctions.

## <a name="dunscale-ldunscale-fdunscale"></a>_dunscale, _ldunscale, _fdunscale

### <a name="syntax"></a>Syntaxe

```C
short __cdecl _dunscale(short* pexp, double* px);
short __cdecl _ldunscale(short* pexp, long double* px);
short __cdecl _fdunscale(short* pexp, float* px);
```

### <a name="parameters"></a>Paramètres

*pexp*<br/>
Pointeur vers un exposant comme un type intégral.

*px*<br/>
Pointeur vers un argument à virgule flottante.

### <a name="remarks"></a>Notes

Ces primitives à virgule flottante décomposent la valeur à virgule flottante pointée par *px* en une mantisse (mantisse) et un exposant, si possible. La mantisse est mis à l’échelle de telle sorte que la valeur absolue est supérieure ou égale à 0,5 et inférieur à 1,0. L’exposant est la valeur *n*, où la valeur à virgule flottante d’origine est égale à la mantisse à l’échelle de temps 2<sup>*n*</sup>. Cette exposant entier *n* est stocké à l’emplacement vers lequel pointé *pexp*. La valeur retournée est le résultat de **fpclassify** sur la valeur d’entrée dans *px* s’il s’agit d’une valeur NaN ou l’infini et sur la valeur de sortie dans le cas contraire. Pour une portabilité, préférez la [frexp, frexpf, frexpl](frexp.md) fonctions.

## <a name="dexp-ldexp-fdexp"></a>_dexp, _ldexp, _fdexp

### <a name="syntax"></a>Syntaxe

```C
short __cdecl _dexp(double* px, double y, long exp);
short __cdecl _ldexp(long double* px, long double y, long exp);
short __cdecl _fdexp(float* px, float y, long exp);
```

### <a name="parameters"></a>Paramètres

*y*<br/>
Argument de fonction à virgule flottante.

*px*<br/>
Pointeur vers un argument à virgule flottante.

*exp*<br/>
Un exposant comme un type intégral.

### <a name="remarks"></a>Notes

Ces primitives à virgule flottante construire une valeur à virgule flottante dans l’emplacement pointé par *px* égal à *y* * 2<sup>*exp*</sup>. La valeur retournée est le résultat de **fpclassify** sur la valeur d’entrée dans *y* s’il s’agit d’une valeur NaN ou l’infini et sur la valeur de sortie dans *px* dans le cas contraire. Pour une portabilité, préférez la [ldexp, ldexpf et ldexpl](ldexp.md) fonctions.

## <a name="dnorm-fdnorm"></a>_dnorm, _fdnorm

### <a name="syntax"></a>Syntaxe

```C
short __cdecl _dnorm(unsigned short* ps);
short __cdecl _fdnorm(unsigned short* ps);
```

### <a name="parameters"></a>Paramètres

*ps*<br/>
Pointeur vers la représentation au niveau du bit d’une valeur à virgule flottante exprimée sous forme de tableau de **non signé** **court**.

### <a name="remarks"></a>Notes

Ces primitives à virgule flottante normaliser la partie fractionnaire d’une valeur à virgule flottante underflowed et ajustez la *caractéristique*, ou exposant biaisé, pour faire correspondre. La valeur est passée en tant que la représentation au niveau du bit du type à virgule flottante converti en un tableau de **non signé** **court** via la `_double_val`, `_ldouble_val`, ou `_float_val` type union punning déclaré dans math.h. La valeur de retour est le résultat de **fpclassify** sur la valeur à virgule flottante d’entrée s’il s’agit d’une valeur NaN ou l’infini et sur la valeur de sortie dans le cas contraire.

## <a name="dpoly-ldpoly-fdpoly"></a>_dpoly, _ldpoly, _fdpoly

### <a name="syntax"></a>Syntaxe

```C
double __cdecl _dpoly(double x, double const* table, int n);
long double __cdecl _ldpoly(long double x, long double const* table, int n);
float __cdecl _fdpoly(float x, _float const* table, int n);
```

### <a name="parameters"></a>Paramètres

*x*<br/>
Argument de fonction à virgule flottante.

*table*<br/>
Pointeur vers une table de coefficients constante pour une représentation polynomiale.

*n*<br/>
Ordre de la représentation polynomiale à évaluer.

### <a name="remarks"></a>Notes

Ces primitives à virgule flottante retournent la version d’évaluation de *x* dans la représentation polynomiale d’ordre *n* dont les coefficients sont représentés par les valeurs de constante correspondantes dans *table*. Par exemple, si *table*\[0] = 3.0, *table*\[1] = 4.0, *table*\[2] = 5.0, et *n* = 2, il représente le x 5.0 polynomiale<sup>2</sup> + 4.0 x + 3.0. Si cette représentation polynomiale est évaluée pour *x* de 2.0, le résultat est 31,0. Ces fonctions ne sont pas utilisées en interne.

## <a name="dlog-dlog-dlog"></a>_dlog, _dlog, _dlog

### <a name="syntax"></a>Syntaxe

```C
double __cdecl _dlog(double x, int base_flag);
long double __cdecl _ldlog(long double x, int base_flag);
float __cdecl _fdlog(float x, int base_flag);
```

### <a name="parameters"></a>Paramètres

*x*<br/>
Argument de fonction à virgule flottante.

*base_flag*<br/>
Indicateur qui détermine la base à utiliser, 0 pour la base de *e* et différent de zéro pour la base 10.

### <a name="remarks"></a>Notes

Ces primitives à virgule flottante retournent le logarithme naturel de *x*, à savoir ln (*x*) ou journal<sub>*e*</sub>(*x*), Lorsque *base_flag* est 0. Elles retournent le journal de base 10 de *x*, ou journal<sub>10</sub>(*x*), lorsque *base_flag* est différente de zéro. Ces fonctions ne sont pas utilisées en interne. Pour une portabilité, préférez les fonctions [journal logf, logl, log10, log10f et log10l](log-logf-log10-log10f.md).

## <a name="dsin-ldsin-fdsin"></a>_dsin, _ldsin, _fdsin

### <a name="syntax"></a>Syntaxe

```C
double __cdecl _dsin(double x, unsigned int quadrant);
long double __cdecl _ldsin(long double x, unsigned int quadrant);
float __cdecl _fdsin(float x, unsigned int quadrant);
```

### <a name="parameters"></a>Paramètres

*x*<br/>
Argument de fonction à virgule flottante.

*quadrant*<br/>
Décalage du quadrant de 0, 1, 2 ou 3 à utiliser pour produire `sin`, `cos`, `-sin`, et `-cos` résultats.

### <a name="remarks"></a>Notes

Ces primitives à virgule flottante retournent le sinus de *x* décalage par le *quadrant* modulo 4. En effet, elles retournent le sinus, cosinus, - sinus et - cosinus de *x* lorsque *quadrant* modulo 4 est 0, 1, 2 ou 3, respectivement. Ces fonctions ne sont pas utilisées en interne. Pour une portabilité, préférez la [sin, sinf, sinl](sin-sinf-sinl.md), [cos, cosf et cosl](cos-cosf-cosl.md) fonctions.

## <a name="requirements"></a>Spécifications

En-tête : \<math.h >

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[Prise en charge à virgule flottante](../floating-point-support.md)<br/>
[fpclassify](fpclassify.md)<br/>
[_fpclass, _fpclassf](fpclass-fpclassf.md)<br/>
[isfinite, _finite, _finitef](finite-finitef.md)<br/>
[isinf](isinf.md)<br/>
[isnan, _isnan, _isnanf](isnan-isnan-isnanf.md)<br/>
[isnormal](isnormal.md)<br/>
[cos, cosf, cosl](cos-cosf-cosl.md)<br/>
[frexp, frexpf, frexpl](frexp.md)<br/>
[ldexp, ldexpf, and ldexpl](ldexp.md)<br/>
[log, logf, logl, log10, log10f, log10l](log-logf-log10-log10f.md)<br/>
[sin, sinf, sinl](sin-sinf-sinl.md)<br/>
