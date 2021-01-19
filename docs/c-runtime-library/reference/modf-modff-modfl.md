---
title: modf, modff, modfl
description: Informations de référence sur les API pour modf,, modff, et modfl ; qui fractionnent une valeur à virgule flottante en une partie fractionnaire et une partie entière.
ms.date: 1/15/2021
api_name:
- modff
- modf
- modfl
- _o_modf
- _o_modff
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
- modff
- _modfl
- modf
- modfl
- math/modf
- math/modff
- math/modfl
helpviewer_keywords:
- modf function
- modff function
- modfl function
ms.openlocfilehash: fbc68c3369e8b992350534e3baa5f19b0f2a5e39
ms.sourcegitcommit: 92dc6d99ba5dcf3b64dee164df2d29beb1e608da
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/18/2021
ms.locfileid: "98564016"
---
# <a name="modf-modff-modfl"></a>`modf`, `modff`, `modfl`

Scinde une valeur à virgule flottante en une partie fractionnaire et une partie entière.

## <a name="syntax"></a>Syntaxe

```C
double modf( double x, double * intptr );
float modff( float x, float * intptr );
long double modfl( long double x, long double * intptr );
```

```cpp
float modf( float x, float * intptr );  // C++ only
long double modf( long double x, long double * intptr );  // C++ only
```

### <a name="parameters"></a>Paramètres

*`x`*\
Valeur à virgule flottante.

*`intptr`*\
Pointeur désignant la partie entière stockée.

## <a name="return-value"></a>Valeur renvoyée

Cette fonction retourne la partie fractionnaire signée de *`x`* . Il n’y a pas d’erreur de retour.

## <a name="remarks"></a>Remarques

Les fonctions **modf,** décomposent la valeur à virgule flottante *`x`* en parties fractionnaires et entières, chacune ayant le même signe que *`x`* . La partie fractionnaire signée de *`x`* est retournée. La partie entière est stockée sous la forme d’une valeur à virgule flottante à *`intptr`* .

**modf,** a une implémentation qui utilise SSE2 (streaming SIMD Extensions 2). [`_set_SSE2_enable`](set-sse2-enable.md)Pour obtenir des informations et des restrictions sur l’utilisation de l’implémentation SSE2, consultez.

C++ autorisant la surcharge, vous pouvez appeler des surcharges de **`modf`** qui acceptent et retournent des **`float`** **`long double`** paramètres ou. Dans un programme C, **`modf`** accepte toujours deux valeurs doubles et retourne une valeur double.

Par défaut, l’état global de cette fonction est limité à l’application. Pour modifier cette valeur, consultez [état global dans le CRT](../global-state.md).

## <a name="requirements"></a>Configuration requise

|Routine|En-tête requis|
|-------------|---------------------|
|**`modf`**, **`modff`**, **`modfl`**|Secteur `<math.h>`<br /><br /> C++ : `<cmath>` ou `<math.h>`|

Pour plus d’informations sur la compatibilité, consultez [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

```C
// crt_modf.c

#include <math.h>
#include <stdio.h>

int main( void )
{
   double x, y, n;

   x = -14.87654321;      /* Divide x into its fractional */
   y = modf( x, &n );     /* and integer parts            */

   printf( "For %f, the fraction is %f and the integer is %.f\n",
           x, y, n );
}
```

```Output
For -14.876543, the fraction is -0.876543 and the integer is -14
```

## <a name="see-also"></a>Voir aussi

[Prise en charge de la virgule flottante](../../c-runtime-library/floating-point-support.md)\
[`frexp`](frexp.md)\
[`ldexp`](ldexp.md)