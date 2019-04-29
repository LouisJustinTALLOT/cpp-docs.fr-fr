---
title: div, ldiv, lldiv
ms.date: 04/05/2018
apiname:
- div
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
- api-ms-win-crt-utility-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- div
helpviewer_keywords:
- div function
- quotients, computing
- quotients
- dividing integers
- remainder computing
ms.assetid: 8ae80d97-54fd-499e-b14c-e30993b58119
ms.openlocfilehash: 0ee1b3b6a5d7b15470ffe1e667b4077d1f9581e4
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62339258"
---
# <a name="div-ldiv-lldiv"></a>div, ldiv, lldiv

Calcule le quotient et le reste de deux valeurs entières.

## <a name="syntax"></a>Syntaxe

```C
div_t div(
   int numer,
   int denom
);
ldiv_t ldiv(
   long numer,
   long denom
);
lldiv_t lldiv(
   long long numer,
   long long denom
);
```

```cpp
ldiv_t div(
   long numer,
   long denom
); /* C++ only */
lldiv_t div(
   long long numer,
   long long denom
); /* C++ only */
```

### <a name="parameters"></a>Paramètres

*numer*<br/>
Numérateur.

*denom*<br/>
Dénominateur.

## <a name="return-value"></a>Valeur de retour

**div** appelée à l’aide des arguments de type **int** retourne une structure de type **div_t**, qui comprend le quotient et le reste. La valeur de retour avec des arguments de type **long** est **ldiv_t**et la valeur de retour avec des arguments de type **long** **long** est **lldiv_t**. **div_t**, **ldiv_t**, et **lldiv_t** sont définis dans \<stdlib.h >.

## <a name="remarks"></a>Notes

Le **div** fonction divise *nombre* par *denom* et ce qui calcule le quotient et le reste. Le [div_t](../../c-runtime-library/standard-types.md) structure contient le quotient, **quot**et le reste, **rem**. Le signe du quotient est identique à celui du quotient mathématique. Sa valeur absolue est le plus grand entier qui est inférieur à la valeur absolue du quotient mathématique. Si le dénominateur est 0, le programme se termine par un message d’erreur.

Les surcharges de **div** qui acceptent des arguments de type **long** ou **long** **long** sont uniquement disponibles pour le code C++. Les types de retour [ldiv_t](../../c-runtime-library/standard-types.md) et [lldiv_t](../../c-runtime-library/standard-types.md) contient des membres **quot** et **rem**, qui ont la même signification que les membres de **div_t**.

## <a name="requirements"></a>Configuration requise

|Routine|En-tête requis|
|-------------|---------------------|
|**div**, **ldiv**, **lldiv**|\<stdlib.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

```C
// crt_div.c
// arguments: 876 13

// This example takes two integers as command-line
// arguments and displays the results of the integer
// division. This program accepts two arguments on the
// command line following the program name, then calls
// div to divide the first argument by the second.
// Finally, it prints the structure members quot and rem.
//

#include <stdlib.h>
#include <stdio.h>
#include <math.h>

int main( int argc, char *argv[] )
{
   int x,y;
   div_t div_result;

   x = atoi( argv[1] );
   y = atoi( argv[2] );

   printf( "x is %d, y is %d\n", x, y );
   div_result = div( x, y );
   printf( "The quotient is %d, and the remainder is %d\n",
           div_result.quot, div_result.rem );
}
```

```Output
x is 876, y is 13
The quotient is 67, and the remainder is 5
```

## <a name="see-also"></a>Voir aussi

[Prise en charge de la virgule flottante](../../c-runtime-library/floating-point-support.md)<br/>
[ldiv, lldiv](ldiv-lldiv.md)<br/>
[imaxdiv](imaxdiv.md)<br/>
