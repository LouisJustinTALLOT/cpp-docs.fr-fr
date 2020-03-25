---
title: acosh, acoshf, acoshl
ms.date: 04/05/2018
api_name:
- acoshf
- acosh
- acoshl
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
- acosh
- acoshf
- acoshl
- math/acosh
- math/acoshf
- math/acoshl
helpviewer_keywords:
- acoshf function
- acosh function
- acoshl function
ms.assetid: 6985c4d7-9e2a-44ce-9a9b-5a43015f15f7
ms.openlocfilehash: da1d6024cc9f00ebfc7696ddedf92ea9f25728a1
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80170356"
---
# <a name="acosh-acoshf-acoshl"></a>acosh, acoshf, acoshl

Calcule le cosinus hyperbolique inverse.

## <a name="syntax"></a>Syntaxe

```C
double acosh( double x );
float acoshf( float x );
long double acoshl( long double x );
```

```cpp
float acosh( float x );  // C++ only
long double acosh( long double x );  // C++ only
```

### <a name="parameters"></a>Paramètres

*x*<br/>
Valeur à virgule flottante.

## <a name="return-value"></a>Valeur de retour

Les fonctions **acosh** retournent le cosinus hyperbolique inverse (arc cosinus hyperbolique) de *x*. Ces fonctions sont valides sur le domaine *x* ≥ 1. Si *x* est inférieur à 1, `errno` a la valeur `EDOM` et le résultat est une valeur NaN silencieuse. Si *x* est une valeur NaN, indéfinie ou infinie silencieuse, la même valeur est retournée.

|Entrée|Exception SEH|Exception `_matherr`|
|-----------|-------------------|--------------------------|
|± QNAN, IND, INF|Aucun|Aucun|
|*x* < 1|Aucun|Aucun|

## <a name="remarks"></a>Notes

Lorsque vous utilisez C++, vous pouvez appeler des surcharges de **acosh** qui acceptent et retournent des valeurs **float** ou **long** **double** . Dans un programme C, **acosh** accepte et retourne toujours la valeur **double**.

## <a name="requirements"></a>Spécifications

|Fonction|En-tête C|En-tête C++|
|--------------|--------------|------------------|
|**acosh**, **acoshf**, **acoshl**|\<math.h>|\<cmath>|

Pour plus d’informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

```C
// crt_acosh.c
// Compile by using: cl /W4 crt_acosh.c
// This program displays the hyperbolic cosine of pi / 4
// and the arc hyperbolic cosine of the result.

#include <math.h>
#include <stdio.h>

int main( void )
{
   double pi = 3.1415926535;
   double x, y;

   x = cosh( pi / 4 );
   y = acosh( x );
   printf( "cosh( %f ) = %f\n", pi/4, x );
   printf( "acosh( %f ) = %f\n", x, y );
}
```

```Output
cosh( 0.785398 ) = 1.324609
acosh( 1.324609 ) = 0.785398
```

## <a name="see-also"></a>Voir aussi

[Prise en charge de la virgule flottante](../../c-runtime-library/floating-point-support.md)<br/>
[asinh, asinhf, asinhl](asinh-asinhf-asinhl.md)<br/>
[atanh, atanhf, atanhl](atanh-atanhf-atanhl.md)<br/>
[cos, cosf, cosl](cosh-coshf-coshl.md)<br/>
[sinh, sinhf, sinhl](sinh-sinhf-sinhl.md)<br/>
[tanh, tanhf, tanhl](tanh-tanhf-tanhl.md)
