---
title: remainder, remainderf, remainderl
description: Informations de référence sur l’API pour le reste, remainderf et le reste ; qui calcule le reste du quotient de deux valeurs à virgule flottante, arrondi à la valeur intégrale la plus proche.
ms.date: 9/1/2020
api_name:
- remainderl
- remainder
- remainderf
- _o_remainder
- _o_remainderf
- _o_remainderl
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
- remainderf
- remainder
- remainderl
helpviewer_keywords:
- remainderf
- remainderl
- remainder
ms.assetid: 5f721fb3-8b78-4597-9bc0-ca9bcd1f1d0e
ms.openlocfilehash: ef2b326bef2288b52dba8988749e030ff0b46077
ms.sourcegitcommit: 4ed2d68634eb2fb77e18110a2d26bc0008be369c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89556007"
---
# <a name="remainder-remainderf-remainderl"></a>remainder, remainderf, remainderl

Calcule le reste du quotient de deux valeurs à virgule flottante, arrondi à la valeur entière la plus proche.

## <a name="syntax"></a>Syntaxe

```C
double remainder( double x, double y );
float remainderf( float x, float y );
long double remainderl( long double x, long double y );
#define remainder(X, Y) // Requires C11 or higher

float remainder( float x, float y ); /* C++ only */
long double remainder( long double x, long double y ); /* C++ only */
```

### <a name="parameters"></a>Paramètres

*x*\
Numérateur.

*y*\
Dénominateur.

## <a name="return-value"></a>Valeur renvoyée

Reste à virgule flottante de *x*  /  *y*. Si la valeur de *y* est 0,0, la fonction **Remainder** retourne une valeur NaN calme. Pour plus d’informations sur la représentation d’une NaN calme par la famille **printf** , consultez [printf, _printf_l, wprintf, _wprintf_l](printf-printf-l-wprintf-wprintf-l.md).

## <a name="remarks"></a>Notes

Les fonctions **restantes** calculent le reste à virgule flottante *r* de *x*  /  *y* , de telle sorte que *x*  =  *n* \* *o*  +  *r*, où *n*est l’entier le plus proche dans la valeur de *x*  /  *y* et *n*, même chaque fois que &#124; *n*  -  *x*  /  *y* &#124; = 1/2. Lorsque *r* = 0, *r* a le même signe que *x*.

C++ autorisant la surcharge, vous pouvez appeler des surcharges de **reste** qui acceptent et retournent des **`float`** **`long double`** valeurs ou. Dans un programme C, à moins que vous n’utilisiez la \<tgmath.h> macro pour appeler cette fonction, le **reste** prend toujours deux **`double`** arguments et retourne un **`double`** .

Si vous utilisez la \<tgmath.h> `remainder()` macro, le type de l’argument détermine la version de la fonction qui est sélectionnée. Pour plus d’informations [, consultez Math type-Generic](../../c-runtime-library/tgmath.md) .

Par défaut, l’état global de cette fonction est limité à l’application. Pour modifier cette valeur, consultez [état global dans le CRT](../global-state.md).

## <a name="requirements"></a>Spécifications

|Function|En-tête requis (C)|En-tête requis (C++)|
|--------------|---------------------|-|
|**reste**, **remainderf**, **restante**|\<math.h>|\<cmath> ou \<math.h>|
|**reste** , macro | \<tgmath.h> ||

Pour plus d’informations sur la compatibilité, consultez [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

```C
// crt_remainder.c
// This program displays a floating-point remainder.

#include <math.h>
#include <stdio.h>

int main( void )
{
   double w = -10.0, x = 3.0, z;

   z = remainder(w, x);
   printf("The remainder of %.2f / %.2f is %f\n", w, x, z);
}
```

```Output
The remainder of -10.00 / 3.00 is -1.000000
```

## <a name="see-also"></a>Voir aussi

[Prise en charge de la virgule flottante](../../c-runtime-library/floating-point-support.md)\
[ldiv, lldiv](ldiv-lldiv.md)\
[imaxdiv](imaxdiv.md)\
[fmod, fmodf,](fmod-fmodf.md)\
[remquo, remquof, remquol](remquo-remquof-remquol.md)
