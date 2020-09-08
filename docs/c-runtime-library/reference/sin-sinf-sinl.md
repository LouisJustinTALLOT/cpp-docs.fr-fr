---
title: sin, sinf, sinl
description: Informations de référence sur les API pour Sin, sinf et sinl ; qui calcule le sinus d’une valeur à virgule flottante.
ms.date: 08/31/2020
api_name:
- sinl
- sinf
- sin
- _o_sin
- _o_sinf
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
- _sinl
- sinf
- sinl
- sin
helpviewer_keywords:
- _sinl function
- sinl function
- calculating sines
- sin function
- trigonometric functions
- sinf function
ms.assetid: 737de73e-3590-45f9-8257-dc1c0c489dfc
ms.openlocfilehash: 7d1921dd4537c9dcc955c264a36992d86defada8
ms.sourcegitcommit: 4ed2d68634eb2fb77e18110a2d26bc0008be369c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89556189"
---
# <a name="sin-sinf-sinl"></a>sin, sinf, sinl

Calcule le sinus d’une valeur à virgule flottante.

## <a name="syntax"></a>Syntaxe

```C
double sin(double x);
float sinf(float x);
long double sinl(long double x);
#define sin(x) // Requires C11 or higher
```

```cpp
float sin(float x);  // C++ only
long double sin(long double x);  // C++ only
```

### <a name="parameters"></a>Paramètres

*x*\
Angle en radians.

## <a name="return-value"></a>Valeur renvoyée

Les fonctions **Sin** retournent le sinus de *x*. Si *x* est supérieur ou égal à 263, ou inférieur ou égal à-263, une perte de précision dans le résultat se produit.

|Entrée|Exception SEH|Exception\{b\> \<b\}Matherr|
|-----------|-------------------|-----------------------|
|± QNAN,IND|Aucun|_DOMAIN|
|± ∞ (Sin, sinf, sinl)|NON VALIDE|_DOMAIN|

Pour plus d’informations sur les codes de retour, consultez [errno, _doserrno, _sys_errlist et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Notes

C++ autorisant la surcharge, vous pouvez appeler des surcharges de **Sin** qui acceptent et retournent des **`float`** **`long double`** valeurs ou. Dans un programme C, à moins que vous n’utilisiez la \<tgmath.h> macro pour appeler cette fonction, **Sin** prend et retourne toujours **`double`** .

Si vous utilisez la \<tgmath.h> `sin()` macro, le type de l’argument détermine la version de la fonction qui est sélectionnée. Pour plus d’informations [, consultez Math type-Generic](../../c-runtime-library/tgmath.md) .

Par défaut, l’état global de cette fonction est limité à l’application. Pour modifier cette valeur, consultez [état global dans le CRT](../global-state.md).

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis (C)|En-tête requis (C++)|
|-|-|-|
|**Sin**, **sinf**, **sinl**|\<math.h>|\<cmath> ou \<math.h>|
|**Sin () (macro)** | \<tgmath.h> ||

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

```C
// crt_sincos.c
// This program displays the sine and cosine of pi / 2.
// Compile by using: cl /W4 crt_sincos.c

#include <math.h>
#include <stdio.h>

int main( void)
{
   double pi = 3.1415926535;
   double x, y;

   x = pi / 2;
   y = sin( x );
   printf( "sin( %f ) = %f\n", x, y );
   y = cos( x );
   printf( "cos( %f ) = %f\n", x, y );
}
```

```Output
sin( 1.570796 ) = 1.000000
cos( 1.570796 ) = 0.000000
```

## <a name="see-also"></a>Voir aussi

[Prise en charge de la virgule flottante](../../c-runtime-library/floating-point-support.md)<br/>
[acos, acosf, acosl](acos-acosf-acosl.md)<br/>
[asin, asinf, asinl](asin-asinf-asinl.md)<br/>
[atan, atanf, atanl, atan2, atan2f, atan2l](atan-atanf-atanl-atan2-atan2f-atan2l.md)<br/>
[cos, cosf, cosl](cos-cosf-cosl.md)<br/>
[tan, tanf, tanl](tan-tanf-tanl.md)<br/>
[_CIsin](../../c-runtime-library/cisin.md)<br/>
