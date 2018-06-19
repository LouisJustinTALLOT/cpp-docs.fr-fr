---
title: _strtoui64, _wcstoui64, _strtoui64_l, _wcstoui64_l | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _strtoui64
- _strtoui64_l
- _wcstoui64
- _wcstoui64_l
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
- _wcstoui64_l
- strtoui64_l
- wcstoui64
- _wcstoui64
- _strtoui64_l
- strtoui64
- _strtoui64
- wcstoui64_l
dev_langs:
- C++
helpviewer_keywords:
- _strtoui64_l function
- _wcstoui64_l function
- string conversion, to integers
- wcstoui64_l function
- _strtoui64 function
- _wcstoui64 function
- wcstoui64 function
- strtoui64_l function
- strtoui64 function
ms.assetid: 7fcb537e-4554-4ceb-a5b6-bc09244e72ef
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ab70c1d74c0db837ba3d8e453988ca441f6fc06d
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32417880"
---
# <a name="strtoui64-wcstoui64-strtoui64l-wcstoui64l"></a>_strtoui64, _wcstoui64, _strtoui64_l, _wcstoui64_l

Convertir une chaîne non **__int64** valeur.

## <a name="syntax"></a>Syntaxe

```C
unsigned __int64 _strtoui64(
   const char *strSource,
   char **endptr,
   int base
);
unsigned __int64 _wcstoui64(
   const wchar_t *strSource,
   wchar_t **endptr,
   int base
);
unsigned __int64 _strtoui64_l(
   const char *strSource,
   char **endptr,
   int base,
   _locale_t locale
);
unsigned __int64 _wcstoui64(
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

**_strtoui64** retourne la valeur représentée dans la chaîne *strSource*, sauf lors de la représentation sous forme de risque d’entraîner un dépassement de capacité, auquel cas il retourne **_UI64_MAX**. **_strtoui64** retourne 0 si aucune conversion ne peut être effectuée.

**_UI64_MAX** est défini dans les limites. H.

Si *strSource* est **NULL** ou *base* est différente de zéro et inférieure à 2 ou supérieure à 36, **errno** a la valeur **EINVAL** .

Pour plus d’informations sur ces codes de retour et les autres, consultez [_doserrno, errno, _sys_errlist et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Notes

Le **_strtoui64** fonction convertit *strSource* à un **non signé** **__int64**. **_wcstoui64** est une version à caractères larges de **_strtoui64**; sa *strSource* argument est une chaîne à caractères larges. Sinon, ces fonctions se comportent de façon identique.

Les deux fonctions arrêter la lecture de la chaîne *strSource* au premier caractère ne reconnaît pas comme partie d’un nombre. Cela peut être le caractère null de fin, ou il peut être le premier caractère numérique supérieur ou égal à *base*.

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine TCHAR.H|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcstoui64**|**_strtoui64**|**_strtoui64**|**_wstrtoui64**|
|**_tcstoui64_l**|**_strtoui64_l**|**_strtoui64_l**|**_wstrtoui64_l**|

Les paramètres régionaux actuels **LC_NUMERIC** catégorie détermine la reconnaissance du caractère de base *strSource*; pour plus d’informations, consultez [setlocale](setlocale-wsetlocale.md). Les fonctions sans le suffixe _l utilisent les paramètres régionaux ; **_strtoui64_l** et **_wcstoui64_l** sont identiques aux fonctions correspondantes sans le **_l** suffixe, sauf qu’elles utilisent les paramètres régionaux passé à la place. Pour plus d’informations, consultez [Locale](../../c-runtime-library/locale.md).

Si *endptr* n’est pas **NULL**, un pointeur vers le caractère qui l’a arrêté l’analyse est stocké à l’emplacement vers lequel pointé *endptr*. Si aucune conversion ne peut être effectuée (aucun chiffre valide a été trouvé ou une base non valide a été spécifiée), la valeur de *strSource* est stocké à l’emplacement vers lequel pointé *endptr*.

**_strtoui64** attend *strSource* pour pointer vers une chaîne sous la forme suivante :

> [*espace blanc*] [{**+** &#124; **-**}] [**0** [{ **x** &#124; **X** }]] [*chiffres* &#124; *lettres*]  

A *espace blanc* peut contenir les caractères espace et la tabulation, qui sont ignorés. *chiffres* sont un ou plusieurs chiffres décimaux. *lettres* sont une ou plusieurs des lettres 'a' 'z' via (ou un 'A' à 'Z'). Le premier caractère qui ne correspond pas à ce format a pour effet d’arrêter l’analyse. Si *base* est comprise entre 2 et 36, il est utilisé comme base du nombre. Si *base* est 0, les premiers caractères de la chaîne pointée par *strSource* servent à déterminer la base. Si le premier caractère est 0 et que le deuxième est différent de « x » ou « X », la chaîne est interprétée comme étant un entier octal. Si le premier caractère est « 0 » et que le deuxième est « x » ou « X », la chaîne est interprétée comme étant un entier hexadécimal. Si le premier caractère est un chiffre compris entre « 1 » et « 9 », la chaîne est interprétée comme étant un entier décimal. Les lettres de « a » à « z » (ou de « A » à « Z ») se voient affecter des valeurs comprises entre 10 et 35 ; seules sont autorisées les lettres dont les valeurs affectées sont inférieures à la *base*. Le premier caractère situé en dehors de la plage de la base a pour effet d’arrêter l’analyse. Par exemple, si *base* est 0 et le premier caractère analysé est « 0 », un entier octal est supposé et un caractère '8' ou '9' arrête l’analyse.

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**_strtoui64**|\<stdlib.h>|
|**_wcstoui64**|\<stdlib.h> ou \<wchar.h>|
|**_strtoui64_l**|\<stdlib.h>|
|**_wcstoui64_l**|\<stdlib.h> ou \<wchar.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

```C
// crt_strtoui64.c
#include <stdio.h>

unsigned __int64 atoui64(const char *szUnsignedInt) {
   return _strtoui64(szUnsignedInt, NULL, 10);
}

int main() {
   unsigned __int64 u = atoui64("18446744073709551615");
   printf( "u = %I64u\n", u );
}
```

```Output
u = 18446744073709551615
```

## <a name="see-also"></a>Voir aussi

[Conversion de données](../../c-runtime-library/data-conversion.md)<br/>
[Paramètres régionaux](../../c-runtime-library/locale.md)<br/>
[localeconv](localeconv.md)<br/>
[setlocale, _wsetlocale](setlocale-wsetlocale.md)<br/>
[Fonctions de valeur chaîne en valeur numérique](../../c-runtime-library/string-to-numeric-value-functions.md)<br/>
[strtod, _strtod_l, wcstod, _wcstod_l](strtod-strtod-l-wcstod-wcstod-l.md)<br/>
[strtoul, _strtoul_l, wcstoul, _wcstoul_l](strtoul-strtoul-l-wcstoul-wcstoul-l.md)<br/>
[atof, _atof_l, _wtof, _wtof_l](atof-atof-l-wtof-wtof-l.md)<br/>
