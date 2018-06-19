---
title: localtime_s, _localtime32_s, _localtime64_s | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _localtime64_s
- _localtime32_s
- localtime_s
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
- _localtime32_s
- localtime32_s
- localtime_s
- localtime64_s
- _localtime64_s
dev_langs:
- C++
helpviewer_keywords:
- _localtime64_s function
- localtime32_s function
- _localtime32_s function
- localtime64_s function
- time, converting values
- localtime_s function
ms.assetid: 842d1dc7-d6f8-41d3-b340-108d4b90df54
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 513bfe5baa16c9cae5052da084c65f580aad7f2e
ms.sourcegitcommit: 19a108b4b30e93a9ad5394844c798490cb3e2945
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/17/2018
ms.locfileid: "34255806"
---
# <a name="localtimes-localtime32s-localtime64s"></a>localtime_s, _localtime32_s, _localtime64_s

Convertit un **time_t** temps valeur pour un **tm** structurer et corrige le fuseau horaire local. Ces versions de [localtime, _localtime32, _localtime64](localtime-localtime32-localtime64.md) intègrent les améliorations de sécurité décrites dans [Fonctionnalités de sécurité dans le CRT](../../c-runtime-library/security-features-in-the-crt.md).

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

*sourceTime*<br/>
Pointeur désignant la valeur de temps stockée.

## <a name="return-value"></a>Valeur de retour

Zéro si l’opération réussit. En cas d’échec, la valeur de retour est un code d’erreur. Les codes d’erreur sont définis dans Errno.h. Pour obtenir la liste de ces erreurs, consultez [errno](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

### <a name="error-conditions"></a>Conditions d’erreur

|*tmDest*|*sourceTime*|Valeur de retour|Valeur de *tmDest*|Appelle un gestionnaire de paramètres non valides|
|-----------|------------|------------------|--------------------|---------------------------------------|
|**NULL**|any|**EINVAL**|Non modifiée|Oui|
|Pas **NULL** (pointe vers une mémoire valide)|**NULL**|**EINVAL**|Tous les champs définis sur -1|Oui|
|Pas **NULL** (pointe vers une mémoire valide)|inférieur à 0 ou supérieur à **_MAX__TIME64_T**|**EINVAL**|Tous les champs définis sur -1|Non|

Concernant les deux premières conditions d’erreur, le gestionnaire de paramètres non valides est appelé, comme décrit dans [Validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, ces fonctions définissent **errno** à **EINVAL** et retourner **EINVAL**.

## <a name="remarks"></a>Notes

Le **_localtime32_s** fonction convertit une heure stockée en tant qu’un [time_t](../../c-runtime-library/standard-types.md) valeur et stocke le résultat dans une structure de type [tm](../../c-runtime-library/standard-types.md). Le **long** valeur *sourceTime* représente les secondes écoulées depuis minuit (00 : 00:00), le 1er janvier 1970, UTC. Cette valeur est généralement obtenue à partir de la [temps](time-time32-time64.md) (fonction).

**_localtime32_s** corrige le fuseau horaire local si l’utilisateur définit la variable d’environnement global **TZ**. Lorsque **TZ** est défini, les trois autres variables d’environnement (**_timezone**, **_daylight**, et **_tzname**) sont définies automatiquement ainsi. Si le **TZ** variable n’est pas définie, **localtime32_s** tente d’utiliser les informations de fuseau horaire spécifiées dans l’application de Date/heure dans le panneau de configuration. Si ces informations ne peuvent pas être obtenues, PST8PDT (fuseau horaire Pacifique) est utilisé par défaut. Consultez [_tzset](tzset.md) pour obtenir une description de ces variables. **TZ** est une extension Microsoft et ne fait pas partie de la définition standard ANSI de **localtime**.

> [!NOTE]
> L’environnement cible doit tenter de déterminer si l’heure d’été est en vigueur.

**_localtime64_s**, qui utilise le **__time64_t** structure, permet des dates d’exprimer des et 23:59:59, le 18 janvier 3001, temps universel coordonné (UTC), tandis que **_localtime32_s** représente les dates et 23:59:59 18 janvier 2038, UTC.

**localtime_s** est une fonction inline qui prend la valeur **_localtime64_s**, et **time_t** équivaut à **__time64_t**. Si vous avez besoin forcer le compilateur à interpréter **time_t** en tant que l’ancien 32 bits **time_t**, vous pouvez définir **_USE_32BIT_TIME_T**. Cette action provoquerait **localtime_s** à évaluer à **_localtime32_s**. Cela n’est pas recommandé, car votre application peut échouer après le 18 janvier 2038 et cela n’est pas autorisé sur les plateformes 64 bits.

Les champs du type structure [tm](../../c-runtime-library/standard-types.md) stocker les valeurs suivantes, chacune d’elles étant un **int**.

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

Si le **TZ** variable d’environnement est définie, la bibliothèque Runtime C suppose que les règles appropriées aux États-Unis pour le calcul de l’heure d’été (DST).

## <a name="requirements"></a>Spécifications

|Routine|En-tête C requis|En-tête C++ requis|
|-------------|---------------------|-|
|**localtime_s**, **_localtime32_s**, **_localtime64_s**|\<time.h>|\<CTime > ou \<time.h >|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

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
