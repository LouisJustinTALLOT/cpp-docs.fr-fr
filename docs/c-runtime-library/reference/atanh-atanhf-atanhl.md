---
title: atanh, atanhf, atanhl
ms.date: 04/05/2018
api_name:
- atanhl
- atanhf
- atanh
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- atanhl
- atanhf
- atanh
helpviewer_keywords:
- atanhf function
- atanhl function
- atanh funciton
ms.assetid: 83a43b5b-2580-4461-854f-dc84236d9f32
ms.openlocfilehash: 539d015d5691f62f990faf650ab738f60066a2a6
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70939594"
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

Les fonctions **atanh** retournent la tangente hyperbolique inverse (arc tangente hyperbolique) de *x*. Si *x* est supérieur à 1, ou inférieur à-1, **errno** a la valeur **Edom** et le résultat est une valeur NaN silencieuse. Si *x* est égal à 1 ou-1, un infini positif ou négatif est retourné, respectivement, et **errno** a la valeur **ERANGE**.

|Entrée|Exception SEH|**Supertherr** Titre|
|-----------|-------------------|-------------------------|
|± QNAN,IND|none|none|
|*X* ≥ 1 ; *x* ≤-1|none|none|

## <a name="remarks"></a>Notes

Étant C++ donné que autorise la surcharge, vous pouvez appeler des surcharges de **atanh** qui acceptent et retournent des valeurs **float** ou **long** **double** . Dans un programme C, **atanh** prend toujours et retourne **double**.

## <a name="requirements"></a>Configuration requise

|Fonction|En-tête C|En-tête C++|
|--------------|--------------|------------------|
|**atanh**, **atanhf**, **atanhl**|\<math.h>|\<cmath> ou \<math.h>|

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
