---
title: floor, floorf, floorl
description: Informations de référence sur les API pour Floor, floorf, et Floor- qui calcule le plancher d’une valeur.
ms.date: 9/1/2020
api_name:
- floorf
- floorl
- floor
- _o_floor
- _o_floorf
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
- floor
- floorl
- _floorl
- floorf
helpviewer_keywords:
- floor function
- floorf function
- calculating floors of values
- floorl function
ms.assetid: e9955f70-d659-414f-8050-132e13c8ff36
ms.openlocfilehash: 6af047d3da891270ab6a596dfc3ebef0941a91cf
ms.sourcegitcommit: 4ed2d68634eb2fb77e18110a2d26bc0008be369c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89556734"
---
# <a name="floor-floorf-floorl"></a>floor, floorf, floorl

Calcule le plancher d’une valeur.

## <a name="syntax"></a>Syntaxe

```C
double floor(
   double x
);
float floor(
   float x
); // C++ only
long double floor(
   long double x
); // C++ only
float floorf(
   float x
);
long double floorl(
   long double x
);
#define floor(X) // Requires C11 or higher
```

### <a name="parameters"></a>Paramètres

*x*\
Valeur à virgule flottante.

## <a name="return-value"></a>Valeur renvoyée

Les fonctions **Floor** retournent une valeur à virgule flottante qui représente le plus grand entier inférieur ou égal à *x*. Il n’y a pas d’erreur de retour.

|Entrée|Exception SEH|Exception\{b\> \<b\}Matherr|
|-----------|-------------------|-----------------------|
|± QNAN,IND|aucun|_DOMAIN|

**Floor** a une implémentation qui utilise SSE2 (streaming SIMD Extensions 2). Pour plus d’informations sur l’utilisation de l’implémentation SSE2 et sur les restrictions qui s’y rattachent, consultez [_set_SSE2_enable](set-sse2-enable.md).

## <a name="remarks"></a>Notes

C++ autorisant la surcharge, vous pouvez appeler des surcharges de **plancher** qui acceptent et retournent des **`float`** **`long double`** valeurs et. Dans un programme C, à moins que vous n’utilisiez la \<tgmath.h> macro pour appeler cette fonction, **Floor** prend toujours et retourne un **`double`** .

Si vous utilisez la \<tgmath.h> `floor()` macro, le type de l’argument détermine la version de la fonction qui est sélectionnée. Pour plus d’informations [, consultez Math type-Generic](../../c-runtime-library/tgmath.md) .

Par défaut, l’état global de cette fonction est limité à l’application. Pour modifier cette valeur, consultez [état global dans le CRT](../global-state.md).

## <a name="requirements"></a>Spécifications

|Function|En-tête requis|
|--------------|---------------------|
|**plancher**, **floorf,**, **plancher**|\<math.h>|
|**Floor** (macro) | \<tgmath.h> ||

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

```C
// crt_floor.c
// This example displays the largest integers
// less than or equal to the floating-point values 2.8
// and -2.8. It then shows the smallest integers greater
// than or equal to 2.8 and -2.8.

#include <math.h>
#include <stdio.h>

int main( void )
{
   double y;

   y = floor( 2.8 );
   printf( "The floor of 2.8 is %f\n", y );
   y = floor( -2.8 );
   printf( "The floor of -2.8 is %f\n", y );

   y = ceil( 2.8 );
   printf( "The ceil of 2.8 is %f\n", y );
   y = ceil( -2.8 );
   printf( "The ceil of -2.8 is %f\n", y );
}
```

```Output
The floor of 2.8 is 2.000000
The floor of -2.8 is -3.000000
The ceil of 2.8 is 3.000000
The ceil of -2.8 is -2.000000
```

## <a name="see-also"></a>Voir aussi

[Prise en charge de la virgule flottante](../../c-runtime-library/floating-point-support.md)<br/>
[ceil, ceilf, ceill](ceil-ceilf-ceill.md)<br/>
[round, roundf, roundl](round-roundf-roundl.md)<br/>
[fmod, fmodf](fmod-fmodf.md)<br/>
