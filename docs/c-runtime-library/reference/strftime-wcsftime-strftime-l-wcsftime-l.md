---
title: strftime, wcsftime, _strftime_l, _wcsftime_l
ms.date: 4/2/2020
api_name:
- strftime
- _wcsftime_l
- _strftime_l
- wcsftime
- _o__strftime_l
- _o__wcsftime_l
- _o_strftime
- _o_wcsftime
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
ms.openlocfilehash: 5da2c128c54fd88bb874b360f5a966f17b14a935
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81350010"
---
# <a name="strftime-wcsftime-_strftime_l-_wcsftime_l"></a>strftime, wcsftime, _strftime_l, _wcsftime_l

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

*Maxsize*<br/>
Taille du tampon *strDest,* mesuré en caractères **(char** ou **wchar_t**).

*Format*<br/>
Chaîne de contrôle de format.

*timeptr*<br/>
**tm** structure de données.

*locale*<br/>
Paramètres régionaux à utiliser.

## <a name="return-value"></a>Valeur de retour

**strftime** renvoie le nombre de caractères placés dans *strDest* et **wcsftime** renvoie le nombre correspondant de caractères larges.

Si le nombre total de *caractères,* y compris la mise fin nulle, est plus que maxsize , à la fois **strftime** et **wcsftime** retour 0 et le contenu de *strDest* sont indéterminés.

Le nombre de caractères dans *strDest* est égal au nombre de caractères littéral dans le *format* ainsi que tous les caractères qui peuvent être ajoutés au *format* via des codes de formatage. Le caractère Null de fin d’une chaîne n’est pas compté dans la valeur de retour.

## <a name="remarks"></a>Notes

Le **strftime** et **wcsftime** fonctions format la valeur de temps **tm** dans *timeptr* selon l’argument de *format* fourni et stocker le résultat dans le *strDest*tampon . Tout au plus, *les caractères maxsize* sont placés dans la chaîne. Pour une description des champs dans la structure *de timeptr,* voir [asctime](asctime-wasctime.md). **wcsftime** est l’équivalent de caractère large de **strftime**; son argument de pointe de corde indique une corde de caractère large. Ces fonctions se comportent sinon de façon identique.

