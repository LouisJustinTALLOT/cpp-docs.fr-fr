---
title: sinh, sinhf, sinhl
description: Référence d’API pour le calcul du sinus hyperbolique d’une valeur à virgule flottante.
ms.date: 1/15/2021
api_name:
- sinh
- sinhl
- sinhf
- sinhl
- _o_sinh
- _o_sinhf
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
- sinh
- sinhf
- sinhl
helpviewer_keywords:
- sinh function
- sinhl function
- sinhf function
- calculating hyperbolic sines
- trigonometric functions
- sinhf function
- sinhl function
- hyperbolic functions
ms.openlocfilehash: 73f7210105419c4b8cb9a6e47e5c5f0e43437738
ms.sourcegitcommit: 92dc6d99ba5dcf3b64dee164df2d29beb1e608da
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/18/2021
ms.locfileid: "98563794"
---
# <a name="sinh-sinhf-sinhl"></a>`sinh`, `sinhf`, `sinhl`

Calcule le sinus hyperbolique.

## <a name="syntax"></a>Syntaxe

```C
double sinh(double x);
float sinhf(float x);
long double sinhl(long double x);
#define sinh(x) // Requires C11 or higher

float sinh(float x);  // C++ only
long double sinh(long double x);  // C++ only
```

### <a name="parameters"></a>Paramètres

*`x`*\
Angle en radians.

## <a name="return-value"></a>Valeur renvoyée

Les **`sinh`** fonctions retournent le sinus hyperbolique de *`x`* . Par défaut, si le résultat est trop grand, **`sinh`** affecte **`errno`** à la valeur **`ERANGE`** et retourne ± **`HUGE_VAL`** .

|Entrée|Exception SEH|`Matherr` titre|
|-----------|-------------------|-----------------------|
|± `QNAN`,`IND`|None|`_DOMAIN`|
|&#124;x&#124; ≥ 7.104760 e + 002|`OVERFLOW+INEXACT`|`OVERFLOW`|

Pour plus d’informations sur les codes de retour, consultez [ `errno` ,, `_doserrno` `_sys_errlist` et `_sys_nerr` ](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Remarques

C++ autorisant la surcharge, vous pouvez appeler des surcharges de **`sinh`** qui acceptent et retournent des **`float`** **`long double`** valeurs ou. Dans un programme C, à moins que vous n’utilisiez la `<tgmath.h>` macro pour appeler cette fonction, **`sinh`** prend et retourne toujours **`double`** .

Si vous utilisez la `<tgmath.h>` `sinh()` macro, le type de l’argument détermine la version de la fonction qui est sélectionnée. Pour plus d’informations [, consultez Math type-Generic](../../c-runtime-library/tgmath.md) .

Par défaut, l’état global de cette fonction est limité à l’application. Pour modifier cette valeur, consultez [état global dans le CRT](../global-state.md).

## <a name="requirements"></a>Configuration requise

|Routine|En-tête requis (C)|En-tête requis (C++)|
|-|-|-|
|**`sinh`**, **`sinhf`**, **`sinhl`**|`<math.h>`|`<cmath>` ou `<math.h>`|
|**`sinh()`** macrovirus | `<tgmath.h>` ||

Pour plus d’informations sur la compatibilité, consultez [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

```C
// crt_sinhcosh.c
// This program displays the hyperbolic
// sine and hyperbolic cosine of pi / 2.
// Compile by using: cl /W4 crt_sinhcosh.c

#include <math.h>
#include <stdio.h>

int main( void)
{
   double pi = 3.1415926535;
   double x, y;

   x = pi / 2;
   y = sinh( x );
   printf( "sinh( %f ) = %f\n",x, y );
   y = cosh( x );
   printf( "cosh( %f ) = %f\n",x, y );
}
```

```Output
sinh( 1.570796 ) = 2.301299
cosh( 1.570796 ) = 2.509178
```

## <a name="see-also"></a>Voir aussi

[Prise en charge de la virgule flottante](../../c-runtime-library/floating-point-support.md)\
[`acosh`, `acoshf`, `acoshl`](acosh-acoshf-acoshl.md)\
[`asinh`, `asinhf`, `asinhl`](asinh-asinhf-asinhl.md)\
[`atanh`, `atanhf`, `atanhl`](atanh-atanhf-atanhl.md)\
[`cosh`, `coshf`, `coshl`](cosh-coshf-coshl.md)\
[`tanh`, `tanhf`, `tanhl`](tanh-tanhf-tanhl.md)