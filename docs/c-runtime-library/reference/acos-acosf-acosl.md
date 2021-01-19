---
title: acos, acosf, acosl
description: Informations de référence sur l’API pour ACOS, acosf et acosl ; qui calcule l’arc cosinus d’une valeur à virgule flottante.
ms.date: 1/15/2021
api_name:
- acosf
- acos
- acosl
- _o_acos
- _o_acosf
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
- acos
- acosl
- acosf
- math/acosf
- math/acosl
helpviewer_keywords:
- acos function
- acosl function
- acosf function
- trigonometric functions
- arccosine function
ms.openlocfilehash: 63a9c9577e252c506191b7a49ec9da6502968095
ms.sourcegitcommit: 92dc6d99ba5dcf3b64dee164df2d29beb1e608da
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/18/2021
ms.locfileid: "98563833"
---
# <a name="acos-acosf-acosl"></a>`acos`, `acosf`, `acosl`

Calcule l’arc cosinus.

## <a name="syntax"></a>Syntaxe

```C
double acos( double x );
float acosf( float x );
long double acosl( long double x );
#define acos(X) // Requires C11 or higher

float acos( float x );   // C++ only
long double acos( long double x );   // C++ only
```

### <a name="parameters"></a>Paramètres

*`x`*\
Valeur comprise entre-1 et 1, pour laquelle calculer l’arccosinus (cosinus inverse).

## <a name="return-value"></a>Valeur renvoyée

La **`acos`** fonction retourne l’arc cosinus de *x* dans la plage comprise entre 0 et π radians.

Par défaut, si *`x`* est inférieur à-1 ou supérieur à 1, **`acos`** retourne un indéfini.

|Entrée|`SEH` titre|`Matherr` titre|
|-----------|-------------------|-----------------------|
|`± ∞`|`INVALID`|`_DOMAIN`|
|`± QNAN, IND`|aucun|`_DOMAIN`|
|&#124;`x`&#124;>1|`INVALID`|`_DOMAIN`|

## <a name="remarks"></a>Remarques

C++ autorisant la surcharge, vous pouvez appeler des surcharges de **`acos`** qui acceptent et retournent des **`float`** **`long double`** types et. Dans un programme C, à moins que vous n’utilisiez la `<tgmath.h>` macro pour appeler cette fonction, **`acos`** accepte et retourne toujours un **`double`** .

Si vous utilisez la `<tgmath.h>` `acos()` macro, le type de l’argument détermine la version de la fonction qui est sélectionnée. Pour plus d’informations [, consultez Math type-Generic](../../c-runtime-library/tgmath.md) .

Par défaut, l’état global de cette fonction est limité à l’application. Pour modifier cette valeur, consultez [état global dans le CRT](../global-state.md).

## <a name="requirements"></a>Configuration requise

|Routine|En-tête requis|En-têtes facultatifs|
|-------------|---------------------|----------------------|
|**`acos`**, **`acosf`**, **`acosl`**|`<math.h>`|`<errno.h>`|
|**`acos()`** macrovirus | `<tgmath.h>` ||

## <a name="example"></a>Exemple

Ce programme vous invite à entrer une valeur comprise entre -1 et 1. Les valeurs d’entrée en dehors de cette plage génèrent des messages d’erreur `_DOMAIN`. Si une valeur valide est entrée, le programme affiche l’arc sinus et l’arc cosinus de cette valeur.

```C
// crt_asincos.c
// arguments: 0

#include <math.h>
#include <stdio.h>
#include <stdlib.h>
#include <errno.h>

int main( int ac, char* av[] )
{
    double  x,
            y;
    errno_t err;

    // argument checking
    if (ac != 2)
    {
        fprintf_s( stderr, "Usage: %s <number between -1 and 1>\n",
                   av[0]);
        return 1;
    }

    // Convert argument into a double value
    if ((err = sscanf_s( av[1], "%lf", &x )) != 1)
    {
        fprintf_s( stderr, "Error converting argument into ",
                   "double value.\n");
        return 1;
    }

    // Arcsine of X
    y = asin( x );
    printf_s( "Arcsine of %f = %f\n", x, y );

    // Arccosine of X
    y = acos( x );
    printf_s( "Arccosine of %f = %f\n", x, y );
}
```

```Output
Arcsine of 0.000000 = 0.000000
Arccosine of 0.000000 = 1.570796
```

## <a name="see-also"></a>Voir aussi

[Prise en charge de la virgule flottante](../../c-runtime-library/floating-point-support.md)\
[`asin`, `asinf`, `asinl`](asin-asinf-asinl.md)\
[`atan`, `atanf`, `atanl`, `atan2`, `atan2f`, `atan2l`](atan-atanf-atanl-atan2-atan2f-atan2l.md)\
[`cos`, `cosf`, `cosl`](cos-cosf-cosl.md)\
[`_matherr`](matherr.md)\
[`sin`, `sinf`, `sinl`](sin-sinf-sinl.md)\
[`tan`, `tanf`, `tanl`](tan-tanf-tanl.md)