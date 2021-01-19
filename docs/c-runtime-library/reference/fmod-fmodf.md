---
title: fmod, fmodf, fmodl
description: Informations de référence sur les API pour fmod, fmodf, et fmodl ; qui calcule le reste à virgule flottante.
ms.date: 1/15/2021
api_name:
- fmod
- fmodf
- fmodl
- _o_fmod
- _o_fmodf
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
- fmod
- _fmodl
- fmodf
helpviewer_keywords:
- calculating floating-point remainders
- fmodf function
- fmodl function
- fmod function
- floating-point numbers, calculating remainders
ms.openlocfilehash: 8d2c3bcb0f871eb707f264478c4ce492bbb9c80c
ms.sourcegitcommit: 92dc6d99ba5dcf3b64dee164df2d29beb1e608da
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/18/2021
ms.locfileid: "98563936"
---
# <a name="fmod-fmodf-fmodl"></a>`fmod`, `fmodf`, `fmodl`

Calcule le reste à virgule flottante.

## <a name="syntax"></a>Syntaxe

```C
double fmod(
   double x,
   double y
);
float fmod(
   float x,
   float y
);  // C++ only
long double fmod(
   long double x,
   long double y
);  // C++ only
float fmodf(
   float x,
   float y
);
long double fmodl(
   long double x,
   long double y
);

#define fmod(X, Y) // Requires C11 or higher
```

### <a name="parameters"></a>Paramètres

*`x`*, *`y`*\
Valeurs à virgule flottante.

## <a name="return-value"></a>Valeur renvoyée

**`fmod`** retourne le reste à virgule flottante de *`x`*  /  *`y`* . Si la valeur de *`y`* est 0,0, **`fmod`** retourne une valeur NaN silencieuse. Pour plus d’informations sur la représentation d’une NaN faible par la **`printf`** famille, consultez [printf](printf-printf-l-wprintf-wprintf-l.md).

## <a name="remarks"></a>Remarques

La **`fmod`** fonction calcule le reste de la virgule  flottante de *`x`*  /  *`y`* telle que *`x`*  =  *i* \* *`y`*  +  *`f`* , où *`i`* est un entier, *`f`* a le même signe que *`x`* , et la valeur absolue de *`f`* est inférieure à la valeur absolue de *`y`* .

C++ autorisant la surcharge, vous pouvez appeler des surcharges de **`fmod`** qui acceptent et retournent des **`float`** **`long double`** valeurs et. Dans un programme C, à moins que vous n’utilisiez la `<tgmath.h>` macro pour appeler cette fonction, **`fmod`** accepte toujours deux **`double`** arguments et retourne un **`double`** .

Si vous utilisez la `<tgmath.h>` `fmod()` macro, le type de l’argument détermine la version de la fonction qui est sélectionnée. Pour plus d’informations [, consultez Math type-Generic](../../c-runtime-library/tgmath.md) .

Par défaut, l’état global de cette fonction est limité à l’application. Pour modifier cette valeur, consultez [état global dans le CRT](../global-state.md).

## <a name="requirements"></a>Configuration requise

|Fonction|En-tête requis|
|--------------|---------------------|
|**`fmod`**, **`fmodf`**, **`fmodl`**|`<math.h>`|
|**`fmod`** macrovirus | `<tgmath.h>` |

Pour plus d’informations sur la compatibilité, consultez [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

```C
// crt_fmod.c
// This program displays a floating-point remainder.

#include <math.h>
#include <stdio.h>

int main( void )
{
   double w = -10.0, x = 3.0, z;

   z = fmod( w, x );
   printf( "The remainder of %.2f / %.2f is %f\n", w, x, z );
}
```

```Output
The remainder of -10.00 / 3.00 is -1.000000
```

## <a name="see-also"></a>Voir aussi

[Prise en charge de la virgule flottante](../../c-runtime-library/floating-point-support.md)\
[`ceil, ceilf, ceill`](ceil-ceilf-ceill.md)\
[`fabs, fabsf, fabsl`](fabs-fabsf-fabsl.md)\
[FA`loor, floorf, floorl`](floor-floorf-floorl.md)\
[`_CIfmod`](../../c-runtime-library/cifmod.md)