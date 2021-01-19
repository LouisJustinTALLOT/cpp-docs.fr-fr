---
title: nextafter, nextafterf, nextafterl, _nextafter, _nextafterf, nexttoward, nexttowardf, nexttowardl
description: Informations de référence sur les API pour nextafter, nextafterf, nextafterl, _nextafter, _nextafterf, nexttoward, nexttowardf et nexttowardl ; qui retournent la valeur à virgule flottante représentable suivante.
ms.date: 1/15/2021
api_name:
- nextafterf
- _nextafterf
- nextafter
- nextafterl
- _nextafter
- nexttoward
- nexttowardf
- nexttowardl
- _o__nextafter
- _o_nextafter
- _o_nextafterf
- _o_nextafterl
- _o_nexttoward
- _o_nexttowardf
- _o_nexttowardl
- _o__nextafterf
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
- nextafter
- _nextafter
- nextafterf
- nextafterl
- _nextafterf
- math/nextafter
- math/nextafterf
- math/nextafterl
- nexttoward
- nexttowardf
- nexttowardl
- math/nexttoward
- math/nexttowardf
- math/nexttowardl
helpviewer_keywords:
- _nextafter function
- nextafter function
- _nextafterf function
- nextafterf function
- nextafterl function
- nexttoward function
- nexttowardf function
- nexttowardl function
ms.openlocfilehash: 664ddb204fa089f83acebf6a9042b17a776ea306
ms.sourcegitcommit: 92dc6d99ba5dcf3b64dee164df2d29beb1e608da
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/18/2021
ms.locfileid: "98564132"
---
# <a name="nextafter-nextafterf-nextafterl-_nextafter-_nextafterf-nexttoward-nexttowardf-nexttowardl"></a>`nextafter`, `nextafterf`, `nextafterl`, `_nextafter`, `_nextafterf`, `nexttoward`, `nexttowardf`, `nexttowardl`

Retourne la valeur à virgule flottante représentable suivante.

## <a name="syntax"></a>Syntaxe

```C
double nextafter( double x, double y );
float nextafterf( float x, float y );
long double nextafterl( long double x, long double y );

double _nextafter( double x, double y );
float _nextafterf( float x, float y ); /* x64 only */

#define nextafter(X, Y) // Requires C11 or higher

double nexttoward( double x, long double y );
float nexttowardf( float x, long double y );
long double nexttowardl( long double x, long double y );

#define nexttoward(X, Y) // Requires C11 or higher

float nextafter( float x, float y ); /* C++ only, requires <cmath> */
long double nextafter( long double x, long double y ); /* C++ only, requires <cmath> */

float nexttoward( float x, long double y ); /* C++ only, requires <cmath> */
long double nexttoward( long double x, long double y ); /* C++ only, requires <cmath> */
```

### <a name="parameters"></a>Paramètres

*`x`*\
Valeur à virgule flottante de départ.

*`y`*\
Valeur à virgule flottante d’arrivée.

## <a name="return-value"></a>Valeur renvoyée

Retourne la valeur à virgule flottante représentable suivante du type de retour après *`x`* dans la direction de *`y`* . Si *`x`* et *`y`* sont égaux, la fonction retourne la valeur *`y`* , convertie dans le type de retour, sans qu’aucune exception ne soit déclenchée. Si *`x`* n’est pas égal à *`y`* et que le résultat est une valeur normale ou égale à zéro, les **`FE_UNDERFLOW`** États d’exception et de **`FE_INEXACT`** virgule flottante sont définis et le résultat correct est retourné. Si *`x`* ou *`y`* est un Nan, la valeur de retour est l’un des valeurs NaN d’entrée. Si *`x`* est fini et que le résultat est infini ou n’est pas représentable dans le type, une valeur infinie ou Nan correctement signée est retournée, **`FE_OVERFLOW`** et les **`FE_INEXACT`** États d’exception de virgule flottante sont définis, et **`errno`** prend la valeur **`ERANGE`** .

## <a name="remarks"></a>Remarques

Les **`nextafter`** **`nexttoward`** familles de fonctions et sont équivalentes, à l’exception du type de paramètre de *`y`* . Si *`x`* et *`y`* sont égaux, la valeur retournée est *`y`* convertie en type de retour.

C++ autorisant la surcharge, si vous incluez, `<cmath>` vous pouvez appeler des surcharges de **`nextafter`** et **`nexttoward`** qui retournent des **`float`** **`long double`** types et. Dans un programme C, à moins que vous n’utilisiez la `<tgmath.h>` macro pour appeler cette fonction, **`nextafter`** et **`nexttoward`** retournent toujours **`double`** .

Si vous utilisez la `<tgmath.h>` `nextafter()` `nexttoward()` macro ou, le type de l’argument détermine la version de la fonction qui est sélectionnée. Pour plus d’informations [, consultez Math type-Generic](../../c-runtime-library/tgmath.md) .

Les fonctions **_nextafter** et **_nextafterf** sont spécifiques à Microsoft. La fonction **_nextafterf** n’est disponible que lors de la compilation pour x64.

Par défaut, l’état global de cette fonction est limité à l’application. Pour modifier cette valeur, consultez [état global dans le CRT](../global-state.md).

## <a name="requirements"></a>Configuration requise

|Routine|En-tête requis (C)|En-tête requis (C++)|
|-------------|---------------------------|-------------------------------|
|**`nextafter`**, **`nextafterf`**, **`nextafterl`**, **`_nextafterf`**, **`nexttoward`**, **`nexttowardf`**, **`nexttowardl`**|`<math.h>`|`<math.h>` ou `<cmath>`|
|**`_nextafter`**|`<float.h>`|`<float.h>` ou `<cfloat>`|
|**`nextafter`** macro,  **`nexttoward`** macro| `<tgmath.h>` ||

Pour plus d’informations sur la compatibilité, consultez [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[Prise en charge de la virgule flottante](../../c-runtime-library/floating-point-support.md)\
[`isnan`, `_isnan`, `_isnanf`](isnan-isnan-isnanf.md)
