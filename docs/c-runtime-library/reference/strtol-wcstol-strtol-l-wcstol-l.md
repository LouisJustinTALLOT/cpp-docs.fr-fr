---
title: strtol, wcstol, _strtol_l, _wcstol_l
ms.date: 11/04/2016
api_name:
- strtol
- wcstol
- _strtol_l
- _wcstol_l
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _wcstol_l
- strtol
- _tcstol
- wcstol
- _strtol_l
- _tcstol_l
helpviewer_keywords:
- wcstol function
- wcstol_l function
- _tcstol function
- string conversion, to integers
- tcstol function
- strtol_l function
- _wcstol_l function
- _strtol_l function
- strtol function
ms.assetid: 1787c96a-f283-4a83-9325-33cfc1c7e240
ms.openlocfilehash: b40362e93a41730e46ad0911b5a633118d024e9c
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70957636"
---
# <a name="strtol-wcstol-_strtol_l-_wcstol_l"></a>strtol, wcstol, _strtol_l, _wcstol_l

Convertit les chaînes en valeur entière de type long.

## <a name="syntax"></a>Syntaxe

```C
long strtol(
   const char *strSource,
   char **endptr,
   int base
);
long wcstol(
   const wchar_t *strSource,
   wchar_t **endptr,
   int base
);
long _strtol_l(
   const char *strSource,
   char **endptr,
   int base,
   _locale_t locale
);
long _wcstol_l(
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

**strtol** retourne la valeur représentée dans la chaîne *strSource*, sauf lorsque la représentation provoque un dépassement de capacité, auquel cas elle retourne **LONG_MAX** ou **LONG_MIN**. **strtol** retourne 0 si aucune conversion ne peut être effectuée. **wcstol** retourne des valeurs de façon analogue à **strtol**. Pour les deux fonctions, **errno** a la valeur **ERANGE** si le dépassement de capacité positif ou négatif se produit.

Pour plus d’informations sur ces codes de retour et les autres, consultez [_doserrno, errno, _sys_errlist et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Notes

La fonction **strtol** convertit *strSource* en **long**. **strtol** arrête de lire la chaîne *strSource* au premier caractère qu’elle ne peut pas reconnaître comme faisant partie d’un nombre. Il peut s’agir du caractère null de fin, ou il peut s’agir du premier caractère numérique supérieur ou égal à *base*.

**wcstol** est une version à caractères larges de **strtol**; son argument *strSource* est une chaîne de caractères larges. Ces fonctions se comportent sinon de façon identique.

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine TCHAR.H|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcstol**|**strtol**|**strtol**|**wcstol**|
|**_tcstol_l**|**_strtol_l**|**_strtol_l**|**_wcstol_l**|

Le paramètre de catégorie **LC_NUMERIC** des paramètres régionaux actuels détermine la reconnaissance du caractère de base dans *strSource*; Pour plus d’informations, consultez [setlocale](setlocale-wsetlocale.md). Les fonctions sans le suffixe **_L** utilisent les paramètres régionaux actuels. **_strtol_l** et **_wcstol_l** sont identiques aux fonctions correspondantes sans le suffixe **_L** , sauf qu’elles utilisent à la place les paramètres régionaux transmis. Pour plus d’informations, consultez [Locale](../../c-runtime-library/locale.md).

Si *endptr* n’a pas la **valeur null**, un pointeur vers le caractère qui a arrêté l’analyse est stocké à l’emplacement désigné par *endptr*. Si aucune conversion ne peut être effectuée (aucun chiffre valide n’a été trouvé ou une base non valide a été spécifiée), la valeur de *strSource* est stockée à l’emplacement désigné par *endptr*.

**strtol** attend que *strSource* pointe vers une chaîne au format suivant :

> [*whitespace*] [{ **+** &#124; **-** }] [**0** [{ **x** &#124; **X** }]] [*digits*  &#124; *letters*]

Un espace *blanc* peut se composer d’espaces et de caractères de tabulation, qui sont ignorés ; les *chiffres* correspondent à un ou plusieurs chiffres décimaux ; les *lettres* sont une ou plusieurs lettres de « a » à « z » (ou de « a » à « z »).  Le premier caractère qui ne correspond pas à ce format a pour effet d’arrêter l’analyse. Si la *base* est comprise entre 2 et 36, elle est utilisée comme base du nombre. Si *base* a la valeur 0, les caractères initiaux de la chaîne vers laquelle pointe *strSource* sont utilisés pour déterminer la base. Si le premier caractère est 0 et que le deuxième est différent de « x » ou « X », la chaîne est interprétée comme étant un entier octal. Si le premier caractère est « 0 » et que le deuxième est « x » ou « X », la chaîne est interprétée comme étant un entier hexadécimal. Si le premier caractère est un chiffre compris entre « 1 » et « 9 », la chaîne est interprétée comme étant un entier décimal. Les lettres de « a » à « z » (ou de « A » à « Z ») se voient affecter des valeurs comprises entre 10 et 35 ; seules sont autorisées les lettres dont les valeurs affectées sont inférieures à la *base*. Le premier caractère situé en dehors de la plage de la base a pour effet d’arrêter l’analyse. Par exemple, si *base* a la valeur 0 et que le premier caractère analysé est « 0 », un entier octal est supposé et un caractère « 8 » ou « 9 » arrête l’analyse.

## <a name="requirements"></a>Configuration requise

|Routine|En-tête requis|
|-------------|---------------------|
|**strtol**|\<stdlib.h>|
|**wcstol**|\<stdlib.h> ou \<wchar.h>|
|**_strtol_l**|\<stdlib.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

Consultez l’exemple relatif à [strtod](strtod-strtod-l-wcstod-wcstod-l.md).

## <a name="see-also"></a>Voir aussi

[Conversion de données](../../c-runtime-library/data-conversion.md)<br/>
[Paramètres régionaux](../../c-runtime-library/locale.md)<br/>
[localeconv](localeconv.md)<br/>
[setlocale, _wsetlocale](setlocale-wsetlocale.md)<br/>
[Fonctions de valeur chaîne en valeur numérique](../../c-runtime-library/string-to-numeric-value-functions.md)<br/>
[strtod, _strtod_l, wcstod, _wcstod_l](strtod-strtod-l-wcstod-wcstod-l.md)<br/>
[strtoul, _strtoul_l, wcstoul, _wcstoul_l](strtoul-strtoul-l-wcstoul-wcstoul-l.md)<br/>
[atof, _atof_l, _wtof, _wtof_l](atof-atof-l-wtof-wtof-l.md)<br/>
