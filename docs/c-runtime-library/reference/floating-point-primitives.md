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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: e28c873206d8f050dbde2afc9ebfe3540b6642ff
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87218679"
---
# <a name="floating-point-primitives"></a>Primitives à virgule flottante

Fonctions primitives spécifiques à Microsoft utilisées pour implémenter certaines fonctions à virgule flottante de la bibliothèque C Runtime (CRT) standard. Elles sont documentées ici à des fins d’exhaustivité, mais ne sont pas recommandées pour une utilisation. Certaines de ces fonctions sont notées comme inutilisées, car elles sont connues pour présenter des problèmes de précision, de gestion des exceptions et de conformité au comportement IEEE-754. Ils existent uniquement dans la bibliothèque à des fins de compatibilité descendante. Pour un comportement, une portabilité et un respect corrects des normes, préférez les fonctions à virgule flottante standard sur ces fonctions.

Par défaut, l’état global de cette fonction est limité à l’application. Pour modifier cette valeur, consultez [état global dans le CRT](../global-state.md).

## <a name="_dclass-_ldclass-_fdclass"></a>_dclass, _ldclass _fdclass

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

Ces primitives à virgule flottante implémentent les versions C de la macro CRT [fpclassify](fpclassify.md) pour les types à virgule flottante. La classification de l’argument *x* est retournée en tant que l’une de ces constantes, définie dans Math. h :

|Valeur|Description|
|-----------|-----------------|
| **FP_NAN** | NaN silencieux, signalant ou indéterminé |
| **FP_INFINITE** | Infini positif ou négatif |
| **FP_NORMAL** | Valeur non nulle normalisée positive ou négative |
| **FP_SUBNORMAL** | Valeur subnormale positive ou négative (dénormalisée) |
| **FP_ZERO** | Valeur nulle positive ou négative |

Pour plus d’informations, vous pouvez utiliser les fonctions de [_fpclass, _fpclassf](fpclass-fpclassf.md) spécifiques à Microsoft. Utilisez la macro ou la fonction [fpclassify](fpclassify.md) pour la portabilité.

## <a name="_dsign-_ldsign-_fdsign"></a>_dsign, _ldsign _fdsign

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

Ces primitives à virgule flottante implémentent la macro ou la fonction [signbit,](signbit.md) dans le CRT. Elles retournent une valeur différente de zéro si le bit de signe est défini dans la mantisse (mantisse) de l’argument *x*, et 0 si le bit de signe n’est pas défini.

## <a name="_dpcomp-_ldpcomp-_fdpcomp"></a>_dpcomp, _ldpcomp _fdpcomp

### <a name="syntax"></a>Syntaxe

```C
int __cdecl _dpcomp(double x, double y);
int __cdecl _ldpcomp(long double x, long double y);
int __cdecl _fdpcomp(float x, float y);
```

### <a name="parameters"></a>Paramètres

*x*, *y*<br/>
Arguments de fonction à virgule flottante.

### <a name="remarks"></a>Notes

Ces primitives à virgule flottante prennent deux arguments, *x* et *y*, et retournent une valeur qui indique leur relation de classement, exprimée sous la forme d’une opération de bits or de ces constantes, définie dans Math. h :

| Valeur | Description |
|------------|-----------------|
| **_FP_LT** | *x* peut être considéré comme inférieur à *y* |
| **_FP_EQ** | *x* peut être considéré comme égal à *y* |
| **_FP_GT** | *x* peut être considéré comme supérieur à *y* |

Ces primitives implémentent les macros [isgreater, isgreaterequal, îless, islessequal, islessgreater et isunordered](floating-point-ordering.md) et les fonctions dans le CRT.

## <a name="_dtest-_ldtest-_fdtest"></a>_dtest, _ldtest _fdtest

### <a name="syntax"></a>Syntaxe

```C
short __cdecl _dtest(double* px);
short __cdecl _ldtest(long double* px);
short __cdecl _fdtest(float* px);
```

### <a name="parameters"></a>Paramètres

*pix*<br/>
Pointeur vers un argument à virgule flottante.

### <a name="remarks"></a>Notes

Ces primitives à virgule flottante implémentent les versions C++ de la fonction CRT [fpclassify](fpclassify.md) pour les types à virgule flottante. L’argument *x* est évalué et la classification est retournée en tant que l’une de ces constantes, définie dans Math. h :

