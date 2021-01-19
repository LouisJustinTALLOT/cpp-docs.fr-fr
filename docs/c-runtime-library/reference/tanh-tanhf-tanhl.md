---
title: tanh, tanhf, tanhl
description: Informations de référence sur l’API pour Tanh, tanhf, et tanhl ; qui calcule la tangente hyperbolique d’une valeur à virgule flottante.
ms.date: 1/15/2021
api_name:
- tanh
- tanhf
- tanhl
- _o_tanh
- _o_tanhf
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
- tanh
- tanhf
- tanhl
- _tanhl
helpviewer_keywords:
- tanhl function
- _tanhl function
- tanh function
- tanhf function
- trigonometric functions
- hyperbolic functions
ms.openlocfilehash: c09655b4a86010ff6a476f7dacbce4f9f73ab3cc
ms.sourcegitcommit: 92dc6d99ba5dcf3b64dee164df2d29beb1e608da
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/18/2021
ms.locfileid: "98564119"
---
# <a name="tanh-tanhf-tanhl"></a>`tanh`, `tanhf`, `tanhl`

Calcule la tangente hyperbolique.

## <a name="syntax"></a>Syntaxe

```C
double tanh( double x );
float tanhf( float x );
long double tanhl( long double x );
#define tanh(x) // Requires C11 or higher
```

```cpp
float tanh( float x );  // C++ only
long double tanh( long double x );  // C++ only
```

### <a name="parameters"></a>Paramètres

*`x`*\
Angle en radians.

## <a name="return-value"></a>Valeur retournée

Les **`tanh`** fonctions retournent la tangente hyperbolique de *`x`* . Il n’y a pas d’erreur de retour.

|Entrée|Exception SEH|**`Matherr`** titre|
|-----------|-------------------|-------------------------|
|± `QNAN`,`IND`|aucun|`_DOMAIN`|

## <a name="remarks"></a>Remarques

C++ autorisant la surcharge, vous pouvez appeler des surcharges de **`tanh`** qui acceptent et retournent des **`float`** **`long double`** valeurs ou. Dans un programme C, à moins que vous n’utilisiez la `<tgmath.h>` macro pour appeler cette fonction, **`tanh`** prend et retourne toujours **`double`** .

Si vous utilisez la `<tgmath.h>` `tanh()` macro, le type de l’argument détermine la version de la fonction qui est sélectionnée. Pour plus d’informations [, consultez Math type-Generic](../../c-runtime-library/tgmath.md) .

Par défaut, l’état global de cette fonction est limité à l’application. Pour modifier cette valeur, consultez [état global dans le CRT](../global-state.md).

## <a name="requirements"></a>Configuration requise

|Routine|En-tête requis (C)|En-tête requis (C)|
|-------------|---------------------|-|
|**`tanh`**, **`tanhf`**, **`tanhl`**|`<math.h>`|`<cmath>` ou `<math.h>`|
|**`tanh()`** macrovirus | `<tgmath.h>` ||

Pour plus d’informations sur la compatibilité, consultez [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

```C
// crt_tanh.c
// This program displays the tangent of pi / 4
// and the hyperbolic tangent of the result.
// Compile by using: cl crt_tanh.c

#include <math.h>
#include <stdio.h>

int main( void )
{
   double pi = 3.1415926535;
   double x, y;

   x = tan( pi / 4 );
   y = tanh( x );
   printf( "tan( %f ) = %f\n", pi/4, x );
   printf( "tanh( %f ) = %f\n", x, y );
}
```

```Output
tan( 0.785398 ) = 1.000000
tanh( 1.000000 ) = 0.761594
```

## <a name="see-also"></a>Voir aussi

[Prise en charge de la virgule flottante](../../c-runtime-library/floating-point-support.md)\
[`acosh, acoshf, acoshl`](acosh-acoshf-acoshl.md)\
[`asinh, asinhf, asinhl`](asinh-asinhf-asinhl.md)\
[`atanh, atanhf, atanhl`](atanh-atanhf-atanhl.md)\
[`cosh, coshf, coshl`](cosh-coshf-coshl.md)\
[`sinh, sinhf, sinhl`](sinh-sinhf-sinhl.md)