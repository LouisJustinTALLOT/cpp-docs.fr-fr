---
title: strtoll, _strtoll_l, wcstoll, _wcstoll_l
ms.date: 4/2/2020
api_name:
- strtoll
- wcstoll
- _strtoll_l
- _wcstoll_l
- _o__strtoll_l
- _o__wcstoll_l
- _o_strtoll
- _o_wcstoll
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
- _strtoll_l
- _tcstoll_l
- _tcstoll
- _wcstoll_l
- strtoll
- wcstoll
helpviewer_keywords:
- _tcstoll_l function
- _wcstoll_l function
- strtoll function
- wcstoll function
- _tcstoll function
- _strtoll_l function
ms.assetid: e2d05dcf-d3b2-4291-9e60-dee77e540fd7
ms.openlocfilehash: d5a0ce8cb2c1d5f88d5439b99047609b32c8d2ec
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365176"
---
# <a name="strtoll-_strtoll_l-wcstoll-_wcstoll_l"></a>strtoll, _strtoll_l, wcstoll, _wcstoll_l

Convertit une corde à une **longue** **valeur.**

## <a name="syntax"></a>Syntaxe

```C
long long strtoll(
   const char *strSource,
   char **endptr,
   int base
);
long long wcstoll(
   const wchar_t *strSource,
   wchar_t **endptr,
   int base
);
long long _strtoll_l(
   const char *strSource,
   char **endptr,
   int base,
   _locale_t locale
);
long long _wcstoll_l(
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

**strtoll** retourne la valeur qui est représentée dans la chaîne *strSource*, sauf lorsque la représentation causerait un débordement, dans ce cas, il retourne **LLONG_MAX** ou **LLONG_MIN**. La fonction retourne 0 si aucune conversion ne peut être effectuée. **wcstoll** retourne des valeurs de façon analogue à **strtoll**.

**LLONG_MAX** et **LLONG_MIN** sont définis dans LIMITS. H.

Si *strSource* est **NULL** ou que la *base* n’est pas zéro et moins de 2 ou plus de 36, **errno** est réglé sur **EINVAL**.

Pour plus d’informations sur les codes de retour, consultez [errno, _doserrno, _sys_errlist et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Notes

La fonction **strtoll** convertit *strSource* en une **longue.** **long** Les deux fonctions cessent de lire la chaîne *strSource* au premier caractère qu’ils ne peuvent pas reconnaître comme faisant partie d’un certain nombre. Il peut s’agir du caractère nul qui met fin, ou il peut s’agir du premier caractère numérique supérieur ou égal à *la base.* **wcstoll** est une version à caractère large de **strtoll;** son argument *strSource* est une chaîne de caractère large. Sinon, ces fonctions se comportent de façon identique.

Par défaut, l’état global de cette fonction est étendue à l’application. Pour changer cela, voir [Global State dans le CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine TCHAR.H|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcstoll**|**strtoll strtoll**|**strtoll strtoll**|**wcstoll**|
|**_tcstoll_l**|**_strtoll_l**|**_strtoll_l**|**_wcstoll_l**|

Le cadre de la catégorie **LC_NUMERIC** du lieu détermine la reconnaissance du caractère radix dans *strSource*; pour plus d’informations, voir [setlocale, _wsetlocale](setlocale-wsetlocale.md). Les fonctions qui n’ont pas le **suffixe _l** utilisent le lieu actuel; **_strtoll_l** et **_wcstoll_l** sont identiques aux fonctions correspondantes qui n’ont pas le suffixe, sauf qu’ils utilisent plutôt le lieu qui est passé dedans. Pour plus d’informations, consultez [Locale](../../c-runtime-library/locale.md).

Si *endptr n’est* pas **NULL**, un pointeur pour le personnage qui a arrêté l’analyse est stocké à l’endroit qui est pointé vers par *endptr*. Si aucune conversion ne peut être effectuée (aucun chiffre valide n’a été trouvé ou une base invalide a été spécifiée), la valeur de *strSource* est stockée à l’endroit qui est indiqué par *endptr*.

**strtoll** s’attend à ce que *strSource* pointe vers une série de la forme suivante :

> [*espace blanc*] [&#124;]**+** **-** [**0** **[x** &#124; **X]]** [*chiffres* &#124; *lettres*]

Un *espace blanc* peut se composer de caractères d’espace et d’onglet, qui sont ignorés ; *les chiffres* sont un ou plusieurs chiffres décimaux; *sont* une ou plusieurs des lettres 'a' par 'z' (ou 'A' par 'Z'). Le premier caractère qui ne correspond pas à ce format a pour effet d’arrêter l’analyse. Si *la base* se situe entre 2 et 36, elle est utilisée comme base du nombre. Si la *base* est de 0, les caractères initiaux de la chaîne qui est pointé par *strSource* sont utilisés pour déterminer la base. Si le premier caractère est « 0 » et que le deuxième est différent de « x » ou « X », la chaîne est interprétée comme étant un entier octal. Si le premier caractère est « 0 » et que le deuxième est « x » ou « X », la chaîne est interprétée comme étant un entier hexadécimal. Si le premier caractère est un chiffre compris entre « 1 » et « 9 », la chaîne est interprétée comme étant un entier décimal. Les lettres de « a » à « z » (ou de « A » à « Z ») se voient affecter des valeurs comprises entre 10 et 35 ; seules sont autorisées les lettres dont les valeurs affectées sont inférieures à la *base*. Le premier caractère situé en dehors de la plage de la base a pour effet d’arrêter l’analyse. Par exemple, si la *base* est de 0 et que le premier personnage numérisé est ' 0', un intégrisé octal est supposé et un caractère '8' ou '9' arrête l’analyse.

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**strtoll**, **_strtoll_l**|\<stdlib.h>|
|**wcstoll**, **_wcstoll_l**|\<stdlib.h> ou \<wchar.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[Conversion de données](../../c-runtime-library/data-conversion.md)<br/>
[Local](../../c-runtime-library/locale.md)<br/>
[localeconv](localeconv.md)<br/>
[setlocale, _wsetlocale](setlocale-wsetlocale.md)<br/>
[Fonctions de valeur chaîne en valeur numérique](../../c-runtime-library/string-to-numeric-value-functions.md)<br/>
[strtod, _strtod_l, wcstod, _wcstod_l](strtod-strtod-l-wcstod-wcstod-l.md)<br/>
[strtol, wcstol, _strtol_l, _wcstol_l](strtol-wcstol-strtol-l-wcstol-l.md)<br/>
[strtoul, _strtoul_l, wcstoul, _wcstoul_l](strtoul-strtoul-l-wcstoul-wcstoul-l.md)<br/>
[atof, _atof_l, _wtof, _wtof_l](atof-atof-l-wtof-wtof-l.md)<br/>
