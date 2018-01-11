---
title: atan, atanf, atanl, atan2, atan2f, atan2l | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
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
dev_langs: C++
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
caps.latest.revision: "21"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 36e90d781c4cc4512f4869247c296b69b19c1f9b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="atan-atanf-atanl-atan2-atan2f-atan2l"></a>atan, atanf, atanl, atan2, atan2f, atan2l
Calcule l’arc tangente de `x` (`atan`, `atanf` et `atanl`) ou l’arc tangente de `y`/`x` (`atan2`, `atan2f` et `atan2l`).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
double atan(   
   double x   
);  
float atan(  
   float x   
);  // C++ only  
long double atan(  
   long double x  
);  // C++ only  
double atan2(   
   double y,   
   double x   
);  
float atan2(  
   float y,  
   float x  
);  // C++ only  
long double atan2(  
   long double y,  
   long double x  
);  // C++ only  
float atanf(   
   float x   
);  
long double atanl(  
   long double x  
);  
float atan2f(  
   float y,  
   float x  
);  
long double atan2l(  
   long double y,  
   long double x  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `x`, `y`  
 N’importe quels nombres.  
  
## <a name="return-value"></a>Valeur de retour  
 `atan`Retourne l’arc tangente de `x` dans la plage - π/2 et π/2 radians. `atan2`Retourne l’arc tangente de `y/x` dans la plage - π en radians la mesure π. Si `x` est 0, `atan` retourne la valeur 0. Si les deux paramètres de `atan2` sont 0, la fonction retourne 0. Tous les résultats sont en radians.  
  
 `atan2` utilise les signes des deux paramètres pour déterminer le quadrant de la valeur de retour.  
  
|Entrée|Exception SEH|Exception Matherr|  
|-----------|-------------------|-----------------------|  
|± `QNAN`,`IND`|aucun|`_DOMAIN`|  
  
## <a name="remarks"></a>Notes  
 La fonction `atan` calcule l’arc tangente (fonction tangente inverse) de `x`. `atan2`calcule l’arc tangente de `y` / `x` (si `x` est égal à 0, `atan2` retourne π/2 si `y` est un nombre positif, - π/2 si `y` est négatif, ou 0 si `y` est 0.)  
  
 `atan` présente une implémentation qui utilise SSE2 (Streaming SIMD Extensions 2). Pour plus d’informations sur l’utilisation de l’implémentation SSE2 et sur les restrictions qui s’y rattachent, consultez [_set_SSE2_enable](../../c-runtime-library/reference/set-sse2-enable.md).  
  
 C++ autorisant la surcharge, vous pouvez appeler des surcharges de `atan` et `atan2`. Dans un programme C, `atan` et `atan2` acceptent et retournent toujours des doubles.  
  
## <a name="requirements"></a>Configuration requise  
  
|Routine|En-tête requis|  
|-------------|---------------------|  
|`atan`, `atan2`, `atanf`, `atan2f`, `atanl`, `atan2l`|\<math.h>|  
  
## <a name="example"></a>Exemple  
  
```  
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
 [Prise en charge de la virgule flottante](../../c-runtime-library/floating-point-support.md)   
 [acos, acosf, acosl](../../c-runtime-library/reference/acos-acosf-acosl.md)   
 [asin, asinf, asinl](../../c-runtime-library/reference/asin-asinf-asinl.md)   
 [cos, cosf, cosl, cosh, coshf, coshl](../../c-runtime-library/reference/cos-cosf-cosl-cosh-coshf-coshl.md)   
 [_matherr](../../c-runtime-library/reference/matherr.md)   
 [sin, sinf, sinl, sinh, sinhf, sinhl](../../c-runtime-library/reference/sin-sinf-sinl-sinh-sinhf-sinhl.md)   
 [tan, tanf, tanl, tanh, tanhf, tanhl](../../c-runtime-library/reference/tan-tanf-tanl-tanh-tanhf-tanhl.md)   
 [_CIatan](../../c-runtime-library/ciatan.md)   
 [_CIatan2](../../c-runtime-library/ciatan2.md)