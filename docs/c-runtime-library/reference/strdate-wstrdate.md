---
title: _strdate, _wstrdate
ms.date: 4/2/2020
api_name:
- _strdate
- _wstrdate
- _o__strdate
- _o__wstrdate
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
- _tstrdate
- wstrdate
- _wstrdate
- _strdate
- strdate
helpviewer_keywords:
- strdate function
- dates, copying
- tstrdate function
- _wstrdate function
- wstrdate function
- _strdate function
- _tstrdate function
- copying dates
ms.assetid: de8e4097-58f8-42ba-9dcd-cb4d9a9f1696
ms.openlocfilehash: 9b4b6d3b81dd1dda968cc42448ab2e53bdd44433
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81361278"
---
# <a name="_strdate-_wstrdate"></a>_strdate, _wstrdate

Copient la date système actuelle dans une mémoire tampon. Il existe des versions plus sécurisées de ces fonctions. Consultez [_strdate_s, _wstrdate_s](strdate-s-wstrdate-s.md).

## <a name="syntax"></a>Syntaxe

```C
char *_strdate(
   char *datestr
);
wchar_t *_wstrdate(
   wchar_t *datestr
);
template <size_t size>
char *_strdate(
   char (&datestr)[size]
); // C++ only
template <size_t size>
wchar_t *_wstrdate(
   wchar_t (&datestr)[size]
); // C++ only
```

### <a name="parameters"></a>Paramètres

*datestr*<br/>
Pointeur désignant une mémoire tampon contenant la chaîne de date mise en forme.

## <a name="return-value"></a>Valeur de retour

Chacune de ces fonctions renvoie un pointeur à la date de la chaîne de caractère *résultante*.

## <a name="remarks"></a>Notes

Il existe des versions plus sécurisées de ces fonctions. Consultez [_strdate_s, _wstrdate_s](strdate-s-wstrdate-s.md). Il est recommandé d’utiliser les fonctions les plus sécurisées, dans la mesure du possible.

La fonction **_strdate** copie la date actuelle du système à la mémoire tampon pointée par *datestr*, formaté **mm**/**dd**/**yy**, où **mm** est deux chiffres représentant le mois, **dd** est deux chiffres représentant le jour, et **yy** est les deux derniers chiffres de l’année. Par exemple, la chaîne **12/05/99** représente le 5 décembre 1999. La mémoire tampon doit avoir une longueur au moins égale à 9 octets.

Si *datestr* est un pointeur **NULL,** le gestionnaire de paramètres invalides est invoqué, tel que décrit dans [La validation des paramètres](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, ces fonctions retournent -1 et **placent errno** à **EINVAL**.

**_wstrdate** est une version à caractère large de **_strdate**; l’argument et la valeur de retour de **_wstrdate** sont des chaînes de caractère large. Ces fonctions se comportent sinon de façon identique.

En C++, ces fonctions ont des surcharges de modèle qui appellent les équivalents plus récents et sécurisés de ces fonctions. Pour plus d’informations, consultez [Sécuriser les surcharges de modèle](../../c-runtime-library/secure-template-overloads.md).

Par défaut, l’état global de cette fonction est étendue à l’application. Pour changer cela, voir [Global State dans le CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine TCHAR.H|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tstrdate**|**_strdate**|**_strdate**|**_wstrdate**|

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**_strdate**|\<time.h>|
|**_wstrdate**|\<time.h> ou \<wchar.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

```C
// strdate.c
// compile with: /W3
#include <time.h>
#include <stdio.h>
int main()
{
    char tmpbuf[9];

    // Set time zone from TZ environment variable. If TZ is not set,
    // the operating system is queried to obtain the default value
    // for the variable.
    //
    _tzset();

    printf( "OS date: %s\n", _strdate(tmpbuf) ); // C4996
    // Note: _strdate is deprecated; consider using _strdate_s instead
}
```

```Output
OS date: 04/25/03
```

## <a name="see-also"></a>Voir aussi

[Gestion du temps](../../c-runtime-library/time-management.md)<br/>
[asctime, _wasctime](asctime-wasctime.md)<br/>
[ctime, _ctime32, _ctime64, _wctime, _wctime32, _wctime64](ctime-ctime32-ctime64-wctime-wctime32-wctime64.md)<br/>
[gmtime, _gmtime32, _gmtime64](gmtime-gmtime32-gmtime64.md)<br/>
[localtime, _localtime32, _localtime64](localtime-localtime32-localtime64.md)<br/>
[mktime, _mktime32, _mktime64](mktime-mktime32-mktime64.md)<br/>
[time, _time32, _time64](time-time32-time64.md)<br/>
[_tzset](tzset.md)<br/>
