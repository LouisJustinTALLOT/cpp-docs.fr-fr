---
title: horloge
ms.date: 11/04/2016
apiname:
- clock
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
- api-ms-win-crt-time-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- clock
helpviewer_keywords:
- processor time used, calculating
- time, calculating processor
- clock function
- processor time used
- calculating processor time used
ms.assetid: 3e1853dd-498f-49ba-b06a-f2315f20904e
ms.openlocfilehash: 4b58b33b533250447cf964134de9869bddee4498
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62347468"
---
# <a name="clock"></a>horloge

Calcule le temps horloge utilisé par le processus appelant.

## <a name="syntax"></a>Syntaxe

```C
clock_t clock( void );
```

## <a name="return-value"></a>Valeur de retour

Temps écoulé depuis l’initialisation du CRT au début du processus, mesurée en **CLOCKS_PER_SEC** unités par seconde. Si le temps écoulé n’est pas disponible ou a dépassé le délai positif maximal qui peut être enregistré en tant qu’un **clock_t cela est** type, la fonction retourne la valeur `(clock_t)(-1)`.

## <a name="remarks"></a>Notes

Le **horloge** fonction indique à combien de temps horloge écoulé depuis l’initialisation du CRT pendant le démarrage du processus. Notez que cette fonction n’est pas strictement conforme à la norme ISO C, selon laquelle le temps processeur net est spécifié par la valeur de retour. Pour obtenir les temps processeur, utilisez la fonction Win32 [GetProcessTimes](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-getprocesstimes). Pour déterminer le temps écoulé en secondes, divisez la valeur retournée par la **horloge** fonction par la macro **CLOCKS_PER_SEC**.

Avec le temps, la valeur retournée par **horloge** peut dépasser la valeur positive maximale de **clock_t cela est**. Lorsque le processus s’exécute plus longtemps, de la valeur retournée par **horloge** est toujours `(clock_t)(-1)`, tel que spécifié par la norme ISO C99 (7.23.2.1) et la norme ISO C11 (7.27.2.1). Microsoft implémente **clock_t cela est** comme un **long**, un entier signé de 32 bits et le **CLOCKS_PER_SEC** macro est définie avec la valeur 1000. Cela donne un maximum **horloge** fonction de valeur de retour de 2 147 483,647 secondes ou 24,8 jours environ. Ne comptez pas sur la valeur retournée par **horloge** dans les processus qui durent plus longtemps que cet intervalle de temps. Vous pouvez utiliser l’instance 64 bits [temps](time-time32-time64.md) fonction ou le Windows [QueryPerformanceCounter](https://msdn.microsoft.com/library/windows/desktop/ms644904) (fonction) pour le processus d’enregistrement des durées de nombreuses années.

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
