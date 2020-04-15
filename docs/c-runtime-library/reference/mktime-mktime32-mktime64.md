---
title: mktime, _mktime32, _mktime64
ms.date: 4/2/2020
api_name:
- _mktime32
- mktime
- _mktime64
- _o__mktime32
- _o__mktime64
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
- mktime
- _mktime64
helpviewer_keywords:
- _mktime32 function
- mktime function
- time functions
- mktime64 function
- converting times
- mktime32 function
- _mktime64 function
- time, converting
ms.assetid: 284ed5d4-7064-48a2-bd50-15effdae32cf
ms.openlocfilehash: b0981f33d70945083eacd28eb7517e80b3f2539f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81338701"
---
# <a name="mktime-_mktime32-_mktime64"></a>mktime, _mktime32, _mktime64

Convertit l'heure locale en valeur de calendrier.

## <a name="syntax"></a>Syntaxe

```C
time_t mktime(
   struct tm *timeptr
);
__time32_t _mktime32(
   struct tm *timeptr
);
__time64_t _mktime64(
   struct tm *timeptr
);
```

### <a name="parameters"></a>Paramètres

*timeptr*<br/>
Pointeur désignant la structure de temps ; consultez [asctime](asctime-wasctime.md).

## <a name="return-value"></a>Valeur de retour

**_mktime32** renvoie le temps de calendrier spécifié codé comme une valeur de type [time_t](../../c-runtime-library/standard-types.md). Si *timeptr* fait référence à une date avant minuit, le 1er janvier 1970, ou si l’heure du calendrier ne peut pas être représentée, **_mktime32** renvoie -1 pour taper **time_t**. Lors de **l’utilisation de _mktime32** et si *timeptr* fait référence à une date après 23:59:59 Janvier 18, 2038, Coordinated Universal Time (UTC), il sera de retour -1 casting pour taper **time_t**.

**_mktime64** retournera -1 casting pour taper **__time64_t** si *timeptr* fait référence à une date après 23:59:59, Décembre 31, 3000, UTC.

## <a name="remarks"></a>Notes

Les fonctions **mktime**, **_mktime32** et **_mktime64** convertissent la structure de temps fournie (peut-être incomplète) pointée par *timeptr* dans une structure entièrement définie avec des valeurs normalisées, puis la convertit en une valeur de temps de calendrier **time_t.** L’heure convertie a le même encodage que les valeurs retournées par la fonction [time](time-time32-time64.md). Les valeurs originales des composants **tm_wday** et **tm_yday** de la structure *du timeptr* sont ignorées, et les valeurs originales des autres composants ne sont pas limitées à leurs plages normales.

**mktime** est une fonction inline qui est équivalente à **_mktime64**, **à** moins _USE_32BIT_TIME_T est définie, auquel cas il est équivalent à **_mktime32**.

Après un ajustement à UTC, **_mktime32** poignées date de minuit, Janvier 1, 1970, à 23:59:59 Janvier 18, 2038, UTC. **_mktime64** poignées date de minuit, janvier 1970 à 23:59:59, Décembre 31, 3000. Cet ajustement peut faire revenir ces fonctions -1 (pour **time_t,** **__time32_t** ou **__time64_t)** même si la date que vous spécifiez est à portée. Par exemple, si vous êtes au Caire en Égypte, où le décalage horaire est de +2 heures par rapport à l’heure UTC, deux heures sont d’abord soustraites de la date que vous spécifiez dans *timeptr*, ce qui risque de faire sortir votre date de la plage.

Ces fonctions peuvent être utilisées pour valider et compléter une structure tm. En cas de succès, ces fonctions fixent les valeurs de **tm_wday** et **tm_yday** le cas échéant et définissez les autres composants pour représenter le temps de calendrier spécifié, mais avec leurs valeurs forcées aux plages normales. La valeur finale de **tm_mday** n’est pas définie tant que **tm_mon** et **tm_year** ne sont pas déterminées. Lorsque vous spécifiez un temps de structure **tm,** définissez le **champ tm_isdst** pour :

