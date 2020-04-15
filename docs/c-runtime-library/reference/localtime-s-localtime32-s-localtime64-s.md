---
title: localtime_s, _localtime32_s, _localtime64_s
ms.date: 4/2/2020
api_name:
- _localtime64_s
- _localtime32_s
- localtime_s
- _o__localtime32_s
- _o__localtime64_s
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
- _localtime32_s
- localtime32_s
- localtime_s
- localtime64_s
- _localtime64_s
helpviewer_keywords:
- _localtime64_s function
- localtime32_s function
- _localtime32_s function
- localtime64_s function
- time, converting values
- localtime_s function
ms.assetid: 842d1dc7-d6f8-41d3-b340-108d4b90df54
ms.openlocfilehash: 3c5d194da85eb5d008dfc9cf19f222ebb575747d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81342122"
---
# <a name="localtime_s-_localtime32_s-_localtime64_s"></a>localtime_s, _localtime32_s, _localtime64_s

Convertit une valeur **temporelle time_t** en une structure **tm,** et corrige pour le fuseau horaire local. Ces versions de [localtime, _localtime32, _localtime64](localtime-localtime32-localtime64.md) intègrent les améliorations de sécurité décrites dans [Fonctionnalités de sécurité dans le CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Syntaxe

```C
errno_t localtime_s(
   struct tm* const tmDest,
   time_t const* const sourceTime
);
errno_t _localtime32_s(
   struct tm* tmDest,
   __time32_t const* sourceTime
);
errno_t _localtime64_s(
   struct tm* tmDest,
   __time64_t const* sourceTime
);
```

### <a name="parameters"></a>Paramètres

*tmDest*<br/>
Pointeur désignant la structure de temps à renseigner.

*sourceTime sourceTime source*<br/>
Pointeur désignant la valeur de temps stockée.

## <a name="return-value"></a>Valeur de retour

Zéro si l’opération réussit. En cas d’échec, la valeur de retour est un code d’erreur. Les codes d’erreur sont définis dans Errno.h. Pour obtenir la liste de ces erreurs, consultez [errno](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

### <a name="error-conditions"></a>Conditions d'erreur

|*tmDest*|*sourceTime sourceTime source*|Valeur retournée|Valeur en *tmDest*|Appelle un gestionnaire de paramètres non valides|
|-----------|------------|------------------|--------------------|---------------------------------------|
|**Null**|n'importe laquelle|**EINVAL (EN)**|Non modifiée|Oui|
|Non **NULL** (points à la mémoire valide)|**Null**|**EINVAL (EN)**|Tous les champs définis sur -1|Oui|
|Non **NULL** (points à la mémoire valide)|moins de 0 ou plus que **_MAX__TIME64_T**|**EINVAL (EN)**|Tous les champs définis sur -1|Non|

Concernant les deux premières conditions d’erreur, le gestionnaire de paramètres non valides est appelé, comme décrit dans [Validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, ces fonctions **définies errno** à **EINVAL** et retourner **EINVAL**.

## <a name="remarks"></a>Notes

La fonction **localtime_s** convertit un temps stocké comme une valeur [time_t](../../c-runtime-library/standard-types.md) et stocke le résultat dans une structure de type [tm](../../c-runtime-library/standard-types.md). La source **de** valeur *time_tTime* représente les secondes écoulées depuis minuit (00:00:00), Janvier 1, 1970, UTC. Cette valeur est généralement obtenue à partir de la fonction [temporelle.](time-time32-time64.md)

**localtime_s** corrige pour le fuseau horaire local si l’utilisateur définit d’abord la variable de l’environnement global **TZ**. Lorsque **TZ** est défini, trois autres variables de l’environnement **(_timezone**, **_daylight**, et **_tzname**) sont automatiquement définies ainsi. Si la variable **TZ** n’est pas définie, **localtime_s** tente d’utiliser les informations du fuseau horaire spécifiées dans l’application Date/Heure dans le panneau de contrôle. Si ces informations ne peuvent pas être obtenues, PST8PDT (fuseau horaire Pacifique) est utilisé par défaut. Consultez [_tzset](tzset.md) pour obtenir une description de ces variables. **TZ** est une extension Microsoft et ne fait pas partie de la définition standard ANSI de **l’heure locale**.

> [!NOTE]
> L’environnement cible doit tenter de déterminer si l’heure d’été est en vigueur.

**_localtime64_s**, qui utilise la structure **__time64_t,** permet d’exprimer les dates jusqu’à 23:59:59, Janvier 18, 3001, le temps universel coordonné (UTC), tandis que **_localtime32_s** représente des dates jusqu’à 23:59:59 Janvier 18, 2038, UTC.

**localtime_s** est une fonction inline qui évalue à **_localtime64_s**, et **time_t** est équivalent à **__time64_t**. Si vous avez besoin de forcer le compilateur à interpréter **time_t** comme l’ancien time_t 32 **bits**, vous pouvez définir **_USE_32BIT_TIME_T**. Cela amènera **localtime_s** à évaluer pour **_localtime32_s**. Cela n’est pas recommandé, car votre application peut échouer après le 18 janvier 2038 et cela n’est pas autorisé sur les plateformes 64 bits.

Les champs du type de structure [tm](../../c-runtime-library/standard-types.md) stockent les valeurs suivantes, dont chacune est une **int.**

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

Par défaut, l’état global de cette fonction est étendue à l’application. Pour changer cela, voir [Global State dans le CRT](../global-state.md).

## <a name="requirements"></a>Spécifications

|Routine|En-tête C requis|En-tête C++ requis|
|-------------|---------------------|-|
|**localtime_s**, **_localtime32_s**, **_localtime64_s**|\<time.h>|\<ctime> ou \<time.h>|

Pour plus d’informations sur la compatibilité, consultez [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

```C
// crt_localtime_s.c
// This program uses _time64 to get the current time
// and then uses _localtime64_s() to convert this time to a structure
// representing the local time. The program converts the result
// from a 24-hour clock to a 12-hour clock and determines the
// proper extension (AM or PM).

#include <stdio.h>
#include <string.h>
#include <time.h>

int main( void )
{
    struct tm newtime;
    char am_pm[] = "AM";
    __time64_t long_time;
    char timebuf[26];
    errno_t err;

    // Get time as 64-bit integer.
    _time64( &long_time );
    // Convert to local time.
    err = _localtime64_s( &newtime, &long_time );
    if (err)
    {
        printf("Invalid argument to _localtime64_s.");
        exit(1);
    }
    if( newtime.tm_hour > 12 )        // Set up extension.
        strcpy_s( am_pm, sizeof(am_pm), "PM" );
    if( newtime.tm_hour > 12 )        // Convert from 24-hour
        newtime.tm_hour -= 12;        // to 12-hour clock.
    if( newtime.tm_hour == 0 )        // Set hour to 12 if midnight.
        newtime.tm_hour = 12;

    // Convert to an ASCII representation.
    err = asctime_s(timebuf, 26, &newtime);
    if (err)
    {
        printf("Invalid argument to asctime_s.");
        exit(1);
    }
    printf( "%.19s %s\n", timebuf, am_pm );
}
```

```Output
Fri Apr 25 01:19:27 PM
```

## <a name="see-also"></a>Voir aussi

[Gestion du temps](../../c-runtime-library/time-management.md)<br/>
[asctime_s, _wasctime_s](asctime-s-wasctime-s.md)<br/>
[ctime, _ctime32, _ctime64, _wctime, _wctime32, _wctime64](ctime-ctime32-ctime64-wctime-wctime32-wctime64.md)<br/>
[_ftime, _ftime32, _ftime64](ftime-ftime32-ftime64.md)<br/>
[gmtime_s, _gmtime32_s, _gmtime64_s](gmtime-s-gmtime32-s-gmtime64-s.md)<br/>
[localtime, _localtime32, _localtime64](localtime-localtime32-localtime64.md)<br/>
[time, _time32, _time64](time-time32-time64.md)<br/>
[_tzset](tzset.md)<br/>
