---
title: ':::no-loc(strtol):::, :::no-loc(wcstol):::, :::no-loc(_strtol_l):::, :::no-loc(_wcstol_l):::'
ms.date: 4/2/2020
api_name:
- ':::no-loc(strtol):::'
- ':::no-loc(wcstol):::'
- ':::no-loc(_strtol_l):::'
- ':::no-loc(_wcstol_l):::'
- '_o_:::no-loc(_strtol_l):::'
- '_o_:::no-loc(_wcstol_l):::'
- '_o_:::no-loc(strtol):::'
- '_o_:::no-loc(wcstol):::'
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
- ':::no-loc(_wcstol_l):::'
- ':::no-loc(strtol):::'
- ':::no-loc(_tcstol):::'
- ':::no-loc(wcstol):::'
- ':::no-loc(_strtol_l):::'
- ':::no-loc(_tcstol_l):::'
helpviewer_keywords:
- ':::no-loc(wcstol)::: function'
- :::no-loc(wcstol):::_l function
- ':::no-loc(_tcstol)::: function'
- string conversion, to integers
- tcstol function
- :::no-loc(strtol):::_l function
- ':::no-loc(_wcstol_l)::: function'
- ':::no-loc(_strtol_l)::: function'
- ':::no-loc(strtol)::: function'
ms.assetid: 1787c96a-f283-4a83-9325-33cfc1c7e240
no-loc:
- ':::no-loc(strtol):::'
- ':::no-loc(wcstol):::'
- ':::no-loc(_strtol_l):::'
- ':::no-loc(_wcstol_l):::'
- ':::no-loc(LONG_MAX):::'
- ':::no-loc(LONG_MIN):::'
- ':::no-loc(errno):::'
- ':::no-loc(ERANGE):::'
- ':::no-loc(EINVAL):::'
- ':::no-loc(LC_NUMERIC):::'
- ':::no-loc(_tcstol):::'
- ':::no-loc(_tcstol_l):::'
- ':::no-loc(localeconv):::'
- ':::no-loc(setlocale):::'
- ':::no-loc(_wsetlocale):::'
- ':::no-loc(strtod):::'
- ':::no-loc(_strtod_l):::'
- ':::no-loc(wcstod):::'
- ':::no-loc(_wcstod_l):::'
- ':::no-loc(strtoll):::'
- ':::no-loc(_strtoll_l):::'
- ':::no-loc(wcstoll):::'
- ':::no-loc(_wcstoll_l):::'
- ':::no-loc(strtoul):::'
- ':::no-loc(_strtoul_l):::'
- ':::no-loc(wcstoul):::'
- ':::no-loc(_wcstoul_l):::'
- ':::no-loc(atof):::'
- ':::no-loc(_atof_l):::'
- ':::no-loc(_wtof):::'
- ':::no-loc(_wtof_l):::'
ms.openlocfilehash: a5265b434f14f299532d6f5ebb65c83d75ea63ca
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87232402"
---
# <a name="no-locstrtol-no-locwcstol-no-loc_strtol_l-no-loc_wcstol_l"></a>:::no-loc(strtol):::, :::no-loc(wcstol):::, :::no-loc(_strtol_l):::, :::no-loc(_wcstol_l):::

Convertit des chaînes en **`long`** valeur entière.

## <a name="syntax"></a>Syntaxe

