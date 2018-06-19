---
title: abs, labs, llabs, _abs64 | Microsoft Docs
ms.custom: ''
ms.date: 04/05/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- abs
- _abs64
- labs
- llabs
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
- stdlib/_abs64
- math/abs
- _abs64
- abs
- labs
- math/labs
- llabs
- math/llabs
- cmath/abs
dev_langs:
- C++
helpviewer_keywords:
- absolute values
- abs function
- abs64 function
- _abs64 function
- calculating absolute values
ms.assetid: 60f789d1-4a1e-49f5-9e4e-0bdb277ea26a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: cc426bbbc28e6eb3b7e6e4a0fa9fab7e74f62093
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32391751"
---
# <a name="abs-labs-llabs-abs64"></a>abs, labs, llabs, _abs64

Calcule la valeur absolue de l’argument.

## <a name="syntax"></a>Syntaxe

```C
int abs( int n );
long labs( long n );
long long llabs( long long n );
__int64 _abs64( __int64 n );
```

```cpp
long abs( long n );   // C++ only
long long abs( long long n );   // C++ only
double abs( double n );   // C++ only
long double abs( long double n );   // C++ only
float abs( float n );   // C++ only
```

### <a name="parameters"></a>Paramètres

*n*<br/>
Valeur numérique.

## <a name="return-value"></a>Valeur de retour

Le **abs**, **labs**, **llabs** et **_abs64** fonctions retournent la valeur absolue du paramètre *n*. Aucun retour d'erreur.

## <a name="remarks"></a>Notes

C++ autorisant la surcharge, vous pouvez appeler des surcharges de **abs** qui acceptent et retournent **long**, **long** **long**,  **float**, **double**, et **long** **double** valeurs. Ces surcharges sont définies dans l’en-tête \<cmath>. Dans un programme C, **abs** toujours prend et retourne un entier.

**Microsoft Specific**: étant donné que la plage d’entiers négatifs qui peuvent être représentées à l’aide de n’importe quel type intégral est supérieure à la plage d’entiers positifs qui peuvent être représentées à l’aide de ce type, il est possible de fournir un argument à ces fonctions qui ne peut pas être converties. Si la valeur absolue de l’argument ne peut pas être représentée par le type de retour, le **abs** fonctions retournent la valeur d’argument inchangée. Plus précisément, `abs(INT_MIN)` retourne **INT_MIN**, `labs(LONG_MIN)` retourne **LONG_MIN**, `llabs(LLONG_MIN)` retourne **LLONG_MIN**, et `_abs64(_I64_MIN)` Retourne **_I64_MIN**. Cela signifie que la **abs** fonctions ne peuvent pas être utilisées pour garantir une valeur positive.

## <a name="requirements"></a>Spécifications

|Routine|En-tête C requis|En-tête C++ requis|
|-------------|-----------------------|---------------------------|
|**ABS**, **labs**, **llabs**|\<math.h> ou \<stdlib.h>|\<cmath>, \<cstdlib>, \<stdlib.h> ou \<math.h>|
|**_abs64**|\<stdlib.h>|\<cstdlib> ou \<stdlib.h>|

Pour utiliser des versions surchargées de **abs** en C++, vous devez inclure le \<cmath > en-tête.

## <a name="example"></a>Exemple

Ce programme calcule et affiche les valeurs absolues de plusieurs nombres.

```C
// crt_abs.c
// Build: cl /W3 /TC crt_abs.c
// This program demonstrates the use of the abs function
// by computing and displaying the absolute values of
// several numbers.

#include <stdio.h>
#include <math.h>
#include <stdlib.h>
#include <limits.h>

int main( void )
{
    int ix = -4;
    long lx = -41567L;
    long long llx = -9876543210LL;
    __int64 wx = -1;

    // absolute 32 bit integer value
    printf_s("The absolute value of %d is %d\n", ix, abs(ix));

    // absolute long integer value
    printf_s("The absolute value of %ld is %ld\n", lx, labs(lx));

    // absolute long long integer value
    printf_s("The absolute value of %lld is %lld\n", llx, llabs(llx));

    // absolute 64 bit integer value
    printf_s("The absolute value of 0x%.16I64x is 0x%.16I64x\n", wx,
        _abs64(wx));

    // Integer error cases:
    printf_s("Microsoft implementation-specific results:\n");
    printf_s(" abs(INT_MIN) returns %d\n", abs(INT_MIN));
    printf_s(" labs(LONG_MIN) returns %ld\n", labs(LONG_MIN));
    printf_s(" llabs(LLONG_MIN) returns %lld\n", llabs(LLONG_MIN));
    printf_s(" _abs64(_I64_MIN) returns 0x%.16I64x\n", _abs64(_I64_MIN));
}
```

```Output
The absolute value of -4 is 4
The absolute value of -41567 is 41567
The absolute value of -9876543210 is 9876543210
The absolute value of 0xffffffffffffffff is 0x0000000000000001
Microsoft implementation-specific results:
abs(INT_MIN) returns -2147483648
labs(LONG_MIN) returns -2147483648
llabs(LLONG_MIN) returns -9223372036854775808
_abs64(_I64_MIN) returns 0x8000000000000000
```

## <a name="see-also"></a>Voir aussi

[Conversion de données](../../c-runtime-library/data-conversion.md)<br/>
[Prise en charge de la virgule flottante](../../c-runtime-library/floating-point-support.md)<br/>
[_cabs](cabs.md)<br/>
[fabs, fabsf, fabsl](fabs-fabsf-fabsl.md)<br/>
[imaxabs](imaxabs.md)<br/>
