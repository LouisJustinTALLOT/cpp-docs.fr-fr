---
title: strftime, wcsftime, _strftime_l, _wcsftime_l
ms.date: 03/22/2018
apiname:
- strftime
- _wcsftime_l
- _strftime_l
- wcsftime
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
- _tcsftime
- strftime
- wcsftime
- _strftime_l
- _wcsftime_l
helpviewer_keywords:
- _strftime_l function
- strftime function
- tcsftime function
- _wcsftime_l function
- wcsftime function
- _tcsftime function
- time strings
ms.assetid: 6330ff20-4729-4c4a-82af-932915d893ea
ms.openlocfilehash: 932a7827ef61a5e111f86f8bc44291827843b76e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62353837"
---
# <a name="strftime-wcsftime-strftimel-wcsftimel"></a>strftime, wcsftime, _strftime_l, _wcsftime_l

Mettent en forme une chaîne d’heure.

## <a name="syntax"></a>Syntaxe

```C
size_t strftime(
   char *strDest,
   size_t maxsize,
   const char *format,
   const struct tm *timeptr
);
size_t _strftime_l(
   char *strDest,
   size_t maxsize,
   const char *format,
   const struct tm *timeptr,
   _locale_t locale
);
size_t wcsftime(
   wchar_t *strDest,
   size_t maxsize,
   const wchar_t *format,
   const struct tm *timeptr
);
size_t _wcsftime_l(
   wchar_t *strDest,
   size_t maxsize,
   const wchar_t *format,
   const struct tm *timeptr,
   _locale_t locale
);
```

### <a name="parameters"></a>Paramètres

*strDest*<br/>
Chaîne de sortie.

*maxsize*<br/>
Taille de la *strDest* mémoire tampon, mesurée en caractères (**char** ou **wchar_t**).

*format*<br/>
Chaîne de contrôle de format.

*timeptr*<br/>
**TM** structure de données.

*locale*<br/>
Paramètres régionaux à utiliser.

## <a name="return-value"></a>Valeur de retour

**strftime** retourne le nombre de caractères placés dans *strDest* et **wcsftime** retourne le nombre correspondant de caractères larges.

Si le nombre total de caractères, y compris le caractère null, est plus de *maxsize*, à la fois **strftime** et **wcsftime** retournent 0 et le contenu de  *strDest* sont indéterminés.

Le nombre de caractères dans *strDest* est égal au nombre de caractères littéraux dans *format* , ainsi que tous les caractères qui peuvent être ajoutés à *format* par le biais de codes de mise en forme. Le caractère Null de fin d’une chaîne n’est pas compté dans la valeur de retour.

## <a name="remarks"></a>Notes

Le **strftime** et **wcsftime** format de fonctions le **tm** temps valeur dans *timeptr* selon fourni  *format* argument et stocke le résultat dans la mémoire tampon *strDest*. Au maximum, *maxsize* caractères sont placés dans la chaîne. Pour obtenir une description des champs dans le *timeptr* structure, consultez [asctime](asctime-wasctime.md). **wcsftime** équivaut à caractères larges **strftime**; son argument de pointeur de chaîne pointe vers une chaîne de caractères larges. Ces fonctions se comportent sinon de façon identique.