|Valeur|Description|
|-----------|-----------------|
| **FP_NAN** | NaN silencieux, signalant ou indéterminé |
| **FP_INFINITE** | Infini positif ou négatif |
| **FP_NORMAL** | Valeur non nulle normalisée positive ou négative |
| **FP_SUBNORMAL** | Valeur subnormale positive ou négative (dénormalisée) |
| **FP_ZERO** | Valeur nulle positive ou négative |

Pour plus d’informations, vous pouvez utiliser les fonctions de [_fpclass, _fpclassf](fpclass-fpclassf.md) spécifiques à Microsoft. Utilisez la fonction [fpclassify](fpclassify.md) pour la portabilité.

## <a name="_d_int-_ld_int-_fd_int"></a>_d_int, _ld_int _fd_int

### <a name="syntax"></a>Syntaxe

```C
short __cdecl _d_int(double* px, short exp);
short __cdecl _ld_int(long double* px, short exp);
short __cdecl _fd_int(float* px, short exp);
```

### <a name="parameters"></a>Paramètres

*pix*<br/>
Pointeur vers un argument à virgule flottante.

*exp*<br/>
Exposant comme type intégral.

### <a name="remarks"></a>Notes

Ces primitives à virgule flottante prennent un pointeur vers une valeur à virgule flottante *PX* et une valeur d’exposant *exp*, et suppriment la partie fractionnaire de la valeur à virgule flottante sous l’exposant donné, si possible. La valeur retournée est le résultat de **fpclassify** sur la valeur d’entrée de *PX* s’il s’agit d’un Nan ou d’une infini, et sur la valeur de sortie dans *PX* dans le cas contraire.

## <a name="_dscale-_ldscale-_fdscale"></a>_dscale, _ldscale _fdscale

### <a name="syntax"></a>Syntaxe

```C
short __cdecl _dscale(double* px, long exp);
short __cdecl _ldscale(long double* px, long exp);
short __cdecl _fdscale(float* px, long exp);
```

### <a name="parameters"></a>Paramètres

*pix*<br/>
Pointeur vers un argument à virgule flottante.

*exp*<br/>
Exposant comme type intégral.

### <a name="remarks"></a>Notes

Ces primitives à virgule flottante prennent un pointeur vers une valeur à virgule flottante *PX* et une valeur d’exposant *exp*, et ajustent la valeur en *PX* de 2<sup>*exp*</sup>, si possible. La valeur retournée est le résultat de **fpclassify** sur la valeur d’entrée de *PX* s’il s’agit d’un Nan ou d’une infini, et sur la valeur de sortie dans *PX* dans le cas contraire. Pour la portabilité, préférez les fonctions [ldexp, ldexpf, et ldexpl](ldexp.md) .

## <a name="_dunscale-_ldunscale-_fdunscale"></a>_dunscale, _ldunscale _fdunscale

### <a name="syntax"></a>Syntaxe

```C
short __cdecl _dunscale(short* pexp, double* px);
short __cdecl _ldunscale(short* pexp, long double* px);
short __cdecl _fdunscale(short* pexp, float* px);
```

### <a name="parameters"></a>Paramètres

*pexp*<br/>
Pointeur vers un exposant en tant que type intégral.

*pix*<br/>
Pointeur vers un argument à virgule flottante.

### <a name="remarks"></a>Notes

Ces primitives à virgule flottante décomposent la valeur à virgule flottante pointée par *PX* dans une mantisse (mantisse) et un exposant, si possible. Le mantisse est mis à l’échelle de telle sorte que la valeur absolue soit supérieure ou égale à 0,5 et inférieure à 1,0. L’exposant est la valeur *n*, où la valeur à virgule flottante d’origine est égale au nombre de mantisse mis à l’échelle 2<sup>*n*</sup>. Cet exposant entier *n* est stocké à l’emplacement désigné par *pexp*. La valeur retournée est le résultat de **fpclassify** sur la valeur d’entrée de *PX* s’il s’agit d’une valeur NaN ou d’une valeur d’infini, et sur la valeur de sortie dans le cas contraire. Pour la portabilité, préférez les fonctions [frexp, frexpf,, frexpl](frexp.md) .

## <a name="_dexp-_ldexp-_fdexp"></a>_dexp, _ldexp _fdexp

### <a name="syntax"></a>Syntaxe

```C
short __cdecl _dexp(double* px, double y, long exp);
short __cdecl _ldexp(long double* px, long double y, long exp);
short __cdecl _fdexp(float* px, float y, long exp);
```

