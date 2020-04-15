---
title: log, logf, logl, log10, log10f, log10l
ms.date: 4/2/2020
api_name:
- log10f
- logf
- log10
- log
- log10l
- logl
- _o_log
- _o_log10
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
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- logf
- logl
- _log10l
- log
- _logl
- log10f
- log10l
- log10
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
ms.openlocfilehash: ab6f2654e9e647f140d5c579087b76001b317887
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81341877"
---
# <a name="log-logf-logl-log10-log10f-log10l"></a>log, logf, logl, log10, log10f, log10l

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

*X*<br/>
Valeur dont le logarithme doit être recherché.

## <a name="return-value"></a>Valeur de retour

Les fonctions **de journal** retournent le logarithm naturel (base *e*) de *x* en cas de succès. Les fonctions **log10** renvoient le logarithme de base-10. Si *x* est négatif, ces fonctions renvoient une indéfini (IND), par défaut. Si *x* est 0, ils retournent à l’infini (INF).

|Entrée|Exception SEH|Exception\{b\> \<b\}Matherr|
|-----------|-------------------|-----------------------|
|QNAN, IND|Aucun|_DOMAIN|
|0|ZERODIVIDE|_SING|
|*x* < 0|NON VALIDE|_DOMAIN|

**journal** et **log10** ont une implémentation qui utilise Streaming SIMD Extensions 2 (SSE2). Consultez [_set_SSE2_enable](set-sse2-enable.md) pour plus d’informations sur l’utilisation de l’implémentation SSE2 et sur les restrictions qui s’y rattachent.

## <a name="remarks"></a>Notes

Le CMD permet la surcharge, de sorte que vous pouvez appeler des surcharges de **journal** et de **journal10** qui prennent et retournent **flotteur** ou de longues valeurs **doubles.** Dans un programme C, **log** et **log10** toujours prendre et retourner un **double**.

Par défaut, l’état global de cette fonction est étendue à l’application. Pour changer cela, voir [Global State dans le CRT](../global-state.md).

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**log**, **logf**, **logl**, **log10**, **log10f**, **log10l**|\<math.h>|

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

[Soutien à la pointe flottante](../../c-runtime-library/floating-point-support.md) <br/>
[exp, expf, expl](exp-expf.md) <br/>
[_matherr](matherr.md) <br/>
[pow, powf, powl](pow-powf-powl.md) <br/>
[_CIlog](../../c-runtime-library/cilog.md) <br/>
[_CIlog10](../../c-runtime-library/cilog10.md)<br/>
