---
title: journal, logf, logl, log10, log10f, log10l | Documents Microsoft
ms.custom: ''
ms.date: 04/05/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- log10f
- logf
- log10
- log
- log10l
- logl
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
- logf
- logl
- _log10l
- log
- _logl
- log10f
- log10l
- log10
dev_langs:
- C++
helpviewer_keywords:
- calculating logarithms
- log10f function
- log10 function
- log function
- log10l function
- logl function
- logf function
- logarithms
ms.assetid: 7adc77c2-04f7-4245-a980-21215563cfae
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 12f475cde27d4660f4b4936f3f7717a665b70e86
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32402840"
---
# <a name="log-logf-logl-log10-log10f-log10l"></a>journal, logf, logl, log10, log10f, log10l

Calcule le logarithme.

## <a name="syntax"></a>Syntaxe

```C
double log( double x );
float logf( float x );
long double logl( double x );
double log10( double x );
float log10f ( float x );
long double log10l( double x );
```

```cpp
float log( float x );  // C++ only
long double log( long double x );  // C++ only
float log10( float x );  // C++ only
long double log10( long double x );  // C++ only
```

### <a name="parameters"></a>Paramètres

*x*<br/>
Valeur dont le logarithme doit être recherché.

## <a name="return-value"></a>Valeur de retour

Le **journal** fonctions retournent le logarithme naturel (base *e*) de *x* en cas de réussite. Le **log10** fonctions retournent le logarithme de base 10. Si *x* est négatif, ces fonctions retournent un indéfini (IND), par défaut. Si *x* est 0, elles retournent l’infini (INF).

|Entrée|Exception SEH|Exception{b> <b}Matherr|
|-----------|-------------------|-----------------------|
|± QNAN, IND|aucun|_DOMAIN|
|± 0|ZERODIVIDE|_SING|
|*x* < 0|INVALID|_DOMAIN|

**journal** et **log10** avoir une implémentation qui utilise des Extensions Streaming SIMD 2 (SSE2). Consultez [_set_SSE2_enable](set-sse2-enable.md) pour plus d’informations sur l’utilisation de l’implémentation SSE2 et sur les restrictions qui s’y rattachent.

## <a name="remarks"></a>Notes

C++ autorise la surcharge, vous pouvez appeler des surcharges de **journal** et **log10** qui acceptent et retournent **float** ou **long double** valeurs. Dans un programme C, **journal** et **log10** acceptent et retournent toujours un **double**.

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**journal**, **logf**, **logl**, **log10**, **log10f**, **log10l**|\<math.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

```C
// crt_log.c
/* This program uses log and log10
* to calculate the natural logarithm and
* the base-10 logarithm of 9,000.
*/

#include <math.h>
#include <stdio.h>

int main( void )
{
   double x = 9000.0;
   double y;

   y = log( x );
   printf( "log( %.2f ) = %f\n", x, y );
   y = log10( x );
   printf( "log10( %.2f ) = %f\n", x, y );
}
```

```Output
log( 9000.00 ) = 9.104980
log10( 9000.00 ) = 3.954243
```

Pour générer le logarithme pour d’autres bases, utilisez la relation mathématique : log base b de a == logarithme népérien (a) / logarithme népérien (b).

```cpp
// logbase.cpp
#include <math.h>
#include <stdio.h>

double logbase(double a, double base)
{
   return log(a) / log(base);
}

int main()
{
   double x = 65536;
   double result;

   result = logbase(x, 2);
   printf("Log base 2 of %lf is %lf\n", x, result);
}
```

```Output
Log base 2 of 65536.000000 is 16.000000
```

## <a name="see-also"></a>Voir aussi

[Prise en charge de la virgule flottante](../../c-runtime-library/floating-point-support.md) <br/>
[exp, expf, expl](exp-expf.md) <br/>
[_matherr](matherr.md) <br/>
[pow, powf, powl](pow-powf-powl.md) <br/>
[_CIlog](../../c-runtime-library/cilog.md) <br/>
[_CIlog10](../../c-runtime-library/cilog10.md)<br/>
