---
title: fmod, fmodf, fmodl
ms.date: 04/05/2018
api_name:
- fmod
- fmodf
- fmodl
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
- fmod
- _fmodl
- fmodf
helpviewer_keywords:
- calculating floating-point remainders
- fmodf function
- fmodl function
- fmod function
- floating-point numbers, calculating remainders
ms.assetid: 6962d369-d11f-40b1-a6d7-6f67239f8a23
ms.openlocfilehash: e98432a73df8b872593d4cd610139bdfa72a25c4
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70957081"
---
# <a name="fmod-fmodf-fmodl"></a>fmod, fmodf, fmodl

Calcule le reste à virgule flottante.

## <a name="syntax"></a>Syntaxe

```C
double fmod(
   double x,
   double y
);
float fmod(
   float x,
   float y
);  // C++ only
long double fmod(
   long double x,
   long double y
);  // C++ only
float fmodf(
   float x,
   float y
);
long double fmodl(
   long double x,
   long double y
);
```

### <a name="parameters"></a>Paramètres

*x*, *y*<br/>
Valeurs à virgule flottante.

## <a name="return-value"></a>Valeur de retour

**fmod** retourne le reste à virgule flottante de *x* / *y*. Si la valeur de *y* est 0,0, **fmod** retourne une valeur NaN calme. Pour plus d’informations sur la représentation d’une NaN calme par la famille **printf** , consultez [printf](printf-printf-l-wprintf-wprintf-l.md).

## <a name="remarks"></a>Notes

La fonction **fmod** calcule le reste à virgule flottante *f* de *x* / *y* , de telle sorte que *x* = *i* \* *y* + *f*, où *i* est un entier, *f* a le même signe que *x*et la valeur absolue de *f* est inférieure à la valeur absolue de *y*.

C++autorise la surcharge, de sorte que vous pouvez appeler des surcharges de **fmod** qui acceptent et retournent des valeurs **float** et **long** **double** . Dans un programme C, **fmod** prend toujours deux arguments **double** et retourne un **double**.

## <a name="requirements"></a>Configuration requise

|Fonction|En-tête requis|
|--------------|---------------------|
|**fmod**, **fmodf**, **fmodl**|\<math.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemples

```C
// crt_fmod.c
// This program displays a floating-point remainder.

#include <math.h>
#include <stdio.h>

int main( void )
{
   double w = -10.0, x = 3.0, z;

   z = fmod( w, x );
   printf( "The remainder of %.2f / %.2f is %f\n", w, x, z );
}
```

```Output
The remainder of -10.00 / 3.00 is -1.000000
```

## <a name="see-also"></a>Voir aussi

[Prise en charge de la virgule flottante](../../c-runtime-library/floating-point-support.md)<br/>
[ceil, ceilf, ceill](ceil-ceilf-ceill.md)<br/>
[fabs, fabsf, fabsl](fabs-fabsf-fabsl.md)<br/>
[floor, floorf, floorl](floor-floorf-floorl.md)<br/>
[_CIfmod](../../c-runtime-library/cifmod.md)<br/>
