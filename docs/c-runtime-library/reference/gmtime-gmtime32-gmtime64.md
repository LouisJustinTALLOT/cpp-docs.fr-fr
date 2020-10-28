---
title: gmtime, _gmtime32, _gmtime64
description: Référence d’API pour `gmtime` , `_gmtime32` et `_gmtime64` , qui convertit une `time_t` valeur en une `tm` structure.
ms.date: 10/27/2020
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
ms.openlocfilehash: bb8bee6b752f64d85dfb0f8c9e5ba7acf204a76f
ms.sourcegitcommit: 9c801a43ee0d4d84956b03fd387716c818705e0d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/28/2020
ms.locfileid: "92907543"
---
# <a name="gmtime-_gmtime32-_gmtime64"></a>`gmtime`, `_gmtime32`, `_gmtime64`

Convertit une `time_t` valeur d’heure en une `tm` structure. Des versions plus sécurisées de ces fonctions sont disponibles ; consultez [ `gmtime_s` , `_gmtime32_s` , `_gmtime64_s` ](gmtime-s-gmtime32-s-gmtime64-s.md).

## <a name="syntax"></a>Syntaxe

```C
struct tm *gmtime( const time_t *sourceTime );
struct tm *_gmtime32( const __time32_t *sourceTime );
struct tm *_gmtime64( const __time64_t *sourceTime );
```

### <a name="parameters"></a>Paramètres

*`sourceTime`*\
Pointeur désignant la valeur de temps stockée. Le temps est représenté sous forme de secondes écoulées depuis le 1er janvier 1970 minuit (00:00:00), temps universel coordonné (UTC).

## <a name="return-value"></a>Valeur de retour

Pointeur vers une structure de type [`tm`](../../c-runtime-library/standard-types.md) . Les champs de la structure retournée contiennent la valeur évaluée de l' *`sourceTime`* argument en heure UTC plutôt qu’en heure locale. Chacun des champs de la structure est de type `int`, comme suit :

|Champ|Description|
|-|-|
|`tm_sec`|Secondes après la minute (0-59).|
|`tm_min`|Minutes après l’heure (0-59).|
|`tm_hour`|Heures depuis minuit (0-23).|
|`tm_mday`|Jour du mois (1-31).|
|`tm_mon`|Mois (0-11 ; Janvier = 0).|
|`tm_year`|Année (année en cours moins 1900).|
|`tm_wday`|Jour de la semaine (0-6 ; Dimanche = 0).|
|`tm_yday`|Jour de l’année (0-365 ; 1er janvier = 0).|
|`tm_isdst`|Toujours 0 pour **gmtime** .|

Les versions 32 bits et 64 bits de **`gmtime`** ,, [`mktime`](mktime-mktime32-mktime64.md) [`mkgmtime`](mkgmtime-mkgmtime32-mkgmtime64.md) et utilisent toutes les deux [`localtime`](localtime-localtime32-localtime64.md) une `tm` structure commune par thread pour la conversion. Chaque appel à une de ces fonctions détruit le résultat de tout appel précédent. Si *`sourceTime`* représente une date antérieure au 1er janvier 1970, **`gmtime`** retourne `NULL` . Il n’y a pas d’erreur de retour.

**_gmtime64** , qui utilise la `__time64_t` structure, permet d’exprimer les dates jusqu’au 31 décembre 3000 à 23:59:59, heure UTC. **`_gmtime32`** représente uniquement les dates jusqu’au 18 23:59:59 Janvier 2038, heure UTC. Le 1er janvier 1970 à minuit est la limite inférieure de la plage de dates pour les deux fonctions.

**`gmtime`** est une fonction inline qui prend la valeur **`_gmtime64`** , et `time_t` est équivalent à, `__time64_t` sauf si `_USE_32BIT_TIME_T` est défini. Si vous devez forcer le compilateur à interpréter `time_t` comme l’ancien-bit 32 `time_t` , vous pouvez définir `_USE_32BIT_TIME_T` , mais ce qui fait qu’il **`gmtime`** soit en ligne vers **`_gmtime32`** et `time_t` être défini comme `__time32_t` . Nous vous déconseillons de le faire, car il n’est pas autorisé sur les plateformes 64 bits. Dans tous les cas, votre application peut échouer après le 18 janvier 2038.

Ces fonctions valident leurs paramètres. Si *`sourceTime`* est un pointeur null ou si la *`sourceTime`* valeur est négative, ces fonctions appellent un gestionnaire de paramètres non valides, comme décrit dans [validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à continuer, les fonctions retournent `NULL` et définissent `errno` sur `EINVAL`.

## <a name="remarks"></a>Notes

La **`_gmtime32`** fonction décompose la *`sourceTime`* valeur et la stocke dans une structure allouée statiquement de type `tm` , définie dans `TIME.H` . La valeur de *`sourceTime`* est généralement obtenue à partir d’un appel à la [`time`](time-time32-time64.md) fonction.

> [!NOTE]
> Dans la plupart des cas, l’environnement cible tente de déterminer si l’heure d’été est en vigueur. La bibliothèque runtime C suppose que les règles de calcul de l’heure d’été utilisées sont celles des États-Unis.

Par défaut, l’état global de cette fonction est limité à l’application. Pour modifier cette valeur, consultez [état global dans le CRT](../global-state.md).

## <a name="requirements"></a>Spécifications

|Routine|En-tête C requis|En-tête C++ requis|
|-------------|---------------------|-|
|**`gmtime`** , **`_gmtime32`** , **`_gmtime64`**|`<time.h>`| `<ctime>` ou `<time.h>`|

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

int main(void)
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

[Gestion du temps](../../c-runtime-library/time-management.md)\
[`asctime`, `_wasctime`](asctime-wasctime.md)\
[`ctime`, `_ctime32`, `_ctime64`, `_wctime`, `_wctime32`, `_wctime64`](ctime-ctime32-ctime64-wctime-wctime32-wctime64.md)\
[`_ftime`, `_ftime32`, `_ftime64`](ftime-ftime32-ftime64.md)\
[`gmtime_s`, `_gmtime32_s`, `_gmtime64_s`](gmtime-s-gmtime32-s-gmtime64-s.md)\
[`localtime`, `_localtime32`, `_localtime64`](localtime-localtime32-localtime64.md)\
[`_mkgmtime`, `_mkgmtime32`, `_mkgmtime64`](mkgmtime-mkgmtime32-mkgmtime64.md)\
[`mktime`, `_mktime32`, `_mktime64`](mktime-mktime32-mktime64.md)\
[`time`, `_time32`, `_time64`](time-time32-time64.md)
