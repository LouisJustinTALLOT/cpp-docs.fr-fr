---
description: 'En savoir plus sur : asctime, _wasctime'
title: asctime, _wasctime
ms.date: 4/2/2020
api_name:
- _wasctime
- asctime
- _o__wasctime
- _o_asctime
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
- _tasctime
- asctime
- _wasctime
helpviewer_keywords:
- asctime function
- tasctime function
- wasctime function
- _tasctime function
- _wasctime function
- time structure conversion
- time, converting
ms.assetid: 974f1727-10ff-4ed4-8cac-2eb2d681f576
ms.openlocfilehash: 3ae075481b364af01bfa75f1cc29423de9fcdbf1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97260798"
---
# <a name="asctime-_wasctime"></a>asctime, _wasctime

Convertit une structure de temps **TM** en une chaîne de caractères. Des versions plus sécurisées de ces fonctions sont disponibles. Consultez [asctime_s, _wasctime_s](asctime-s-wasctime-s.md).

## <a name="syntax"></a>Syntaxe

```C
char *asctime(
   const struct tm *timeptr
);
wchar_t *_wasctime(
   const struct tm *timeptr
);
```

### <a name="parameters"></a>Paramètres

*timeptr*<br/>
Structure date/heure.

## <a name="return-value"></a>Valeur renvoyée

**asctime** retourne un pointeur vers le résultat de chaîne de caractères ; **_wasctime** retourne un pointeur vers le résultat de chaîne à caractères larges. Aucune valeur de retour d’erreur.

## <a name="remarks"></a>Notes

Des versions plus sécurisées de ces fonctions sont disponibles. Consultez [asctime_s, _wasctime_s](asctime-s-wasctime-s.md).

La fonction **asctime** convertit une heure stockée sous la forme d’une structure en une chaîne de caractères. La valeur *timeptr* est généralement obtenue à partir d’un appel à **gmtime** ou **localtime**, qui retournent tous deux un pointeur vers une structure **TM** , définie dans Time. H.

|Membre de timeptr|Valeur|
|--------------------|-----------|
|**tm_hour**|Heures depuis minuit (0-23)|
|**tm_isdst**|Positif si l’heure d’été est en vigueur ; 0 si l’heure d’été n’est pas appliquée ; négatif si l’état de l’heure d’été est inconnu. La bibliothèque runtime C suppose que les règles de calcul de l’heure d’été sont celles des États-Unis.|
|**tm_mday**|Jour du mois (1 à 31)|
|**tm_min**|Minutes après l’heure (0-59)|
|**tm_mon**|Mois (0-11 ; Janvier = 0)|
|**tm_sec**|Secondes après la minute (0-59)|
|**tm_wday**|Jour de la semaine (0-6 ; Dimanche = 0)|
|**tm_yday**|Jour de l’année (0-365 ; 1er janvier = 0)|
|**tm_year**|Année (année en cours moins 1900)|

La chaîne de caractères convertie est également ajustée en fonction des paramètres de fuseau horaire local. Pour plus d’informations sur la configuration de l’heure locale, consultez les fonctions [time](time-time32-time64.md), [_ftime](ftime-ftime32-ftime64.md) et [localtime](localtime-localtime32-localtime64.md) et, pour plus d’informations sur la définition des variables globales et d’environnement des fuseaux horaires, consultez la fonction [_tzset](tzset.md).

Le résultat de chaîne produit par **asctime** contient exactement 26 caractères et se présente sous la forme `Wed Jan 02 02:03:55 1980\n\0` . Une horloge de 24 heures est utilisée. Tous les champs ont une largeur constante. Le caractère de saut de ligne et le caractère null occupent les deux dernières positions de la chaîne. **asctime** utilise une seule mémoire tampon allouée de manière statique pour contenir la chaîne de retour. Chaque appel à cette fonction détruit le résultat de l’appel précédent.

**_wasctime** est une version à caractères larges de **asctime**. dans le cas contraire, **_wasctime** et **asctime** se comportent de la même façon.

Ces fonctions valident leurs paramètres. Si *timeptr* est un pointeur null, ou s’il contient des valeurs hors limites, le gestionnaire de paramètres non valides est appelé, comme décrit dans [validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, la fonction retourne la **valeur null** et définit **errno** sur **EINVAL**.

Par défaut, l’état global de cette fonction est limité à l’application. Pour modifier cette valeur, consultez [état global dans le CRT](../global-state.md).

### <a name="generic-text-routine-mapping"></a>Mappage de routines de texte générique

|Routine TCHAR.H|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tasctime**|**asctime**|**asctime**|**_wasctime**|

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**asctime**|\<time.h>|
|**_wasctime**|\<time.h> ou \<wchar.h>|

## <a name="example"></a>Exemple

Ce programme place l’heure système dans l’entier long **aclock**, le convertit en structure **Newtime** , puis le convertit sous forme de chaîne pour la sortie, à l’aide de la fonction **asctime** .

```C
// crt_asctime.c
// compile with: /W3

#include <time.h>
#include <stdio.h>

int main( void )
{
    struct tm   *newTime;
    time_t      szClock;

    // Get time in seconds
    time( &szClock );

    // Convert time to struct tm form
    newTime = localtime( &szClock );

    // Print local time as a string.
    printf_s( "Current date and time: %s", asctime( newTime ) ); // C4996
    // Note: asctime is deprecated; consider using asctime_s instead
}
```

```Output
Current date and time: Sun Feb 03 11:38:58 2002
```

## <a name="see-also"></a>Voir aussi

[Gestion du temps](../../c-runtime-library/time-management.md)<br/>
[ctime, _ctime32, _ctime64, _wctime, _wctime32, _wctime64](ctime-ctime32-ctime64-wctime-wctime32-wctime64.md)<br/>
[_ftime, _ftime32, _ftime64](ftime-ftime32-ftime64.md)<br/>
[gmtime, _gmtime32, _gmtime64](gmtime-gmtime32-gmtime64.md)<br/>
[localtime, _localtime32, _localtime64](localtime-localtime32-localtime64.md)<br/>
[time, _time32, _time64](time-time32-time64.md)<br/>
[_tzset](tzset.md)<br/>
[asctime_s, _wasctime_s](asctime-s-wasctime-s.md)<br/>
