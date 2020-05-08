---
title: ctime, _ctime32, _ctime64, _wctime, _wctime32, _wctime64
ms.date: 4/2/2020
api_name:
- _ctime64
- _wctime32
- ctime
- _wctime64
- _ctime32
- _wctime
- _o__wctime32
- _o__wctime64
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
- _wctime64
- _ctime32
- _tctime
- _wctime
- _wctime32
- _tctime64
- _ctime64
- ctime
helpviewer_keywords:
- tctime64 function
- _ctime32 function
- ctime32 function
- _wctime function
- wctime64 function
- _tctime64 function
- _tctime32 function
- _ctime64 function
- _wctime64 function
- ctime function
- wctime32 function
- ctime64 function
- _wctime32 function
- _tctime function
- tctime32 function
- tctime function
- wctime function
- time, converting
ms.assetid: 2423de37-a35c-4f0a-a378-3116bc120a9d
ms.openlocfilehash: 7dc87f417db93f8ad0d90de1270c19997669fb7c
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2020
ms.locfileid: "82914839"
---
# <a name="ctime-_ctime32-_ctime64-_wctime-_wctime32-_wctime64"></a>ctime, _ctime32, _ctime64, _wctime, _wctime32, _wctime64

Convertissent une valeur de temps en une chaîne et ajustent les paramètres de fuseau horaire local. Des versions plus sécurisées de ces fonctions sont disponibles ; consultez [ctime_s, _ctime32_s, _ctime64_s, _wctime_s, _wctime32_s, _wctime64_s](ctime-s-ctime32-s-ctime64-s-wctime-s-wctime32-s-wctime64-s.md).

## <a name="syntax"></a>Syntaxe

```C
char *ctime( const time_t *sourceTime );
char *_ctime32( const __time32_t *sourceTime );
char *_ctime64( const __time64_t *sourceTime );
wchar_t *_wctime( const time_t *sourceTime );
wchar_t *_wctime32( const __time32_t *sourceTime );
wchar_t *_wctime64( const __time64_t *sourceTime );
```

### <a name="parameters"></a>Paramètres

*sourceTime*<br/>
Pointeur vers le temps stocké à convertir.

## <a name="return-value"></a>Valeur de retour

Pointeur désignant le résultat de chaîne de caractères. La **valeur null** est retournée si :

- *sourceTime* représente une date antérieure au 1er janvier 1970 à minuit, heure UTC.

- Si vous utilisez **_ctime32** ou **_Wctime32** et que *sourceTime* représente une date postérieure au 18 23:59:59 Janvier 2038, heure UTC.

- Si vous utilisez **_ctime64** ou **_wctime64** et *sourceTime* représente une date 23:59:59 postérieure au 31 décembre 3000, UTC.

**ctime** est une fonction inline qui prend la valeur **_ctime64** et **time_t** équivaut à **__time64_t**. Si vous devez forcer le compilateur à interpréter **time_t** comme l’ancien **time_t**32 bits, vous pouvez définir **_USE_32BIT_TIME_T**. En procédant ainsi, **ctime** est évalué à **_ctime32**. Cela n’est pas recommandé, car votre application peut échouer après le 18 janvier 2038 et cela n’est pas autorisé sur les plateformes 64 bits.

## <a name="remarks"></a>Notes 

La fonction **ctime** convertit une valeur de temps stockée en tant que valeur [time_t](../../c-runtime-library/standard-types.md) en une chaîne de caractères. La valeur *sourceTime* est généralement obtenue à partir d’un appel à [Time](time-time32-time64.md), qui retourne le nombre de secondes écoulées depuis minuit (00:00:00), le 1er janvier 1970, le temps universel coordonné (UTC). La chaîne de valeur de retour contient exactement 26 caractères et présente la forme suivante :

```Output
Wed Jan 02 02:03:55 1980\n\0
```

Une horloge de 24 heures est utilisée. Tous les champs ont une largeur constante. Le caractère de saut de ligne (« \n ») et le caractère null (« \0 ») occupent les deux dernières positions de la chaîne.

La chaîne de caractères convertie est également ajustée en fonction des paramètres de fuseau horaire local. Consultez les fonctions [Time](time-time32-time64.md), [_ftime](ftime-ftime32-ftime64.md)et [localtime](localtime-localtime32-localtime64.md) pour plus d’informations sur la configuration de l’heure locale et la fonction [_tzset](tzset.md) pour plus d’informations sur la définition de l’environnement de fuseau horaire et des variables globales.

Un appel à **ctime** modifie la mémoire tampon unique allouée statiquement utilisée par les fonctions **gmtime** et **localtime** . Chaque appel à une de ces routines détruit le résultat de l’appel précédent. **ctime** partage une mémoire tampon statique avec la fonction **asctime** . Ainsi, un appel à **ctime** détruit les résultats de tout appel précédent à **asctime**, **localtime**ou **gmtime**.

**_wctime** et **_wctime64** sont la version à caractères larges de **ctime** et **_ctime64**; retour d’un pointeur vers une chaîne de caractères larges. Sinon, **_ctime64**, **_wctime**et **_wctime64** se comportent de la même façon que **ctime**.

Ces fonctions valident leurs paramètres. Si *sourceTime* est un pointeur null ou si la valeur *sourceTime* est négative, ces fonctions appellent le gestionnaire de paramètres non valides, comme décrit dans [validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, les fonctions retournent la **valeur null** et attribuent à **errno** la valeur **EINVAL**.

Par défaut, l’état global de cette fonction est limité à l’application. Pour modifier cette valeur, consultez [état global dans le CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine TCHAR.H|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tctime**|**ctime**|**ctime**|**_wctime**|
|**_tctime32**|**_ctime32**|**_ctime32**|**_wctime32**|
|**_tctime64**|**_ctime64**|**_ctime64**|**_wctime64**|

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**ctime**|\<time.h>|
|**_ctime32**|\<time.h>|
|**_ctime64**|\<time.h>|
|**_wctime**|\<time.h> ou \<wchar.h>|
|**_wctime32**|\<time.h> ou \<wchar.h>|
|**_wctime64**|\<time.h> ou \<wchar.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

```C
// crt_ctime64.c
// compile with: /W3
/* This program gets the current
* time in _time64_t form, then uses ctime to
* display the time in string form.
*/

#include <time.h>
#include <stdio.h>

int main( void )
{
   __time64_t ltime;

   _time64( &ltime );
   printf( "The time is %s\n", _ctime64( &ltime ) ); // C4996
   // Note: _ctime64 is deprecated; consider using _ctime64_s
}
```

```Output
The time is Wed Feb 13 16:04:43 2002
```

## <a name="see-also"></a>Voir aussi

[Gestion du temps](../../c-runtime-library/time-management.md)<br/>
[asctime, _wasctime](asctime-wasctime.md)<br/>
[ctime_s, _ctime32_s, _ctime64_s, _wctime_s, _wctime32_s, _wctime64_s](ctime-s-ctime32-s-ctime64-s-wctime-s-wctime32-s-wctime64-s.md)<br/>
[_ftime, _ftime32, _ftime64](ftime-ftime32-ftime64.md)<br/>
[gmtime, _gmtime32, _gmtime64](gmtime-gmtime32-gmtime64.md)<br/>
[localtime, _localtime32, _localtime64](localtime-localtime32-localtime64.md)<br/>
[time, _time32, _time64](time-time32-time64.md)<br/>
