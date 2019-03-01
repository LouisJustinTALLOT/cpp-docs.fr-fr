---
title: strtoul, _strtoul_l, wcstoul, _wcstoul_l
ms.date: 11/04/2016
apiname:
- _wcstoul_l
- _strtoul_l
- strtoul
- wcstoul
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
- api-ms-win-crt-convert-l1-1-0.dll
- ntoskrnl.exe
apitype: DLLExport
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
ms.openlocfilehash: d4d974084c9249740d565f879f471bc7dfc697bd
ms.sourcegitcommit: e06648107065f3dea35f40c1ae5999391087b80b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/01/2019
ms.locfileid: "57210781"
---
# <a name="strtoul-strtoull-wcstoul-wcstoull"></a>strtoul, _strtoul_l, wcstoul, _wcstoul_l

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

**strtoul** retourne la valeur convertie, le cas échéant, ou **ULONG_MAX** de dépassement de capacité. **strtoul** retourne 0 si aucune conversion ne peut être effectuée. **wcstoul** retourne des valeurs de façon analogue à **strtoul**. Pour les deux fonctions, **errno** a la valeur **ERANGE** si dépassement de capacité positif ou négatif se produit.

Pour plus d’informations sur ce code de retour et sur les autres codes, consultez [_doserrno, errno, _sys_errlist, and _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) .

## <a name="remarks"></a>Notes

Chacune de ces fonctions convertit la chaîne d’entrée *strSource* à un **non signé** **long**.

**strtoul** arrête la lecture de la chaîne *strSource* au premier caractère qu’il ne peut pas identifier comme partie d’un nombre. Cela peut être le caractère null de fin, ou il peut être le premier caractère numérique supérieur ou égal à *base*. Le **LC_NUMERIC** paramètre de catégorie de paramètres régionaux détermine la reconnaissance du caractère de base dans *strSource*; pour plus d’informations, consultez [setlocale](setlocale-wsetlocale.md). **strtoul** et **wcstoul** utilisent le paramètres régionaux actifs ; **_strtoul_l** et **_wcstoul_l** sont identiques, sauf qu’ils utilisent les paramètres régionaux à la place. Pour plus d’informations, consultez [Locale](../../c-runtime-library/locale.md).

Si *endptr* n’est pas **NULL**, un pointeur désignant le caractère qui a arrêté l’analyse est stocké à l’emplacement vers lequel pointé *endptr*. Si aucune conversion ne peut être effectuée (aucun chiffre valide a été trouvé ou une base non valide a été spécifiée), la valeur de *strSource* est stocké à l’emplacement vers lequel pointé *endptr*.

**wcstoul** est une version à caractères larges de **strtoul**; son *strSource* argument est une chaîne de caractères larges. Sinon, ces fonctions se comportent de façon identique.

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine TCHAR.H|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcstoul**|**strtoul**|**strtoul**|**wcstoul**|
|**_tcstoul_l**|**strtoul_l**|**_strtoul_l**|**_wcstoul_l**|

**strtoul** attend *strSource* pour pointer vers une chaîne au format suivant :

> [*whitespace*] [{**+** &#124; **-**}] [**0** [{ **x** &#124; **X** }]] [*digits*  &#124; *letters*]

Un *espace blanc* peut se composer d’espaces et tabulations, qui sont ignorés. *chiffres* représente un ou plusieurs chiffres décimaux. *lettres* sont un ou plusieurs des lettres « a » 'z' via (ou un « A » à « Z »). Le premier caractère qui ne correspond pas à ce format a pour effet d’arrêter l’analyse. Si *base* est comprise entre 2 et 36, elle est utilisée comme base du nombre. Si *base* est 0, les premiers caractères de la chaîne pointée par *strSource* servent à déterminer la base. Si le premier caractère est 0 et que le deuxième est différent de « x » ou « X », la chaîne est interprétée comme étant un entier octal. Si le premier caractère est « 0 » et que le deuxième est « x » ou « X », la chaîne est interprétée comme étant un entier hexadécimal. Si le premier caractère est un chiffre compris entre « 1 » et « 9 », la chaîne est interprétée comme étant un entier décimal. Les lettres de « a » à « z » (ou de « A » à « Z ») se voient affecter des valeurs comprises entre 10 et 35 ; seules sont autorisées les lettres dont les valeurs affectées sont inférieures à la *base*. Le premier caractère situé en dehors de la plage de la base a pour effet d’arrêter l’analyse. Par exemple, si *base* est égal à 0 et le premier caractère analysé est « 0 », un entier octal est supposé et un caractère « 8 » ou « 9 » s’arrête l’analyse. **strtoul** permet un signe plus (**+**) ou moins (**-**) de préfixe ; un signe moins de début indique que la valeur de retour est inversée.

## <a name="requirements"></a>Spécifications

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
