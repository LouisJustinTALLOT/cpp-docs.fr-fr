---
title: gmtime, _gmtime32, _gmtime64
ms.date: 11/04/2016
apiname:
- _gmtime32
- gmtime
- _gmtime64
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
- gmtime
- _gmtime32
- _gmtime64
helpviewer_keywords:
- gmtime32 function
- _gmtime64 function
- gmtime function
- time functions
- _gmtime32 function
- gmtime64 function
- time structure conversion
ms.assetid: 315501f3-477e-475d-a414-ef100ee0db27
ms.openlocfilehash: 4f32da5920a0cb892619195207d6501a4b1fd874
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50480000"
---
# <a name="gmtime-gmtime32-gmtime64"></a>gmtime, _gmtime32, _gmtime64

Convertit un **time_t** temps valeur pour un **tm** structure. Des versions plus sécurisées de ces fonctions sont disponibles. Consultez [gmtime_s, _gmtime32_s, _gmtime64_s](gmtime-s-gmtime32-s-gmtime64-s.md).

## <a name="syntax"></a>Syntaxe

```C
struct tm *gmtime( const time_t *sourceTime );
struct tm *_gmtime32( const __time32_t *sourceTime );
struct tm *_gmtime64( const __time64_t *sourceTime );
```

### <a name="parameters"></a>Paramètres

*sourceTime*<br/>
Pointeur désignant la valeur de temps stockée. Le temps est représenté sous forme de secondes écoulées depuis le 1er janvier 1970 minuit (00:00:00), temps universel coordonné (UTC).

## <a name="return-value"></a>Valeur de retour

Pointeur désignant une structure de type [tm](../../c-runtime-library/standard-types.md). Les champs de la structure retournée doit contenir la valeur évaluée de la *sourceTime* argument en UTC plutôt qu’en heure locale. Chacun des champs de structure est de type **int**, comme suit :

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
|**tm_isdst**|Toujours 0 pour **gmtime**.|

Les versions 32 bits et 64 bits de **gmtime**, [mktime](mktime-mktime32-mktime64.md), [mkgmtime](mkgmtime-mkgmtime32-mkgmtime64.md), et [localtime](localtime-localtime32-localtime64.md) utilisent toutes un commun **tm**  structure par thread pour la conversion. Chaque appel à une de ces fonctions détruit le résultat de tout appel précédent. Si *sourceTime* représente une date antérieure au 1er janvier 1970 à minuit **gmtime** retourne **NULL**. Aucun retour d'erreur.

**_gmtime64**, qui utilise le **__time64_t** structure, permet des dates exprimer à 23:59:59 le 31 décembre 3000, UTC, tandis que **_gmtime32** représentent uniquement les dates à 23:59:59 Le 18 janvier 2038, UTC. Le 1er janvier 1970 à minuit est la limite inférieure de la plage de dates pour les deux fonctions.

**gmtime** est une fonction inline qui prend la valeur **_gmtime64**, et **time_t** équivaut à **__time64_t** , sauf si **_USE_32BIT_TIME_ T** est défini. Si vous devez forcer le compilateur à interpréter **time_t** l’ancien 32-bit **time_t**, vous pouvez définir **_USE_32BIT_TIME_T**, mais ce faisant **gmtime** pour être inline à **_gmtime32** et **time_t** soit définie comme **__time32_t**. Nous vous recommandons de ne pas effectuer cette opération, car elle n’est pas autorisée sur les plateformes 64 bits et, dans tous les cas, votre application risque d’échouer après le 18 janvier 2038.

Ces fonctions valident leurs paramètres. Si *sourceTime* est un pointeur null, ou si le *sourceTime* valeur est négative, ces fonctions appellent un gestionnaire de paramètre non valide, comme décrit dans [Validation de paramètre](../../c-runtime-library/parameter-validation.md) . Si l’exécution est autorisée à se poursuivre, les fonctions retournent **NULL** et définissez **errno** à **EINVAL**.

## <a name="remarks"></a>Notes

Le **_gmtime32** fonction décompose le *sourceTime* valeur et le stocke dans une structure allouée de manière statique de type **tm**, défini dans le temps. H. La valeur de *sourceTime* est généralement obtenue à partir d’un appel à la [temps](time-time32-time64.md) (fonction).

> [!NOTE]
> Dans la plupart des cas, l’environnement cible tente de déterminer si l’heure d’été est en vigueur. La bibliothèque runtime C suppose que les règles de calcul de l’heure d’été utilisées sont celles des États-Unis.

## <a name="requirements"></a>Configuration requise

|Routine|En-tête C requis|En-tête C++ requis|
|-------------|---------------------|-|
|**gmtime**, **_gmtime32**, **_gmtime64**|\<time.h>|\<CTime > ou \<time.h >|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

```C
// crt_gmtime.c
// compile with: /W3
// This program uses _gmtime64 to convert a long-
// integer representation of coordinated universal time
// to a structure named newtime, then uses asctime to
// convert this structure to an output string.

#include <time.h>
#include <stdio.h>

int main( void )
{
   struct tm *newtime;
   __int64 ltime;
   char buff[80];

   _time64( &ltime );

   // Obtain coordinated universal time:
   newtime = _gmtime64( &ltime ); // C4996
   // Note: _gmtime64 is deprecated; consider using _gmtime64_s
   asctime_s( buff, sizeof(buff), newtime );
   printf( "Coordinated universal time is %s\n", buff );
}
```

```Output
Coordinated universal time is Tue Feb 12 23:11:31 2002
```

## <a name="see-also"></a>Voir aussi

[Gestion du temps](../../c-runtime-library/time-management.md)<br/>
[asctime, _wasctime](asctime-wasctime.md)<br/>
[ctime, _ctime32, _ctime64, _wctime, _wctime32, _wctime64](ctime-ctime32-ctime64-wctime-wctime32-wctime64.md)<br/>
[_ftime, _ftime32, _ftime64](ftime-ftime32-ftime64.md)<br/>
[gmtime_s, _gmtime32_s, _gmtime64_s](gmtime-s-gmtime32-s-gmtime64-s.md)<br/>
[localtime, _localtime32, _localtime64](localtime-localtime32-localtime64.md)<br/>
[_mkgmtime, _mkgmtime32, _mkgmtime64](mkgmtime-mkgmtime32-mkgmtime64.md)<br/>
[mktime, _mktime32, _mktime64](mktime-mktime32-mktime64.md)<br/>
[time, _time32, _time64](time-time32-time64.md)<br/>
