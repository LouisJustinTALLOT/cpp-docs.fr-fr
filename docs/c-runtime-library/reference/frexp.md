---
title: frexp, frexpf, frexpl | Documents Microsoft
ms.custom: ''
ms.date: 04/05/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- frexp
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
- frexp
- _frexpl
dev_langs:
- C++
helpviewer_keywords:
- _frexpl function
- mantissas, floating-point variables
- frexpl function
- exponent, floating-point numbers
- frexp function
- floating-point functions, mantissa and exponent
ms.assetid: 9b020f2e-3967-45ec-a6a8-d467a071aa55
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c3bf79e954274b1cedb104ed637ad14b8e1c6431
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32400087"
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

**frexp** renvoie la mantisse. Si *x* est 0, la fonction retourne 0 pour la mantisse et l’exposant. Si *expptr* est **NULL**, le Gestionnaire de paramètres non valides est appelé, comme décrit dans [Validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, cette fonction affecte **errno** à **EINVAL** et retourne 0.

## <a name="remarks"></a>Notes

Le **frexp** fonction décompose la valeur à virgule flottante (*x*) dans une mantisse (*m*) et un exposant (*n*), telle qu’absolu valeur de *m* est supérieur ou égal à 0,5 et inférieur à 1,0, et *x* = *m* * 2<sup>*n*</sup>. L’exposant entier *n* est stocké à l’emplacement vers lequel pointé *expptr*.

C++ autorise la surcharge, vous pouvez appeler des surcharges de **frexp**. Dans un programme C, **frexp** prend toujours un **double** et un **int** pointeur et retourne un **double**.

## <a name="requirements"></a>Spécifications

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
