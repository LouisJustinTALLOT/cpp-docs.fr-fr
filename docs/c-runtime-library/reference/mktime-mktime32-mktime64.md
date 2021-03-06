---
description: 'En savoir plus sur : mktime, _mktime32, _mktime64'
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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: aebb12324de5a18dfac6ab84b3b7b2c3da15a2ad
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97256417"
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

## <a name="return-value"></a>Valeur renvoyée

**_mktime32** retourne l’heure de calendrier spécifiée encodée sous la forme d’une valeur de type [time_t](../../c-runtime-library/standard-types.md). Si *timeptr* référence une date antérieure au 1er janvier 1970, ou si l’heure de calendrier ne peut pas être représentée, **_mktime32** retourne-1 casté en type **time_t**. Lors de l’utilisation de **_mktime32** et si *timeptr* fait référence à une date 23:59:59 postérieure au 18 janvier 2038, au temps universel coordonné (UTC, Coordinated Universal Time), elle retourne-1 casté en type **time_t**.

**_mktime64** retourne-1 cast en type **__time64_t** si *timeptr* fait référence à une date 23:59:59 postérieure au 31 décembre 3000, UTC.

## <a name="remarks"></a>Notes

Les fonctions **mktime**, **_mktime32** et **_mktime64** convertissent la structure de temps fournie (peut-être incomplète) pointée par *timeptr* dans une structure entièrement définie avec des valeurs normalisées, puis les convertit en **time_t** valeur d’heure calendaire. L’heure convertie a le même encodage que les valeurs retournées par la fonction [time](time-time32-time64.md). Les valeurs d’origine des composants **tm_wday** et **tm_yday** de la structure *timeptr* sont ignorées, et les valeurs d’origine des autres composants ne sont pas limitées à leurs plages normales.

**mktime** est une fonction inline qui est équivalente à **_mktime64**, à moins que **_USE_32BIT_TIME_T** soit définie, auquel cas elle équivaut à **_mktime32**.

Après un ajustement à l’heure UTC, **_mktime32** gère les dates comprises entre le 1er janvier 1970 et le 23:59:59 le 18 janvier 2038, heure UTC. **_mktime64** gère les dates comprises entre le 1er janvier 1970 et 23:59:59, le 31 décembre 3000. Cet ajustement peut amener ces fonctions à retourner-1 (cast en **time_t**, **__time32_t** ou **__time64_t**) même si la date que vous spécifiez est comprise dans la plage. Par exemple, si vous êtes au Caire en Égypte, où le décalage horaire est de +2 heures par rapport à l’heure UTC, deux heures sont d’abord soustraites de la date que vous spécifiez dans *timeptr*, ce qui risque de faire sortir votre date de la plage.

Ces fonctions peuvent être utilisées pour valider et compléter une structure tm. En cas de réussite, ces fonctions définissent les valeurs de **tm_wday** et **tm_yday** le cas échéant et définissent les autres composants pour représenter l’heure de calendrier spécifiée, mais avec leurs valeurs imposées aux plages normales. La valeur finale de **tm_mday** n’est pas définie tant que **tm_mon** et **tm_year** ne sont pas déterminés. Lorsque vous spécifiez une durée de structure **TM** , définissez le champ **tm_isdst** sur :

- zéro (0) pour indiquer que l'heure d'hiver est active ;

- une valeur supérieure à 0 pour indiquer que l'heure d'été est active ;

- une valeur inférieure à zéro pour que le code de la bibliothèque Runtime C calcule si l'heure active est l'heure d'hiver ou l'heure d'été.

La bibliothèque Runtime C détermine le comportement d’heure d’été à partir de la variable d’environnement [TZ](tzset.md). Si **TZ** n’est pas défini, l’appel de l’API Win32 [GetTimeZoneInformation](/windows/win32/api/timezoneapi/nf-timezoneapi-gettimezoneinformation) est utilisé pour récupérer les informations d’heure d’été à partir du système d’exploitation. En cas d'échec, la bibliothèque part du principe que les règles de calcul de l'heure d'été sont celles des États-Unis. **tm_isdst** est un champ obligatoire. S'il n'est pas défini, sa valeur est indéfinie et la valeur de retour de ces fonctions est imprévisible. Si *timeptr* pointe vers une structure **TM** retournée par un appel précédent [à asctime](asctime-wasctime.md), [gmtime](gmtime-gmtime32-gmtime64.md)ou [localtime](localtime-localtime32-localtime64.md) (ou des variantes de ces fonctions), le champ **tm_isdst** contient la valeur correcte.

Notez que **gmtime** et **localtime** (et **_gmtime32**, **_gmtime64**, **_localtime32** et **_localtime64**) utilisent une seule mémoire tampon par thread pour la conversion. Si vous fournissez cette mémoire tampon à **mktime**, **_mktime32** ou **_mktime64**, le contenu précédent est détruit.

Ces fonctions valident leur paramètre. Si *timeptr* est un pointeur Null, le gestionnaire de paramètres non valides est appelé, comme décrit dans [Validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, les fonctions retournent-1 et attribuent à **errno** la valeur **EINVAL**.

Par défaut, l’état global de cette fonction est limité à l’application. Pour modifier cette valeur, consultez [état global dans le CRT](../global-state.md).

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
