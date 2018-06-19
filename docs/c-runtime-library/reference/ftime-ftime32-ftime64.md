---
title: _ftime, _ftime32, _ftime64 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _ftime64
- _ftime
- _ftime32
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
- _ftime32
- _ftime
- _ftime64
- ftime64
- ftime
- ftime32
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9fd388e2963a0e28389fbf7cc2c4bd146ac9b61e
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32401436"
---
# <a name="ftime-ftime32-ftime64"></a>_ftime, _ftime32, _ftime64

Obtenir l’heure actuelle. Des versions plus sécurisées de ces fonctions sont disponibles ; consultez [_ftime_s, _ftime32_s, _ftime64_s](ftime-s-ftime32-s-ftime64-s.md).

## <a name="syntax"></a>Syntaxe

```C
void _ftime( struct _timeb *timeptr );
void _ftime32( struct __timeb32 *timeptr );
void _ftime64( struct __timeb64 *timeptr );
```

### <a name="parameters"></a>Paramètres

*timeptr* pointeur vers un **_timeb**, **__timeb32**, ou **__timeb64** structure.

## <a name="remarks"></a>Notes

Le **_ftime** fonction obtient l’heure locale actuelle et la stocke dans la structure vers laquelle pointée *timeptr*. Le **_timeb**, **__timeb32**, et **__timeb64** structures sont définies dans \<sys\\timeb.h >. Elles contiennent quatre champs, qui sont présentés dans le tableau suivant.

|Champ|Description|
|-|-|
|**dstflag**|Valeur non nulle si l’heure d’été est en vigueur pour le fuseau horaire local. (Consultez [_tzset](tzset.md) pour une explication de la détermination de l’heure d’été.)|
|**millitm**|Fraction de seconde en millisecondes.|
|**time**|Durée en secondes depuis le 1er janvier 1970, minuit (00:00:00), temps universel (UTC).|
|**timezone**|Différence en minutes, en direction de l’ouest, entre les heures UTC et locale. La valeur de **fuseau horaire** est définie à partir de la valeur de la variable globale **_timezone** (consultez **_tzset**).|

Le **_ftime64** (fonction), qui utilise le **__timeb64** de la structure, autorise les dates de création de fichiers d’exprimer des et 23:59:59, le 31 décembre 3000 UTC ; alors que **_ftime32**représente uniquement les dates et 23:59:59 18 janvier 2038, UTC. Le 1er janvier 1970 à minuit est la limite inférieure de la plage de dates pour toutes ces fonctions.

Le **_ftime** fonction est équivalente à **_ftime64**, et **_timeb** contient une heure 64 bits, sauf si **_USE_32BIT_TIME_T** est défini dans auquel cas l’ancien comportement est appliqué. **_ftime** utilise une heure 32 bits et **_timeb** contient une heure 32 bits.

**_ftime** valide ses paramètres. Si un pointeur null en tant que passé *timeptr*, la fonction appelle le Gestionnaire de paramètre non valide, comme décrit dans [Validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, la fonction définit **errno** à **EINVAL**.

## <a name="requirements"></a>Spécifications

|Fonction|En-tête requis|
|--------------|---------------------|
|**_ftime**|\<sys/types.h> et \<sys/timeb.h>|
|**_ftime32**|\<sys/types.h> et \<sys/timeb.h>|
|**_ftime64**|\<sys/types.h> et \<sys/timeb.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

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
