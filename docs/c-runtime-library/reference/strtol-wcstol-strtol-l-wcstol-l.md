---
title: strtol, wcstol, _strtol_l, _wcstol_l
ms.date: 11/04/2016
apiname:
- strtol
- wcstol
- _strtol_l
- _wcstol_l
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
apitype: DLLExport
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
ms.openlocfilehash: 73df5dd3ffcd4a9b2fca8b6b713b645ef94addb5
ms.sourcegitcommit: 1819bd2ff79fba7ec172504b9a34455c70c73f10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2018
ms.locfileid: "51326717"
---
# <a name="strtol-wcstol-strtoll-wcstoll"></a>strtol, wcstol, _strtol_l, _wcstol_l

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

**strtol** retourne la valeur représentée dans la chaîne *strSource*, sauf lors de la représentation entraînerait un dépassement de capacité, auquel cas il retourne **LONG_MAX** ou **LONG_ MIN**. **strtol** retourne 0 si aucune conversion ne peut être effectuée. **wcstol** retourne des valeurs de façon analogue à **strtol**. Pour les deux fonctions, **errno** a la valeur **ERANGE** si dépassement de capacité positif ou négatif se produit.

Pour plus d’informations sur ces codes de retour et les autres, consultez [_doserrno, errno, _sys_errlist et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Notes

Le **strtol** fonction convertit *strSource* à un **long**. **strtol** arrête la lecture de la chaîne *strSource* au premier caractère qu’il ne peut pas identifier comme partie d’un nombre. Cela peut être le caractère null de fin, ou il peut être le premier caractère numérique supérieur ou égal à *base*.

**wcstol** est une version à caractères larges de **strtol**; son *strSource* argument est une chaîne de caractères larges. Ces fonctions se comportent sinon de façon identique.

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine TCHAR.H|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcstol**|**strtol**|**strtol**|**wcstol**|
|**_tcstol_l**|**_strtol_l**|**_strtol_l**|**_wcstol_l**|

Les paramètres régionaux actuels **LC_NUMERIC** paramètre de catégorie détermine la reconnaissance du caractère de base dans *strSource*; pour plus d’informations, consultez [setlocale](setlocale-wsetlocale.md). Les fonctions sans le **_l** suffixe utiliser les paramètres régionaux actifs ; **_strtol_l** et **_wcstol_l** sont identiques aux fonctions correspondantes sans le **_l** suffixe, sauf qu’ils utilisent les paramètres régionaux à la place. Pour plus d’informations, consultez [Locale](../../c-runtime-library/locale.md).

Si *endptr* n’est pas **NULL**, un pointeur désignant le caractère qui a arrêté l’analyse est stocké à l’emplacement vers lequel pointé *endptr*. Si aucune conversion ne peut être effectuée (aucun chiffre valide a été trouvé ou une base non valide a été spécifiée), la valeur de *strSource* est stocké à l’emplacement vers lequel pointé *endptr*.

**strtol** attend *strSource* pour pointer vers une chaîne au format suivant :

> [*espace blanc*] [{**+** &#124; **-**}] [**0** [{ **x** &#124; **X** }]] [*chiffres* &#124; *lettres*]  

Un *espace blanc* peut se composer d’espaces et tabulations, qui sont ignorés ; *chiffres* représente un ou plusieurs chiffres décimaux ; *lettres* sont un ou plusieurs des lettres « a » 'z' via (ou un « A » à « Z »).  Le premier caractère qui ne correspond pas à ce format a pour effet d’arrêter l’analyse. Si *base* est comprise entre 2 et 36, elle est utilisée comme base du nombre. Si *base* est 0, les premiers caractères de la chaîne pointée par *strSource* servent à déterminer la base. Si le premier caractère est 0 et que le deuxième est différent de « x » ou « X », la chaîne est interprétée comme étant un entier octal. Si le premier caractère est « 0 » et que le deuxième est « x » ou « X », la chaîne est interprétée comme étant un entier hexadécimal. Si le premier caractère est un chiffre compris entre « 1 » et « 9 », la chaîne est interprétée comme étant un entier décimal. Les lettres de « a » à « z » (ou de « A » à « Z ») se voient affecter des valeurs comprises entre 10 et 35 ; seules sont autorisées les lettres dont les valeurs affectées sont inférieures à la *base*. Le premier caractère situé en dehors de la plage de la base a pour effet d’arrêter l’analyse. Par exemple, si *base* est égal à 0 et le premier caractère analysé est « 0 », un entier octal est supposé et un caractère « 8 » ou « 9 » s’arrête l’analyse.

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
