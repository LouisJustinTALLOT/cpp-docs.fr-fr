---
title: localtime, _localtime32, _localtime64
ms.date: 11/04/2016
api_name:
- _localtime64
- _localtime32
- localtime
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
- localtime64
- _localtime64
- localtime32
- localtime
- _localtime32
helpviewer_keywords:
- localtime32 function
- _localtime32 function
- _localtime64 function
- localtime64 function
- localtime function
- time, converting values
ms.assetid: 4260ec3d-43ee-4538-b998-402a282bb9b8
ms.openlocfilehash: 7e2f39b3a1b6376e24d8a812d1074840862f398a
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70953343"
---
# <a name="localtime-_localtime32-_localtime64"></a>localtime, _localtime32, _localtime64

Convertit une valeur de temps et effectue une correction en fonction du fuseau horaire local. Des versions plus sécurisées de ces fonctions sont disponibles. Consultez [localtime_s, _localtime32_s, _localtime64_s](localtime-s-localtime32-s-localtime64-s.md).

## <a name="syntax"></a>Syntaxe

```C
struct tm *localtime( const time_t *sourceTime );
struct tm *_localtime32( const __time32_t *sourceTime );
struct tm *_localtime64( const __time64_t *sourceTime );
```

### <a name="parameters"></a>Paramètres

*sourceTime*<br/>
Pointeur désignant la valeur de temps stockée.

## <a name="return-value"></a>Valeur de retour

Retourne un pointeur vers le résultat de la structure, ou **null** si la date passée à la fonction est :

- Avant le 1er janvier 1970 à minuit

- Après 03:14:07, le 19 janvier 2038, UTC (à l’aide de **time32** et **time32_t**).

- Après 23:59:59, le 31 décembre 3000, UTC (à l’aide de **_time64** et **__time64_t**).

**_localtime64**, qui utilise la structure **__time64_t** , permet d’exprimer les dates 23:59:59 jusqu’au 31 décembre 3000, à savoir le temps universel coordonné (UTC), tandis que **_localtime32** représente les dates 23:59:59 jusqu’au 18 janvier 2038, Universel.

**localtime** est une fonction inline qui prend la valeur **_localtime64**et **time_t** est équivalent à **__time64_t**. Si vous devez forcer le compilateur à interpréter **time_t** comme l’ancien **time_t**32 bits, vous pouvez définir **_USE_32BIT_TIME_T**. Si vous procédez ainsi, **localtime** est évalué à **_localtime32**. Cela n’est pas recommandé, car votre application peut échouer après le 18 janvier 2038 et cela n’est pas autorisé sur les plateformes 64 bits.

Les champs de la structure type [TM](../../c-runtime-library/standard-types.md) stockent les valeurs suivantes, chacune d’elles étant un **int**:

|Champ|Description|
|-|-|
|**tm_sec**|Secondes après la minute (0-59).|
|**tm_min**|Minutes après l’heure (0-59).|
|**tm_hour**|Heures depuis minuit (0-23).|
|**tm_mday**|Jour du mois (1-31).|
|**tm_mon**|Mois (0-11 ; Janvier = 0).|
|**tm_year**|Année (année en cours moins 1900).|
|**tm_wday**|Jour de la semaine (0-6 ; Dimanche = 0).|
|**tm_yday**|Jour de l’année (0-365 ; 1er janvier = 0).|
|**tm_isdst**|Valeur positive si l’heure d’été est en vigueur ; 0 si l’heure d’été n’est pas appliquée ; valeur négative si l’état de l’heure d’été est inconnu.|

Si la variable d’environnement **TZ** est définie, la bibliothèque Runtime C suppose des règles appropriées au États-Unis pour l’implémentation du calcul de l’heure d’été (DST).

## <a name="remarks"></a>Notes

La fonction **localtime** convertit une heure stockée en tant que valeur [time_t](../../c-runtime-library/standard-types.md) et stocke le résultat dans une structure de type [TM](../../c-runtime-library/standard-types.md). La valeur long *sourceTime* représente les secondes écoulées depuis minuit (00:00:00), le 1er janvier 1970, UTC. Cette valeur est généralement obtenue à partir de la fonction [Time](time-time32-time64.md) .

