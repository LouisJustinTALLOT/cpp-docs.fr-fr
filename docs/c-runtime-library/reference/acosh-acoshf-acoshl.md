---
title: acosh, acoshf, acoshl
description: Informations de référence sur les API pour acosh, acoshf et acoshl ; qui calcule le cosinus hyperbolique inverse d’une valeur à virgule flottante.
ms.date: 08/31/2020
api_name:
- acoshf
- acosh
- acoshl
- _o_acosh
- _o_acoshf
- _o_acoshl
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
ms.openlocfilehash: ef6d47ca07f96be84962303c13162b154086e5f2
ms.sourcegitcommit: 4ed2d68634eb2fb77e18110a2d26bc0008be369c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89555109"
---
# <a name="acosh-acoshf-acoshl"></a>acosh, acoshf, acoshl

Calcule le cosinus hyperbolique inverse.

## <a name="syntax"></a>Syntaxe

```C
double acosh( double x );
float acoshf( float x );
long double acoshl( long double x );
#define acosh(X) // Requires C11 or higher

float acosh( float x );  // C++ only
long double acosh( long double x );  // C++ only
```

### <a name="parameters"></a>Paramètres

*x*\
Valeur à virgule flottante.

## <a name="return-value"></a>Valeur renvoyée

Les fonctions **acosh** retournent le cosinus hyperbolique inverse (arc cosinus hyperbolique) de *x*. Ces fonctions sont valides sur le domaine *x* ≥ 1. Si *x* est inférieur à 1, `errno` a la valeur `EDOM` et le résultat est une valeur NaN silencieuse. Si *x* est une valeur NaN, indéfinie ou infinie silencieuse, la même valeur est retournée.

|Entrée|Exception SEH|`_matherr`|
|-----------|-------------------|--------------------------|
|± QNAN, IND, INF|aucun|aucun|
|*x* < 1|aucun|aucun|

## <a name="remarks"></a>Notes

Quand vous utilisez C++, vous pouvez appeler des surcharges de **acosh** qui acceptent et retournent des **`float`** **`long double`** valeurs ou. Dans un programme C, à moins que vous n’utilisiez la \<tgmath.h> macro pour appeler cette fonction, **acosh** accepte et retourne toujours **`double`** .

Si vous utilisez la \<tgmath.h> `acosh()` macro, le type de l’argument détermine la version de la fonction qui est sélectionnée. Pour plus d’informations [, consultez Math type-Generic](../../c-runtime-library/tgmath.md) .

Par défaut, l’état global de cette fonction est limité à l’application. Pour modifier cette valeur, consultez [état global dans le CRT](../global-state.md).

## <a name="requirements"></a>Spécifications

|Function|En-tête C|En-tête C++|
|--------------|--------------|------------------|
|**acosh**, **acoshf**, **acoshl**|\<math.h>|\<cmath>|
|**ACOSH () (macro)** | \<tgmath.h> ||

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

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
[cosh, coshf, coshl](cosh-coshf-coshl.md)<br/>
[sinh, sinhf, sinhl](sinh-sinhf-sinhl.md)<br/>
[tanh, tanhf, tanhl](tanh-tanhf-tanhl.md)