- zéro (0) pour indiquer que l'heure d'hiver est active ;

- une valeur supérieure à 0 pour indiquer que l'heure d'été est active ;

- une valeur inférieure à zéro pour que le code de la bibliothèque Runtime C calcule si l'heure active est l'heure d'hiver ou l'heure d'été.

La bibliothèque Runtime C détermine le comportement d’heure d’été à partir de la variable d’environnement [TZ](tzset.md). Si **TZ** n’est pas défini, l’appel Win32 API [GetTimeZoneInformation](/windows/win32/api/timezoneapi/nf-timezoneapi-gettimezoneinformation) est utilisé pour obtenir les informations d’heure d’été du système d’exploitation. En cas d'échec, la bibliothèque part du principe que les règles de calcul de l'heure d'été sont celles des États-Unis. **tm_isdst** est un champ requis. S'il n'est pas défini, sa valeur est indéfinie et la valeur de retour de ces fonctions est imprévisible. Si *timeptr* pointe vers une structure **de tm** retournée par un appel précédent à [asctime](asctime-wasctime.md), [gmtime](gmtime-gmtime32-gmtime64.md), ou [localtime](localtime-localtime32-localtime64.md) (ou variantes de ces fonctions), le champ **tm_isdst** contient la valeur correcte.

Notez que **gmtime** et **localtime** (et **_gmtime32**, **_gmtime64**, **_localtime32**, et **_localtime64**) utiliser un tampon unique par thread pour la conversion. Si vous fournissez ce tampon à **mktime**, **_mktime32** ou **_mktime64**, le contenu précédent sont détruits.

Ces fonctions valident leur paramètre. Si *timeptr* est un pointeur Null, le gestionnaire de paramètres non valides est appelé, comme décrit dans [Validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, les fonctions retournent -1 et **placent errno** à **EINVAL**.

Par défaut, l’état global de cette fonction est étendue à l’application. Pour changer cela, voir [Global State dans le CRT](../global-state.md).

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**mktime**|\<time.h>|
|**_mktime32**|\<time.h>|
|**_mktime64**|\<time.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Bibliothèques

Toutes les versions des [bibliothèques Runtime C](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a>Exemple

```C
// crt_mktime.c
/* The example takes a number of days
* as input and returns the time, the current
* date, and the specified number of days.
*/

#include <time.h>
#include <stdio.h>

int main( void )
{
   struct tm  when;
   __time64_t now, result;
   int        days;
   char       buff[80];

   time( &now );
   _localtime64_s( &when, &now );
   asctime_s( buff, sizeof(buff), &when );
   printf( "Current time is %s\n", buff );
   days = 20;
   when.tm_mday = when.tm_mday + days;
   if( (result = mktime( &when )) != (time_t)-1 ) {
      asctime_s( buff, sizeof(buff), &when );
      printf( "In %d days the time will be %s\n", days, buff );
   } else
      perror( "mktime failed" );
}
```

### <a name="sample-output"></a>Exemple de sortie

```Output
Current time is Fri Apr 25 13:34:07 2003

In 20 days the time will be Thu May 15 13:34:07 2003
```

## <a name="see-also"></a>Voir aussi

[Gestion du temps](../../c-runtime-library/time-management.md)<br/>
[asctime, _wasctime](asctime-wasctime.md)<br/>
[gmtime, _gmtime32, _gmtime64](gmtime-gmtime32-gmtime64.md)<br/>
[localtime, _localtime32, _localtime64](localtime-localtime32-localtime64.md)<br/>
[_mkgmtime, _mkgmtime32, _mkgmtime64](mkgmtime-mkgmtime32-mkgmtime64.md)<br/>
[time, _time32, _time64](time-time32-time64.md)<br/>
