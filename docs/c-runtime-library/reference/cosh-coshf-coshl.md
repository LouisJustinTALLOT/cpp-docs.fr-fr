---
title: cosh, coshf, coshl
description: Informations de référence sur l’API pour cosh, coshf, et COSL ; qui calcule le cosinus hyperbolique d’une valeur à virgule flottante.
ms.date: 1/15/2021
api_name:
- cosh
- coshf
- coshl
- _o_cosh
- _o_coshf
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
- cosh
- coshf
- coshl
helpviewer_keywords:
- cosh function
- coshf function
- coshl function
- trigonometric functions
- hyperbolic functions
ms.openlocfilehash: c010dcdc30b16f94f55fca99d67b58e5c19370c7
ms.sourcegitcommit: 92dc6d99ba5dcf3b64dee164df2d29beb1e608da
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/18/2021
ms.locfileid: "98564093"
---
# <a name="cosh-coshf-coshl"></a>`cosh`, `coshf`, `coshl`

Calcule le cosinus hyperbolique.

## <a name="syntax"></a>Syntaxe

```C
double cosh( double x );
float coshf( float x );
long double coshl( long double x );
#define cosh(X) // Requires C11 or higher

float cosh( float x );  // C++ only
long double cosh( long double x );  // C++ only
```

### <a name="parameters"></a>Paramètres

*`x`*\
Angle en radians.

## <a name="return-value"></a>Valeur renvoyée

Cosinus hyperbolique de *`x`* .

Par défaut, si le résultat est trop grand dans un **`cosh`** **`coshf`** appel, ou **`coshl`** , la fonction retourne **`HUGE_VAL`** et définit **`errno`** sur **`ERANGE`** .

|Entrée|Exception SEH|`Matherr` titre|
|-----------|-------------------|-----------------------|
|± **`QNAN`**, **`IND`**|aucun|**`_DOMAIN`**|
|*`x`* ≥ 7.104760 e + 002|**`INEXACT`**+**`OVERFLOW`**|**`OVERFLOW`**|

## <a name="remarks"></a>Remarques

C++ autorisant la surcharge, vous pouvez appeler des surcharges de **`cosh`** qui acceptent et retournent des **`float`** **`long double`** valeurs ou. Dans un programme C, à moins que vous n’utilisiez la `<tgmath.h>` macro pour appeler cette fonction, **`cosh`** accepte et retourne toujours un **`double`** .

Si vous utilisez la `<tgmath.h>` `cosh()` macro, le type de l’argument détermine la version de la fonction qui est sélectionnée. Pour plus d’informations [, consultez Math type-Generic](../../c-runtime-library/tgmath.md) .

Par défaut, l’état global de cette fonction est limité à l’application. Pour modifier cette valeur, consultez [état global dans le CRT](../global-state.md).

## <a name="requirements"></a>Configuration requise

|Routine|En-tête requis (C)|En-tête requis (C++)|
|-------------|---------------------|-|
|**`coshf`**, **`cosl`**, **`coshl`**|`<math.h>`|`<cmath>` ou `<math.h>`|
|**`coshf()`** macrovirus | `<tgmath.h>` ||

Pour plus d’informations sur la compatibilité, consultez [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

Consultez l’exemple dans [ `sinh` , `sinhf` , `sinhl` ](sinh-sinhf-sinhl.md).

## <a name="see-also"></a>Voir aussi

[Prise en charge de la virgule flottante](../../c-runtime-library/floating-point-support.md)\
[`acosh, acoshf, acoshl`](acosh-acoshf-acoshl.md)\
[`asinh, asinhf, asinhl`](asinh-asinhf-asinhl.md)\
[`atanh, atanhf, atanhl`](atanh-atanhf-atanhl.md)\
[`_matherr`](matherr.md)\
[`sinh, sinhf, sinhl`](sinh-sinhf-sinhl.md)\
[`tanh, tanhf, tanhl`](tanh-tanhf-tanhl.md)