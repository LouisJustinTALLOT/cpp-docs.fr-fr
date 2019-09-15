---
title: horloge
ms.date: 11/04/2016
api_name:
- clock
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
- clock
helpviewer_keywords:
- processor time used, calculating
- time, calculating processor
- clock function
- processor time used
- calculating processor time used
ms.assetid: 3e1853dd-498f-49ba-b06a-f2315f20904e
ms.openlocfilehash: 836d0c6448adb4c99a251a0e97aa642e30362dcb
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70939126"
---
# <a name="clock"></a>horloge

Calcule le temps horloge utilisé par le processus appelant.

## <a name="syntax"></a>Syntaxe

```C
clock_t clock( void );
```

## <a name="return-value"></a>Valeur de retour

Temps écoulé depuis l’initialisation du CRT au début du processus, mesuré en unités **CLOCKS_PER_SEC** par seconde. Si le temps écoulé n’est pas disponible ou a dépassé le délai positif maximal pouvant être enregistré en tant que type **clock_t** , la fonction retourne la valeur `(clock_t)(-1)`.

## <a name="remarks"></a>Notes

La fonction **Clock** indique la quantité de temps horloge écoulée depuis l’initialisation du CRT pendant le démarrage du processus. Notez que cette fonction n’est pas strictement conforme à la norme ISO C, selon laquelle le temps processeur net est spécifié par la valeur de retour. Pour obtenir les temps processeur, utilisez la fonction Win32 [GetProcessTimes](/windows/win32/api/processthreadsapi/nf-processthreadsapi-getprocesstimes). Pour déterminer le temps écoulé en secondes, divisez la valeur retournée par la fonction **Clock** par la macro **CLOCKS_PER_SEC**.

En raison de suffisamment de temps, la valeur retournée par **Clock** peut dépasser la valeur positive maximale de **clock_t**. Lorsque le processus s’exécute plus longtemps, la valeur retournée par **Clock** est toujours `(clock_t)(-1)`, comme spécifié par la norme ISO C99 (7.23.2.1) et ISO C11 standard (7.27.2.1). Microsoft implémente **clock_t** comme **long**, un entier signé 32 bits et la macro **CLOCKS_PER_SEC** est définie comme 1000. Cela donne une valeur de retour de fonction d' **horloge** maximale de 2147483,647 secondes, soit environ 24,8 jours. Ne vous fiez pas à la valeur retournée par **Clock** dans les processus qui ont été exécutés pendant plus longtemps que ce laps de temps. Vous pouvez utiliser la fonction [temps](time-time32-time64.md) 64 bits ou la fonction Windows [QueryPerformanceCounter](/windows/win32/api/profileapi/nf-profileapi-queryperformancecounter) pour enregistrer les durées de traitement écoulées de plusieurs années.

## <a name="requirements"></a>Configuration requise

|Routine|En-tête requis|
|-------------|---------------------|
|**horloge**|\<time.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

```C
// crt_clock.c
// This sample uses clock() to 'sleep' for three
// seconds, then determines how long it takes
// to execute an empty loop 600000000 times.

#include <stdio.h>
#include <stdlib.h>
#include <time.h>

// Pauses for a specified number of milliseconds.
void do_sleep( clock_t wait )
{
   clock_t goal;
   goal = wait + clock();
   while( goal > clock() )
      ;
}

const long num_loops = 600000000L;

int main( void )
{
   long    i = num_loops;
   clock_t start, finish;
   double  duration;

   // Delay for a specified time.
   printf( "Delay for three seconds\n" );
   do_sleep( (clock_t)3 * CLOCKS_PER_SEC );
   printf( "Done!\n" );

   // Measure the duration of an event.
   start = clock();
   while( i-- )
      ;
   finish = clock();
   duration = (double)(finish - start) / CLOCKS_PER_SEC;
   printf( "Time to do %ld empty loops is ", num_loops );
   printf( "%2.3f seconds\n", duration );
}
```

```Output
Delay for three seconds
Done!
Time to do 600000000 empty loops is 1.354 seconds
```

## <a name="see-also"></a>Voir aussi

[Gestion du temps](../../c-runtime-library/time-management.md)<br/>
[difftime, _difftime32, _difftime64](difftime-difftime32-difftime64.md)<br/>
[time, _time32, _time64](time-time32-time64.md)<br/>
