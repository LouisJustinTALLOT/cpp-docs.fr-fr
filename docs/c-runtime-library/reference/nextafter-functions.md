---
title: nextafter, nextafterf, nextafterl, _nextafter, _nextafterf, nexttoward, nexttowardf, nexttowardl | Microsoft Docs
ms.custom: ''
ms.date: 04/05/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- nextafterf
- _nextafterf
- nextafter
- nextafterl
- _nextafter
- nexttoward
- nexttowardf
- nexttowardl
apilocation:
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
apitype: DLLExport
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
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9c68d039ff1318ea082d409078a55c8d337a48de
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32403714"
---
# <a name="nextafter-nextafterf-nextafterl-nextafter-nextafterf-nexttoward-nexttowardf-nexttowardl"></a>nextafter, nextafterf, nextafterl, _nextafter, _nextafterf, nexttoward, nexttowardf, nexttowardl

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

Retourne la valeur à virgule flottante représentable suivante d’après le type de retour *x* dans la direction de *y*. Si *x* et *y* sont égales, la fonction retourne *y*, convertie en type de retour, aucune exception déclenchée. Si *x* n’est pas égal à *y*, et le résultat est une dénormalisée ou égal à zéro, le **FE_UNDERFLOW** et **FE_INEXACT** les États d’exception à virgule flottante sont définies, et le résultat correct est retourné. Si le paramètre *x* ou *y* est une valeur NAN, la valeur de retour est un des valeurs NaN d’entrée. Si *x* reste limité et le résultat est l’infini ou n’est pas représentable dans le type, un correctement signé infini ou NAN est retourné, le **FE_OVERFLOW** et **FE_INEXACT** les États d’exception à virgule flottante sont définies, et **errno** a la valeur **ERANGE**.

## <a name="remarks"></a>Notes

Le **nextafter** et **nexttoward** familles de fonction sont équivalents, sauf le type de paramètre de *y*. Si *x* et *y* sont identiques, la valeur retournée est *y* converti au type de retour.

C++ autorisant la surcharge, si vous incluez \<cmath > vous pouvez appeler des surcharges de **nextafter** et **nexttoward** qui retournent **float** et **long** **double** types. Dans un programme C, **nextafter** et **nexttoward** retournent toujours **double**.

Le **_nextafter** et **_nextafterf** fonctions sont spécifiques de Microsoft. Le **_nextafterf** fonction est disponible uniquement lors de la compilation pour x64.

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis (C)|En-tête requis (C++)|
|-------------|---------------------------|-------------------------------|
|**nextafter**, **nextafterf**, **nextafterl**, **_nextafterf**, **nexttoward**, **nexttowardf** , **nexttowardl**|\<math.h>|\<math.h> ou \<cmath>|
|**_nextafter**|\<float.h>|\<float.h> ou \<cfloat>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[Prise en charge de la virgule flottante](../../c-runtime-library/floating-point-support.md)<br/>
[isnan, _isnan, _isnanf](isnan-isnan-isnanf.md)<br/>