```C
long :::no-loc(strtol):::(
   const char *string,
   char **end_ptr,
   int base
);
long :::no-loc(wcstol):::(
   const wchar_t *string,
   wchar_t **end_ptr,
   int base
);
long :::no-loc(_strtol_l):::(
   const char *string,
   char **end_ptr,
   int base,
   _locale_t locale
);
long :::no-loc(_wcstol_l):::(
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

*paramètres régionaux*\
Paramètres régionaux à utiliser.

## <a name="return-value"></a>Valeur de retour

**:::no-loc(strtol):::**, **:::no-loc(wcstol):::** , **:::no-loc(_strtol_l):::** et **:::no-loc(_wcstol_l):::** retournent la valeur représentée dans *String*. Elles retournent 0 si aucune conversion n’est possible. Lorsque la représentation provoque un dépassement de capacité, elles retournent **:::no-loc(LONG_MAX):::** ou **:::no-loc(LONG_MIN):::** .

**:::no-loc(errno):::** a la valeur **:::no-loc(ERANGE):::** si le dépassement de capacité positif ou négatif se produit. Elle a la valeur **:::no-loc(EINVAL):::** si la *chaîne* est **null**. Ou, si *base* a une valeur différente de zéro et inférieure à 2, ou supérieure à 36. Pour plus d’informations sur **:::no-loc(ERANGE):::** , **:::no-loc(EINVAL):::** et d’autres codes de retour, consultez [_dos :::no-loc(errno)::: , :::no-loc(errno)::: , _sys_errlist et _sys_nerr](../../c-runtime-library/:::no-loc(errno):::-dos:::no-loc(errno):::-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Notes

Les **:::no-loc(strtol):::** fonctions,, **:::no-loc(wcstol):::** **:::no-loc(_strtol_l):::** et **:::no-loc(_wcstol_l):::** convertissent une *chaîne* en **`long`** . Ils cessent de lire la *chaîne* au premier caractère qui n’est pas reconnu comme faisant partie d’un nombre. Il peut s’agir du caractère de fin-null ou du premier caractère alphanumérique supérieur ou égal à *base*.

**:::no-loc(wcstol):::** et **:::no-loc(_wcstol_l):::** sont des versions à caractères larges de **:::no-loc(strtol):::** et **:::no-loc(_strtol_l):::** . Leur argument de *chaîne* est une chaîne de caractères larges. Ces fonctions se comportent de la même façon **:::no-loc(strtol):::** que et dans le **:::no-loc(_strtol_l):::** cas contraire. Le paramètre de catégorie des paramètres régionaux **:::no-loc(LC_NUMERIC):::** détermine la reconnaissance du caractère de base (la marque fractionnaire ou la virgule décimale) dans la *chaîne*. Les fonctions **:::no-loc(strtol):::** et **:::no-loc(wcstol):::** utilisent les paramètres régionaux actuels. **:::no-loc(_strtol_l):::** et **:::no-loc(_wcstol_l):::** utilisent les paramètres régionaux passés à la place. Pour plus d’informations, consultez [ :::no-loc(setlocale)::: ] et [paramètres régionaux](../../c-runtime-library/locale.md).

Lorsque *end_ptr* a la **valeur null**, il est ignoré. Sinon, un pointeur vers le caractère qui a arrêté l’analyse est stocké à l’emplacement désigné par *end_ptr*. Aucune conversion n’est possible si aucun chiffre valide n’est trouvé, ou si une base non valide est spécifiée. La valeur de la *chaîne* est ensuite stockée à l’emplacement désigné par *end_ptr*.

**:::no-loc(strtol):::** attend que la *chaîne* pointe vers une chaîne au format suivant :

> [*espace blanc*] [{ **+** &#124; **-** }] [**0** [{ **x** &#124; **x** }]] [*alphanumériques*]

Les crochets ( `[ ]` ) entourent les éléments facultatifs. Les accolades et une barre verticale ( `{ | }` ) entourent des alternatives pour un élément unique. les *espaces blancs* peuvent être constitués d’espaces et de caractères de tabulation, qui sont ignorés. les *caractères alphanumériques* sont des chiffres décimaux ou des lettres de « a » à « z » (ou de « a » à « z »). Le premier caractère qui ne correspond pas à ce formulaire arrête l’analyse. Si *base* est comprise entre 2 et 36, elle est utilisée comme base du nombre. Si *base* a la valeur 0, les caractères initiaux de la chaîne vers laquelle pointe la *chaîne* sont utilisés pour déterminer la base. Si le premier caractère est 0 et que le deuxième est différent de « x » ou « X », la chaîne est interprétée comme un entier octal. Si le premier caractère est « 0 » et que le deuxième est « x » ou « X », la chaîne est interprétée comme étant un entier hexadécimal. Si le premier caractère est un chiffre compris entre « 1 » et « 9 », la chaîne est interprétée comme étant un entier décimal. Les lettres de « a » à « z » (ou de « A » à « Z ») se voient assigner les valeurs 10 à 35. L’analyse autorise uniquement les lettres dont les valeurs sont inférieures à la *base*. Le premier caractère situé en dehors de la plage de la base a pour effet d’arrêter l’analyse. Par exemple, supposons que la *chaîne* commence par « 01 ». Si *base* a la valeur 0, le scanneur suppose qu’il s’agit d’un entier octal. Un caractère « 8 » ou « 9 » arrête l’analyse.

Par défaut, l’état global de cette fonction est limité à l’application. Pour modifier cette valeur, consultez [état global dans le CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine TCHAR.H|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|------------------------------------|--------------------|-----------------------|
|**:::no-loc(_tcstol):::**|**:::no-loc(strtol):::**|**:::no-loc(strtol):::**|**:::no-loc(wcstol):::**|
|**:::no-loc(_tcstol_l):::**|**:::no-loc(_strtol_l):::**|**:::no-loc(_strtol_l):::**|**:::no-loc(_wcstol_l):::**|

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**:::no-loc(strtol):::**|\<stdlib.h>|
|**:::no-loc(wcstol):::**|\<stdlib.h> ou \<wchar.h>|
|**:::no-loc(_strtol_l):::**|\<stdlib.h>|
|**:::no-loc(_wcstol_l):::**|\<stdlib.h> ou \<wchar.h>|

Les **:::no-loc(_strtol_l):::** **:::no-loc(_wcstol_l):::** fonctions et sont spécifiques à Microsoft et ne font pas partie de la bibliothèque C standard. Pour plus d'informations sur la compatibilité, voir [Compatibilité](../compatibility.md).

## <a name="example"></a>Exemple

Consultez l’exemple pour [:::no-loc(strtod):::](:::no-loc(strtod):::-:::no-loc(strtod):::-l-:::no-loc(wcstod):::-:::no-loc(wcstod):::-l.md) .

## <a name="see-also"></a>Voir aussi

[Conversion de données](../data-conversion.md)\
[Paramètres régionaux](../locale.md)\
[:::no-loc(localeconv):::](:::no-loc(localeconv):::.md)\
[:::no-loc(setlocale):::, :::no-loc(_wsetlocale):::](:::no-loc(setlocale):::-w:::no-loc(setlocale):::.md)\
[Fonctions de chaîne en valeur numérique](../string-to-numeric-value-functions.md)\
[:::no-loc(strtod):::, :::no-loc(_strtod_l):::, :::no-loc(wcstod):::, :::no-loc(_wcstod_l):::](:::no-loc(strtod):::-:::no-loc(strtod):::-l-:::no-loc(wcstod):::-:::no-loc(wcstod):::-l.md)\
[:::no-loc(strtoll):::, :::no-loc(_strtoll_l):::, :::no-loc(wcstoll):::, :::no-loc(_wcstoll_l):::](:::no-loc(strtoll):::-:::no-loc(strtoll):::-l-:::no-loc(wcstoll):::-:::no-loc(wcstoll):::-l.md)\
[:::no-loc(strtoul):::, :::no-loc(_strtoul_l):::, :::no-loc(wcstoul):::, :::no-loc(_wcstoul_l):::](:::no-loc(strtoul):::-:::no-loc(strtoul):::-l-:::no-loc(wcstoul):::-:::no-loc(wcstoul):::-l.md)\
[:::no-loc(atof):::, :::no-loc(_atof_l):::, :::no-loc(_wtof):::, :::no-loc(_wtof_l):::](:::no-loc(atof):::-:::no-loc(atof):::-l-wtof-wtof-l.md)
