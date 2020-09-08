---
title: remquo, remquof, remquol
description: Informations de référence sur les API pour remquo, remquof et remquol ; qui calcule le reste de deux valeurs entières et stocke une valeur entière avec le signe et l’amplitude approximative du quotient dans un emplacement spécifié dans un paramètre.
ms.date: 9/1/2020
api_name:
- remquof
- remquo
- remquol
- _o_remquo
- _o_remquof
- _o_remquol
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
- remquof
- remquol
- remquo
helpviewer_keywords:
- remquol function
- remquof function
- remquo function
ms.assetid: a1d3cb8b-8027-4cd3-8deb-04eb17f299fc
ms.openlocfilehash: d99204ad9a80c6320869cbb72aee905981a5224d
ms.sourcegitcommit: 4ed2d68634eb2fb77e18110a2d26bc0008be369c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89554966"
---
# <a name="remquo-remquof-remquol"></a>remquo, remquof, remquol

Calcule le reste de deux valeurs entières et stocke une valeur entière avec le signe et la grandeur approximative du quotient à un emplacement spécifié dans un paramètre.

## <a name="syntax"></a>Syntaxe

```C
double remquo( double numer, double denom, int* quo );
float remquof( float numer, float denom, int* quo );
long double remquol( long double numer, long double denom, int* quo );
#define remquo(X, Y, INT_PTR) // Requires C11 or higher

float remquo( float numer, float denom, int* quo ); /* C++ only */
long double remquo( long double numer, long double denom, int* quo ); /* C++ only */
```

### <a name="parameters"></a>Paramètres

*univoque*\
Numérateur.

*denom*\
Dénominateur.

*devenu*\
Pointeur désignant un entier pour stocker une valeur qui a le signe et la grandeur approximative du quotient.

## <a name="return-value"></a>Valeur renvoyée

**remquo** retourne le reste à virgule flottante de *x*  /  *y*. Si la valeur de *y* est 0,0, **remquo** retourne une valeur NaN calme. Pour plus d’informations sur la représentation d’une NaN calme par la famille **printf** , consultez [printf, _printf_l, wprintf, _wprintf_l](printf-printf-l-wprintf-wprintf-l.md).

## <a name="remarks"></a>Notes

La fonction **remquo** calcule le reste à virgule flottante *f* de *x*  /  *y* , de telle sorte que *x*  =  *i* \* *y*  +  *f*, où *i* est un entier, *f* a le même signe que *x*, et la valeur absolue de *f* est inférieure à la valeur absolue de *y*.

C++ autorisant la surcharge, vous pouvez appeler des surcharges de **remquo** qui acceptent et retournent des **`float`** **`long double`** valeurs ou. Dans un programme C, à moins que vous n’utilisiez la \<tgmath.h> macro pour appeler cette fonction, **remquo** accepte toujours deux **`double`** arguments et retourne un **`double`** .

Si vous utilisez la \<tgmath.h> `remquo()` macro, le type de l’argument détermine la version de la fonction qui est sélectionnée. Pour plus d’informations [, consultez Math type-Generic](../../c-runtime-library/tgmath.md) .

Par défaut, l’état global de cette fonction est limité à l’application. Pour modifier cette valeur, consultez [état global dans le CRT](../global-state.md).

## <a name="requirements"></a>Spécifications

|Function|En-tête requis (C)|En-tête requis (C++)|
|--------------|---------------------|-|
|**remquo**, **remquof**, **remquol**|\<math.h>|\<cmath> ou \<math.h>|
|**remquo** macro) | \<tgmath.h> ||

Pour plus d’informations sur la compatibilité, consultez [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

```C
// crt_remquo.c
// This program displays a floating-point remainder.

#include <math.h>
#include <stdio.h>

int main( void )
{
   double w = -10.0, x = 3.0, z;
   int quo = 0;

   z = remquo(w, x, &quo);
   printf("The remainder of %.2f / %.2f is %f\n", w, x, z);
   printf("Approximate signed quotient is %d\n", quo);
}
```

```Output
The remainder of -10.00 / 3.00 is -1.000000
Approximate signed quotient is -3
```

## <a name="see-also"></a>Voir aussi

[Prise en charge de la virgule flottante](../../c-runtime-library/floating-point-support.md)<br/>
[ldiv, lldiv](ldiv-lldiv.md)<br/>
[imaxdiv](imaxdiv.md)<br/>
[fmod, fmodf](fmod-fmodf.md)<br/>
[remainder, remainderf, remainderl](remainder-remainderf-remainderl.md)<br/>
