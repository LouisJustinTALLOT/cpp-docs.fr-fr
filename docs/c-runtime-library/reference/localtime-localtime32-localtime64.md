---
title: localtime, _localtime32, _localtime64 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _localtime64
- _localtime32
- localtime
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
- localtime64
- _localtime64
- localtime32
- localtime
- _localtime32
dev_langs:
- C++
helpviewer_keywords:
- localtime32 function
- _localtime32 function
- _localtime64 function
- localtime64 function
- localtime function
- time, converting values
ms.assetid: 4260ec3d-43ee-4538-b998-402a282bb9b8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 778b2d214551c5848dd091e33dbbab1814544fb4
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32405508"
---
# <a name="localtime-localtime32-localtime64"></a>localtime, _localtime32, _localtime64

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

Retourne un pointeur désignant le résultat de la structure, ou **NULL** si la date est transmise à la fonction est :

- Avant le 1er janvier 1970 à minuit

- Après le 03:14:07, le 19 janvier 2038, UTC (à l’aide de **_time32** et **time32_t**).

- Après avoir 23:59:59, le 31 décembre 3000 UTC (à l’aide de **_time64** et **__time64_t**).

**_localtime64**, qui utilise le **__time64_t** structure, permet des dates d’exprimer des et 23:59:59, le 31 décembre 3000, temps universel coordonné (UTC), tandis que **_localtime32** représente les dates et 23:59:59 18 janvier 2038, UTC.

**LocalTime** est une fonction inline qui prend la valeur **_localtime64**, et **time_t** équivaut à **__time64_t**. Si vous avez besoin forcer le compilateur à interpréter **time_t** en tant que l’ancien 32 bits **time_t**, vous pouvez définir **_USE_32BIT_TIME_T**. Cette action provoquerait **localtime** à évaluer à **_localtime32**. Cela n’est pas recommandé, car votre application peut échouer après le 18 janvier 2038 et cela n’est pas autorisé sur les plateformes 64 bits.

Les champs du type structure [tm](../../c-runtime-library/standard-types.md) stocker les valeurs suivantes, chacune d’elles étant un **int**:

|Champ|Description|
|-|-|
|**tm_sec**|Secondes après la minute (0 - 59).|
|**tm_min**|Minutes après l’heure (0 - 59).|
|**tm_hour**|Heures écoulées depuis minuit (0 - 23).|
|**tm_mday**|Jour du mois (1 à 31).|
|**tm_mon**|Mois (0 - 11 ; Janvier = 0).|
|**tm_year**|Année (année en cours moins 1900).|
|**tm_wday**|Jour de la semaine (0 - 6 ; Dimanche = 0).|
|**tm_yday**|Jour de l’année (0 - 365 ; Le 1er janvier = 0).|
|**tm_isdst**|Valeur positive si l’heure d’été est en vigueur ; 0 si l’heure d’été n’est pas appliquée ; valeur négative si l’état de l’heure d’été est inconnu.|

Si le **TZ** variable d’environnement est définie, la bibliothèque Runtime C suppose que les règles appropriées pour les États-Unis de calcul de l’heure d’été (DST).

## <a name="remarks"></a>Notes

Le **localtime** fonction convertit une heure stockée en tant qu’un [time_t](../../c-runtime-library/standard-types.md) valeur et stocke le résultat dans une structure de type [tm](../../c-runtime-library/standard-types.md). Le **long** valeur *sourceTime* représente les secondes écoulées depuis minuit (00 : 00:00), le 1er janvier 1970, UTC. Cette valeur est généralement obtenue à partir de la [temps](time-time32-time64.md) (fonction).

Les versions 32 bits et 64 bits de [gmtime](gmtime-gmtime32-gmtime64.md), [mktime](mktime-mktime32-mktime64.md), [mkgmtime](mkgmtime-mkgmtime32-mkgmtime64.md), et **localtime** tous utiliseront une seule **tm** structure par thread pour la conversion. Chaque appel à une de ces routines détruit le résultat de l’appel précédent.

**LocalTime** corrige le fuseau horaire local si l’utilisateur définit la variable d’environnement global **TZ**. Lorsque **TZ** est défini, les trois autres variables d’environnement (**_timezone**, **_daylight**, et **_tzname**) sont définies automatiquement ainsi. Si le **TZ** variable n’est pas définie, **localtime** tente d’utiliser les informations de fuseau horaire spécifiées dans l’application de Date/heure dans le panneau de configuration. Si ces informations ne peuvent pas être obtenues, PST8PDT (fuseau horaire Pacifique) est utilisé par défaut. Consultez [_tzset](tzset.md) pour obtenir une description de ces variables. **TZ** est une extension Microsoft et ne fait pas partie de la définition standard ANSI de **localtime**.

> [!NOTE]
> L’environnement cible doit tenter de déterminer si l’heure d’été est en vigueur.

Ces fonctions valident leurs paramètres. Si *sourceTime* est un pointeur null, ou si le *sourceTime* valeur est négative, ces fonctions appellent un gestionnaire de paramètre non valide, comme décrit dans [Validation de paramètre](../../c-runtime-library/parameter-validation.md) . Si l’exécution est autorisée à se poursuivre, les fonctions retournent **NULL** et **errno** à **EINVAL**.

## <a name="requirements"></a>Spécifications

|Routine|En-tête C requis|En-tête C++ requis|
|-------------|---------------------|-|
|**LocalTime**, **_localtime32**, **_localtime64**|\<time.h>|\<CTime > ou \<time.h >|

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
