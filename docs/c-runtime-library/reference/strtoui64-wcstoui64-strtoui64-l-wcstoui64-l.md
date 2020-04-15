---
title: _strtoui64, _wcstoui64, _strtoui64_l, _wcstoui64_l
ms.date: 4/2/2020
api_name:
- _strtoui64
- _strtoui64_l
- _wcstoui64
- _wcstoui64_l
- _o__strtoui64
- _o__strtoui64_l
- _o__wcstoui64
- _o__wcstoui64_l
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
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _wcstoui64_l
- strtoui64_l
- wcstoui64
- _wcstoui64
- _strtoui64_l
- strtoui64
- _strtoui64
- wcstoui64_l
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
ms.openlocfilehash: f3c5631a34c35ed5f5b74e15dfc4225224215b89
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365464"
---
# <a name="_strtoui64-_wcstoui64-_strtoui64_l-_wcstoui64_l"></a>_strtoui64, _wcstoui64, _strtoui64_l, _wcstoui64_l

Convertir une corde en une valeur **__int64** non signée.

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

*strSource (en)*<br/>
Chaîne se terminant par un caractère Null à convertir.

*endptr*<br/>
Pointeur désignant le caractère qui arrête l’analyse.

*base*<br/>
Base numérique à utiliser.

*locale*<br/>
Paramètres régionaux à utiliser.

## <a name="return-value"></a>Valeur de retour

**_strtoui64** retourne la valeur représentée dans la chaîne *strSource*, sauf lorsque la représentation provoquerait un débordement, auquel cas il retourne **_UI64_MAX**. **_strtoui64** renvoie 0 si aucune conversion ne peut être effectuée.

**_UI64_MAX** est définie dans LIMITS. H.

Si *strSource* est **NULL** ou que la *base* n’est pas zéro et moins de 2 ou plus de 36, **errno** est réglé sur **EINVAL**.

Voir [_doserrno, errno, _sys_errlist, et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) pour plus d’informations sur ces codes de retour, et d’autres.

## <a name="remarks"></a>Notes

La fonction **_strtoui64** convertit *strSource* en une **__int64** **non signée.** **_wcstoui64** est une version à caractère large de **_strtoui64**; son argument *strSource* est une chaîne de caractère large. Sinon, ces fonctions se comportent de façon identique.

Les deux fonctions cessent de lire la chaîne *strSource* au premier caractère qu’ils ne peuvent pas reconnaître comme faisant partie d’un certain nombre. Il peut s’agir du caractère nul qui met fin, ou il peut s’agir du premier caractère numérique supérieur ou égal à *la base.*

Par défaut, l’état global de cette fonction est étendue à l’application. Pour changer cela, voir [Global State dans le CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine TCHAR.H|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcstoui64**|**_strtoui64**|**_strtoui64**|**_wstrtoui64**|
|**_tcstoui64_l**|**_strtoui64_l**|**_strtoui64_l**|**_wstrtoui64_l**|

Le cadre de la catégorie **LC_NUMERIC** de l’endroit actuel détermine la reconnaissance du caractère radix dans *strSource*; pour plus d’informations, voir [setlocale](setlocale-wsetlocale.md). Les fonctions sans le suffixe _l utilisent le lieu actuel; **_strtoui64_l** et **_wcstoui64_l** sont identiques aux fonctions correspondantes sans le **suffixe _l,** sauf qu’ils utilisent le lieu passé à la place. Pour plus d’informations, consultez [Locale](../../c-runtime-library/locale.md).

Si *endptr n’est* pas **NULL**, un pointeur sur le personnage qui a arrêté l’analyse est stocké à l’emplacement indiqué par *endptr*. Si aucune conversion ne peut être effectuée (aucun chiffre valide n’a été trouvé ou une base invalide a été spécifiée), la valeur de *strSource* est stockée à l’endroit indiqué par *endptr*.

**_strtoui64** s’attend à ce que *strSource* pointe vers une série de formulaires suivants :

> [*espace blanc*] [&#124;]**+** **-** [**0** **[x** &#124; **X]]** [*chiffres* &#124; *lettres*]

Un *espace blanc* peut se composer de caractères d’espace et d’onglet, qui sont ignorés. *les chiffres* sont un ou plusieurs chiffres décimaux. *sont* une ou plusieurs des lettres 'a' par 'z' (ou 'A' par 'Z'). Le premier caractère qui ne correspond pas à ce format a pour effet d’arrêter l’analyse. Si *la base* se situe entre 2 et 36, elle est utilisée comme base du nombre. Si la *base* est de 0, les caractères initiaux de la chaîne pointées par *strSource* sont utilisés pour déterminer la base. Si le premier caractère est 0 et que le deuxième est différent de « x » ou « X », la chaîne est interprétée comme étant un entier octal. Si le premier caractère est « 0 » et que le deuxième est « x » ou « X », la chaîne est interprétée comme étant un entier hexadécimal. Si le premier caractère est un chiffre compris entre « 1 » et « 9 », la chaîne est interprétée comme étant un entier décimal. Les lettres de « a » à « z » (ou de « A » à « Z ») se voient affecter des valeurs comprises entre 10 et 35 ; seules sont autorisées les lettres dont les valeurs affectées sont inférieures à la *base*. Le premier caractère situé en dehors de la plage de la base a pour effet d’arrêter l’analyse. Par exemple, si la *base* est de 0 et que le premier personnage numérisé est ' 0', un intégrisé octal est supposé et un caractère '8' ou '9' arrêtera l’analyse.

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
[Local](../../c-runtime-library/locale.md)<br/>
[localeconv](localeconv.md)<br/>
[setlocale, _wsetlocale](setlocale-wsetlocale.md)<br/>
[Fonctions de valeur chaîne en valeur numérique](../../c-runtime-library/string-to-numeric-value-functions.md)<br/>
[strtod, _strtod_l, wcstod, _wcstod_l](strtod-strtod-l-wcstod-wcstod-l.md)<br/>
[strtoul, _strtoul_l, wcstoul, _wcstoul_l](strtoul-strtoul-l-wcstoul-wcstoul-l.md)<br/>
[atof, _atof_l, _wtof, _wtof_l](atof-atof-l-wtof-wtof-l.md)<br/>
