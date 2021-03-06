---
description: 'En savoir plus sur les éléments suivants : _ftime_s, _ftime32_s _ftime64_s'
title: _ftime_s, _ftime32_s, _ftime64_s
ms.date: 4/2/2020
api_name:
- _ftime_s
- _ftime64_s
- _ftime32_s
- _o__ftime32_s
- _o__ftime64_s
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
- _ftime_s
- _ftime64_s
- ftime_s
- _ftime32_s
- ftime32_s
- ftime64_s
helpviewer_keywords:
- ftime32_s function
- ftime_s function
- _ftime64_s function
- current time
- ftime64_s function
- time, getting current
- _ftime_s function
- _ftime32_s function
ms.assetid: d03080d9-a520-45be-aa65-504bdb197e8b
ms.openlocfilehash: 97b709f014c463022e18b209e374afd6c18c20e8
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97334191"
---
# <a name="_ftime_s-_ftime32_s-_ftime64_s"></a>_ftime_s, _ftime32_s, _ftime64_s

Obtient l’heure actuelle. Ces versions de [_ftime, _ftime32, _ftime64](ftime-ftime32-ftime64.md) intègrent les améliorations de sécurité décrites dans [Fonctionnalités de sécurité dans le CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Syntaxe

```C
errno_t _ftime_s( struct _timeb *timeptr );
errno_t _ftime32_s( struct __timeb32 *timeptr );
errno_t _ftime64_s( struct __timeb64 *timeptr );
```

### <a name="parameters"></a>Paramètres

*timeptr*<br/>
Pointeur vers une structure **_timeb**, **__timeb32** ou **__timeb64** .

## <a name="return-value"></a>Valeur renvoyée

Zéro si l'opération a réussi, un code d'erreur en cas d'échec. Si *timeptr* a la valeur **null**, la valeur de retour est **EINVAL**.

## <a name="remarks"></a>Notes

La fonction **_ftime_s** obtient l’heure locale actuelle et la stocke dans la structure vers laquelle pointe *timeptr*. Les structures **_timeb**, **__timeb32** et **__timeb64** sont définies dans SYS\Timeb.h. Elles contiennent quatre champs, qui sont présentés dans le tableau suivant.

|Champ|Description|
|-|-|
|**dstflag**|Valeur non nulle si l’heure d’été est en vigueur pour le fuseau horaire local. (Consultez [_tzset](tzset.md) pour une explication de la détermination de l’heure d’été.)|
|**millitm**|Fraction de seconde en millisecondes.|
|**time**|Durée en secondes depuis le 1er janvier 1970, minuit (00:00:00), temps universel (UTC).|
|**horaires**|Différence en minutes, en direction de l’ouest, entre les heures UTC et locale. La valeur **TimeZone** est définie à partir de la valeur de la variable globale **_timezone** (consultez **_tzset**).|

La fonction **_ftime64_s** , qui utilise la structure **__timeb64** , permet d’exprimer les dates de création de fichiers jusqu’au 31 décembre 3000 à 23:59:59, heure UTC ; tandis que **_ftime32_s** représente uniquement les dates jusqu' 23:59:59 au 18 janvier 2038, heure UTC. Le 1er janvier 1970 à minuit est la limite inférieure de la plage de dates pour toutes ces fonctions.

La fonction **_ftime_s** équivaut à **_ftime64_s** et **_timeb** contient une heure de 64 bits, sauf si **_USE_32BIT_TIME_T** est défini, auquel cas l’ancien comportement est appliqué. **_ftime_s** utilise une heure de 32 bits et **_timeb** contient une heure de 32 bits.

**_ftime_s** valide ses paramètres. Si un pointeur null est passé en tant que *timeptr*, la fonction appelle le gestionnaire de paramètre non valide, comme décrit dans [validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, la fonction affecte à **errno** la valeur **EINVAL**.

Par défaut, l’état global de cette fonction est limité à l’application. Pour modifier cette valeur, consultez [état global dans le CRT](../global-state.md).

## <a name="requirements"></a>Spécifications

|Fonction|En-tête requis|
|--------------|---------------------|
|**_ftime_s**|\<sys/types.h> et \<sys/timeb.h>|
|**_ftime32_s**|\<sys/types.h> et \<sys/timeb.h>|
|**_ftime64_s**|\<sys/types.h> et \<sys/timeb.h>|

Pour plus d’informations sur la compatibilité, consultez [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Bibliothèques

Toutes les versions des [bibliothèques Runtime C](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a>Exemple

```C
// crt_ftime64_s.c
// This program uses _ftime64_s to obtain the current
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

   _ftime64_s( &timebuffer );

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
