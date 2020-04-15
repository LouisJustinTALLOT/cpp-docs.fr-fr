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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: dbeaf04d34aa20e15de48e99082ed07edb6129ab
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81320475"
---
# <a name="strtol-wcstol-_strtol_l-_wcstol_l"></a>strtol, wcstol, _strtol_l, _wcstol_l

Convertir les cordes en une **longue** valeur d’intégrage.

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

*String*\
Chaîne se terminant par un caractère Null à convertir.

*end_ptr*\
Un paramètre de sortie, défini pour indiquer le personnage après le dernier caractère interprété. Ignoré, si **NULL**.

*Base*\
Base numérique à utiliser.

*locale*\
Paramètres régionaux à utiliser.

## <a name="return-value"></a>Valeur de retour

**strtol**, **wcstol**, **_strtol_l**, et **_wcstol_l** retourner la valeur représentée en *chaîne*. Ils retournent 0 si aucune conversion n’est possible. Lorsque la représentation provoquerait un débordement, ils reviennent **LONG_MAX** ou **LONG_MIN**.

**errno** est réglé sur **ERANGE** en cas de débordement ou de sous-flux. Il est réglé à **EINVAL** si *la chaîne* est **NULL**. Ou, si *la base* est non zéro et moins de 2, ou plus de 36. Pour plus d’informations sur **ERANGE**, **EINVAL**, et d’autres codes de retour, voir [_doserrno, errno, _sys_errlist, et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Notes

Le **strtol**, **wcstol**, **_strtol_l**, et **_wcstol_l** fonctions convertir *la chaîne* en une **longue**. Ils cessent de lire la *chaîne* au premier personnage non reconnu comme faisant partie d’un certain nombre. Il peut s’agir du caractère de fin nul, ou du premier caractère alphanumérique supérieur ou égal à *la base.*

**wcstol** et **_wcstol_l** sont des versions à caractère large de **strtol** et **_strtol_l**. Leur argument *de cordes* est une corde de caractère large. Ces fonctions se comportent de la même façon que **le strtol** et **_strtol_l** autrement. Le réglage de la catégorie **LC_NUMERIC** du lieu détermine la reconnaissance du caractère radix (le marqueur fractionnel ou le point décimal) en *chaîne.* Les fonctions **strtol** et **wcstol** utilisent le lieu actuel. **_strtol_l** et **_wcstol_l** utiliser le lieu passé à la place. Pour plus d’informations, voir [setlocale] et [Local](../../c-runtime-library/locale.md).

Lorsque *end_ptr* est **NULL**, il est ignoré. Sinon, un pointeur sur le personnage qui a arrêté l’analyse est stocké à l’endroit indiqué par *end_ptr*. Aucune conversion n’est possible si aucun chiffre valide n’est trouvé, ou une base invalide est spécifiée. La valeur de *la chaîne* est ensuite stockée à l’endroit indiqué par *end_ptr*.

**strtol** s’attend à *ce que la chaîne* pointe vers une chaîne de la forme suivante:

> [*espace blanc*] [&#124;]**+** **-** [**0** **[x** &#124; **X]]** [*alphanumériques*]

Les supports`[ ]`carrés () entourent les éléments optionnels. Des accolades bouclées et`{ | }`une barre verticale () entourent des alternatives pour un seul élément. *l’espace blanc* peut se composer de caractères d’espace et d’onglet, qui sont ignorés. *alphanumériques* sont des chiffres décimaux ou les lettres 'a' par 'z' (ou 'A' par 'Z'). Le premier personnage qui ne correspond pas à ce formulaire arrête l’analyse. Si *la base* est comprise entre 2 et 36, alors il est utilisé comme base du nombre. Si la *base* est de 0, les caractères initiaux de la chaîne pointées par *la ficelle* sont utilisés pour déterminer la base. Si le premier personnage est 0, et le second personnage n’est pas 'x' ou 'X', la chaîne est interprétée comme un intégrant octal. Si le premier caractère est « 0 » et que le deuxième est « x » ou « X », la chaîne est interprétée comme étant un entier hexadécimal. Si le premier caractère est un chiffre compris entre « 1 » et « 9 », la chaîne est interprétée comme étant un entier décimal. Les lettres 'a' par 'z' (ou 'A' par 'Z') se voient attribuer les valeurs 10 à 35. L’analyse ne permet que les lettres dont les valeurs sont inférieures à *la base.* Le premier caractère situé en dehors de la plage de la base a pour effet d’arrêter l’analyse. Par exemple, supposons que *la chaîne* commence par "01". Si la *base* est de 0, le scanner suppose que c’est un intégrant octal. Un personnage '8' ou '9' arrête l’analyse.

Par défaut, l’état global de cette fonction est étendue à l’application. Pour changer cela, voir [Global State dans le CRT](../global-state.md).

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

Les **_strtol_l** **_wcstol_l** fonctions et les fonctions sont spécifiques à Microsoft, ne faisant pas partie de la bibliothèque Standard C. Pour plus d'informations sur la compatibilité, voir [Compatibilité](../compatibility.md).

## <a name="example"></a>Exemple

Voir l’exemple pour [strtod](strtod-strtod-l-wcstod-wcstod-l.md).

## <a name="see-also"></a>Voir aussi

[Conversion de données](../data-conversion.md)\
[Local](../locale.md)\
[localeconv](localeconv.md)\
[setlocale, _wsetlocale](setlocale-wsetlocale.md)\
[Fonctions de valeur ajoutée à numérique](../string-to-numeric-value-functions.md)\
[strtod, _strtod_l, wcstod, _wcstod_l](strtod-strtod-l-wcstod-wcstod-l.md)\
[strtoll, _strtoll_l, wcstoll, _wcstoll_l](strtoll-strtoll-l-wcstoll-wcstoll-l.md)\
[strtoul, _strtoul_l, wcstoul, _wcstoul_l](strtoul-strtoul-l-wcstoul-wcstoul-l.md)\
[atof, _atof_l, _wtof, _wtof_l](atof-atof-l-wtof-wtof-l.md)
