---
title: gmtime_s, _gmtime32_s, _gmtime64_s
ms.date: 11/04/2016
apiname:
- _gmtime32_s
- gmtime_s
- _gmtime64_s
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
- _gmtime_s
- gmtime64_s
- gmtime32_s
- _gmtime64_s
- gmtime_s
- _gmtime32_s
helpviewer_keywords:
- gmtime_s function
- gmtime32_s function
- time functions
- gmtime64_s function
- _gmtime64_s function
- time structure conversion
- _gmtime_s function
- _gmtime32_s function
ms.assetid: 261c7df0-2b0c-44ba-ba61-cb83efaec60f
ms.openlocfilehash: 1d9bfc7858dbc718e0f6c07358c5ebcec546063e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50650006"
---
# <a name="gmtimes-gmtime32s-gmtime64s"></a>gmtime_s, _gmtime32_s, _gmtime64_s

Convertit une valeur d’heure en un **tm** structure. Ces versions de [_gmtime32, _gmtime64](gmtime-gmtime32-gmtime64.md) intègrent les améliorations de sécurité décrites dans [Fonctionnalités de sécurité dans le CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Syntaxe

```C
errno_t gmtime_s(
   struct tm* tmDest,
   const __time_t* sourceTime
);
errno_t _gmtime32_s(
   struct tm* tmDest,
   const __time32_t* sourceTime
);
errno_t _gmtime64_s(
   struct tm* tmDest,
   const __time64_t* sourceTime
);
```

### <a name="parameters"></a>Paramètres

*tmDest*<br/>
Pointeur vers un [tm](../../c-runtime-library/standard-types.md) structure. Les champs de la structure retournée doit contenir la valeur évaluée de la *minuteur* argument en UTC plutôt qu’en heure locale.

*sourceTime*<br/>
Pointeur désignant la valeur de temps stockée. Le temps est représenté sous forme de secondes écoulées depuis le 1er janvier 1970 minuit (00:00:00), temps universel coordonné (UTC).

## <a name="return-value"></a>Valeur de retour

Zéro si l’opération réussit. En cas d’échec, la valeur de retour est un code d’erreur. Les codes d’erreur sont définis dans Errno.h ; pour obtenir la liste de ces erreurs, consultez [errno](../../c-runtime-library/errno-constants.md).

### <a name="error-conditions"></a>Conditions d’erreur

|*tmDest*|*sourceTime*|Retourner|Valeur dans *tmDest*|
|-----------|------------|------------|--------------------|
|**NULL**|any|**EINVAL**|Non modifiée.|
|Pas **NULL** (pointe vers une mémoire valide)|**NULL**|**EINVAL**|Tous les champs définis sur -1.|
|Pas **NULL**|< 0|**EINVAL**|Tous les champs définis sur -1.|

Concernant les deux premières conditions d’erreur, le gestionnaire de paramètres non valides est appelé, comme décrit dans [Validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, ces fonctions définissent **errno** à **EINVAL** et retourner **EINVAL**.

## <a name="remarks"></a>Notes

Le **_gmtime32_s** fonction décompose le *sourceTime* valeur et le stocke dans une structure de type **tm**, définie dans Time.h. L’adresse de la structure est passée dans *tmDest*. La valeur de *sourceTime* est généralement obtenue à partir d’un appel à la [temps](time-time32-time64.md) (fonction).

> [!NOTE]
> L’environnement cible doit tenter de déterminer si l’heure d’été est en vigueur. La bibliothèque runtime C suppose que les règles de calcul de l’heure d’été sont celles des États-Unis.

Chacun des champs de structure est de type **int**, comme illustré dans le tableau suivant.

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
|**tm_isdst**|Toujours 0 pour **gmtime_s**.|

**_gmtime64_s**, qui utilise le **__time64_t** structure, permet d’exprimer à 23:59:59 le 31 décembre 3000, UTC ; les dates alors que **gmtime32_s** représentent uniquement les dates via 23:59:59 le 18 janvier 2038, UTC. Le 1er janvier 1970 à minuit est la limite inférieure de la plage de dates pour ces deux fonctions.

**gmtime_s** est une fonction inline qui prend la valeur **_gmtime64_s** et **time_t** équivaut à **__time64_t**. Si vous devez forcer le compilateur à interpréter **time_t** l’ancien 32-bit **time_t**, vous pouvez définir **_USE_32BIT_TIME_T**. Ainsi, **gmtime_s** pour être inline à **_gmtime32_s**. Cela n’est pas recommandé, car votre application peut échouer après le 18 janvier 2038 et cela n’est pas autorisé sur les plateformes 64 bits.

## <a name="requirements"></a>Configuration requise

|Routine|En-tête C requis|En-tête C++ requis|
|-------------|---------------------|-|
|**gmtime_s**|, **_gmtime32_s**, **_gmtime64_s**|\<time.h>|\<CTime > ou \<time.h >|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

```C
// crt_gmtime64_s.c
// This program uses _gmtime64_s to convert a 64-bit
// integer representation of coordinated universal time
// to a structure named newtime, then uses asctime_s to
// convert this structure to an output string.

#include <time.h>
#include <stdio.h>

int main( void )
{
   struct tm newtime;
   __int64 ltime;
   char buf[26];
   errno_t err;

   _time64( &ltime );

   // Obtain coordinated universal time:
   err = _gmtime64_s( &newtime, &ltime );
   if (err)
   {
      printf("Invalid Argument to _gmtime64_s.");
   }

   // Convert to an ASCII representation
   err = asctime_s(buf, 26, &newtime);
   if (err)
   {
      printf("Invalid Argument to asctime_s.");
   }

   printf( "Coordinated universal time is %s\n",
           buf );
}
```

```Output
Coordinated universal time is Fri Apr 25 20:12:33 2003
```

## <a name="see-also"></a>Voir aussi

[Gestion du temps](../../c-runtime-library/time-management.md)<br/>
[asctime_s, _wasctime_s](asctime-s-wasctime-s.md)<br/>
[ctime, _ctime32, _ctime64, _wctime, _wctime32, _wctime64](ctime-ctime32-ctime64-wctime-wctime32-wctime64.md)<br/>
[_ftime, _ftime32, _ftime64](ftime-ftime32-ftime64.md)<br/>
[gmtime, _gmtime32, _gmtime64](gmtime-gmtime32-gmtime64.md)<br/>
[localtime_s, _localtime32_s, _localtime64_s](localtime-s-localtime32-s-localtime64-s.md)<br/>
[_mkgmtime, _mkgmtime32, _mkgmtime64](mkgmtime-mkgmtime32-mkgmtime64.md)<br/>
[mktime, _mktime32, _mktime64](mktime-mktime32-mktime64.md)<br/>
[time, _time32, _time64](time-time32-time64.md)<br/>
