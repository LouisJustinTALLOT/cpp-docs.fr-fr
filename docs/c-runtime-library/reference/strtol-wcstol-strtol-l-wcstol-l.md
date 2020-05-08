---
title: strtol, wcstol, _strtol_l, _wcstol_l
ms.date: 4/2/2020
api_name:
- strtol
- wcstol
- _strtol_l
- _wcstol_l
- _o__strtol_l
- _o__wcstol_l
- _o_strtol
- _o_wcstol
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
no-loc:
- strtol
- wcstol
- _strtol_l
- _wcstol_l
- LONG_MAX
- LONG_MIN
- errno
- ERANGE
- EINVAL
- LC_NUMERIC
- _tcstol
- _tcstol_l
- localeconv
- setlocale
- _wsetlocale
- strtod
- _strtod_l
- wcstod
- _wcstod_l
- strtoll
- _strtoll_l
- wcstoll
- _wcstoll_l
- strtoul
- _strtoul_l
- wcstoul
- _wcstoul_l
- atof
- _atof_l
- _wtof
- _wtof_l
ms.openlocfilehash: cc54884cd32ffa9118abfb6d46d659125a44262c
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2020
ms.locfileid: "82912653"
---
# <a name="strtol-wcstol-_strtol_l-_wcstol_l"></a>strtol, wcstol, _strtol_l, _wcstol_l

Convertit des chaînes en valeur entière **longue** .

## <a name="syntax"></a>Syntaxe

```C
long strtol(
   const char *string,
   char **end_ptr,
   int base
);
long wcstol(
   const wchar_t *string,
   wchar_t **end_ptr,
   int base
);
long _strtol_l(
   const char *string,
   char **end_ptr,
   int base,
   _locale_t locale
);
long _wcstol_l(
   const wchar_t *string,
   wchar_t **end_ptr,
   int base,
   _locale_t locale
);
```

### <a name="parameters"></a>Paramètres

*chaîne*\
Chaîne se terminant par un caractère Null à convertir.

*end_ptr*\
Paramètre de sortie, défini pour pointer vers le caractère après le dernier caractère interprété. Ignoré, si **null**.

*base*\
Base numérique à utiliser.

*locale*\
Paramètres régionaux à utiliser.

## <a name="return-value"></a>Valeur de retour

**strtol**, **wcstol**, **_strtol_l**et **_wcstol_l** retournent la valeur représentée dans *String*. Elles retournent 0 si aucune conversion n’est possible. Lorsque la représentation provoque un dépassement de capacité, elles retournent **LONG_MAX** ou **LONG_MIN**.

