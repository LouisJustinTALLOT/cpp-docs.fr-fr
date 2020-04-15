---
title: strtoull, _strtoull_l, wcstoull, _wcstoull_l
ms.date: 4/2/2020
api_name:
- _strtoull_l
- _wcstoull_l
- strtoull
- wcstoull
- _o__strtoull_l
- _o__wcstoull_l
- _o_strtoull
- _o_wcstoull
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
- api-ms-win-crt-convert-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _wcstoull_l
- _tcstoull
- _tcstoull_l
- wcstoull
- _strtoull_l
- strtoull
helpviewer_keywords:
- strtoull function
- _tcstoull_l function
- _tcstoull function
- _wcstoull_l function
- _strtoull_l function
- wcstoull function
ms.assetid: 36dac1cc-e901-40a0-8802-63562d6d01df
ms.openlocfilehash: 5a27218b9d83314f995df30fbe21d97031d371af
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81354050"
---
# <a name="strtoull-_strtoull_l-wcstoull-_wcstoull_l"></a>strtoull, _strtoull_l, wcstoull, _wcstoull_l

Convertit les chaînes en valeur entière de type long long non signée.

## <a name="syntax"></a>Syntaxe

```C
unsigned long long strtoull(
   const char *strSource,
   char **endptr,
   int base
);
unsigned long long _strtoull_l(
   const char *strSource,
   char **endptr,
   int base,
   _locale_t locale
);
unsigned long long wcstoull(
   const wchar_t *strSource,
   wchar_t **endptr,
   int base
);
unsigned long long _wcstoull_l(
   const wchar_t *strSource,
   wchar_t **endptr,
   int base,
   _locale_t locale
);
```

### <a name="parameters"></a>Paramètres

*strSource (en)*<br/>
Chaîne se terminant par un caractère Null à convertir.

*endptr*<br/>
Pointeur désignant le caractère qui arrête l’analyse.

*base*<br/>
Base numérique à utiliser.

*locale*<br/>
Paramètres régionaux à utiliser.

## <a name="return-value"></a>Valeur de retour

**strtoull** retourne la valeur convertie, le cas échéant, ou **ULLONG_MAX** sur le débordement. **strtoull** retourne 0 si aucune conversion ne peut être effectuée. **wcstoull** retourne des valeurs de façon analogue à **strtoull**. Pour les deux fonctions, **errno** est réglé sur **ERANGE** en cas de débordement ou de sous-flux.

Pour plus d’informations sur les codes de retour, consultez [errno, _doserrno, _sys_errlist et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Notes

Chacune de ces fonctions convertit la chaîne d’entrée *strSource* en une **longue** **long** valeur integer **non signée.**

**strtoull** cesse de lire la chaîne *strSource* au premier personnage qu’il ne peut pas reconnaître comme faisant partie d’un certain nombre. Il peut s’agir du caractère nul qui met fin, ou il peut s’agir du premier caractère numérique supérieur ou égal à *la base.* Le réglage de la **LC_NUMERIC** catégorie de la localité détermine la reconnaissance du caractère radix dans *strSource*; pour plus d’informations, voir [setlocale, _wsetlocale](setlocale-wsetlocale.md). **strtoull** et **wcstoull** utilisent le lieu actuel; **_strtoull_l** et **_wcstoull_l** utilisent plutôt le lieu qui est passé dans mais sont identiques autrement. Pour plus d’informations, consultez [Locale](../../c-runtime-library/locale.md).

Si *endptr n’est* pas **NULL**, un pointeur pour le personnage qui a arrêté l’analyse est stocké à l’endroit qui est pointé vers par *endptr*. Si aucune conversion ne peut être effectuée (aucun chiffre valide n’a été trouvé ou une base invalide a été spécifiée), la valeur de *strSource* est stockée à l’endroit qui est indiqué par *endptr*.

**wcstoull** est une version à caractère large de **strtoull** et son argument *strSource* est une chaîne de caractère large. Sinon, ces fonctions se comportent de façon identique.

Par défaut, l’état global de cette fonction est étendue à l’application. Pour changer cela, voir [Global State dans le CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine TCHAR.H|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcstoull**|**strtoull**|**strtoull**|**wcstoull**|
|**_tcstoull_l**|**strtoull_l**|**_strtoull_l**|**_wcstoull_l**|

**strtoull** s’attend à *ce que strSource* pointe vers une série de la forme suivante :

> [*espace blanc*] [&#124;]**+** **-** [**0** **[x** &#124; **X]]** [*chiffres* &#124; *lettres*]

Un *espace blanc* peut se composer de caractères d’espace et d’onglet, qui sont ignorés. *les chiffres* sont un ou plusieurs chiffres décimaux. *sont* une ou plusieurs des lettres 'a' par 'z' (ou 'A' par 'Z'). Le premier caractère qui ne correspond pas à ce format a pour effet d’arrêter l’analyse. Si *la base* se situe entre 2 et 36, elle est utilisée comme base du nombre. Si la *base* est de 0, les caractères initiaux de la chaîne qui est pointé par *strSource* sont utilisés pour déterminer la base. Si le premier caractère est « 0 » et que le deuxième est différent de « x » ou « X », la chaîne est interprétée comme étant un entier octal. Si le premier caractère est « 0 » et que le deuxième est « x » ou « X », la chaîne est interprétée comme étant un entier hexadécimal. Si le premier caractère est un chiffre compris entre « 1 » et « 9 », la chaîne est interprétée comme étant un entier décimal. Les lettres de « a » à « z » (ou de « A » à « Z ») se voient affecter des valeurs comprises entre 10 et 35 ; seules sont autorisées les lettres dont les valeurs affectées sont inférieures à la *base*. Le premier caractère situé en dehors de la plage de la base a pour effet d’arrêter l’analyse. Par exemple, si la *base* est de 0 et que le premier personnage numérisé est ' 0', un intégrisé octal est supposé et un caractère '8' ou '9' arrête l’analyse. **strtoull** permet un**+** signe plus (**-**) ou moins signe ( ) préfixe; un signe de premier plan moins indique que la valeur de rendement est annulée.

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**strtoull**|\<stdlib.h>|
|**wcstoull**|\<stdlib.h> ou \<wchar.h>|
|**_strtoull_l**|\<stdlib.h>|
|**_wcstoull_l**|\<stdlib.h> ou \<wchar.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

Consultez l’exemple relatif à [strtod](strtod-strtod-l-wcstod-wcstod-l.md).

## <a name="see-also"></a>Voir aussi

[Conversion de données](../../c-runtime-library/data-conversion.md)<br/>
[Local](../../c-runtime-library/locale.md)<br/>
[localeconv](localeconv.md)<br/>
[setlocale, _wsetlocale](setlocale-wsetlocale.md)<br/>
[Fonctions de valeur chaîne en valeur numérique](../../c-runtime-library/string-to-numeric-value-functions.md)<br/>
[strtod, _strtod_l, wcstod, _wcstod_l](strtod-strtod-l-wcstod-wcstod-l.md)<br/>
[strtol, wcstol, _strtol_l, _wcstol_l](strtol-wcstol-strtol-l-wcstol-l.md)<br/>
[strtoul, _strtoul_l, wcstoul, _wcstoul_l](strtoul-strtoul-l-wcstoul-wcstoul-l.md)<br/>
[strtoll, _strtoll_l, wcstoll, _wcstoll_l](strtoll-strtoll-l-wcstoll-wcstoll-l.md)<br/>
[atof, _atof_l, _wtof, _wtof_l](atof-atof-l-wtof-wtof-l.md)<br/>
