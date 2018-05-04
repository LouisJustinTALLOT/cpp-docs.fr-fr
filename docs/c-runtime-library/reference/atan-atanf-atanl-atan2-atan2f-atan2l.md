---
title: atan, atanf, atanl, atan2, atan2f, atan2l | Microsoft Docs
ms.custom: ''
ms.date: 04/05/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- atan2f
- atan2l
- atan2
- atanf
- atan
- atanl
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
- atan
- atan2l
- atan2
- atanl
- atanf
- atan2f
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5e1f8b60c25c57e3e2eb6a9a964fd80664e3aa4c
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="atan-atanf-atanl-atan2-atan2f-atan2l"></a>atan, atanf, atanl, atan2, atan2f, atan2l

Calcule l’arc tangente de **x** (**atan**, **atanf**, et **atanl**) ou de l’arc tangente de **y** / **x** (**atan2**, **atan2f**, et **atan2l**).

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

**ATAN** renvoie l’arc tangente de *x* dans la plage - π/2 et π/2 radians. **ATAN2** renvoie l’arc tangente de *y*/*x* dans la plage - π en radians la mesure π. Si *x* est 0, **atan** retourne 0. Si les deux paramètres de **atan2** sont 0, la fonction retourne 0. Tous les résultats sont en radians.

**ATAN2** utilise les signes des deux paramètres afin de déterminer le secteur de la valeur de retour.

|Entrée|Exception SEH|Exception{b> <b}Matherr|
|-----------|-------------------|-----------------------|
|± **QNAN**, **IND**|aucun|**_DOMAIN**|

## <a name="remarks"></a>Notes

Le **atan** fonction calcule l’arc tangente (la fonction tangente inverse) de *x*. **ATAN2** calcule l’arc tangente de *y*/*x* (si *x* est égal à 0, **atan2** retourne π/2 si *y* est un nombre positif, - π/2 si *y* est négatif, ou 0 si *y* est 0.)

**ATAN** possède une implémentation qui utilise des Extensions Streaming SIMD 2 (SSE2). Pour obtenir des informations sur l’utilisation de l’implémentation SSE2 et sur les restrictions qui s’y rattachent, consultez [_set_SSE2_enable](set-sse2-enable.md).

C++ autorisant la surcharge, vous pouvez appeler des surcharges de **atan** et **atan2** acceptant **float** ou **long** **double**  arguments. Dans un programme C, **atan** et **atan2** sont toujours **double** argument et retourner un **double**.

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis (C)|En-tête requis (C++)|
|-------------|---------------------|-|
|**ATAN**, **atan2**, **atanf**, **atan2f**, **atanl**, **atan2l**|\<math.h>|\<cmath> ou \<math.h>|

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
