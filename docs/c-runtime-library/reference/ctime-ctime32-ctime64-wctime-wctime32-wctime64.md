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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: 6056ad8bac6561c0ce2902928364996b2be9ae92
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81348246"
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

*sourceTime sourceTime source*<br/>
Pointeur pour stocker le temps de convertir.

## <a name="return-value"></a>Valeur de retour

Pointeur désignant le résultat de chaîne de caractères. **NULL** sera retourné si :

- *sourceTime* représente une date avant minuit, le 1er janvier 1970, UTC.

- Si vous utilisez **_ctime32** ou **_wctime32** et *sourceTime* représente une date après 23:59:59 Janvier 18, 2038, UTC.

- Si vous utilisez **_ctime64** ou **_wctime64** et *sourceTime* représente une date après 23:59:59, Décembre 31, 3000, UTC.

**ctime** est une fonction inline qui évalue à **_ctime64** et **time_t** est équivalente à **__time64_t**. Si vous avez besoin de forcer le compilateur à interpréter **time_t** comme l’ancien time_t 32 **bits**, vous pouvez définir **_USE_32BIT_TIME_T**. Cela entraînera **ctime** d’évaluer à **_ctime32**. Cela n’est pas recommandé, car votre application peut échouer après le 18 janvier 2038 et cela n’est pas autorisé sur les plateformes 64 bits.

## <a name="remarks"></a>Notes

La fonction **ctime** convertit une valeur temporelle stockée sous [forme de valeur time_t](../../c-runtime-library/standard-types.md) en une chaîne de caractères. La *valeur sourceTime* est généralement obtenue à partir d’un appel à [l’heure](time-time32-time64.md), qui retourne le nombre de secondes écoulées depuis minuit (00:00:00), Janvier 1, 1970, heure universelle coordonnée (UTC). La chaîne de valeur de retour contient exactement 26 caractères et présente la forme suivante :

```Output
Wed Jan 02 02:03:55 1980\n\0
```

Une horloge de 24 heures est utilisée. Tous les champs ont une largeur constante. Le caractère de saut de ligne (« \n ») et le caractère null (« \0 ») occupent les deux dernières positions de la chaîne.

La chaîne de caractères convertie est également ajustée en fonction des paramètres de fuseau horaire local. Voir [l’heure,](time-time32-time64.md) [_ftime](ftime-ftime32-ftime64.md), et les fonctions [locales](localtime-localtime32-localtime64.md) pour des informations sur la configuration de l’heure locale et la fonction [_tzset](tzset.md) pour plus de détails sur la définition de l’environnement fuseau horaire et les variables globales.

Un appel au **ctime** modifie le tampon statiquement alloué utilisé par les fonctions **gmtime** et **localtime.** Chaque appel à une de ces routines détruit le résultat de l’appel précédent. **ctime** partage un tampon statique avec la fonction **asctime.** Ainsi, un appel à **ctime** détruit les résultats de tout appel précédent à **asctime**, **localtime**, ou **gmtime**.

**_wctime** et **_wctime64** sont la version à caractère large de **ctime** et **_ctime64**; retour d’un pointeur à la corde de caractère large. Sinon, **_ctime64**, **_wctime**, et **_wctime64** se comportent de la même façon à **ctime**.

Ces fonctions valident leurs paramètres. Si *sourceTime* est un pointeur nul, ou si la valeur *sourceTime* est négative, ces fonctions invoquent le gestionnaire de paramètres invalides, tel que décrit dans [La validation de paramètres](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, les fonctions retournent **NULL** et **placent errno** à **EINVAL**.

Par défaut, l’état global de cette fonction est étendue à l’application. Pour changer cela, voir [Global State dans le CRT](../global-state.md).

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
