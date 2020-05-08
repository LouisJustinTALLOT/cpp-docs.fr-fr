---
title: _ftime, _ftime32, _ftime64
ms.date: 4/2/2020
api_name:
- _ftime64
- _ftime
- _ftime32
- _o__ftime32
- _o__ftime64
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
- _ftime32
- _ftime
- _ftime64
- ftime64
- ftime
- ftime32
helpviewer_keywords:
- ftime64 function
- _ftime64 function
- current time
- _ftime function
- ftime function
- _ftime32 function
- ftime32 function
- time, getting current
ms.assetid: 96bc464c-3bcd-41d5-a212-8bbd836b814a
ms.openlocfilehash: a0d012c89058209832d1e78867e89b4bd87bf226
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2020
ms.locfileid: "82909937"
---
# <a name="_ftime-_ftime32-_ftime64"></a>_ftime, _ftime32, _ftime64

Obtenir l’heure actuelle. Des versions plus sécurisées de ces fonctions sont disponibles ; consultez [_ftime_s, _ftime32_s, _ftime64_s](ftime-s-ftime32-s-ftime64-s.md).

## <a name="syntax"></a>Syntaxe

```C
void _ftime( struct _timeb *timeptr );
void _ftime32( struct __timeb32 *timeptr );
void _ftime64( struct __timeb64 *timeptr );
```

### <a name="parameters"></a>Paramètres

*timeptr*<br/>
Pointeur vers une structure **_timeb**, **__timeb32**ou **__timeb64** .

## <a name="remarks"></a>Notes 

La fonction **_ftime** obtient l’heure locale actuelle et la stocke dans la structure vers laquelle pointe *timeptr*. Les structures **_timeb**, **__timeb32**et **__timeb64** sont définies dans \<sys\\timeb. h>. Elles contiennent quatre champs, qui sont présentés dans le tableau suivant.

|Champ|Description|
|-|-|
|**dstflag**|Valeur non nulle si l’heure d’été est en vigueur pour le fuseau horaire local. (Consultez [_tzset](tzset.md) pour une explication de la détermination de l’heure d’été.)|
|**millitm**|Fraction de seconde en millisecondes.|
|**time**|Durée en secondes depuis le 1er janvier 1970, minuit (00:00:00), temps universel (UTC).|
|**horaires**|Différence en minutes, en direction de l’ouest, entre les heures UTC et locale. La valeur **TimeZone** est définie à partir de la valeur de la variable globale **_timezone** (consultez **_tzset**).|

La fonction **_ftime64** , qui utilise la structure **__timeb64** , permet d’exprimer les dates de création de fichiers jusqu’au 31 décembre 3000 à 23:59:59, heure UTC ; tandis que **_ftime32** représente uniquement les dates jusqu' 23:59:59 au 18 janvier 2038, heure UTC. Le 1er janvier 1970 à minuit est la limite inférieure de la plage de dates pour toutes ces fonctions.

La fonction **_ftime** équivaut à **_ftime64**et **_timeb** contient une heure de 64 bits, sauf si **_USE_32BIT_TIME_T** est défini, auquel cas l’ancien comportement est appliqué. **_ftime** utilise une heure de 32 bits et **_timeb** contient une heure de 32 bits.

**_ftime** valide ses paramètres. Si un pointeur null est passé en tant que *timeptr*, la fonction appelle le gestionnaire de paramètre non valide, comme décrit dans [validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, la fonction affecte à **errno** la valeur **EINVAL**.

Par défaut, l’état global de cette fonction est limité à l’application. Pour modifier cette valeur, consultez [état global dans le CRT](../global-state.md).

## <a name="requirements"></a>Spécifications

|Function|En-tête requis|
|--------------|---------------------|
|**_ftime**|\<sys/types.h> et \<sys/timeb.h>|
|**_ftime32**|\<sys/types.h> et \<sys/timeb.h>|
|**_ftime64**|\<sys/types.h> et \<sys/timeb.h>|

Pour plus d’informations sur la compatibilité, consultez [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

```C
// crt_ftime.c
// compile with: /W3
// This program uses _ftime to obtain the current
// time and then stores this time in timebuffer.

#include <stdio.h>
#include <sys/timeb.h>
#include <time.h>

int main( void )
{
   struct _timeb timebuffer;
   char timeline[26];
   errno_t err;
   time_t time1;
   unsigned short millitm1;
   short timezone1;
   short dstflag1;

   _ftime( &timebuffer ); // C4996
   // Note: _ftime is deprecated; consider using _ftime_s instead

   time1 = timebuffer.time;
   millitm1 = timebuffer.millitm;
   timezone1 = timebuffer.timezone;
   dstflag1 = timebuffer.dstflag;

   printf( "Seconds since midnight, January 1, 1970 (UTC): %I64d\n",
   time1);
   printf( "Milliseconds: %d\n", millitm1);
   printf( "Minutes between UTC and local time: %d\n", timezone1);
   printf( "Daylight savings time flag (1 means Daylight time is in "
           "effect): %d\n", dstflag1);

   err = ctime_s( timeline, 26, & ( timebuffer.time ) );
   if (err)
   {
       printf("Invalid argument to ctime_s. ");
   }
   printf( "The time is %.19s.%hu %s", timeline, timebuffer.millitm,
           &timeline[20] );
}
```

```Output
Seconds since midnight, January 1, 1970 (UTC): 1051553334
Milliseconds: 230
Minutes between UTC and local time: 480
Daylight savings time flag (1 means Daylight time is in effect): 1
The time is Mon Apr 28 11:08:54.230 2003
```

## <a name="see-also"></a>Voir aussi

[Gestion du temps](../../c-runtime-library/time-management.md)<br/>
[asctime, _wasctime](asctime-wasctime.md)<br/>
[ctime, _ctime32, _ctime64, _wctime, _wctime32, _wctime64](ctime-ctime32-ctime64-wctime-wctime32-wctime64.md)<br/>
[gmtime, _gmtime32, _gmtime64](gmtime-gmtime32-gmtime64.md)<br/>
[localtime, _localtime32, _localtime64](localtime-localtime32-localtime64.md)<br/>
[time, _time32, _time64](time-time32-time64.md)<br/>