Cette fonction valide ses paramètres. Si *strDest*, *format*, ou *timeptr* est un pointeur null, ou si le **tm** structure de données traité par *timeptr* n’est pas valide (par exemple, si elle contient des valeurs hors limites pour la date ou heure), ou si le *format* chaîne contient un code de mise en forme non valide, le Gestionnaire de paramètre non valide est appelé, comme décrit dans [Validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, la fonction retourne 0 et affecte **errno** à **EINVAL**.

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine TCHAR.H|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcsftime**|**strftime**|**strftime**|**wcsftime**|

Le *format* argument se compose d’un ou plusieurs codes ; comme dans **printf**, les codes de mise en forme sont précédés d’un signe de pourcentage (**%**). Les caractères qui ne commencent pas par **%** sont copiés tels quels dans *strDest*. Le **LC_TIME** catégorie des paramètres régionaux affecte la sortie de la mise en forme de **strftime**. (Pour plus d’informations sur **LC_TIME**, consultez [setlocale](setlocale-wsetlocale.md).) Le **strftime** et **wcsftime** fonctions utilisent actuellement définis aux paramètres régionaux. Le **_strftime_l** et **_wcsftime_l** versions de ces fonctions sont identiques, sauf qu’ils prennent les paramètres régionaux en tant que paramètre et utilisent à la place actuellement définis aux paramètres régionaux. Pour plus d’informations, consultez [Locale](../../c-runtime-library/locale.md).

Le **strftime** fonctions prennent en charge ces codes de mise en forme :

|||
|-|-|
|Code|Chaîne de remplacement|
|**%a**|Nom abrégé du jour de semaine dans les paramètres régionaux|
|**%A**|Nom du jour complet dans les paramètres régionaux|
|**%b**|Nom de mois abrégé dans les paramètres régionaux|
|**%B**|Nom complet du mois dans les paramètres régionaux|
|**%c**|Représentation de la date et de l’heure correspondant aux paramètres régionaux|
|**%C**|L’année divisé par 100 et tronquée en entier, comme un nombre décimal (00−99)|
|**%d**|Jour du mois sous la forme d’un nombre décimal (01 à 31)|
|**%D**|Équivalent à **%m/%d/%y**|
|**%e**|Jour du mois sous la forme d’un nombre décimal (1-31), où les chiffres uniques sont précédées par un espace|
|**%F**|Équivalent à **%Y-%m-%d**|
|**%g**|2 chiffres de l’année en fonction de semaine ISO 8601 comme un nombre décimal (00 - 99)|
|**%G**|L’année basée sur une semaine ISO 8601 comme un nombre décimal|
|**%h**|Nom de mois abrégé (équivalent à **%b**)|
|**%H**|Heure au format 24 heures (00 - 23)|
|**%I**|Heure au format 12 heures (01 à 12)|
|**%j**|Jour de l’année sous la forme d’un nombre décimal (001 à 366)|
|**%m**|Mois sous la forme d’un nombre décimal (01 à 12)|
|**%M**|Minute sous la forme d’un nombre décimal (00 - 59)|
|**%n**|Un caractère de saut de ligne (**\n**)|
|**%p**|PM les paramètres régionaux. pour l’heure au format 12 heures|
|**%r**|Heure de l’horloge de 12 heures de paramètres régionaux|
|**%R**|Équivalent à **% H: %M**|
|**%S**|Seconde sous la forme d’un nombre décimal (00 - 59)|
|**%t**|Un caractère de tabulation horizontale (**\t**)|
|**%T**|Équivalent à **% H: % M: %S**, le format d’heure ISO 8601|
|**%u**|Jour de la semaine ISO 8601 comme un nombre décimal (de 1 à 7 ; Lundi = 1)|
|**%U**|Numéro de semaine de l’année sous la forme d’un nombre décimal (00 - 53), où le premier dimanche est le premier jour de la semaine 1|
|**%V**|Numéro de semaine ISO 8601 comme un nombre décimal (00 - 53)|
|**%w**|Jour de la semaine comme un nombre décimal (0 - 6 ; Dimanche est 0)|
|**%W**|Numéro de semaine de l’année sous la forme d’un nombre décimal (00 - 53), où le premier lundi est le premier jour de la semaine 1|
|**%x**|Représentation sous forme de date pour les paramètres régionaux|
|**%X**|Représentation sous forme de temps pour les paramètres régionaux|
|**%y**|Année sans le siècle, sous forme de nombre décimal (00 - 99)|
|**%Y**|Année avec le siècle, sous forme de nombre décimal|
|**%z**|Le décalage UTC au format ISO 8601 ; aucun caractère si le fuseau horaire est inconnu|
|**%Z**|Du paramètres régionaux nom du fuseau horaire ou abréviation du fuseau horaire, en fonction des paramètres de Registre ; aucun caractère si le fuseau horaire est inconnu|
|**%%**|Signe de pourcentage|

Comme dans le **printf** (fonction), le **#** indicateur peut servir de préfixe de code de mise en forme. Dans ce cas, la signification du code de format change comme suit.

|Code du format|Signification|
|-----------------|-------------|
|**%#a**, **%#A**, **%#b**, **%#B**, **%#g**, **%#G**, **%#h**, **%#n**, **%#p**, **%#t**, **%#u**, **%#w**, **%#X**, **%#z**, **%#Z**, **%#%**|**#** l’indicateur est ignoré.|
|**%#c**|Durée pendant laquelle date et heure de représentation, appropriée pour les paramètres régionaux. Exemple : « Mardi, 14 mars 1995, 12:41:29 ».|
|**%#x**|Représentation de date longue appropriée aux paramètres régionaux. Exemple : « Mardi 14 mars 1995. »|
|**%#d**, **%#D**, **%#e**, **%#F**, **%#H**, **% #I**, **%#j**, **%#m**, **%#M**, **%#r**, **%#R**, **%#S**, **%#T** , **%#U**, **%#V**, **%#W**, **%#y**, **%#Y**|Supprimer les zéros non significatifs ou des espaces (le cas échéant).|

La semaine de l’ISO 8601 et année semaine basée produites par **%V**, **%g**, et **%G**, utilise une semaine commence le lundi, où la semaine 1 est la semaine qui contient le 4 janvier, est le premier semaine comprenant au moins quatre jours de l’année. Si le premier lundi de l’année est la 2e, 3e et 4e, les jours précédents font partie de la dernière semaine de l’année précédente. Pour ces jours, **%V** est remplacé par 53 et les deux **%g** et **%G** sont remplacés par les chiffres de l’année précédente.

## <a name="requirements"></a>Configuration requise

|Routine|En-tête requis|
|-------------|---------------------|
|**strftime**|\<time.h>|
|**wcsftime**|\<time.h> ou \<wchar.h>|
|**_strftime_l**|\<time.h>|
|**_wcsftime_l**|\<time.h> ou \<wchar.h>|

Le **_strftime_l** et **_wcsftime_l** fonctions sont spécifiques à Microsoft. Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

Consultez l’exemple relatif à [time](time-time32-time64.md).

## <a name="see-also"></a>Voir aussi

[Paramètres régionaux](../../c-runtime-library/locale.md) <br/>
[Gestion du temps](../../c-runtime-library/time-management.md) <br/>
[Manipulation de chaînes](../../c-runtime-library/string-manipulation-crt.md) <br/>
[localeconv](localeconv.md) <br/>
[setlocale, _wsetlocale](setlocale-wsetlocale.md) <br/>
[strcoll, fonctions](../../c-runtime-library/strcoll-functions.md) <br/>
[strxfrm, wcsxfrm, _strxfrm_l, _wcsxfrm_l](strxfrm-wcsxfrm-strxfrm-l-wcsxfrm-l.md)<br/>
