---
title: _mkgmtime, _mkgmtime32, _mkgmtime64
ms.date: 11/04/2016
apiname:
- _mkgmtime32
- _mkgmtime64
- _mkgmtime
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
- _mkgmtime64
- mkgmtime32
- _mkgmtime32
- mkgmtime
- mkgmtime64
- _mkgmtime
helpviewer_keywords:
- mkgmtime32 function
- time functions
- mkgmtime function
- _mkgmtime function
- converting times
- mkgmtime64 function
- _mkgmtime64 function
- _mkgmtime32 function
- time, converting
ms.assetid: b4ca2b67-e198-4f43-b3e2-e8ad6bd01867
ms.openlocfilehash: 65d96d79a45e05e4b371315c0612ed086f6ea2a0
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62156497"
---
# <a name="mkgmtime-mkgmtime32-mkgmtime64"></a>_mkgmtime, _mkgmtime32, _mkgmtime64

Convertit une heure UTC représentée par un **struct** **tm** en heure UTC représentée par un **time_t** type.

## <a name="syntax"></a>Syntaxe

```C
time_t _mkgmtime(
   struct tm* timeptr
);
__time32_t _mkgmtime32(
   struct tm* timeptr
);
__time64_t _mkgmtime64(
   struct tm* timeptr
);
```

### <a name="parameters"></a>Paramètres

*timeptr*<br/>
Un pointeur vers l’heure UTC en tant qu’un **struct** **tm** à convertir.

## <a name="return-value"></a>Valeur de retour

Une quantité de type **__time32_t** ou **__time64_t** représentant le nombre de secondes écoulées depuis minuit, le 1er janvier 1970, temps universel coordonné (UTC). Si la date est hors limites (voir la section Notes) ou l’entrée ne peut pas être interprétée comme une heure valide, la valeur de retour est -1.

## <a name="remarks"></a>Notes

Le **_mkgmtime32** et **_mkgmtime64** fonctions convertissent une heure UTC en un **__time32_t** ou **__time64_t** type représentant l’heure dans HEURE UTC. Pour convertir une heure locale en heure UTC, utilisez **mktime**, **_mktime32**, et **_mktime64** à la place.

**_mkgmtime** est une fonction inline qui prend la valeur **_mkgmtime64**, et **time_t** équivaut à **__time64_t**. Si vous devez forcer le compilateur à interpréter **time_t** l’ancien 32-bit **time_t**, vous pouvez définir **_USE_32BIT_TIME_T**. Cela n’est pas recommandée, car votre application peut échouer après le 18 janvier 2038 (la plage maximale de 32 bits **time_t**), et il n’est pas autorisée à tout sur les plateformes 64 bits.

La structure de temps passée sera modifiée comme suit, dans la même façon qu’elle est modifiée avec le **_mktime** fonctions : le **tm_wday** et **tm_yday** champs sont définis nouveau valeurs en fonction des valeurs de **tm_mday** et **tm_year**. Lorsque vous spécifiez un **tm** heure de structure, définissez la **tm_isdst** champ :

- zéro (0) pour indiquer que l'heure d'hiver est active ;

- une valeur supérieure à 0 pour indiquer que l'heure d'été est active ;

- une valeur inférieure à zéro pour que le code de la bibliothèque Runtime C calcule si l'heure active est l'heure d'hiver ou l'heure d'été.

La bibliothèque Runtime C utilise la variable d’environnement TZ pour déterminer l’heure d’été correcte. Si TZ n’est pas définie, le système d’exploitation est interrogé pour obtenir le comportement d’heure d’été régionale correct. **tm_isdst** est un champ obligatoire. S’il est ne pas définie, sa valeur est indéfinie et la valeur de retour à partir de **mktime** est imprévisible.

