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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: c59e8297013e02592e623859621bb1ff11474733
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87215138"
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

*MaxSize*<br/>
Taille de la mémoire tampon *strDest* , mesurée en caractères ( **`char`** ou **`wchar_t`** ).

*format*<br/>
Chaîne de contrôle de format.

*timeptr*<br/>
structure de données **TM** .

*locale*<br/>
Paramètres régionaux à utiliser.

## <a name="return-value"></a>Valeur de retour

**strftime** retourne le nombre de caractères placés dans *strDest* et **wcsftime** retourne le nombre correspondant de caractères larges.

Si le nombre total de caractères, y compris le caractère null de fin, est supérieur à *MaxSize*, **strftime** et **wcsftime** retournent 0 et le contenu de *strDest* est indéterminé.

Le nombre de caractères dans *strDest* est égal au nombre de caractères littéraux au *format* , ainsi qu’à tous les caractères qui peuvent être ajoutés au *format* par le biais des codes de mise en forme. Le caractère Null de fin d’une chaîne n’est pas compté dans la valeur de retour.

## <a name="remarks"></a>Notes

Les fonctions **strftime** et **wcsftime** mettent en forme la valeur de temps **TM** dans *timeptr* en fonction de l’argument de *format* fourni et stockent le résultat dans le *strDest*de mémoire tampon. Au maximum, les caractères *MaxSize* sont placés dans la chaîne. Pour obtenir une description des champs de la structure *timeptr* , consultez [asctime](asctime-wasctime.md). **wcsftime** est l’équivalent à caractères larges de **strftime**; son argument de pointeur de chaîne pointe vers une chaîne de caractères larges. Ces fonctions se comportent sinon de façon identique.

