---
title: strtoll, _strtoll_l, wcstoll, _wcstoll_l | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- strtoll
- wcstoll
- _strtoll_l
- _wcstoll_l
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
- _strtoll_l
- _tcstoll_l
- _tcstoll
- _wcstoll_l
- strtoll
- wcstoll
dev_langs:
- C++
helpviewer_keywords:
- _tcstoll_l function
- _wcstoll_l function
- strtoll function
- wcstoll function
- _tcstoll function
- _strtoll_l function
ms.assetid: e2d05dcf-d3b2-4291-9e60-dee77e540fd7
caps.latest.revision: 5
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 9138ec6a298c302446077a2c071aef659c9a0ccb
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/20/2018
---
# <a name="strtoll-strtolll-wcstoll-wcstolll"></a>strtoll, _strtoll_l, wcstoll, _wcstoll_l

Convertit une chaîne en un **long** **long** valeur.

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

**strtoll** retourne la valeur qui est représentée dans la chaîne *strSource*, sauf lorsque la représentation sous forme de provoquerait un dépassement de capacité, dans ce cas, elle retourne **LLONG_MAX** ou **LLONG_MIN**. La fonction retourne 0 si aucune conversion ne peut être effectuée. **wcstoll** renvoie les valeurs comme **strtoll**.

**LLONG_MAX** et **LLONG_MIN** sont définis dans les limites. H.

Si *strSource* est **NULL** ou *base* est différente de zéro et inférieure à 2 ou supérieure à 36, **errno** a la valeur **EINVAL** .

Pour plus d’informations sur les codes de retour, consultez [errno, _doserrno, _sys_errlist et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Notes

Le **strtoll** fonction convertit *strSource* à un **long** **long**. Les deux fonctions arrêter la lecture de la chaîne *strSource* au premier caractère ne reconnaît pas comme partie d’un nombre. Cela peut être le caractère null de fin, ou il peut être le premier caractère numérique qui est supérieur ou égal à *base*. **wcstoll** est une version à caractères larges de **strtoll**; sa *strSource* argument est une chaîne à caractères larges. Sinon, ces fonctions se comportent de façon identique.

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine TCHAR.H|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcstoll**|**strtoll**|**strtoll**|**wcstoll**|
|**_tcstoll_l**|**_strtoll_l**|**_strtoll_l**|**_wcstoll_l**|

Le paramètres régionaux **LC_NUMERIC** catégorie détermine la reconnaissance du caractère de base *strSource*; pour plus d’informations, consultez [setlocale, _wsetlocale](setlocale-wsetlocale.md). Les fonctions qui n’ont pas le **_l** suffixe utilisent les paramètres régionaux ; **_strtoll_l** et **_wcstoll_l** sont identiques aux fonctions correspondantes qui n’ont pas le suffixe, sauf qu’ils utilisent à la place les paramètres régionaux qui sont passé. Pour plus d’informations, consultez [Locale](../../c-runtime-library/locale.md).

Si *endptr* n’est pas **NULL**, un pointeur vers le caractère qui l’a arrêté l’analyse est stocké à l’emplacement qui est désigné par *endptr*. Si aucune conversion ne peut être effectuée (aucun chiffre valide a été trouvé ou une base non valide a été spécifiée), la valeur de *strSource* est stocké à l’emplacement qui est désigné par *endptr*.

**strtoll** attend *strSource* pour pointer vers une chaîne sous la forme suivante :

> [*espace blanc*] [{**+** &#124; **-**}] [**0** [{ **x** &#124; **X** }]] [*chiffres* &#124; *lettres*]  

A *espace blanc* peut contenir les caractères espace et la tabulation, qui sont ignorés ; *chiffres* sont un ou plusieurs chiffres décimaux ; *lettres* sont une ou plusieurs des lettres 'a' 'z' via (ou un 'A' à 'Z'). Le premier caractère qui ne correspond pas à ce format a pour effet d’arrêter l’analyse. Si *base* est comprise entre 2 et 36, il est utilisé comme base du nombre. Si *base* est 0, les premiers caractères de la chaîne qui pointe vers *strSource* servent à déterminer la base. Si le premier caractère est « 0 » et que le deuxième est différent de « x » ou « X », la chaîne est interprétée comme étant un entier octal. Si le premier caractère est « 0 » et que le deuxième est « x » ou « X », la chaîne est interprétée comme étant un entier hexadécimal. Si le premier caractère est un chiffre compris entre « 1 » et « 9 », la chaîne est interprétée comme étant un entier décimal. Les lettres de « a » à « z » (ou de « A » à « Z ») se voient affecter des valeurs comprises entre 10 et 35 ; seules sont autorisées les lettres dont les valeurs affectées sont inférieures à la *base*. Le premier caractère situé en dehors de la plage de la base a pour effet d’arrêter l’analyse. Par exemple, si *base* est 0 et le premier caractère analysé est « 0 », un entier octal est supposé et un caractère '8' ou '9' arrête l’analyse.

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
[Fonctions de valeur chaîne en valeur numérique](../../c-runtime-library/string-to-numeric-value-functions.md)<br/>
[strtod, _strtod_l, wcstod, _wcstod_l](strtod-strtod-l-wcstod-wcstod-l.md)<br/>
[strtol, wcstol, _strtol_l, _wcstol_l](strtol-wcstol-strtol-l-wcstol-l.md)<br/>
[strtoul, _strtoul_l, wcstoul, _wcstoul_l](strtoul-strtoul-l-wcstoul-wcstoul-l.md)<br/>
[atof, _atof_l, _wtof, _wtof_l](atof-atof-l-wtof-wtof-l.md)<br/>
