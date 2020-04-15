---
title: asctime_s, _wasctime_s
ms.date: 4/2/2020
api_name:
- _wasctime_s
- asctime_s
- _o__wasctime_s
- _o_asctime_s
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
- asctime_s
- _wasctime_s
- _tasctime_s
helpviewer_keywords:
- tasctime_s function
- _tasctime_s function
- time structure conversion
- wasctime_s function
- time, converting
- _wasctime_s function
- asctime_s function
ms.assetid: 17ad9b2b-a459-465d-976a-42822897688a
ms.openlocfilehash: 52391eb1237e4c1d7ef320dacd211b603a21ab8b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81334223"
---
# <a name="asctime_s-_wasctime_s"></a>asctime_s, _wasctime_s

Convertir une structure temporelle **tm** en chaîne de caractères. Ces fonctions sont des versions de [asctime, _wasctime](asctime-wasctime.md) assortie des améliorations de sécurité décrites dans [Fonctionnalités de sécurité dans le CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Syntaxe

```C
errno_t asctime_s(
   char* buffer,
   size_t numberOfElements,
   const struct tm *tmSource
);
errno_t _wasctime_s(
   wchar_t* buffer,
   size_t numberOfElements
   const struct tm *tmSource
);
template <size_t size>
errno_t asctime_s(
   char (&buffer)[size],
   const struct tm *tmSource
); // C++ only
template <size_t size>
errno_t _wasctime_s(
   wchar_t (&buffer)[size],
   const struct tm *tmSource
); // C++ only
```

### <a name="parameters"></a>Paramètres

*buffer*<br/>
Un pointeur vers un tampon pour stocker le résultat de la chaîne de caractère. Cette fonction suppose un pointeur à un emplacement de mémoire valide avec une taille spécifiée par *numberOfElements*.

*nombreOfElements*<br/>
La taille du tampon utilisé pour stocker le résultat.

*tmSource (en)*<br/>
Structure date/heure. Cette fonction suppose un pointeur à un objet **tm** **structurant** valide.

## <a name="return-value"></a>Valeur de retour

Zéro si l’opération réussit. En cas d’échec, le gestionnaire de paramètres non valides est appelé, comme décrit dans [Validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, la valeur de retour est un code d’erreur. Les codes d’erreur sont définis dans ERRNO.H. Pour plus d’informations, consultez [Constantes errno](../../c-runtime-library/errno-constants.md). Les codes d’erreur retournés pour chaque condition d’erreur sont répertoriés dans le tableau suivant.

### <a name="error-conditions"></a>Conditions d'erreur

|*buffer*|*nombreOfElements*|*tmSource (en)*|Renvoie|Valeur dans *le tampon*|
|--------------|------------------------|----------|------------|-----------------------|
|**Null**|Quelconque|Quelconque|**EINVAL (EN)**|Non modifiée|
|Non **NULL** (points à la mémoire valide)|0|Quelconque|**EINVAL (EN)**|Non modifiée|
|Non **NULL**|0 < taille < 26|Quelconque|**EINVAL (EN)**|Chaîne vide|
|Non **NULL**|>= 26|**Null**|**EINVAL (EN)**|Chaîne vide|
|Non **NULL**|>= 26|Structure de temps non valide ou hors de la plage de valeurs pour les composants de temps|**EINVAL (EN)**|Chaîne vide|

> [!NOTE]
> Les conditions d’erreur pour **wasctime_s** sont similaires à **asctime_s,** à l’exception que la limite de taille est mesurée en mots.

## <a name="remarks"></a>Notes

La fonction **asctime** convertit un temps stocké comme une structure en une chaîne de caractères. La valeur *tmSource* est généralement obtenue à partir d’un appel à **gmtime** ou **localtime**. Les deux fonctions peuvent être utilisées pour remplir une structure **de tm,** telle que définie dans TIME. H.

|Membre de timeptr|Value|
|--------------------|-----------|
|**tm_hour**|Heures depuis minuit (0-23)|
|**tm_isdst**|Positif si l’heure d’été est en vigueur ; 0 si l’heure d’été n’est pas appliquée ; négatif si l’état de l’heure d’été est inconnu. La bibliothèque runtime C suppose que les règles de calcul de l’heure d’été sont celles des États-Unis.|
|**tm_mday**|Jour du mois (1-31)|
|**tm_min**|Minutes après heure (0-59)|
|**tm_mon**|Mois (0-11; Janvier et 0)|
|**tm_sec**|Secondes après minute (0-59)|
|**tm_wday**|Jour de la semaine (0-6; Dimanche 0)|
|**tm_yday**|Jour de l’année (0-365; 1er janvier à 0)|
|**tm_year**|Année (année en cours moins 1900)|

La chaîne de caractères convertie est également ajustée en fonction des paramètres de fuseau horaire local. Consultez les fonctions [time, _time32, _time64](time-time32-time64.md), [_ftime, _ftime32, _ftime64](ftime-ftime32-ftime64.md) et [localtime_s, _localtime32_s, _localtime64_s](localtime-s-localtime32-s-localtime64-s.md) pour plus d’informations sur la configuration de l’heure locale, et la fonction [_tzset](tzset.md) pour plus d’informations sur la définition des variables globales et d’environnement des fuseaux horaires.

Le résultat de la chaîne produite par **asctime_s** contient exactement `Wed Jan 02 02:03:55 1980\n\0`26 caractères et a la forme . Une horloge de 24 heures est utilisée. Tous les champs ont une largeur constante. Le caractère de saut de ligne et le caractère null occupent les deux dernières positions de la chaîne. La valeur passée comme deuxième paramètre doit être au moins de cette taille. Si c’est moins, un code d’erreur, **EINVAL**, sera retourné.

**_wasctime_s** est une version à caractère large de **asctime_s**. **_wasctime_s** et **asctime_s** se comportent de façon identique autrement.

Les versions de bibliothèque de débogé de ces fonctions remplissent d’abord le tampon avec 0xFE. Pour désactiver ce comportement, utilisez [_CrtSetDebugFillThreshold](crtsetdebugfillthreshold.md).

Par défaut, l’état global de cette fonction est étendue à l’application. Pour changer cela, voir [Global State dans le CRT](../global-state.md).

### <a name="generic-text-routine-mapping"></a>Mappage de routines de texte générique

|Routine TCHAR.H|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tasctime_s**|**asctime_s**|**asctime_s**|**_wasctime_s**|

En C++, l’utilisation de ces fonctions est simplifiée par les surcharges de modèle ; celles-ci peuvent déduire automatiquement la longueur de la mémoire tampon, ce qui évite d’avoir à spécifier un argument de taille. Pour plus d’informations, consultez [Sécuriser les surcharges de modèle](../../c-runtime-library/secure-template-overloads.md).

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**asctime_s**|\<time.h>|
|**_wasctime_s**|\<time.h> ou \<wchar.h>|

## <a name="security"></a>Sécurité

Si le pointeur tampon n’est pas **NULL** et que le pointeur ne pointe pas vers un tampon valide, la fonction remplacera tout ce qui se trouve à l’endroit. Cela peut également entraîner une violation d’accès.

Un [dépassement de mémoire tampon](/windows/win32/SecBP/avoiding-buffer-overruns) peut se produire si l’argument de la taille passé est supérieur à la taille réelle de la mémoire tampon.

## <a name="example"></a>Exemple

Ce programme place le temps du système dans **l’aclock**integer long , le traduit dans la structure **newtime,** puis le convertit en forme de chaîne pour la sortie, en utilisant la fonction **asctime_s.**

```C
// crt_asctime_s.c
#include <time.h>
#include <stdio.h>

struct tm newtime;
__time32_t aclock;

int main( void )
{
   char buffer[32];
   errno_t errNum;
   _time32( &aclock );   // Get time in seconds.
   _localtime32_s( &newtime, &aclock );   // Convert time to struct tm form.

   // Print local time as a string.

   errNum = asctime_s(buffer, 32, &newtime);
   if (errNum)
   {
       printf("Error code: %d", (int)errNum);
       return 1;
   }
   printf( "Current date and time: %s", buffer );
   return 0;
}
```

```Output
Current date and time: Wed May 14 15:30:17 2003
```

## <a name="see-also"></a>Voir aussi

[Gestion du temps](../../c-runtime-library/time-management.md)<br/>
[ctime_s, _ctime32_s, _ctime64_s, _wctime_s, _wctime32_s, _wctime64_s](ctime-s-ctime32-s-ctime64-s-wctime-s-wctime32-s-wctime64-s.md)<br/>
[_ftime, _ftime32, _ftime64](ftime-ftime32-ftime64.md)<br/>
[gmtime_s, _gmtime32_s, _gmtime64_s](gmtime-s-gmtime32-s-gmtime64-s.md)<br/>
[localtime_s, _localtime32_s, _localtime64_s](localtime-s-localtime32-s-localtime64-s.md)<br/>
[time, _time32, _time64](time-time32-time64.md)<br/>
[_tzset](tzset.md)<br/>