### <a name="parameters"></a>Paramètres

*y*<br/>
Argument de fonction à virgule flottante.

*pix*<br/>
Pointeur vers un argument à virgule flottante.

*exp*<br/>
Exposant comme type intégral.

### <a name="remarks"></a>Notes

Ces primitives à virgule flottante construisent une valeur à virgule flottante à l’emplacement désigné par *PX* égal à *y* * 2<sup>*exp*</sup>. La valeur retournée est le résultat de **fpclassify** sur la valeur d’entrée de *y* s’il s’agit d’un Nan ou d’une infini, et sur la valeur de sortie dans *PX* dans le cas contraire. Pour la portabilité, préférez les fonctions [ldexp, ldexpf, et ldexpl](ldexp.md) .

## <a name="_dnorm-_fdnorm"></a>_dnorm, _fdnorm

### <a name="syntax"></a>Syntaxe

```C
short __cdecl _dnorm(unsigned short* ps);
short __cdecl _fdnorm(unsigned short* ps);
```

### <a name="parameters"></a>Paramètres

*ps*<br/>
Pointeur vers la représentation au niveau du bit d’une valeur à virgule flottante exprimée sous la forme d’un tableau de **`unsigned short`** .

### <a name="remarks"></a>Notes

Ces primitives à virgule flottante normalisent la partie fractionnaire d’une valeur à virgule flottante dépassée et ajustent la *caractéristique*, ou exposant biais, pour qu’elle corresponde. La valeur est passée en tant que représentation au niveau du bit du type à virgule flottante convertie en un tableau de **`unsigned short`** par le biais de `_double_val` , ou d’une `_ldouble_val` `_float_val` Union punning de type déclarée dans Math. h. La valeur de retour est le résultat de **fpclassify** sur la valeur à virgule flottante d’entrée s’il s’agit d’un Nan ou d’une infini, et sur la valeur de sortie dans le cas contraire.

## <a name="_dpoly-_ldpoly-_fdpoly"></a>_dpoly, _ldpoly _fdpoly

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
Pointeur vers une table de coefficients de constante pour un polynomial.

*n*<br/>
Ordre du polynôme à évaluer.

### <a name="remarks"></a>Notes

Ces primitives à virgule flottante retournent l’évaluation de *x* dans le degré polynomial de l’ordre *n* dont les coefficients sont représentés par les valeurs constantes correspondantes dans la *table*. Par exemple, si *table* \[ 0] = 3,0, *table* \[ 1] = 4,0, *table* \[ 2] = 5,0, et *n* = 2, il représente le polynôme 5,0 x<sup>2</sup> + 4.0 x + 3,0. Si ce polynôme est évaluée pour *x* de 2,0, le résultat est 31,0. Ces fonctions ne sont pas utilisées en interne.

## <a name="_dlog-_dlog-_dlog"></a>_dlog, _dlog _dlog

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
Indicateur qui contrôle la base à utiliser, 0 pour la base *e* et différente de zéro pour base 10.

### <a name="remarks"></a>Notes

Ces primitives à virgule flottante retournent le logarithme népérien de *x*, ln (*x*) ou log<sub>*e*</sub>(*x*), lorsque *base_flag* est égal à 0. Ils retournent la base du journal 10 sur *x*ou log<sub>10</sub>(*x*), lorsque *base_flag* est différent de zéro. Ces fonctions ne sont pas utilisées en interne. Pour la portabilité, préférez les fonctions [log, LogF,, logl, log10, log10f, et log10L](log-logf-log10-log10f.md).

## <a name="_dsin-_ldsin-_fdsin"></a>_dsin, _ldsin _fdsin

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
Décalage du quadrant de 0, 1, 2 ou 3 à utiliser pour produire `sin` `cos` `-sin` les résultats,, et `-cos` .

### <a name="remarks"></a>Notes

Ces primitives à virgule flottante retournent le sinus de décalage *x* par le *quadrant* modulo 4. En effet, elles retournent le sinus, le cosinus, le sinus et le cosinus de *x* lorsque le *quadrant* modulo 4 est respectivement 0, 1, 2 ou 3. Ces fonctions ne sont pas utilisées en interne. Pour la portabilité, préférez les fonctions [Sin, sinf, sinl](sin-sinf-sinl.md), [cos, cosf, et COSL](cos-cosf-cosl.md) .

## <a name="requirements"></a>Spécifications

En-tête : \<math.h>

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
