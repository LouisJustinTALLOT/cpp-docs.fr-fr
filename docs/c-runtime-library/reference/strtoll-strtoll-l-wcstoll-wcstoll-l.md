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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: 047932a1f1474d443179a37b3dbc4fde6c995a99
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87213474"
---
# <a name="strtoll-_strtoll_l-wcstoll-_wcstoll_l"></a>strtoll, _strtoll_l, wcstoll, _wcstoll_l

Convertit une chaîne en **`long long`** valeur.

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

*strSource*<br/>
Chaîne se terminant par un caractère Null à convertir.

*endptr*<br/>
Pointeur désignant le caractère qui arrête l’analyse.

*base*<br/>
Base numérique à utiliser.

*locale*<br/>
Paramètres régionaux à utiliser.

## <a name="return-value"></a>Valeur de retour

**strtoll** retourne la valeur représentée dans la chaîne *strSource*, sauf lorsque la représentation provoque un dépassement de capacité, dans ce cas, elle retourne **LLONG_MAX** ou **LLONG_MIN**. La fonction retourne 0 si aucune conversion ne peut être effectuée. **wcstoll** retourne des valeurs de façon analogue à **strtoll**.

Les **LLONG_MAX** et les **LLONG_MIN** sont définis dans des limites. Manutention.

Si *strSource* a la **valeur null** ou si la *base* est différente de zéro et inférieure à 2 ou supérieure à 36, **errno** a la valeur **EINVAL**.

Pour plus d’informations sur les codes de retour, consultez [errno, _doserrno, _sys_errlist et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Notes

La fonction **strtoll** convertit *strSource* en **`long long`** . Les deux fonctions cessent de lire la chaîne *strSource* au premier caractère qu’elles ne peuvent pas reconnaître dans le cadre d’un nombre. Il peut s’agir du caractère null de fin ou du premier caractère numérique supérieur ou égal à *base*. **wcstoll** est une version à caractères larges de **strtoll**; son argument *strSource* est une chaîne de caractères larges. Sinon, ces fonctions se comportent de façon identique.

Par défaut, l’état global de cette fonction est limité à l’application. Pour modifier cette valeur, consultez [état global dans le CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine TCHAR.H|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcstoll**|**strtoll**|**strtoll**|**wcstoll**|
|**_tcstoll_l**|**_strtoll_l**|**_strtoll_l**|**_wcstoll_l**|

Le paramètre de catégorie **LC_NUMERIC** des paramètres régionaux détermine la reconnaissance du caractère de base dans *strSource*; Pour plus d’informations, consultez [setlocale, _wsetlocale](setlocale-wsetlocale.md). Les fonctions qui n’ont pas le suffixe **_L** utilisent les paramètres régionaux actuels ; **_strtoll_l** et **_wcstoll_l** sont identiques aux fonctions correspondantes qui n’ont pas le suffixe, à ceci près qu’elles utilisent à la place les paramètres régionaux qui sont passés. Pour plus d’informations, consultez [Locale](../../c-runtime-library/locale.md).

Si *endptr* n’a pas la **valeur null**, un pointeur vers le caractère qui a arrêté l’analyse est stocké à l’emplacement désigné par *endptr*. Si aucune conversion ne peut être effectuée (aucun chiffre valide n’a été trouvé ou une base non valide a été spécifiée), la valeur de *strSource* est stockée à l’emplacement désigné par *endptr*.

**strtoll** attend que *strSource* pointe vers une chaîne au format suivant :

> [*espace blanc*] [{ **+** &#124; **-** }] [**0** [{ **x** &#124; **x** }]] [*chiffres* &#124; *lettres*]

Un espace *blanc* peut se composer d’espaces et de caractères de tabulation, qui sont ignorés ; les *chiffres* correspondent à un ou plusieurs chiffres décimaux ; les *lettres* sont une ou plusieurs lettres de « a » à « z » (ou de « a » à « z »). Le premier caractère qui ne correspond pas à ce format a pour effet d’arrêter l’analyse. Si la *base* est comprise entre 2 et 36, elle est utilisée comme base du nombre. Si *base* a la valeur 0, les caractères initiaux de la chaîne vers laquelle pointe *strSource* sont utilisés pour déterminer la base. Si le premier caractère est « 0 » et que le deuxième est différent de « x » ou « X », la chaîne est interprétée comme étant un entier octal. Si le premier caractère est « 0 » et que le deuxième est « x » ou « X », la chaîne est interprétée comme étant un entier hexadécimal. Si le premier caractère est un chiffre compris entre « 1 » et « 9 », la chaîne est interprétée comme étant un entier décimal. Les lettres de « a » à « z » (ou de « A » à « Z ») se voient affecter des valeurs comprises entre 10 et 35 ; seules sont autorisées les lettres dont les valeurs affectées sont inférieures à la *base*. Le premier caractère situé en dehors de la plage de la base a pour effet d’arrêter l’analyse. Par exemple, si *base* a la valeur 0 et que le premier caractère analysé est « 0 », un entier octal est supposé et un caractère « 8 » ou « 9 » arrête l’analyse.

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**strtoll**, **_strtoll_l**|\<stdlib.h>|
|**wcstoll**, **_wcstoll_l**|\<stdlib.h> ou \<wchar.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[Conversion de données](../../c-runtime-library/data-conversion.md)<br/>
[Paramètres régionaux](../../c-runtime-library/locale.md)<br/>
[localeconv](localeconv.md)<br/>
[setlocale, _wsetlocale](setlocale-wsetlocale.md)<br/>
[Fonctions de chaîne en valeur numérique](../../c-runtime-library/string-to-numeric-value-functions.md)<br/>
[strtod, _strtod_l, wcstod, _wcstod_l](strtod-strtod-l-wcstod-wcstod-l.md)<br/>
[strtol, wcstol, _strtol_l, _wcstol_l](strtol-wcstol-strtol-l-wcstol-l.md)<br/>
[strtoul, _strtoul_l, wcstoul, _wcstoul_l](strtoul-strtoul-l-wcstoul-wcstoul-l.md)<br/>
[atof, _atof_l, _wtof, _wtof_l](atof-atof-l-wtof-wtof-l.md)<br/>
