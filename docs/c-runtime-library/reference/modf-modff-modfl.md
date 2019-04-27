---
title: modf, modff, modfl
ms.date: 04/05/2018
apiname:
- modff
- modf
- modfl
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
ms.assetid: b1c7abf5-d476-43ca-a03c-02072a86e32d
ms.openlocfilehash: 59d6e2b9b02ad182c5630d6dc9a989c035e8fa92
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62156328"
---
# <a name="modf-modff-modfl"></a>modf, modff, modfl

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

*x*<br/>
Valeur à virgule flottante.

*intptr*<br/>
Pointeur désignant la partie entière stockée.

## <a name="return-value"></a>Valeur de retour

Cette fonction retourne la partie fractionnaire signée de *x*. Aucun retour d'erreur.

## <a name="remarks"></a>Notes

Le **modf** fonctions décomposent la valeur à virgule flottante *x* en une partie fractionnaire et une partie entière, chacune ayant le même signe que *x*. La partie fractionnaire signée de *x* est retourné. La partie entière est stockée en tant que valeur à virgule flottante à *intptr*.

**modf** a une implémentation qui utilise des Extensions Streaming SIMD 2 (SSE2). Consultez [_set_SSE2_enable](set-sse2-enable.md) pour plus d’informations sur l’utilisation de l’implémentation SSE2 et sur les restrictions qui s’y rattachent.

C++ autorisant la surcharge, vous pouvez appeler des surcharges de **modf** qui acceptent et retournent **float** ou **long** **double** paramètres. Dans un programme C, **modf** toujours prend deux valeurs doubles et retourne une valeur double.

## <a name="requirements"></a>Configuration requise

|Routine|En-tête requis|
|-------------|---------------------|
|**modf**, **modff**, **modfl**|C : \<math.h><br /><br /> C++ : \<cmath> ou \<math.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

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

[Prise en charge de la virgule flottante](../../c-runtime-library/floating-point-support.md)<br/>
[frexp](frexp.md)<br/>
[ldexp](ldexp.md)<br/>
