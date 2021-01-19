---
title: tan, tanf, tanl
description: Informations de référence sur les API pour Tan, Tanf, et tanl ; qui calcule la tangente d’une valeur à virgule flottante.
ms.date: 1/15/2021
api_name:
- tan
- tanf
- tanl
- _o_tan
- _o_tanf
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
ms.openlocfilehash: 056afdf0bbac422c498bd54c2a154472bfd97c34
ms.sourcegitcommit: 92dc6d99ba5dcf3b64dee164df2d29beb1e608da
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/18/2021
ms.locfileid: "98564054"
---
# <a name="tan-tanf-tanl"></a>`tan`, `tanf`, `tanl`

Calcule la tangente.

## <a name="syntax"></a>Syntaxe

```C
double tan( double x );
float tanf( float x );
long double tanl( long double x );
#define tan(x) // Requires C11 or higher
```

```cpp
float tan( float x );  // C++ only
long double tan( long double x );  // C++ only
```

### <a name="parameters"></a>Paramètres

*`x`*\
Angle en radians.

## <a name="return-value"></a>Valeur retournée

Les **`tan`** fonctions retournent la tangente de *`x`* . Si *`x`* est supérieur ou égal à 263, ou inférieur ou égal à-263, une perte de précision dans le résultat se produit.

|Entrée|Exception SEH|**`Matherr`** titre|
|-----------|-------------------|-------------------------|
|`± QNAN`,`IND`|aucun|`_DOMAIN`|
|`± INF`|**Non valide**|`_DOMAIN`|

## <a name="remarks"></a>Remarques

C++ autorisant la surcharge, vous pouvez appeler des surcharges de **`tan`** qui acceptent et retournent des **`float`** **`long double`** valeurs ou. Dans un programme C, à moins que vous n’utilisiez la `<tgmath.h>` macro pour appeler cette fonction, **`tan`** prend et retourne toujours **`double`** .

Si vous utilisez la `<tgmath.h>` `tan()` macro, le type de l’argument détermine la version de la fonction qui est sélectionnée. Pour plus d’informations [, consultez Math type-Generic](../../c-runtime-library/tgmath.md) .

Par défaut, l’état global de cette fonction est limité à l’application. Pour modifier cette valeur, consultez [état global dans le CRT](../global-state.md).

## <a name="requirements"></a>Configuration requise

|Routine|En-tête requis (C)|En-tête requis (C++)|
|-------------|---------------------|-|
|**`tan`**, **`tanf`**, **`tanl`**|`<math.h>`|`<cmath>` ou `<math.h>`|
|**`tan()`** macrovirus | `<tgmath.h>` ||

Pour plus d’informations sur la compatibilité, consultez [Compatibility](../../c-runtime-library/compatibility.md).

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

[Prise en charge de la virgule flottante](../../c-runtime-library/floating-point-support.md)\
[`acos, acosf, acosl`](acos-acosf-acosl.md)\
[`asin, asinf, asinl`](asin-asinf-asinl.md)\
[`atan, atanf, atanl, atan2, atan2f, atan2l`](atan-atanf-atanl-atan2-atan2f-atan2l.md)\
[`cos, cosf, cosl`](cos-cosf-cosl.md)\
[`sin, sinf, sinl`](sin-sinf-sinl.md)\
[`_CItan`](../../c-runtime-library/citan.md)