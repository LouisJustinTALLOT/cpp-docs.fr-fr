---
title: remquo, remquof, remquol | Microsoft Docs
ms.custom: ''
ms.date: 04/05/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- remquof
- remquo
- remquol
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
- remquof
- remquol
- remquo
dev_langs:
- C++
helpviewer_keywords:
- remquol function
- remquof function
- remquo function
ms.assetid: a1d3cb8b-8027-4cd3-8deb-04eb17f299fc
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8d2bcb774d7ebe7e71c3877af326177bbf8d7160
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32407000"
---
# <a name="remquo-remquof-remquol"></a>remquo, remquof, remquol

Calcule le reste de deux valeurs entières et stocke une valeur entière avec le signe et la grandeur approximative du quotient à un emplacement spécifié dans un paramètre.

## <a name="syntax"></a>Syntaxe

```C
double remquo( double numer, double denom, int* quo );
float remquof( float numer, float denom, int* quo );
long double remquol( long double numer, long double denom, int* quo );
```

```cpp
float remquo( float numer, float denom, int* quo ); /* C++ only */
long double remquo( long double numer, long double denom, int* quo ); /* C++ only */
```

### <a name="parameters"></a>Paramètres

*nombre*<br/>
Numérateur.

*denom*<br/>
Dénominateur.

*actuel*<br/>
Pointeur désignant un entier pour stocker une valeur qui a le signe et la grandeur approximative du quotient.

## <a name="return-value"></a>Valeur de retour

**remquo** renvoie le reste à virgule flottante de *x* / *y*. Si la valeur de *y* est égale à 0.0, **remquo** retourne une valeur NaN silencieuse. Pour plus d’informations sur la représentation sous forme d’une valeur NaN silencieuse par le **printf** famille, voir [printf, _printf_l, wprintf, _wprintf_l](printf-printf-l-wprintf-wprintf-l.md).

## <a name="remarks"></a>Notes

Le **remquo** fonction calcule le reste à virgule flottante *f* de *x* / *y* tels que *x*   =  *i* * *y* + *f*, où *i* est un entier , *f* a la même signature que *x*et la valeur absolue de *f* est inférieure à la valeur absolue de *y*.

C++ autorise la surcharge, vous pouvez appeler des surcharges de **remquo** qui acceptent et retournent **float** ou **long** **double** valeurs. Dans un programme C, **remquo** toujours prend deux **double** arguments et retourne un **double**.

## <a name="requirements"></a>Spécifications

|Fonction|En-tête requis (C)|En-tête requis (C++)|
|--------------|---------------------|-|
|**remquo**, **remquof**, **remquol**|\<math.h>|\<cmath> ou \<math.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

```C
// crt_remquo.c
// This program displays a floating-point remainder.

#include <math.h>
#include <stdio.h>

int main( void )
{
   double w = -10.0, x = 3.0, z;
   int quo = 0;

   z = remquo(w, x, &quo);
   printf("The remainder of %.2f / %.2f is %f\n", w, x, z);
   printf("Approximate signed quotient is %d\n", quo);
}
```

```Output
The remainder of -10.00 / 3.00 is -1.000000
Approximate signed quotient is -3
```

## <a name="see-also"></a>Voir aussi

[Prise en charge de la virgule flottante](../../c-runtime-library/floating-point-support.md)<br/>
[ldiv, lldiv](ldiv-lldiv.md)<br/>
[imaxdiv](imaxdiv.md)<br/>
[fmod, fmodf](fmod-fmodf.md)<br/>
[remainder, remainderf, remainderl](remainder-remainderf-remainderl.md)<br/>
