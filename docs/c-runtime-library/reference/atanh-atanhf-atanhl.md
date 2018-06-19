---
title: atanh, atanhf, atanhl | Microsoft Docs
ms.custom: ''
ms.date: 04/05/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- atanhl
- atanhf
- atanh
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
- atanhl
- atanhf
- atanh
dev_langs:
- C++
helpviewer_keywords:
- atanhf function
- atanhl function
- atanh funciton
ms.assetid: 83a43b5b-2580-4461-854f-dc84236d9f32
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 90a24945a7d630fac909e097728ea4df61ae2b40
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32393301"
---
# <a name="atanh-atanhf-atanhl"></a>atanh, atanhf, atanhl

Calcule la tangente hyperbolique inverse.

## <a name="syntax"></a>Syntaxe

```C
double atanh( double x );
float atanhf( float x );
long double atanhl( long double x );
```

```cpp
float atanh( float x );  // C++ only
long double atanh( long double x );  // C++ only
```

### <a name="parameters"></a>Paramètres

*x*<br/>
Valeur à virgule flottante.

## <a name="return-value"></a>Valeur de retour

Le **atanh** fonctions retournent la tangente hyperbolique inverse (arc la tangente hyperbolique) de *x*. Si *x* est supérieur à 1 ou inférieure à -1, **errno** a la valeur **EDOM** et le résultat est une valeur NaN silencieuse. Si *x* est égal à 1 ou -1, un infini positif ou négatif est retourné, respectivement, et **errno** a la valeur **ERANGE**.

|Entrée|Exception SEH|**Matherr** (Exception)|
|-----------|-------------------|-------------------------|
|± QNAN,IND|aucun|aucun|
|*X* ≥ 1 ; *x* ≤ -1|aucun|aucun|

## <a name="remarks"></a>Notes

C++ autorisant la surcharge, vous pouvez appeler des surcharges de **atanh** qui acceptent et retournent **float** ou **long** **double** valeurs. Dans un programme C, **atanh** accepte et retourne toujours **double**.

## <a name="requirements"></a>Spécifications

|Fonction|En-tête C|En-tête C++|
|--------------|--------------|------------------|
|**ATANH**, **atanhf**, **atanhl**|\<math.h>|\<cmath> ou \<math.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

```C
// crt_atanh.c
// This program displays the hyperbolic tangent of pi / 4
// and the arc hyperbolic tangent of the result.
//

#include <math.h>
#include <stdio.h>

int main( void )
{
   double pi = 3.1415926535;
   double x, y;

   x = tanh( pi / 4 );
   y = atanh( x );
   printf( "tanh( %f ) = %f\n", pi/4, x );
   printf( "atanh( %f ) = %f\n", x, y );
}
```

```Output
tanh( 0.785398 ) = 0.655794
atanh( 0.655794 ) = 0.785398
```

## <a name="see-also"></a>Voir aussi

[Prise en charge de la virgule flottante](../../c-runtime-library/floating-point-support.md)<br/>
[acosh, acoshf, acoshl](acosh-acoshf-acoshl.md)<br/>
[asinh, asinhf, asinhl](asinh-asinhf-asinhl.md)<br/>
[cos, cosf, cosl](cosh-coshf-coshl.md)<br/>
[sinh, sinhf, sinhl](sinh-sinhf-sinhl.md)<br/>
[tanh, tanhf, tanhl](tanh-tanhf-tanhl.md)<br/>
