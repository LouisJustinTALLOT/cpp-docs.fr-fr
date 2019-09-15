---
title: frexp, frexpf, frexpl
ms.date: 04/05/2018
api_name:
- frexp
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
- frexp
- _frexpl
helpviewer_keywords:
- _frexpl function
- mantissas, floating-point variables
- frexpl function
- exponent, floating-point numbers
- frexp function
- floating-point functions, mantissa and exponent
ms.assetid: 9b020f2e-3967-45ec-a6a8-d467a071aa55
ms.openlocfilehash: 3a67ced9bd6653a7c40c98a8cf015663c37457bb
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70956635"
---
# <a name="frexp-frexpf-frexpl"></a>frexp, frexpf, frexpl

Obtient la mantisse et l’exposant d’un nombre à virgule flottante.

## <a name="syntax"></a>Syntaxe

```C
double frexp(
   double x,
   int *expptr
);
float frexpf(
   float x,
   int * expptr
);
long double frexpl(
   long double x,
   int * expptr
);
float frexp(
   float x,
   int * expptr
);  // C++ only
long double frexp(
   long double x,
   int * expptr
);  // C++ only
```

### <a name="parameters"></a>Paramètres

*x*<br/>
Valeur à virgule flottante.

*expptr*<br/>
Pointeur désignant l’exposant entier stocké.

## <a name="return-value"></a>Valeur de retour

**frexp** retourne la mantisse. Si *x* est égal à 0, la fonction retourne 0 pour la mantisse et l’exposant. Si *expptr* a la **valeur null**, le gestionnaire de paramètre non valide est appelé, comme décrit dans [validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, cette fonction affecte à **errno** la valeur **EINVAL** et retourne 0.

## <a name="remarks"></a>Notes

La fonction **frexp** décompose la valeur à virgule flottante (*x*) en une mantisse (*m*) et un exposant (*n*), de telle sorte que la valeur absolue de *m* est supérieure ou égale à 0,5 et inférieure à 1,0, et *x*  =  *m* * 2<sup>*n*</sup>. L’exposant entier *n* est stocké à l’emplacement désigné par *expptr*.

C++autorise la surcharge, donc vous pouvez appeler des surcharges de **frexp**. Dans un programme C, **frexp** prend toujours un pointeur de type **double** et **int** et retourne un **double**.

## <a name="requirements"></a>Configuration requise

|Fonction|En-tête requis|
|--------------|---------------------|
|**frexp**, **frexpf**, **frexpl**|\<math.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

```C
// crt_frexp.c
// This program calculates frexp( 16.4, &n )
// then displays y and n.

#include <math.h>
#include <stdio.h>

int main( void )
{
   double x, y;
   int n;

   x = 16.4;
   y = frexp( x, &n );
   printf( "frexp( %f, &n ) = %f, n = %d\n", x, y, n );
}
```

```Output
frexp( 16.400000, &n ) = 0.512500, n = 5
```

## <a name="see-also"></a>Voir aussi

[Prise en charge de la virgule flottante](../../c-runtime-library/floating-point-support.md)<br/>
[ldexp](ldexp.md)<br/>
[modf, modff, modfl](modf-modff-modfl.md)<br/>
