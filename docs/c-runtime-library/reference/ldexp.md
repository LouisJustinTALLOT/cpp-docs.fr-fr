---
title: ldexp, ldexpf, ldexpl
description: Informations de référence sur les API pour ldexp, ldexpf, et ldexpl ; qui multiplie un nombre à virgule flottante par une puissance intégrale de deux.
ms.date: 9/1/2020
api_name:
- ldexp
- ldexpf
- ldexpl
- _ldexpl
- _o_ldexp
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
- ldexp
- ldexpf
- ldexpl
- _ldexpl
helpviewer_keywords:
- calculating real numbers
- computing real numbers
- mantissas, floating-point variables
- ldexp function
- ldexpf function
- ldexpl function
- exponent, floating-point numbers
- floating-point functions, mantissa and exponent
ms.assetid: aa7f5310-3879-4f63-ae74-86a39fbdedfa
ms.openlocfilehash: 6ce6bcbc8adbc62e8d8598b97a6f77e04fee1511
ms.sourcegitcommit: 4ed2d68634eb2fb77e18110a2d26bc0008be369c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89555447"
---
# <a name="ldexp-ldexpf-ldexpl"></a>ldexp, ldexpf, ldexpl

Multiplie un nombre à virgule flottante par une puissance intégrale de deux.

## <a name="syntax"></a>Syntaxe

```C
double ldexp(
   double x,
   int exp
);
float ldexpf(
   float x,
   int exp
);
long double ldexpl(
   long double x,
   int exp
);
#define ldexp(X, INT) // Requires C11 or higher

float ldexp(
   float x,
   int exp
);  // C++ only
long double ldexp(
   long double x,
   int exp
);  // C++ only
```

### <a name="parameters"></a>Paramètres

*x*\
Valeur à virgule flottante.

*venir*\
Exposant entier.

## <a name="return-value"></a>Valeur renvoyée

Les fonctions **ldexp** retournent la valeur de *x* \* 2<sup>*exp*</sup> en cas de réussite. En cas de dépassement de capacité et selon le signe de *x*, **ldexp** retourne +/- **HUGE_VAL**; la valeur **errno** est définie sur **ERANGE**.

Pour plus d’informations sur **errno** et les valeurs de retour possibles des erreurs, consultez [errno, _doserrno, _sys_errlist et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Notes

C++ autorisant la surcharge, vous pouvez appeler des surcharges de **ldexp** qui acceptent **`float`** des **`long double`** types ou. Dans un programme C, à moins que vous n’utilisiez la \<tgmath.h> macro pour appeler cette fonction, **ldexp** prend toujours un **`double`** et un **`int`** et retourne un **`double`** .

Si vous utilisez la \<tgmath.h> `ldexp()` macro, le type de l’argument détermine la version de la fonction qui est sélectionnée. Pour plus d’informations [, consultez Math type-Generic](../../c-runtime-library/tgmath.md) .

Par défaut, l’état global de cette fonction est limité à l’application. Pour modifier cette valeur, consultez [état global dans le CRT](../global-state.md).

## <a name="requirements"></a>Spécifications

|Routine|En-tête C|En-tête C++|
|-------------|--------------|------------------|
|**ldexp**, **ldexpf,**, **ldexpl**|\<math.h>|\<cmath>|
|**ldexp** macro) | \<tgmath.h> ||

Pour plus d’informations sur la compatibilité, consultez [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

```C
// crt_ldexp.c

#include <math.h>
#include <stdio.h>

int main( void )
{
   double x = 4.0, y;
   int p = 3;

   y = ldexp( x, p );
   printf( "%2.1f times two to the power of %d is %2.1f\n", x, p, y );
}
```

## <a name="output"></a>Output

```Output
4.0 times two to the power of 3 is 32.0
```

## <a name="see-also"></a>Voir aussi

[Prise en charge de la virgule flottante](../../c-runtime-library/floating-point-support.md)<br/>
[frexp](frexp.md)<br/>
[modf, modff, modfl](modf-modff-modfl.md)<br/>
