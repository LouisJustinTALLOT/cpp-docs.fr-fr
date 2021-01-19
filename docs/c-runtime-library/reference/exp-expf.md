---
title: exp, expf, expl
description: Informations de référence sur les API pour exp, expf, et expl ; qui calcule l’exponentiel.
ms.date: 1/15/2021
api_name:
- expf
- expl
- exp
- _o_exp
- _o_expf
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
- _expl
- expf
- expl
- exp
helpviewer_keywords:
- exponential calculations
- expf function
- expl function
- calculating exponentials
- exp function
ms.openlocfilehash: ac51744fe332fbf378139df11e7d07afe44029ca
ms.sourcegitcommit: 92dc6d99ba5dcf3b64dee164df2d29beb1e608da
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/18/2021
ms.locfileid: "98564002"
---
# <a name="exp-expf-expl"></a>`exp`, `expf`, `expl`

Calcule la valeur exponentielle.

## <a name="syntax"></a>Syntaxe

```C
double exp(
   double x
);
float exp(
   float x
);  // C++ only
long double exp(
   long double x
);  // C++ only
float expf(
   float x
);
long double expl(
   long double x
);
#define exp(z) // Requires C11 or higher
```

### <a name="parameters"></a>Paramètres

*`x`*\
Valeur à virgule flottante pour exponentiate le logarithme népérien de base *e* par.

## <a name="return-value"></a>Valeur renvoyée

Les **`exp`** fonctions retournent la valeur exponentielle du paramètre à virgule flottante, *`x`* , en cas de réussite. Autrement dit, le résultat est *e* <sup>*`x`*</sup> , où *e* est la base du logarithme népérien. En cas de dépassement de capacité, la fonction retourne `INF` (infini) et en négatif, **`exp`** retourne 0.

|Entrée|Exception SEH|`Matherr` titre|
|-----------|-------------------|-----------------------|
|± NaN quiet, indéterminé|None|`_DOMAIN`|
|± Infini|`INVALID`|`_DOMAIN`|
|x ≥ 7,097827e+002|`INEXACT+OVERFLOW`|`OVERFLOW`|
|X ≤ -7,083964e+002|`INEXACT+UNDERFLOW`|`UNDERFLOW`|

La **`exp`** fonction a une implémentation qui utilise SSE2 (streaming SIMD Extensions 2). [`_set_SSE2_enable`](set-sse2-enable.md)Pour obtenir des informations et des restrictions sur l’utilisation de l’implémentation SSE2, consultez.

## <a name="remarks"></a>Remarques

C++ autorisant la surcharge, vous pouvez appeler des surcharges de **`exp`** qui acceptent un **`float`** **`long double`** argument ou. Dans un programme C, à moins que vous n’utilisiez la `<tgmath.h>` macro pour appeler cette fonction, **`exp`** accepte et retourne toujours un **`double`** .

Si vous utilisez la `<tgmath.h>` `exp()` macro, le type de l’argument détermine la version de la fonction qui est sélectionnée. Pour plus d’informations [, consultez Math type-Generic](../../c-runtime-library/tgmath.md) .

Par défaut, l’état global de cette fonction est limité à l’application. Pour modifier cette valeur, consultez [état global dans le CRT](../global-state.md).

## <a name="requirements"></a>Configuration requise

|Fonction|En-tête C requis|En-tête C++ requis|
|--------------|---------------------|---|
|**`exp`**, **`expf`**, **`expl`**|`<math.h>`|`<cmath>` ou `<math.h>`|
|**`exp`** macrovirus| `<tgmath.h>` ||

Pour plus d’informations sur la compatibilité, consultez [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

```C
// crt_exp.c

#include <math.h>
#include <stdio.h>

int main( void )
{
   double x = 2.302585093, y;

   y = exp( x );
   printf( "exp( %f ) = %f\n", x, y );
}
```

```Output
exp( 2.302585 ) = 10.000000
```

## <a name="see-also"></a>Voir aussi

[Prise en charge de la virgule flottante](../../c-runtime-library/floating-point-support.md)\
[budget`og, logf, log10, log10f`](log-logf-log10-log10f.md)\
[`_CIexp`](../../c-runtime-library/ciexp.md)