**errno** a la valeur **ERANGE** si le dépassement de capacité positif ou négatif se produit. Elle est définie sur **EINVAL** si la *chaîne* est **null**. Ou, si *base* a une valeur différente de zéro et inférieure à 2, ou supérieure à 36. Pour plus d’informations sur **ERANGE**, **EINVAL**et d’autres codes de retour, consultez [_doserrno, errno, _sys_errlist et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Notes 

Les fonctions **strtol**, **wcstol**, **_strtol_l**et **_wcstol_l** convertissent une *chaîne* en valeur **long**. Ils cessent de lire la *chaîne* au premier caractère qui n’est pas reconnu comme faisant partie d’un nombre. Il peut s’agir du caractère de fin-null ou du premier caractère alphanumérique supérieur ou égal à *base*.

**wcstol** et **_wcstol_l** sont des versions à caractères larges de **strtol** et de **_strtol_l**. Leur argument de *chaîne* est une chaîne de caractères larges. Ces fonctions se comportent de la même façon que **strtol** et **_strtol_l** dans le cas contraire. Le paramètre de catégorie **LC_NUMERIC** des paramètres régionaux détermine la reconnaissance du caractère de base (marque fractionnaire ou virgule décimale) dans la *chaîne*. Les fonctions **strtol** et **wcstol** utilisent les paramètres régionaux actuels. **_strtol_l** et **_wcstol_l** utilisez à la place les paramètres régionaux transmis. Pour plus d’informations, consultez [setlocale] et [paramètres régionaux](../../c-runtime-library/locale.md).

Lorsque *end_ptr* a la **valeur null**, il est ignoré. Sinon, un pointeur vers le caractère qui a arrêté l’analyse est stocké à l’emplacement désigné par *end_ptr*. Aucune conversion n’est possible si aucun chiffre valide n’est trouvé, ou si une base non valide est spécifiée. La valeur de la *chaîne* est ensuite stockée à l’emplacement désigné par *end_ptr*.

**strtol** s’attend à ce que la *chaîne* pointe vers une chaîne au format suivant :

> [*espace blanc*] [{**+** &#124; **-**}] [**0** [{ **x** &#124; **x** }]] [*alphanumériques*]

Les crochets (`[ ]`) entourent les éléments facultatifs. Les accolades et une barre verticale (`{ | }`) entourent des alternatives pour un élément unique. les *espaces blancs* peuvent être constitués d’espaces et de caractères de tabulation, qui sont ignorés. les *caractères alphanumériques* sont des chiffres décimaux ou des lettres de « a » à « z » (ou de « a » à « z »). Le premier caractère qui ne correspond pas à ce formulaire arrête l’analyse. Si *base* est comprise entre 2 et 36, elle est utilisée comme base du nombre. Si *base* a la valeur 0, les caractères initiaux de la chaîne vers laquelle pointe la *chaîne* sont utilisés pour déterminer la base. Si le premier caractère est 0 et que le deuxième est différent de « x » ou « X », la chaîne est interprétée comme un entier octal. Si le premier caractère est « 0 » et que le deuxième est « x » ou « X », la chaîne est interprétée comme étant un entier hexadécimal. Si le premier caractère est un chiffre compris entre « 1 » et « 9 », la chaîne est interprétée comme étant un entier décimal. Les lettres de « a » à « z » (ou de « A » à « Z ») se voient assigner les valeurs 10 à 35. L’analyse autorise uniquement les lettres dont les valeurs sont inférieures à la *base*. Le premier caractère situé en dehors de la plage de la base a pour effet d’arrêter l’analyse. Par exemple, supposons que la *chaîne* commence par « 01 ». Si *base* a la valeur 0, le scanneur suppose qu’il s’agit d’un entier octal. Un caractère « 8 » ou « 9 » arrête l’analyse.

Par défaut, l’état global de cette fonction est limité à l’application. Pour modifier cette valeur, consultez [état global dans le CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine TCHAR.H|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcstol**|**strtol**|**strtol**|**wcstol**|
|**_tcstol_l**|**_strtol_l**|**_strtol_l**|**_wcstol_l**|

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**strtol**|\<stdlib.h>|
|**wcstol**|\<stdlib.h> ou \<wchar.h>|
|**_strtol_l**|\<stdlib.h>|
|**_wcstol_l**|\<stdlib.h> ou \<wchar.h>|

Les **_strtol_l** fonctions **_wcstol_l** et sont spécifiques à Microsoft et ne font pas partie de la bibliothèque C standard. Pour plus d'informations sur la compatibilité, voir [Compatibilité](../compatibility.md).

## <a name="example"></a> Exemple

Consultez l’exemple pour [strtod](strtod-strtod-l-wcstod-wcstod-l.md).

## <a name="see-also"></a>Voir aussi

[Conversion de données](../data-conversion.md)\
[Paramètres régionaux](../locale.md)\
[localeconv](localeconv.md)\
[setlocale, _wsetlocale](setlocale-wsetlocale.md)\
[Fonctions de chaîne en valeur numérique](../string-to-numeric-value-functions.md)\
[strtod, _strtod_l, wcstod, _wcstod_l](strtod-strtod-l-wcstod-wcstod-l.md)\
[strtoll, _strtoll_l, wcstoll, _wcstoll_l](strtoll-strtoll-l-wcstoll-wcstoll-l.md)\
[strtoul, _strtoul_l, wcstoul, _wcstoul_l](strtoul-strtoul-l-wcstoul-wcstoul-l.md)\
[atof, _atof_l, _wtof, _wtof_l](atof-atof-l-wtof-wtof-l.md)
