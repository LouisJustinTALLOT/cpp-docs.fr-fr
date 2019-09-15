---
title: difftime, _difftime32, _difftime64
ms.date: 11/04/2016
api_name:
- _difftime32
- difftime
- _difftime64
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
- api-ms-win-crt-time-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _difftime64
- difftime
- difftime64
- _difftime32
- difftime32
helpviewer_keywords:
- _difftime32 function
- difftime function
- time, finding the difference
- difftime64 function
- _difftime64 function
- difftime32 function
ms.assetid: 4cc0ac2b-fc7b-42c0-8283-8c9d10c566d0
ms.openlocfilehash: 51d74ae447e87e91e9be3c27864b8dfe7f490b14
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70937645"
---
# <a name="difftime-_difftime32-_difftime64"></a>difftime, _difftime32, _difftime64

Recherche la différence entre deux heures.

## <a name="syntax"></a>Syntaxe

```C
double difftime( time_t timeEnd, time_t timeStart );
double _difftime32( __time32_t timeEnd, __time32_t timeStart );
double _difftime64( __time64_t timeEnd, __time64_t timeStart );
```

### <a name="parameters"></a>Paramètres

*timeEnd*<br/>
Heure de fin

*timeStart*<br/>
Heure de début

## <a name="return-value"></a>Valeur de retour

**difftime** retourne le temps écoulé en secondes, de *timeStart* à *timeEnd*. La valeur retournée est un nombre à virgule flottante double précision. Cette valeur peut être 0, indiquant alors une erreur.

## <a name="remarks"></a>Notes

La fonction **difftime** calcule la différence entre les deux valeurs d’heure fournies *timeStart* et *timeEnd*.

La valeur de temps fournie doit être comprise dans la plage de **time_t**. **time_t** est une valeur de 64 bits. Ainsi, la fin de la plage a été repoussée du 18 janvier 2038 à 23:59:59, heure UTC au 31 décembre 3000 à 23:59:59. La plage inférieure de **time_t** est toujours le 1er janvier 1970.

**difftime** est une fonction inline qui prend la valeur **_difftime32** ou **_difftime64** , selon que **_USE_32BIT_TIME_T** est défini ou non. _difftime32 et _difftime64 peuvent être utilisés directement pour forcer l’utilisation d’une taille particulière du type d’heure.

Ces fonctions valident leurs paramètres. Si l’un des paramètres est zéro ou négatif, le gestionnaire de paramètres non valides est appelé, comme décrit dans [Validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, ces fonctions retournent 0 et attribuent à **errno** la valeur **EINVAL**.

## <a name="requirements"></a>Configuration requise

|Routine|En-tête requis|
|-------------|---------------------|
|**difftime**|\<time.h>|
|**_difftime32**|\<time.h>|
|**_difftime64**|\<time.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

```cpp
// crt_difftime.c
// This program calculates the amount of time
// needed to do a floating-point multiply 100 million times.
//

#include <stdio.h>
#include <stdlib.h>
#include <time.h>
#include <float.h>

double RangedRand( float range_min, float range_max)
{
   // Generate random numbers in the half-closed interval
   // [range_min, range_max). In other words,
   // range_min <= random number < range_max
   return ((double)rand() / (RAND_MAX + 1) * (range_max - range_min)
            + range_min);
}

int main( void )
{
   time_t   start, finish;
   long     loop;
   double   result, elapsed_time;
   double   arNums[3];

   // Seed the random-number generator with the current time so that
   // the numbers will be different every time we run.
   srand( (unsigned)time( NULL ) );

   arNums[0] = RangedRand(1, FLT_MAX);
   arNums[1] = RangedRand(1, FLT_MAX);
   arNums[2] = RangedRand(1, FLT_MAX);
   printf( "Using floating point numbers %.5e %.5e %.5e\n", arNums[0], arNums[1], arNums[2] );

   printf( "Multiplying 2 numbers 100 million times...\n" );

   time( &start );
   for( loop = 0; loop < 100000000; loop++ )
      result = arNums[loop%3] * arNums[(loop+1)%3];
   time( &finish );

   elapsed_time = difftime( finish, start );
   printf( "\nProgram takes %6.0f seconds.\n", elapsed_time );
}
```

```Output
Using random floating point numbers 1.04749e+038 2.01482e+038 1.72737e+038
Multiplying 2 floating point numbers 100 million times...
Program takes      3 seconds.
```

## <a name="see-also"></a>Voir aussi

[Prise en charge de la virgule flottante](../../c-runtime-library/floating-point-support.md)<br/>
[Gestion du temps](../../c-runtime-library/time-management.md)<br/>
[time, _time32, _time64](time-time32-time64.md)<br/>
