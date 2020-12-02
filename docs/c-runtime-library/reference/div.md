---
title: div, ldiv, lldiv
description: Les fonctions div, ldiv et lldiv de la bibliothèque Runtime C de Microsoft calculent le quotient et le reste de deux valeurs entières.
ms.date: 11/21/2020
api_name:
- div
- ldiv
- lldiv
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
- api-ms-win-crt-utility-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- div
- ldiv
- lldiv
helpviewer_keywords:
- div function
- quotients, computing
- quotients
- dividing integers
- remainder computing
ms.openlocfilehash: d87b2e3a84e389be8b14970a3aa611bb288cbec8
ms.sourcegitcommit: 432c24dde31c400437c4320e8432b1ddb232f844
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2020
ms.locfileid: "96440281"
---
# <a name="div-ldiv-lldiv"></a>`div`, `ldiv`, `lldiv`

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

*`numer`*\
Numérateur.

*`denom`*\
Dénominateur.

## <a name="return-value"></a>Valeur renvoyée

**`div`** appelée en utilisant des arguments de type **`int`** retourne une structure de type `div_t` , qui contient le quotient et le reste. La valeur de retour avec des arguments de type **`long`** est `ldiv_t` , et la valeur de retour avec des arguments de type **`long long`** est `lldiv_t` . Les `div_t` `ldiv_t` types, et `lldiv_t` sont définis dans \<stdlib.h> .

## <a name="remarks"></a>Remarques

La **`div`** fonction divise *`numer`* par *`denom`* et calcule le quotient et le reste. La [`div_t`](../../c-runtime-library/standard-types.md) structure contient le quotient, `quot` , et le reste, `rem` . Le signe du quotient est le même que le signe du quotient mathématique. Sa valeur absolue est le plus grand entier inférieur à la valeur absolue du quotient mathématique. Si le dénominateur est 0, le programme se termine par un message d’erreur.

Les surcharges de **`div`** qui acceptent des arguments de type **`long`** ou **`long long`** sont uniquement disponibles pour le code C++. Les types de retour [`ldiv_t`](../../c-runtime-library/standard-types.md) et [`lldiv_t`](../../c-runtime-library/standard-types.md) contiennent des membres `quot` et `rem` , qui ont les mêmes significations que les membres de `div_t` .

## <a name="requirements"></a>Spécifications

| Routine | En-tête requis |
|--|--|
| **`div`**, **`ldiv`**, **`lldiv`** | \<stdlib.h> |

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

[Prise en charge de la virgule flottante](../../c-runtime-library/floating-point-support.md)\
[`imaxdiv`](imaxdiv.md)
