---
title: fmod, fmodf, fmodl
ms.date: 4/2/2020
api_name:
- fmod
- fmodf
- fmodl
- _o_fmod
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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: 0cf25e2029f06c2e02a24ca84926e1a8b8f30159
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81346552"
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

**fmod** retourne le reste de point flottant de *x* / *y*. Si la valeur de *y* est de 0,0, **fmod** retourne un NaN tranquille. Pour plus d’informations sur la représentation d’un NaN tranquille par la famille **printf,** voir [printf](printf-printf-l-wprintf-wprintf-l.md).

## <a name="remarks"></a>Notes

La fonction **fmod** calcule le reste de point flottant *f* de *x* / *y* tel que *x* = *i* \* *y* + *f*, où *je* suis un intégré, *f* a le même signe que *x*, et la valeur absolue de *f* est inférieur à la valeur absolue de *y*.

CMD permet la surcharge, de sorte que vous pouvez appeler des surcharges de **fmod** qui prennent et retournent **flotteur** et **de longues** valeurs **doubles.** Dans un programme C, **fmod** prend toujours deux **doubles** arguments et retourne un **double**.

Par défaut, l’état global de cette fonction est étendue à l’application. Pour changer cela, voir [Global State dans le CRT](../global-state.md).

## <a name="requirements"></a>Spécifications

|Fonction|En-tête requis|
|--------------|---------------------|
|**fmod**, **fmodf**, **fmodl**|\<math.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

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

[Soutien à la pointe flottante](../../c-runtime-library/floating-point-support.md)<br/>
[ceil, ceilf, ceill](ceil-ceilf-ceill.md)<br/>
[fabs, fabsf, fabsl](fabs-fabsf-fabsl.md)<br/>
[floor, floorf, floorl](floor-floorf-floorl.md)<br/>
[_CIfmod](../../c-runtime-library/cifmod.md)<br/>