La plage de la **_mkgmtime32** fonction est à partir du 1er janvier 1970 à minuit UTC à 23:59:59 le 18 janvier 2038, UTC. La plage de **_mkgmtime64** se situe entre le 1er janvier 1970 à minuit UTC et 23:59:59 le 31 décembre 3000, UTC. Une valeur de retour de -1 entraîne une date hors limites. La plage de **_mkgmtime** varie selon que **_USE_32BIT_TIME_T** est défini. Si non définie (la valeur par défaut) la plage est celle de **_mkgmtime64**; sinon, la plage est limitée à la plage de 32 bits de **_mkgmtime32**.

Notez que **gmtime** et **localtime** utilisent un seul tampon alloué de manière statique pour la conversion. Si vous fournissez cette mémoire tampon à **mkgmtime**, le contenu précédent est détruit.

## <a name="example"></a>Exemple

```C
// crt_mkgmtime.c
#include <stdio.h>
#include <time.h>

int main()
{
    struct tm t1, t2;
    time_t now, mytime, gmtime;
    char buff[30];

    time( & now );

    _localtime64_s( &t1, &now );
    _gmtime64_s( &t2, &now );

    mytime = mktime(&t1);
    gmtime = _mkgmtime(&t2);

    printf("Seconds since midnight, January 1, 1970\n");
    printf("My time: %I64d\nGM time (UTC): %I64d\n\n", mytime, gmtime);

    /* Use asctime_s to display these times. */

    _localtime64_s( &t1, &mytime );
    asctime_s( buff, sizeof(buff), &t1 );
    printf( "Local Time: %s\n", buff );

    _gmtime64_s( &t2, &gmtime );
    asctime_s( buff, sizeof(buff), &t2 );
    printf( "Greenwich Mean Time: %s\n", buff );

}
```

### <a name="sample-output"></a>Résultat de l'exemple

```Output
Seconds since midnight, January 1, 1970
My time: 1171588492
GM time (UTC): 1171588492

Local Time: Thu Feb 15 17:14:52 2007

Greenwich Mean Time: Fri Feb 16 01:14:52 2007
```

L’exemple suivant montre comment la structure incomplète est remplie avec les valeurs calculées du jour de la semaine et du jour de l’année.

```C
// crt_mkgmtime2.c
#include <stdio.h>
#include <time.h>
#include <memory.h>

int main()
{
    struct tm t1, t2;
    time_t gmtime;
    char buff[30];

    memset(&t1, 0, sizeof(struct tm));
    memset(&t2, 0, sizeof(struct tm));

    t1.tm_mon = 1;
    t1.tm_isdst = 0;
    t1.tm_year = 103;
    t1.tm_mday = 12;

    // The day of the week and year will be incorrect in the output here.
    asctime_s( buff, sizeof(buff), &t1);
    printf("Before calling _mkgmtime, t1 = %s t.tm_yday = %d\n",
            buff, t1.tm_yday );

    gmtime = _mkgmtime(&t1);

    // The correct day of the week and year were determined.
    asctime_s( buff, sizeof(buff), &t1);
    printf("After calling _mkgmtime, t1 = %s t.tm_yday = %d\n",
            buff, t1.tm_yday );

}
```

### <a name="output"></a>Sortie

```Output
Before calling _mkgmtime, t1 = Sun Feb 12 00:00:00 2003
t.tm_yday = 0
After calling _mkgmtime, t1 = Wed Feb 12 00:00:00 2003
t.tm_yday = 42
```

## <a name="see-also"></a>Voir aussi

[Gestion du temps](../../c-runtime-library/time-management.md)<br/>
[asctime, _wasctime](asctime-wasctime.md)<br/>
[asctime_s, _wasctime_s](asctime-s-wasctime-s.md)<br/>
[gmtime, _gmtime32, _gmtime64](gmtime-gmtime32-gmtime64.md)<br/>
[gmtime_s, _gmtime32_s, _gmtime64_s](gmtime-s-gmtime32-s-gmtime64-s.md)<br/>
[localtime_s, _localtime32_s, _localtime64_s](localtime-s-localtime32-s-localtime64-s.md)<br/>
[mktime, _mktime32, _mktime64](mktime-mktime32-mktime64.md)<br/>
[time, _time32, _time64](time-time32-time64.md)<br/>