Cette fonction valide ses paramètres. Si *strDest*, *format*ou *timeptr* est un pointeur null, ou si la structure de données **TM** adressée par *timeptr* n’est pas valide (par exemple, si elle contient des valeurs hors limites pour la date ou l’heure), ou si la chaîne de *format* contient un code de mise en forme non valide, le gestionnaire de paramètres non valides est appelé, comme décrit dans [validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, la fonction retourne 0 et définit **errno** sur **EINVAL**.

Par défaut, l’état global de cette fonction est limité à l’application. Pour modifier cette valeur, consultez [état global dans le CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine TCHAR.H|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcsftime**|**strftime**|**strftime**|**wcsftime**|

L’argument *format* se compose d’un ou de plusieurs codes. comme dans **printf**, les codes de mise en forme sont précédés d’un signe de pourcentage ( **%** ). Les caractères qui ne commencent pas par **%** sont copiés sans être modifiés dans *strDest*. La catégorie **LC_TIME** des paramètres régionaux actuels affecte la mise en forme de la sortie de **strftime**. (Pour plus d’informations sur **LC_TIME**, consultez [setlocale](setlocale-wsetlocale.md).) Les fonctions **strftime** et **wcsftime** utilisent les paramètres régionaux actuellement définis. Les versions **_strftime_l** et **_wcsftime_l** de ces fonctions sont identiques, sauf qu’elles prennent les paramètres régionaux en tant que paramètre et les utilisent à la place des paramètres régionaux actuellement définis. Pour plus d’informations, consultez [Locale](../../c-runtime-library/locale.md).

Les fonctions **strftime** prennent en charge les codes de mise en forme suivants :

|||
|-|-|
|Code|Chaîne de remplacement|
|**% a**|Nom abrégé du jour de la semaine dans les paramètres régionaux|
|**% A**|Nom complet du jour de la semaine dans les paramètres régionaux|
|**% b**|Nom du mois abrégé dans les paramètres régionaux|
|**% B**|Nom du mois complet dans les paramètres régionaux|
|**% c**|Représentation de la date et de l’heure correspondant aux paramètres régionaux|
|**% C**|Année divisée par 100 et tronquée en entier, sous la forme d’un nombre décimal (00 − 99)|
|**% d**|Jour du mois sous la forme d’un nombre décimal (01-31)|
|**% D**|Équivalent à **% m/% d/% y**|
|**% e**|Jour du mois sous la forme d’un nombre décimal (1-31), où les chiffres uniques sont précédés d’un espace|
|**% F**|Équivalent à **% Y-% m-% d**|
|**% g**|Les 2 derniers chiffres de l’année ISO 8601 semaine en tant que nombre décimal (00-99)|
|**% G**|Année ISO 8601 semaine sous la forme d’un nombre décimal|
|**% h**|Nom de mois abrégé (équivalent à **% b**)|
|**% H**|Heure au format 24 heures (00-23)|
|**% I**|Heure au format 12 heures (01-12)|
|**% j**|Jour de l’année sous la forme d’un nombre décimal (001-366)|
|**% m**|Mois sous forme de nombre décimal (01-12)|
|**% M**|Minute sous la forme d’un nombre décimal (00-59)|
|**% n**|Un caractère de saut de ligne (**\n**)|
|**% p**|Heure du matin de la localité pour l’heure au format 12 heures|
|**% r**|Heure de l’horloge de 12 heures des paramètres régionaux|
|**% R**|Équivalent à **% H :%M**|
|**% S**|Seconde sous la forme d’un nombre décimal (00-59)|
|**% t**|Un caractère de tabulation horizontale (**\t**)|
|**% T**|Équivalent à **% H :%M :% S**, format d’heure ISO 8601|
|**% u**|ISO 8601 jour de la semaine en tant que nombre décimal (1-7 ; Lundi est 1)|
|**% U**|Numéro de semaine de l’année sous la forme d’un nombre décimal (00-53), où le premier dimanche est le premier jour de la semaine 1|
|**% V**|Numéro de semaine ISO 8601 en tant que nombre décimal (00-53)|
|**% w**|Jour de la semaine sous la forme d’un nombre décimal (0-6 ; Le dimanche est 0)|
|**% W**|Numéro de semaine de l’année sous la forme d’un nombre décimal (00-53), où le premier lundi est le premier jour de la semaine 1|
|**% x**|Représentation de la date des paramètres régionaux|
|**% X**|Représentation de l’heure pour les paramètres régionaux|
|**% y**|Année sans siècle, en tant que nombre décimal (00-99)|
|**% Y**|Année avec le siècle, sous forme de nombre décimal|
|**% z**|Décalage par rapport à l’heure UTC au format ISO 8601 ; aucun caractère si le fuseau horaire est inconnu|
|**% Z**|Le nom de fuseau horaire de la région ou l’abréviation du fuseau horaire, selon les paramètres du Registre ; aucun caractère si le fuseau horaire est inconnu|
|**%%**|Signe de pourcentage|

Comme dans la fonction **printf** , l' **#** indicateur peut préfixer tout code de mise en forme. Dans ce cas, la signification du code de format change comme suit.

|Code du format|Signification|
|-----------------|-------------|
|**% #a**, **% #A**, **% #b**, **% #B**, **% #g**, **% #G**, **%**#h, **% #n**, **% #p**, **%**#t, **% #u**, **% #w**, **% #X**, **%**#z, **% #Z**,**%#%**|**#** l’indicateur est ignoré.|
|**% #c**|Représentation de la date et de l’heure longues, adaptée aux paramètres régionaux. Par exemple : « Mardi 14 mars 1995, 12:41:29 ».|
|**% #x**|Représentation de date longue, adaptée aux paramètres régionaux. Par exemple : « Mardi 14 mars 1995 ».|
|**% #d**, **% #D**, **% #e**, **% #F**, **% #H**, **% #I**, **% #j**, **% #m**, **% #M**, **%**#r, **% #R**, **%**#S, **%#T**% #T, **%**#U, **% #V**,% **#W**, **%**#y, **%** #Y|Supprimer les zéros ou les espaces non significatifs (le cas échéant).|

L’année ISO 8601 semaine et semaine générée par **% V**, **% g**et **% g**, utilise une semaine qui commence le lundi, où semaine 1 est la semaine qui contient le 4 janvier, soit la première semaine qui inclut au moins quatre jours de l’année. Si le premier lundi de l’année est le 2e, troisième ou quatrième, les jours précédents font partie de la dernière semaine de l’année précédente. Pour ces jours-ci, **% V** est remplacé par 53, et **% g** et **% g** sont remplacés par les chiffres de l’année précédente.

> [!NOTE]
> Lors de l’utilisation de l’une des `strftime` fonctions avec un `tm` pointeur retourné par `gmtime` , les valeurs imprimées via les `%Z` spécificateurs et ne sont `%z` pas exactes. Cela est dû au fait que le `tm` struct tel que spécifié par la norme C ne contient pas les informations relatives au nom et au décalage du fuseau horaire. Au lieu de cela, les informations de fuseau horaire sont renseignées via les variables globales [ `_timezone` et `_dstbias` ](../../c-runtime-library/daylight-dstbias-timezone-and-tzname.md).

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

[Paramètres régionaux](../../c-runtime-library/locale.md) <br/>
[Gestion du temps](../../c-runtime-library/time-management.md) <br/>
[Manipulation de chaînes](../../c-runtime-library/string-manipulation-crt.md) <br/>
[localeconv](localeconv.md) <br/>
[setlocale, _wsetlocale](setlocale-wsetlocale.md) <br/>
[strcoll, fonctions](../../c-runtime-library/strcoll-functions.md) <br/>
[strxfrm, wcsxfrm, _strxfrm_l, _wcsxfrm_l](strxfrm-wcsxfrm-strxfrm-l-wcsxfrm-l.md)<br/>