Les versions 32 bits et 64 bits de [gmtime](gmtime-gmtime32-gmtime64.md), [mktime](mktime-mktime32-mktime64.md), [mkgmtime](mkgmtime-mkgmtime32-mkgmtime64.md)et **localtime** utilisent toutes les deux une seule structure **TM** par thread pour la conversion. Chaque appel à une de ces routines détruit le résultat de l’appel précédent.

**localtime** corrige le fuseau horaire local si l’utilisateur définit d’abord la variable d’environnement globale **TZ**. Quand **TZ** est défini, trois autres variables d’environnement ( **_timezone**, **_daylight**et **_tzname**) sont automatiquement définies. Si la variable **TZ** n’est pas définie, le port **localtime** tente d’utiliser les informations de fuseau horaire spécifiées dans l’application date/heure du panneau de configuration. Si ces informations ne peuvent pas être obtenues, PST8PDT (fuseau horaire Pacifique) est utilisé par défaut. Consultez [_tzset](tzset.md) pour obtenir une description de ces variables. **TZ** est une extension Microsoft et ne fait pas partie de la définition ANSI standard de **localtime**.

> [!NOTE]
> L’environnement cible doit tenter de déterminer si l’heure d’été est en vigueur.

Ces fonctions valident leurs paramètres. Si *sourceTime* est un pointeur null ou si la valeur *sourceTime* est négative, ces fonctions appellent un gestionnaire de paramètres non valides, comme décrit dans [validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, les fonctions retournent la **valeur null** et attribuent à **errno** la valeur **EINVAL**.

## <a name="requirements"></a>Configuration requise

|Routine|En-tête C requis|En-tête C++ requis|
|-------------|---------------------|-|
|**localtime**, **_localtime32**, **_localtime64**|\<time.h>|\<CTime > ou \<Time. h >|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemples

```C
// crt_localtime.cpp
// compile with: /W3
// This program uses _time64 to get the current time
// and then uses localtime64() to convert this time to a structure
// representing the local time. The program converts the result
// from a 24-hour clock to a 12-hour clock and determines the
// proper extension (AM or PM).

#include <stdio.h>
#include <string.h>
#include <time.h>

int main( void )
{
    struct tm *newtime;
    char am_pm[] = "AM";
    __time64_t long_time;

    _time64( &long_time );             // Get time as 64-bit integer.
                                       // Convert to local time.
    newtime = _localtime64( &long_time ); // C4996
    // Note: _localtime64 deprecated; consider _localetime64_s

    if( newtime->tm_hour > 12 )        // Set up extension.
        strcpy_s( am_pm, sizeof(am_pm), "PM" );
    if( newtime->tm_hour > 12 )        // Convert from 24-hour
        newtime->tm_hour -= 12;        //   to 12-hour clock.
    if( newtime->tm_hour == 0 )        // Set hour to 12 if midnight.
        newtime->tm_hour = 12;

    char buff[30];
    asctime_s( buff, sizeof(buff), newtime );
    printf( "%.19s %s\n", buff, am_pm );
}
```

```Output
Tue Feb 12 10:05:58 AM
```

## <a name="see-also"></a>Voir aussi

[Gestion du temps](../../c-runtime-library/time-management.md)<br/>
[asctime, _wasctime](asctime-wasctime.md)<br/>
[ctime, _ctime32, _ctime64, _wctime, _wctime32, _wctime64](ctime-ctime32-ctime64-wctime-wctime32-wctime64.md)<br/>
[_ftime, _ftime32, _ftime64](ftime-ftime32-ftime64.md)<br/>
[gmtime, _gmtime32, _gmtime64](gmtime-gmtime32-gmtime64.md)<br/>
[localtime_s, _localtime32_s, _localtime64_s](localtime-s-localtime32-s-localtime64-s.md)<br/>
[time, _time32, _time64](time-time32-time64.md)<br/>
[_tzset](tzset.md)<br/>
