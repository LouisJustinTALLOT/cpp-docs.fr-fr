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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: 16f4315837873c8d78065ea97a11188bdddedbed
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2020
ms.locfileid: "82916238"
---
# <a name="gmtime-_gmtime32-_gmtime64"></a>gmtime, _gmtime32, _gmtime64

Convertit une valeur de temps de **time_t** en une structure de **TM** . Des versions plus sécurisées de ces fonctions sont disponibles. Consultez [gmtime_s, _gmtime32_s, _gmtime64_s](gmtime-s-gmtime32-s-gmtime64-s.md).

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

Pointeur désignant une structure de type [tm](../../c-runtime-library/standard-types.md). Les champs de la structure retournée contiennent la valeur évaluée de l’argument *sourceTime* en UTC plutôt qu’en heure locale. Chacun des champs de structure est de type **int**, comme suit :

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
|**tm_isdst**|Toujours 0 pour **gmtime**.|

Les versions 32 bits et 64 bits de **gmtime**, [mktime](mktime-mktime32-mktime64.md), [mkgmtime](mkgmtime-mkgmtime32-mkgmtime64.md)et [localtime](localtime-localtime32-localtime64.md) utilisent toutes les deux une structure de **TM** commune par thread pour la conversion. Chaque appel à une de ces fonctions détruit le résultat de tout appel précédent. Si *sourceTime* représente une date antérieure au 1er janvier 1970, **gmtime** retourne la **valeur null**. Aucun retour d'erreur.

**_gmtime64**, qui utilise la structure **__time64_t** , permet d’exprimer les dates jusqu’au 31 décembre 3000 à 23:59:59, tandis que les **_gmtime32** représentent uniquement les dates 23:59:59 jusqu’au 18 janvier 2038, heure UTC. Le 1er janvier 1970 à minuit est la limite inférieure de la plage de dates pour les deux fonctions.

**gmtime** est une fonction inline qui prend la valeur **_gmtime64**et **time_t** équivaut à **__time64_t** , sauf si **_USE_32BIT_TIME_T** est défini. Si vous devez forcer le compilateur à interpréter les **time_t** comme l’ancien **time_t**32 bits, vous pouvez définir **_USE_32BIT_TIME_T**, mais cela entraîne l’inversion de **gmtime** en ligne pour **_gmtime32** et **time_t** à définir en tant que **__time32_t**. Nous vous recommandons de ne pas effectuer cette opération, car elle n’est pas autorisée sur les plateformes 64 bits et, dans tous les cas, votre application risque d’échouer après le 18 janvier 2038.

Ces fonctions valident leurs paramètres. Si *sourceTime* est un pointeur null ou si la valeur *sourceTime* est négative, ces fonctions appellent un gestionnaire de paramètres non valides, comme décrit dans [validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, les fonctions retournent la **valeur null** et attribuent à **errno** la valeur **EINVAL**.

## <a name="remarks"></a>Notes 

La fonction **_gmtime32** décompose la valeur *sourceTime* et la stocke dans une structure allouée de manière statique de type **TM**, définie dans le temps. Manutention. La valeur de *sourceTime* est généralement obtenue à partir d’un appel à la fonction [Time](time-time32-time64.md) .

> [!NOTE]
> Dans la plupart des cas, l’environnement cible tente de déterminer si l’heure d’été est en vigueur. La bibliothèque runtime C suppose que les règles de calcul de l’heure d’été utilisées sont celles des États-Unis.

Par défaut, l’état global de cette fonction est limité à l’application. Pour modifier cette valeur, consultez [état global dans le CRT](../global-state.md).

## <a name="requirements"></a>Spécifications

|Routine|En-tête C requis|En-tête C++ requis|
|-------------|---------------------|-|
|**gmtime**, **_gmtime32**, **_gmtime64**|\<time.h>|\<CTime> ou \<Time. h>|

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
