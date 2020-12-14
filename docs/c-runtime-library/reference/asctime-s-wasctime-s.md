---
description: 'En savoir plus sur : asctime_s, _wasctime_s'
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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: d743aea81abdba2e1aa2b470f71081cb92e6fc64
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97211321"
---
# <a name="asctime_s-_wasctime_s"></a>asctime_s, _wasctime_s

Convertit une structure de temps **TM** en une chaîne de caractères. Ces fonctions sont des versions de [asctime, _wasctime](asctime-wasctime.md) assortie des améliorations de sécurité décrites dans [Fonctionnalités de sécurité dans le CRT](../../c-runtime-library/security-features-in-the-crt.md).

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

*mémoire tampon*<br/>
Pointeur vers une mémoire tampon pour stocker le résultat de la chaîne de caractères. Cette fonction suppose un pointeur vers un emplacement de mémoire valide avec une taille spécifiée par *NumberOfElements*.

*numberOfElements*<br/>
Taille de la mémoire tampon utilisée pour stocker le résultat.

*tmSource*<br/>
Structure date/heure. Cette fonction suppose un pointeur vers un **`struct`** objet **TM** valide.

## <a name="return-value"></a>Valeur renvoyée

Zéro si l’opération réussit. En cas d’échec, le gestionnaire de paramètres non valides est appelé, comme décrit dans [Validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, la valeur de retour est un code d’erreur. Les codes d’erreur sont définis dans ERRNO.H. Pour plus d’informations, consultez [Constantes errno](../../c-runtime-library/errno-constants.md). Les codes d’erreur retournés pour chaque condition d’erreur sont répertoriés dans le tableau suivant.

### <a name="error-conditions"></a>Conditions d'erreur

|*mémoire tampon*|*numberOfElements*|*tmSource*|Renvoie|Valeur dans la *mémoire tampon*|
|--------------|------------------------|----------|------------|-----------------------|
|**NULL**|Quelconque|Quelconque|**EINVAL**|Non modifiée|
|Not **null** (pointe vers une mémoire valide)|0|Quelconque|**EINVAL**|Non modifiée|
|Non **null**|0 < taille < 26|Quelconque|**EINVAL**|Chaîne vide|
|Non **null**|>= 26|**NULL**|**EINVAL**|Chaîne vide|
|Non **null**|>= 26|Structure de temps non valide ou hors de la plage de valeurs pour les composants de temps|**EINVAL**|Chaîne vide|

> [!NOTE]
> Les conditions d’erreur pour **wasctime_s** sont similaires à **asctime_s** , sauf que la limite de taille est mesurée en mots.

## <a name="remarks"></a>Notes

La fonction **asctime** convertit une heure stockée sous la forme d’une structure en une chaîne de caractères. La valeur *tmSource* est généralement obtenue à partir d’un appel à **gmtime** ou **localtime**. Les deux fonctions peuvent être utilisées pour remplir une structure **TM** , telle que définie dans Time. H.

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

La chaîne de caractères convertie est également ajustée en fonction des paramètres de fuseau horaire local. Consultez les fonctions [time, _time32, _time64](time-time32-time64.md), [_ftime, _ftime32, _ftime64](ftime-ftime32-ftime64.md) et [localtime_s, _localtime32_s, _localtime64_s](localtime-s-localtime32-s-localtime64-s.md) pour plus d’informations sur la configuration de l’heure locale, et la fonction [_tzset](tzset.md) pour plus d’informations sur la définition des variables globales et d’environnement des fuseaux horaires.

Le résultat de chaîne produit par **asctime_s** contient exactement 26 caractères et se présente sous la forme `Wed Jan 02 02:03:55 1980\n\0` . Une horloge de 24 heures est utilisée. Tous les champs ont une largeur constante. Le caractère de saut de ligne et le caractère null occupent les deux dernières positions de la chaîne. La valeur passée comme deuxième paramètre doit être au moins de cette taille. S’il est inférieur, un code d’erreur, **EINVAL**, est retourné.

**_wasctime_s** est une version à caractères larges de **asctime_s**. dans le cas contraire, **_wasctime_s** et **asctime_s** se comportent de la même façon.

Les versions de la bibliothèque de débogage de ces fonctions remplissent d’abord la mémoire tampon avec 0xFE. Pour désactiver ce comportement, utilisez [_CrtSetDebugFillThreshold](crtsetdebugfillthreshold.md).

Par défaut, l’état global de cette fonction est limité à l’application. Pour modifier cette valeur, consultez [état global dans le CRT](../global-state.md).

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

Si le pointeur de la mémoire tampon n’est pas **null** et que le pointeur ne pointe pas vers une mémoire tampon valide, la fonction remplace tout ce qui se trouve à l’emplacement. Cela peut également entraîner une violation d’accès.

Un [dépassement de mémoire tampon](/windows/win32/SecBP/avoiding-buffer-overruns) peut se produire si l’argument de la taille passé est supérieur à la taille réelle de la mémoire tampon.

## <a name="example"></a>Exemple

Ce programme place l’heure système dans l’entier long **aclock**, le convertit en structure **Newtime** , puis le convertit sous forme de chaîne pour la sortie, à l’aide de la fonction **asctime_s** .

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
