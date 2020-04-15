---
title: _strtoi64, _wcstoi64, _strtoi64_l, _wcstoi64_l
ms.date: 4/2/2020
api_name:
- _strtoi64
- _strtoi64_l
- _wcstoi64_l
- _wcstoi64
- _o__strtoi64
- _o__strtoi64_l
- _o__wcstoi64
- _o__wcstoi64_l
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
- _strtoi64
- strtoi64
- _stroi64_l
- _wcstoi64_l
- wcstoi64_l
- _wcstoi64
- wcstoi64
- strtoi64_l
helpviewer_keywords:
- _strtoi64 function
- _wcstoi64 function
- _strtoi64_l function
- string conversion, to integers
- _wcstoi64_l function
- strtoi64_l function
- wcstoi64 function
- strtoi64 function
- wcstoi64_l function
ms.assetid: ea2abc50-7bfe-420e-a46b-703c3153593a
ms.openlocfilehash: 8dcdff4cf6f3eff191dc126583c1ca8290133e02
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365128"
---
# <a name="_strtoi64-_wcstoi64-_strtoi64_l-_wcstoi64_l"></a>_strtoi64, _wcstoi64, _strtoi64_l, _wcstoi64_l

Convertir une corde en valeur **__int64.**

## <a name="syntax"></a>Syntaxe

```C
__int64 _strtoi64(
   const char *strSource,
   char **endptr,
   int base
);
__int64 _wcstoi64(
   const wchar_t *strSource,
   wchar_t **endptr,
   int base
);
__int64 _strtoi64_l(
   const char *strSource,
   char **endptr,
   int base,
   _locale_t locale
);
__int64 _wcstoi64_l(
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

**_strtoi64** retourne la valeur représentée dans la chaîne *strSource*, sauf lorsque la représentation provoquerait un débordement, auquel cas il retourne **_I64_MAX** ou **_I64_MIN**. La fonction retourne 0 si aucune conversion ne peut être effectuée. **_wcstoi64** renvoie des valeurs de manière analogue à **strtoi64**.

**_I64_MAX** et **_I64_MIN** sont définis dans LIMITS. H.

Si *strSource* est **NULL** ou que la *base* n’est pas zéro et moins de 2 ou plus de 36, **errno** est réglé sur **EINVAL**.

Voir [_doserrno, errno, _sys_errlist, et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) pour plus d’informations sur ces codes de retour, et d’autres.

## <a name="remarks"></a>Notes

La fonction **_strtoi64** convertit *strSource* en **__int64**. Les deux fonctions cessent de lire la chaîne *strSource* au premier caractère qu’ils ne peuvent pas reconnaître comme faisant partie d’un certain nombre. Il peut s’agir du caractère nul qui met fin, ou il peut s’agir du premier caractère numérique supérieur ou égal à *la base.* **_wcstoi64** est une version à caractère large de **_strtoi64**; son argument *strSource* est une chaîne de caractère large. Ces fonctions se comportent sinon de façon identique.

Par défaut, l’état global de cette fonction est étendue à l’application. Pour changer cela, voir [Global State dans le CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine TCHAR.H|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcstoi64**|**_strtoi64**|**_strtoi64**|**_wcstoi64**|
|**_tcstoi64_l**|**_strtoi64_l**|**_strtoi64_l**|**_wcstoi64_l**|

Le cadre de la catégorie **LC_NUMERIC** du lieu détermine la reconnaissance du caractère radix dans *strSource*; pour plus d’informations, voir [setlocale](setlocale-wsetlocale.md). Les fonctions sans le suffixe _l utilisent le lieu actuel; **_strtoi64_l** et **_wcstoi64_l** sont identiques à la fonction correspondante sans le **suffixe _l,** sauf qu’ils utilisent le lieu passé à la place. Pour plus d’informations, consultez [Locale](../../c-runtime-library/locale.md).

Si *endptr n’est* pas **NULL**, un pointeur sur le personnage qui a arrêté l’analyse est stocké à l’emplacement indiqué par *endptr*. Si aucune conversion ne peut être effectuée (aucun chiffre valide n’a été trouvé ou une base invalide a été spécifiée), la valeur de *strSource* est stockée à l’endroit indiqué par *endptr*.

**_strtoi64** s’attend à ce que *strSource* pointe vers une série de formulaires suivants :

> [*espace blanc*] [&#124;]**+** **-** [**0** **[x** &#124; **X]]** [*chiffres* &#124; *lettres*]

Un *espace blanc* peut se composer de caractères d’espace et d’onglet, qui sont ignorés ; *les chiffres* sont un ou plusieurs chiffres décimaux; *sont* une ou plusieurs des lettres 'a' par 'z' (ou 'A' par 'Z').  Le premier caractère qui ne correspond pas à ce format a pour effet d’arrêter l’analyse. Si *la base* se situe entre 2 et 36, elle est utilisée comme base du nombre. Si la *base* est de 0, les caractères initiaux de la chaîne pointées par *strSource* sont utilisés pour déterminer la base. Si le premier caractère est 0 et que le deuxième est différent de « x » ou « X », la chaîne est interprétée comme étant un entier octal. Si le premier caractère est « 0 » et que le deuxième est « x » ou « X », la chaîne est interprétée comme étant un entier hexadécimal. Si le premier caractère est un chiffre compris entre « 1 » et « 9 », la chaîne est interprétée comme étant un entier décimal. Les lettres de « a » à « z » (ou de « A » à « Z ») se voient affecter des valeurs comprises entre 10 et 35 ; seules sont autorisées les lettres dont les valeurs affectées sont inférieures à la *base*. Le premier caractère situé en dehors de la plage de la base a pour effet d’arrêter l’analyse. Par exemple, si la *base* est de 0 et que le premier personnage numérisé est ' 0', un intégrisé octal est supposé et un caractère '8' ou '9' arrêtera l’analyse.

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**_strtoi64**, **_strtoi64_l**|\<stdlib.h>|
|**_wcstoi64**, **_wcstoi64_l**|\<stdlib.h> ou \<wchar.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[Conversion de données](../../c-runtime-library/data-conversion.md)<br/>
[Local](../../c-runtime-library/locale.md)<br/>
[localeconv](localeconv.md)<br/>
[setlocale, _wsetlocale](setlocale-wsetlocale.md)<br/>
[Fonctions de valeur chaîne en valeur numérique](../../c-runtime-library/string-to-numeric-value-functions.md)<br/>
[strtod, _strtod_l, wcstod, _wcstod_l](strtod-strtod-l-wcstod-wcstod-l.md)<br/>
[strtoul, _strtoul_l, wcstoul, _wcstoul_l](strtoul-strtoul-l-wcstoul-wcstoul-l.md)<br/>
[atof, _atof_l, _wtof, _wtof_l](atof-atof-l-wtof-wtof-l.md)<br/>
