---
title: strtoul, _strtoul_l, wcstoul, _wcstoul_l
ms.date: 11/04/2016
api_name:
- _wcstoul_l
- _strtoul_l
- strtoul
- wcstoul
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
- ntoskrnl.exe
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- strtoul
- _tcstoul
- wcstoul
helpviewer_keywords:
- _wcstoul_l function
- _tcstoul function
- _strtoul_l function
- string conversion, to integers
- wcstoul function
- strtoul function
- wcstoul_l function
- strtoul_l function
- tcstoul function
ms.assetid: 38f2afe8-8178-4e0b-8bbe-d5c6ad66e3ab
ms.openlocfilehash: 29edd517b9aa4737497a36557820bf45b6b9804f
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70946325"
---
# <a name="strtoul-_strtoul_l-wcstoul-_wcstoul_l"></a>strtoul, _strtoul_l, wcstoul, _wcstoul_l

Convertit les chaînes en valeur entière de type long non signée.

## <a name="syntax"></a>Syntaxe

```C
unsigned long strtoul(
   const char *strSource,
   char **endptr,
   int base
);
unsigned long _strtoul_l(
   const char *strSource,
   char **endptr,
   int base,
   _locale_t locale
);
unsigned long wcstoul(
   const wchar_t *strSource,
   wchar_t **endptr,
   int base
);
unsigned long _wcstoul_l(
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

**strtoul** retourne la valeur convertie, le cas échéant, ou **ULONG_MAX** en cas de dépassement de capacité. **strtoul** retourne 0 si aucune conversion ne peut être effectuée. **wcstoul** retourne des valeurs de façon analogue à **strtoul**. Pour les deux fonctions, **errno** a la valeur **ERANGE** si le dépassement de capacité positif ou négatif se produit.

Pour plus d’informations sur ce code de retour et sur les autres codes, consultez [_doserrno, errno, _sys_errlist, and _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) .

## <a name="remarks"></a>Notes

Chacune de ces fonctions convertit la chaîne d’entrée *strSource* en une valeur **unsigned** **long**.

**strtoul** arrête de lire la chaîne *strSource* au premier caractère qu’elle ne peut pas reconnaître comme faisant partie d’un nombre. Il peut s’agir du caractère null de fin, ou il peut s’agir du premier caractère numérique supérieur ou égal à *base*. Le paramètre de catégorie **LC_NUMERIC** des paramètres régionaux détermine la reconnaissance du caractère de base dans *strSource*; Pour plus d’informations, consultez [setlocale](setlocale-wsetlocale.md). **strtoul** et **wcstoul** utilisent les paramètres régionaux actuels. **_strtoul_l** et **_wcstoul_l** sont identiques, sauf qu’ils utilisent à la place les paramètres régionaux transmis. Pour plus d’informations, consultez [Locale](../../c-runtime-library/locale.md).

Si *endptr* n’a pas la **valeur null**, un pointeur vers le caractère qui a arrêté l’analyse est stocké à l’emplacement désigné par *endptr*. Si aucune conversion ne peut être effectuée (aucun chiffre valide n’a été trouvé ou une base non valide a été spécifiée), la valeur de *strSource* est stockée à l’emplacement désigné par *endptr*.

**wcstoul** est une version à caractères larges de **strtoul**; son argument *strSource* est une chaîne de caractères larges. Sinon, ces fonctions se comportent de façon identique.

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine TCHAR.H|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcstoul**|**strtoul**|**strtoul**|**wcstoul**|
|**_tcstoul_l**|**strtoul_l**|**_strtoul_l**|**_wcstoul_l**|

**strtoul** attend que *strSource* pointe vers une chaîne au format suivant :

> [*whitespace*] [{ **+** &#124; **-** }] [**0** [{ **x** &#124; **X** }]] [*digits*  &#124; *letters*]

Un espace *blanc* peut se composer d’espaces et de caractères de tabulation, qui sont ignorés. les *chiffres* correspondent à un ou plusieurs chiffres décimaux. les *lettres* sont une ou plusieurs lettres de « a » à « z » (ou de « a » à « z »). Le premier caractère qui ne correspond pas à ce format a pour effet d’arrêter l’analyse. Si la *base* est comprise entre 2 et 36, elle est utilisée comme base du nombre. Si *base* a la valeur 0, les caractères initiaux de la chaîne vers laquelle pointe *strSource* sont utilisés pour déterminer la base. Si le premier caractère est 0 et que le deuxième est différent de « x » ou « X », la chaîne est interprétée comme étant un entier octal. Si le premier caractère est « 0 » et que le deuxième est « x » ou « X », la chaîne est interprétée comme étant un entier hexadécimal. Si le premier caractère est un chiffre compris entre « 1 » et « 9 », la chaîne est interprétée comme étant un entier décimal. Les lettres de « a » à « z » (ou de « A » à « Z ») se voient affecter des valeurs comprises entre 10 et 35 ; seules sont autorisées les lettres dont les valeurs affectées sont inférieures à la *base*. Le premier caractère situé en dehors de la plage de la base a pour effet d’arrêter l’analyse. Par exemple, si *base* a la valeur 0 et que le premier caractère analysé est « 0 », un entier octal est supposé et un caractère « 8 » ou « 9 » arrête l’analyse. **strtoul** autorise un préfixe **+** de signe plus ( **-** ) ou moins (); un signe moins de début indique que la valeur de retour est négative.

## <a name="requirements"></a>Configuration requise

|Routine|En-tête requis|
|-------------|---------------------|
|**strtoul**|\<stdlib.h>|
|**wcstoul**|\<stdlib.h> ou \<wchar.h>|
|**_strtoul_l**|\<stdlib.h>|
|**_wcstoul_l**|\<stdlib.h> ou \<wchar.h>|

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
[strtol, wcstol, _strtol_l, _wcstol_l](strtol-wcstol-strtol-l-wcstol-l.md)<br/>
[atof, _atof_l, _wtof, _wtof_l](atof-atof-l-wtof-wtof-l.md)<br/>