Cette fonction valide ses paramètres. Si *strDest*, *format,* ou *timeptr* est un pointeur nul, ou si la structure de données **tm** abordée par *timeptr* est invalide (par exemple, si elle contient des valeurs hors de portée pour l’heure ou la date), ou si la chaîne *de format* contient un code de formatage invalide, le gestionnaire de paramètres invalide est invoqué, tel que décrit dans La validation de [paramètres](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, la fonction renvoie 0 et définit **errno** à **EINVAL**.

Par défaut, l’état global de cette fonction est étendue à l’application. Pour changer cela, voir [Global State dans le CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine TCHAR.H|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcsftime**|**strftime**|**strftime**|**wcsftime**|

*L’argument* du format se compose d’un ou plusieurs codes; comme dans **printf**, les codes de formatage**%** sont précédés d’un signe pour cent ( ). Les caractères qui **%** ne commencent pas sont copiés inchangés à *strDest*. La **LC_TIME** catégorie de la localisation actuelle affecte le formatage de sortie de **strftime**. (Pour plus d’informations sur **LC_TIME**, voir [setlocale](setlocale-wsetlocale.md).) Les fonctions **strftime** et **wcsftime** utilisent le lieu actuellement défini. Les versions **_strftime_l** et **_wcsftime_l** de ces fonctions sont identiques, sauf qu’elles prennent le lieu comme un paramètre et l’utilisent au lieu du lieu actuellement défini. Pour plus d’informations, consultez [Locale](../../c-runtime-library/locale.md).

Les fonctions **strftime** prennent en charge ces codes de formatage :

|||
|-|-|
|Code|Chaîne de remplacement|
|**%a**|Nom abrégé en semaine dans le lieu|
|**%A**|Nom complet en semaine dans le lieu|
|**%b**|Nom abrégé de mois dans le lieu|
|**%B**|Nom du mois complet dans le lieu|
|**%c**|Représentation de la date et de l’heure correspondant aux paramètres régionaux|
|**%C**|L’année divisée par 100 et tronquée à un intégrant, comme un nombre décimal (00-99)|
|**%d**|Jour du mois en tant que nombre décimal (01 - 31)|
|**%D**|Équivalent à **%m/%d/%y**|
|**%e**|Jour du mois en tant que nombre décimal (1 - 31), où les chiffres simples sont précédés d’un espace|
|**%F**|Équivalent à **%Y-%m-%d**|
|**%g**|Les 2 derniers chiffres de l’année ISO 8601 par semaine en tant que nombre décimal (00 - 99)|
|**%G**|L’année de la semaine ISO 8601 en tant que nombre décimal|
|**%h**|Nom abrégé du mois (équivalent à **%b**)|
|**%H**|Heure en format 24 heures (00 - 23)|
|**%Je**|Heure en format 12 heures (01 - 12)|
|**%j**|Jour de l’année en tant que nombre décimal (001 - 366)|
|**%m**|Mois en tant que nombre décimal (01 - 12)|
|**%M**|Minute comme nombre décimal (00 - 59)|
|**%n**|Un personnage newline (**n**)|
|**%p**|Le local est A.M./P.M. pour l’heure au format 12 heures|
|**%r**|L’heure d’horloge de 12 heures de l’endroit|
|**%R**|Équivalent à **%H:%M**|
|**%S**|Deuxième en tant que nombre décimal (00 - 59)|
|**%t**|Un caractère d’onglet horizontal **( t**)|
|**%T**|Équivalent à **%H:%M:%S**, le format de temps ISO 8601|
|**%u**|ISO 8601 en semaine en tant que nombre décimal (1 - 7; Lundi est 1)|
|**%U**|Numéro de semaine de l’année en tant que nombre décimal (00 - 53), où le premier dimanche est le premier jour de la semaine 1|
|**%V**|NUMÉRO de semaine ISO 8601 en tant que nombre décimal (00 - 53)|
|**%w**|En semaine en tant que nombre décimal (0 - 6; Dimanche est 0)|
|**%W**|Numéro de semaine de l’année en tant que nombre décimal (00 - 53), où le premier lundi est le premier jour de la semaine 1|
|**%x**|Représentation de la date pour le lieu|
|**%X**|Représentation temporelle de la région|
|**%y**|Année sans siècle, en tant que nombre décimal (00 - 99)|
|**%Y**|Année avec le siècle, sous forme de nombre décimal|
|**%z**|Le décalage de l’UTC en format ISO 8601; aucun personnage si le fuseau horaire est inconnu|
|**%Z**|Soit le nom du fuseau horaire ou l’abréviation du fuseau horaire, selon les paramètres du registre; aucun personnage si le fuseau horaire est inconnu|
|**%%**|Signe de pourcentage|

Comme dans la fonction **#** **d’impression,** le drapeau peut préfixer n’importe quel code de formatage. Dans ce cas, la signification du code de format change comme suit.

|Code du format|Signification|
|-----------------|-------------|
|**%#a**, **%#A**, **%#b**, **%#B**, **%#g**, **%#G**, **%#h**, **%#n**, **%#p**, **%#t**, **%#u**, **% #w**, **% #X**, % **#z**, **% #Z**,**%#%**|**#** drapeau est ignoré.|
|**% #c**|Longue représentation de la date et de l’heure, appropriée pour le lieu. Par exemple : « Mardi 14 mars 1995, 12:41:29 ».|
|**% #x**|Représentation à long terme, appropriée à la localisation. Par exemple : « Mardi 14 mars 1995 ».|
|**% #d**, **%#D**, **%#e**, **%#F**, **%#H**, **%#I**, **%#j**, **%#m**, **%#M**, **%#r**, **% #R**, **% #S**, % **#T**, **% #U**, % #V **%**, % **#W**, % **#y**, % #y , % #y , % #Y #y , % #y , % #y , % #y , % #y , % #y % #y % **#y %**|Supprimer les zéros ou les espaces de premier plan (le cas échéant).|

L’année de semaine et de semaine ISO 8601 produite par **%V**, **%g**, et **%G**, utilise une semaine qui commence le lundi, où la semaine 1 est la semaine qui contient Janvier 4th, qui est la première semaine qui comprend au moins quatre jours de l’année. Si le premier lundi de l’année est le 2, 3 ou 4, les jours précédents font partie de la dernière semaine de l’année précédente. Pour ces jours, **%V** est remplacé par 53, et à la fois **%g** et **%G** sont remplacés par les chiffres de l’année précédente.

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**strftime**|\<time.h>|
|**wcsftime**|\<time.h> ou \<wchar.h>|
|**_strftime_l**|\<time.h>|
|**_wcsftime_l**|\<time.h> ou \<wchar.h>|

Les fonctions **_strftime_l** et **_wcsftime_l** sont spécifiques à Microsoft. Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

Consultez l’exemple relatif à [time](time-time32-time64.md).

## <a name="see-also"></a>Voir aussi

[Local](../../c-runtime-library/locale.md) <br/>
[Gestion du temps](../../c-runtime-library/time-management.md) <br/>
[Manipulation des cordes](../../c-runtime-library/string-manipulation-crt.md) <br/>
[localeconv](localeconv.md) <br/>
[setlocale, _wsetlocale](setlocale-wsetlocale.md) <br/>
[fonctions strcoll](../../c-runtime-library/strcoll-functions.md) <br/>
[strxfrm, wcsxfrm, _strxfrm_l, _wcsxfrm_l](strxfrm-wcsxfrm-strxfrm-l-wcsxfrm-l.md)<br/>
