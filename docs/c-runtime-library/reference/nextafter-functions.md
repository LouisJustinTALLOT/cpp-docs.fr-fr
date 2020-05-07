---
title: nextafter, nextafterf, nextafterl, _nextafter, _nextafterf, nexttoward, nexttowardf, nexttowardl
ms.date: 4/2/2020
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
ms.assetid: 9785bfb9-de53-4bd0-9637-f05fa0c1f6ab
ms.openlocfilehash: b137fd131536da6b8630b9cadf69238ce48964bf
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2020
ms.locfileid: "82909339"
---
# <a name="nextafter-nextafterf-nextafterl-_nextafter-_nextafterf-nexttoward-nexttowardf-nexttowardl"></a>nextafter, nextafterf, nextafterl, _nextafter, _nextafterf, nexttoward, nexttowardf, nexttowardl

Retourne la valeur à virgule flottante représentable suivante.

## <a name="syntax"></a>Syntaxe

```C
double nextafter( double x, double y );
float nextafterf( float x, float y );
long double nextafterl( long double x, long double y );

double _nextafter( double x, double y );
float _nextafterf( float x, float y ); /* x64 only */

double nexttoward( double x, long double y );
float nexttowardf( float x, long double y );
long double nexttowardl( long double x, long double y );
```

```cpp
float nextafter( float x, float y ); /* C++ only, requires <cmath> */
long double nextafter( long double x, long double y ); /* C++ only, requires <cmath> */

float nexttoward( float x, long double y ); /* C++ only, requires <cmath> */
long double nexttoward( long double x, long double y ); /* C++ only, requires <cmath> */
```

### <a name="parameters"></a>Paramètres

*x*<br/>
Valeur à virgule flottante de départ.

*y*<br/>
Valeur à virgule flottante d’arrivée.

## <a name="return-value"></a>Valeur de retour

Retourne la valeur à virgule flottante représentable suivante du type de retour après *x* dans la direction de *y*. Si les valeurs *x* et *y* sont égales, la fonction retourne *y*, converti en type de retour, sans qu’aucune exception ne soit déclenchée. Si *x* n’est pas égal à *y*et que le résultat est une valeur dénormalisée ou zéro, les États d’exception de virgule flottante **FE_UNDERFLOW** et **FE_INEXACT** sont définis, et le résultat correct est retourné. Si *x* ou *y* est un Nan, la valeur de retour est l’une des valeurs NaN d’entrée. Si *x* est fini et que le résultat est infini ou n’est pas représentable dans le type, une valeur Infinite ou Nan correctement signée est retournée, les États d’exception de virgule flottante **FE_OVERFLOW** et **FE_INEXACT** sont définis, et **errno** a la valeur **ERANGE**.

## <a name="remarks"></a>Notes 

Les familles de fonctions **nextafter** et **nexttoward** sont équivalentes, à l’exception du type de paramètre de *y*. Si les valeurs *x* et *y* sont égales, la valeur retournée est *y* convertie dans le type de retour.

C++ autorisant la surcharge, si vous incluez \<cmath> vous pouvez appeler des surcharges de **nextafter** et **nexttoward** qui retournent des types **float** et **long** **double** . Dans un programme C, **nextafter** et **nexttoward** retournent toujours **double**.

Les fonctions **_nextafter** et **_nextafterf** sont spécifiques à Microsoft. La fonction **_nextafterf** n’est disponible que lors de la compilation pour x64.

Par défaut, l’état global de cette fonction est limité à l’application. Pour modifier cette valeur, consultez [état global dans le CRT](../global-state.md).

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis (C)|En-tête requis (C++)|
|-------------|---------------------------|-------------------------------|
|**nextafter**, **nextafterf**, **nextafterl**, **_nextafterf**, **nexttoward**, **nexttowardf**, **nexttowardl**|\<math.h>|\<math.h> ou \<cmath>|
|**_nextafter**|\<float.h>|\<float.h> ou \<cfloat>|

Pour plus d’informations sur la compatibilité, consultez [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[Prise en charge de la virgule flottante](../../c-runtime-library/floating-point-support.md)<br/>
[isnan, _isnan, _isnanf](isnan-isnan-isnanf.md)<br/>
