---
title: remainder, remainderf, remainderl
ms.date: 04/05/2018
api_name:
- remainderl
- remainder
- remainderf
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
- remainderf
- remainder
- remainderl
helpviewer_keywords:
- remainderf
- remainderl
- remainder
ms.assetid: 5f721fb3-8b78-4597-9bc0-ca9bcd1f1d0e
ms.openlocfilehash: 851f022325bb617cb2b0ae9a331b680b9d9fd303
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70949422"
---
# <a name="remainder-remainderf-remainderl"></a>remainder, remainderf, remainderl

Calcule le reste du quotient de deux valeurs à virgule flottante, arrondi à la valeur entière la plus proche.

## <a name="syntax"></a>Syntaxe

```C
double remainder( double x, double y );
float remainderf( float x, float y );
long double remainderl( long double x, long double y );
```

```cpp
float remainder( float x, float y ); /* C++ only */
long double remainder( long double x, long double y ); /* C++ only */
```

### <a name="parameters"></a>Paramètres

*x*<br/>
Numérateur.

*y*<br/>
Dénominateur.

## <a name="return-value"></a>Valeur de retour

Reste à virgule flottante de *x* / *y*. Si la valeur de *y* est 0,0, la fonction **Remainder** retourne une valeur NaN calme. Pour plus d’informations sur la représentation d’une NaN calme par la famille **printf** , consultez [printf, _printf_l, wprintf, _wprintf_l](printf-printf-l-wprintf-wprintf-l.md).

## <a name="remarks"></a>Notes

Les **fonctions restantes** calculent le reste à virgule flottante *r* de *x* / *y* , de telle sorte que *x* = *n* \* *y* + *r*, où *n* est l’entier le plus proche de la valeur de *x* / *y* et *n*est &#124; même chaque fois que *n* - *x* / *y* &#124; = 1/2. Lorsque *r* = 0, *r* a le même signe que *x*.

Étant C++ donné que autorise la surcharge, vous pouvez appeler des surcharges de **reste** qui acceptent et retournent des valeurs **float** ou **long** **double** . Dans un programme C, le **reste** prend toujours deux arguments **double** et retourne un **double**.

## <a name="requirements"></a>Configuration requise

|Fonction|En-tête requis (C)|En-tête requis (C++)|
|--------------|---------------------|-|
|**remainder**, **remainderf**, **remainderl**|\<math.h>|\<cmath> ou \<math.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

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

[Prise en charge de la virgule flottante](../../c-runtime-library/floating-point-support.md)<br/>
[ldiv, lldiv](ldiv-lldiv.md)<br/>
[imaxdiv](imaxdiv.md)<br/>
[fmod, fmodf](fmod-fmodf.md)<br/>
[remquo, remquof, remquol](remquo-remquof-remquol.md)<br/>
