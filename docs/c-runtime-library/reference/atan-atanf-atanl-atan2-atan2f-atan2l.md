---
title: atan, atanf, atanl, atan2, atan2f, atan2l
ms.date: 6/5/2020
api_name:
- atan2f
- atan2l
- atan2
- atanf
- atan
- atanl
- _o_atan
- _o_atan2
- _o_atan2f
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
- atan
- atan2l
- atan2
- atanl
- atanf
- atan2f
helpviewer_keywords:
- atan function
- atanf function
- atanl function
- atan2 function
- atan2l function
- arctangent function
- trigonometric functions
- atan2f function
ms.assetid: 7a87a18e-c94d-4727-9cb1-1bb5c2725ae4
ms.openlocfilehash: ad6bed621a0f1b5dd686909e4bf579e915662079
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87232610"
---
# <a name="atan-atanf-atanl-atan2-atan2f-atan2l"></a>atan, atanf, atanl, atan2, atan2f, atan2l

Calcule l’arc tangente de **x** (**atan**, **atanf,** et **atanl**) ou l’arc tangente de **y** / **x** (**atan2**, **atan2f,** et **atan2l**).

## <a name="syntax"></a>Syntaxe

```C
double atan( double x );
float atanf( float x );
long double atanl( long double x );

double atan2( double y, double x );
float atan2f( float y, float x );
long double atan2l( long double y, long double x );
```

```cpp
float atan( float x );  // C++ only
long double atan( long double x );  // C++ only

float atan2( float y, float x );  // C++ only
long double atan2( long double y, long double x );  // C++ only
```

### <a name="parameters"></a>Paramètres

*x*, *y*<br/>
N’importe quels nombres.

## <a name="return-value"></a>Valeur de retour

**atan** retourne l’arc tangente de *x* dans la plage-π/2 à π/2 radians. **atan2** retourne l’arc tangente de *y* / *x* dans la plage-π à π radians. Si *x* est égal à 0, **atan** retourne 0. Si les deux paramètres de **atan2** sont 0, la fonction retourne 0. Tous les résultats sont en radians.

**atan2** utilise les signes des deux paramètres pour déterminer le quadrant de la valeur de retour.

|Entrée|Exception SEH|Exception\{b\> \<b\}Matherr|
|-----------|-------------------|-----------------------|
|± **QNAN**, **IND**|aucun|**_DOMAIN**|

## <a name="remarks"></a>Notes

La fonction **atan** calcule l’arc tangente (fonction tangente inverse) de *x*. **atan2** calcule l’arc tangente de *y* / *x* (si *x* est égal à 0, **atan2** retourne π/2 Si *y* est positif,-π/2 Si *y* est négatif, ou 0 si *y* est égal à 0.)

**atan** a une implémentation qui utilise SSE2 (streaming SIMD Extensions 2). Pour plus d’informations sur l’utilisation de l’implémentation SSE2 et sur les restrictions qui s’y rattachent, consultez [_set_SSE2_enable](set-sse2-enable.md).

C++ autorisant la surcharge, vous pouvez appeler des surcharges de **atan** et **atan2** qui acceptent **`float`** des **`long double`** arguments ou. Dans un programme C, **atan** et **atan2** prennent toujours **`double`** des arguments et retournent un **`double`** .

Par défaut, l’état global de cette fonction est limité à l’application. Pour modifier cette valeur, consultez [état global dans le CRT](../global-state.md).

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis (C)|En-tête requis (C++)|
|-------------|---------------------|-|
|**atan**, **atan2**, **atanf,**, **atan2f,**, **atanl**, **atan2l**|\<math.h>|\<cmath> ou \<math.h>|

## <a name="example"></a>Exemple

```C
// crt_atan.c
// arguments: 5 0.5
#include <math.h>
#include <stdio.h>
#include <errno.h>

int main( int ac, char* av[] )
{
   double x, y, theta;
   if( ac != 3 ){
      fprintf( stderr, "Usage: %s <x> <y>\n", av[0] );
      return 1;
   }
   x = atof( av[1] );
   theta = atan( x );
   printf( "Arctangent of %f: %f\n", x, theta );
   y = atof( av[2] );
   theta = atan2( y, x );
   printf( "Arctangent of %f / %f: %f\n", y, x, theta );
   return 0;
}
```

```Output
Arctangent of 5.000000: 1.373401
Arctangent of 0.500000 / 5.000000: 0.099669
```

## <a name="see-also"></a>Voir aussi

[Prise en charge de la virgule flottante](../../c-runtime-library/floating-point-support.md)<br/>
[acos, acosf, acosl](acos-acosf-acosl.md)<br/>
[asin, asinf, asinl](asin-asinf-asinl.md)<br/>
[cos, cosf, cosl](cos-cosf-cosl.md)<br/>
[_matherr](matherr.md)<br/>
[sin, sinf, sinl](sin-sinf-sinl.md)<br/>
[tan, tanf, tanl](tan-tanf-tanl.md)<br/>
[_CIatan](../../c-runtime-library/ciatan.md)<br/>
[_CIatan2](../../c-runtime-library/ciatan2.md)<br/>
