---
title: localtime, _localtime32, _localtime64
ms.date: 4/2/2020
api_name:
- _localtime64
- _localtime32
- localtime
- _o__localtime32
- _o__localtime64
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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: 21496b71c354c7bed7b87526dc40bc9b24865da2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81342139"
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

*sourceTime sourceTime source*<br/>
Pointeur désignant la valeur de temps stockée.

## <a name="return-value"></a>Valeur de retour

Retournez un pointeur au résultat de la structure, ou **NULL** si la date passée à la fonction est la suivante :

- Avant le 1er janvier 1970 à minuit

- Après 03:14:07, Janvier 19, 2038, UTC (en utilisant **_time32** et **time32_t**).

- Après 23:59:59, Décembre 31, 3000, UTC (en utilisant **_time64** et **__time64_t**).

**_localtime64**, qui utilise la structure **__time64_t,** permet d’exprimer les dates jusqu’à 23:59:59, Décembre 31, 3000, le temps universel coordonné (UTC), tandis que **_localtime32** représente des dates jusqu’à 23:59:59 Janvier 18, 2038, UTC.

**l’heure locale** est une fonction inline qui évalue à **_localtime64**, et **time_t** est équivalente à **__time64_t**. Si vous avez besoin de forcer le compilateur à interpréter **time_t** comme l’ancien time_t 32 **bits**, vous pouvez définir **_USE_32BIT_TIME_T**. Cela entraînera **l’évaluation locale** pour **_localtime32**. Cela n’est pas recommandé, car votre application peut échouer après le 18 janvier 2038 et cela n’est pas autorisé sur les plateformes 64 bits.

Les champs du type de structure [tm](../../c-runtime-library/standard-types.md) stockent les valeurs suivantes, dont chacune est une **int**:

|Champ|Description|
|-|-|
|**tm_sec**|Quelques secondes après minute (0 - 59).|
|**tm_min**|Minutes après heure (0 - 59).|
|**tm_hour**|Heures depuis minuit (0 - 23).|
|**tm_mday**|Jour du mois (1 - 31).|
|**tm_mon**|Mois (0 - 11; Janvier et 0).|
|**tm_year**|Année (année en cours moins 1900).|
|**tm_wday**|Jour de la semaine (0 - 6; Dimanche 0).|
|**tm_yday**|Jour de l’année (0 - 365; 1er janvier et 0).|
|**tm_isdst**|Valeur positive si l’heure d’été est en vigueur ; 0 si l’heure d’été n’est pas appliquée ; valeur négative si l’état de l’heure d’été est inconnu.|

Si la variable de l’environnement **TZ** est définie, la bibliothèque C run-time suppose des règles appropriées aux États-Unis pour la mise en œuvre du calcul de l’heure d’été (heure d’été).

## <a name="remarks"></a>Notes

La fonction **locale** convertit un temps stocké comme une valeur [time_t](../../c-runtime-library/standard-types.md) et stocke le résultat dans une structure de type [tm](../../c-runtime-library/standard-types.md). La source **de valeur longue** *Durée* représente les secondes écoulées depuis minuit (00:00:00), Janvier 1, 1970, UTC. Cette valeur est généralement obtenue à partir de la fonction [temporelle.](time-time32-time64.md)

Les versions 32-bit et 64 bits de [gmtime](gmtime-gmtime32-gmtime64.md), [mktime](mktime-mktime32-mktime64.md), [mkgmtime](mkgmtime-mkgmtime32-mkgmtime64.md), et **local** tous utilisent une structure **de tm** unique par thread pour la conversion. Chaque appel à une de ces routines détruit le résultat de l’appel précédent.

**localtime** corrige pour le fuseau horaire local si l’utilisateur définit d’abord la variable de l’environnement global **TZ**. Lorsque **TZ** est défini, trois autres variables de l’environnement **(_timezone**, **_daylight**, et **_tzname**) sont automatiquement définies ainsi. Si la variable **TZ** n’est pas définie, **l’heure locale** tente d’utiliser les informations du fuseau horaire spécifiées dans l’application Date/Heure dans le panneau de contrôle. Si ces informations ne peuvent pas être obtenues, PST8PDT (fuseau horaire Pacifique) est utilisé par défaut. Consultez [_tzset](tzset.md) pour obtenir une description de ces variables. **TZ** est une extension Microsoft et ne fait pas partie de la définition standard ANSI de **l’heure locale**.

> [!NOTE]
> L’environnement cible doit tenter de déterminer si l’heure d’été est en vigueur.

Ces fonctions valident leurs paramètres. Si *sourceTime* est un pointeur nul, ou si la valeur *sourceTime* est négative, ces fonctions invoquent un gestionnaire de paramètres invalide, tel que décrit dans [La validation de paramètres](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, les fonctions retournent **NULL** et **placent errno** à **EINVAL**.

Par défaut, l’état global de cette fonction est étendue à l’application. Pour changer cela, voir [Global State dans le CRT](../global-state.md).

## <a name="requirements"></a>Spécifications

|Routine|En-tête C requis|En-tête C++ requis|
|-------------|---------------------|-|
|**localtime**, **_localtime32**, **_localtime64**|\<time.h>|\<ctime> ou \<time.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

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
