---
title: 'Fonctions de Bessel : _j0, _j1, _jn, _y0, _y1, _yn'
ms.date: 04/05/2018
apiname:
- _j0
- _j1
- _jn
- _y0
- _y1
- _yn
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
- c.bessel
- _j0
- _j1
- _jn
- _y0
- _y1
- _yn
helpviewer_keywords:
- Bessel functions
- _j0 function
- _j1 function
- _jn function
- _y0 function
- _y1 function
- _yn function
ms.assetid: a21a8bf1-df9d-4ba0-a8c2-e7ef71921d96
ms.openlocfilehash: 682eaa99d0be1b959152ff94cc10a86aa68d988d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50531861"
---
# <a name="bessel-functions-j0-j1-jn-y0-y1-yn"></a>Fonctions de Bessel : _j0, _j1, _jn, _y0, _y1, _yn

Calcule la fonction de Bessel de première ou deuxième espèce, d’ordre 0, 1 ou n. Les fonctions de Bessel sont couramment utilisées dans les calculs mathématiques de la théorie sur les ondes électromagnétiques.

## <a name="syntax"></a>Syntaxe

```C
double _j0(
   double x
);
double _j1(
   double x
);
double _jn(
   int n,
   double x
);
double _y0(
   double x
);
double _y1(
   double x
);
double _yn(
   int n,
   double x
);
```

### <a name="parameters"></a>Paramètres

*x*<br/>
Valeur à virgule flottante.

*n*<br/>
Ordre d’entier de la fonction de Bessel.

## <a name="return-value"></a>Valeur de retour

Chacune de ces routines retourne une fonction de Bessel de *x*. Si *x* est un nombre négatif dans le **_y0**, **_y1**, ou **_yn** fonctions, la routine affecte **errno** à  **EDOM**, imprime un **_domaine** message d’erreur à **stderr**et retourne **_HUGE_VAL**. Vous pouvez modifier à l’aide de gestion des erreurs **_matherr**.

## <a name="remarks"></a>Notes

Le **_j0**, **_j1**, et **_jn** retournent des routines de Bessel fonctions de première espèce : respectivement d’ordre n, 0 et 1.

|Entrée|Exception SEH|Exception{b> <b}Matherr|
|-----------|-------------------|-----------------------|
|+ **QNAN**, **IND**|**NON VALIDE**|**_DOMAINE**|

Le **_y0**, **_y1**, et **_yn** retournent des routines de Bessel functions de deuxième espèce : respectivement d’ordre n, 0 et 1.

|Entrée|Exception SEH|Exception{b> <b}Matherr|
|-----------|-------------------|-----------------------|
|+ **QNAN**, **IND**|**NON VALIDE**|**_DOMAINE**|
|± 0|**ZERODIVIDE**|**_SING**|
|&#124;x&#124; < 0.0|**NON VALIDE**|**_DOMAINE**|

## <a name="requirements"></a>Configuration requise

|Routine|En-tête requis|
|-------------|---------------------|
|**_j0**, **_j1**, **_jn**, **_y0**, **_y1**, **_yn**|\<cmath> (C++), \<math.h> (C, C++)|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

```C
// crt_bessel1.c
#include <math.h>
#include <stdio.h>

int main( void )
{
   double x = 2.387;
   int n = 3, c;

   printf( "Bessel functions for x = %f:\n", x );
   printf( "   Kind   Order  Function     Result\n\n" );
   printf( "   First  0      _j0( x )     %f\n", _j0( x ) );
   printf( "   First  1      _j1( x )     %f\n", _j1( x ) );
   for( c = 2; c < 5; c++ )
      printf( "   First  %d      _jn( %d, x )  %f\n", c, c, _jn( c, x ) );
   printf( "   Second 0      _y0( x )     %f\n", _y0( x ) );
   printf( "   Second 1      _y1( x )     %f\n", _y1( x ) );
   for( c = 2; c < 5; c++ )
      printf( "   Second %d      _yn( %d, x )  %f\n", c, c, _yn( c, x ) );
}
```

```Output
Bessel functions for x = 2.387000:
   Kind   Order  Function     Result

   First  0      _j0( x )     0.009288
   First  1      _j1( x )     0.522941
   First  2      _jn( 2, x )  0.428870
   First  3      _jn( 3, x )  0.195734
   First  4      _jn( 4, x )  0.063131
   Second 0      _y0( x )     0.511681
   Second 1      _y1( x )     0.094374
   Second 2      _yn( 2, x )  -0.432608
   Second 3      _yn( 3, x )  -0.819314
   Second 4      _yn( 4, x )  -1.626833
```

## <a name="see-also"></a>Voir aussi

[Prise en charge de la virgule flottante](../../c-runtime-library/floating-point-support.md)<br/>
[_matherr](matherr.md)<br/>
