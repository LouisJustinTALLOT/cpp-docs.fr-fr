---
title: gmtime, _gmtime32, _gmtime64
ms.date: 4/2/2020
api_name:
- _gmtime32
- gmtime
- _gmtime64
- _o__gmtime32
- _o__gmtime64
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
ms.openlocfilehash: afa46e583437ebace8edd3a54a6d85e61e02854c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81344098"
---
# <a name="gmtime-_gmtime32-_gmtime64"></a>gmtime, _gmtime32, _gmtime64

Convertit une valeur **temporelle time_t** en une structure **tm.** Des versions plus sécurisées de ces fonctions sont disponibles. Consultez [gmtime_s, _gmtime32_s, _gmtime64_s](gmtime-s-gmtime32-s-gmtime64-s.md).

## <a name="syntax"></a>Syntaxe

```C
struct tm *gmtime( const time_t *sourceTime );
struct tm *_gmtime32( const __time32_t *sourceTime );
struct tm *_gmtime64( const __time64_t *sourceTime );
```

### <a name="parameters"></a>Paramètres

*sourceTime sourceTime source*<br/>
Pointeur désignant la valeur de temps stockée. Le temps est représenté sous forme de secondes écoulées depuis le 1er janvier 1970 minuit (00:00:00), temps universel coordonné (UTC).

## <a name="return-value"></a>Valeur de retour

Pointeur désignant une structure de type [tm](../../c-runtime-library/standard-types.md). Les champs de la structure retournée détiennent la valeur évaluée de l’argument *sourceTime* dans UTC plutôt qu’en heure locale. Chacun des champs de structure est de type **int**, comme suit:

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
|**tm_isdst**|Toujours 0 pour **gmtime**.|

Les versions 32-bit et 64 bits de **gmtime**, [mktime](mktime-mktime32-mktime64.md), [mkgmtime](mkgmtime-mkgmtime32-mkgmtime64.md), et [local](localtime-localtime32-localtime64.md) tout utiliser une structure **tm** commune par fil pour la conversion. Chaque appel à une de ces fonctions détruit le résultat de tout appel précédent. Si *sourceTime* représente une date avant minuit, le 1er janvier 1970, **gmtime** retourne **NULL**. Aucun retour d'erreur.

**_gmtime64**, qui utilise la structure **__time64_t,** permet d’exprimer les dates jusqu’à 23:59:59, Décembre 31, 3000, UTC, tandis que **_gmtime32** ne représentent les dates jusqu’à 23:59:59 Janvier 18, 2038, UTC. Le 1er janvier 1970 à minuit est la limite inférieure de la plage de dates pour les deux fonctions.

**gmtime** est une fonction inline qui évalue à **_gmtime64**, et **time_t** est équivalent à **__time64_t** à moins **que _USE_32BIT_TIME_T** est définie. Si vous devez forcer le compilateur à interpréter **time_t** comme l’ancien time_t 32 **bits**, vous pouvez définir **_USE_32BIT_TIME_T**, mais ce faisant provoque **gmtime** d’être en ligne de **_gmtime32** et **time_t** d’être défini comme **__time32_t**. Nous vous recommandons de ne pas effectuer cette opération, car elle n’est pas autorisée sur les plateformes 64 bits et, dans tous les cas, votre application risque d’échouer après le 18 janvier 2038.

Ces fonctions valident leurs paramètres. Si *sourceTime* est un pointeur nul, ou si la valeur *sourceTime* est négative, ces fonctions invoquent un gestionnaire de paramètres invalide, tel que décrit dans [La validation de paramètres](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, les fonctions retournent **NULL** et **placent errno** à **EINVAL**.

## <a name="remarks"></a>Notes

La fonction **_gmtime32** décompose la valeur *sourceTime* et la stocke dans une structure statiquement attribuée de type **tm**, définie dans TIME. H. La valeur de *sourceTime* est généralement obtenue à partir d’un appel à la fonction [de temps.](time-time32-time64.md)

> [!NOTE]
> Dans la plupart des cas, l’environnement cible tente de déterminer si l’heure d’été est en vigueur. La bibliothèque runtime C suppose que les règles de calcul de l’heure d’été utilisées sont celles des États-Unis.

Par défaut, l’état global de cette fonction est étendue à l’application. Pour changer cela, voir [Global State dans le CRT](../global-state.md).

## <a name="requirements"></a>Spécifications

|Routine|En-tête C requis|En-tête C++ requis|
|-------------|---------------------|-|
|**gmtime**, **_gmtime32**, **_gmtime64**|\<time.h>|\<ctime> ou \<time.h>|

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
