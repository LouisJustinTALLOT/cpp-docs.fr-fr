---
title: tan, tanf, tanl
ms.date: 04/10/2018
api_name:
- tan
- tanf
- tanl
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
- tan
- tanf
- _tanl
- tanl
helpviewer_keywords:
- tanl function
- _tanl function
- tan function
- calculating tangents
- tangent
- tanf function
- trigonometric functions
ms.assetid: 36cc0ce8-9c80-4653-b354-ddb3b378b6bd
ms.openlocfilehash: c79c56555e04c865b70d52a6b1a6e3da1ce94c87
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70946898"
---
# <a name="tan-tanf-tanl"></a>tan, tanf, tanl

Calcule la tangente.

## <a name="syntax"></a>Syntaxe

```C
double tan( double x );
float tanf( float x );
long double tanl( long double x );
```

```cpp
float tan( float x );  // C++ only
long double tan( long double x );  // C++ only
```

### <a name="parameters"></a>Paramètres

*x*<br/>
Angle en radians.

## <a name="return-value"></a>Valeur de retour

Les fonctions **Tan** retournent la tangente de *x*. Si *x* est supérieur ou égal à 263, ou inférieur ou égal à-263, une perte de précision dans le résultat se produit.

|Entrée|Exception SEH|**Supertherr** Titre|
|-----------|-------------------|-------------------------|
|± QNAN,IND|none|_DOMAIN|
|FICHIER INF ±|**NON VALIDE**|_DOMAIN|

## <a name="remarks"></a>Notes

Étant C++ donné que autorise la surcharge, vous pouvez appeler des surcharges de **Tan** qui acceptent et retournent des valeurs **float** ou **long** **double** . Dans un programme C, **Tan** prend toujours et retourne **double**.

## <a name="requirements"></a>Configuration requise

|Routine|En-tête requis (C)|En-tête requis (C++)|
|-------------|---------------------|-|
|**tan**, **tanf**, **tanl**|\<math.h>|\<cmath> ou \<math.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

```C
// crt_tan.c
// This program displays the tangent of pi / 4
// Compile by using: cl crt_tan.c

#include <math.h>
#include <stdio.h>

int main( void )
{
   double pi = 3.1415926535;
   double x;

   x = tan( pi / 4 );
   printf( "tan( %f ) = %f\n", pi/4, x );
}
```

```Output
tan( 0.785398 ) = 1.000000
```

## <a name="see-also"></a>Voir aussi

[Prise en charge de la virgule flottante](../../c-runtime-library/floating-point-support.md)<br/>
[acos, acosf, acosl](acos-acosf-acosl.md)<br/>
[asin, asinf, asinl](asin-asinf-asinl.md)<br/>
[atan, atanf, atanl, atan2, atan2f, atan2l](atan-atanf-atanl-atan2-atan2f-atan2l.md)<br/>
[cos, cosf, cosl](cos-cosf-cosl.md)<br/>
[sin, sinf, sinl](sin-sinf-sinl.md)<br/>
[_CItan](../../c-runtime-library/citan.md)<br/>