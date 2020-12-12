---
description: 'En savoir plus sur : strstr, wcsstr, _mbsstr, _mbsstr_l'
title: strstr, wcsstr, _mbsstr, _mbsstr_l
ms.date: 4/2/2020
api_name:
- _mbsstr
- wcsstr
- _mbsstr_l
- strstr
- _o__mbsstr
- _o__mbsstr_l
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
- ntdll.dll
- ucrtbase.dll
- api-ms-win-crt-multibyte-l1-1-0.dll
- ntoskrnl.exe
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _fstrstr
- _ftcsstr
- strstr
- wcsstr
- _mbsstr
- _tcsstr
helpviewer_keywords:
- strings [C++], searching
- mbsstr function
- _ftcsstr function
- ftcsstr function
- fstrstr function
- _tcsstr function
- substrings, finding
- mbsstr_l function
- tcsstr function
- _mbsstr function
- wcsstr function
- _fstrstr function
- _mbsstr_l function
- strstr function
ms.assetid: 03d70c3f-2473-45cb-a5f8-b35beeb2748a
ms.openlocfilehash: 05f7cd3b03a56cb5e0e9343bd8cdee98af124988
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97181681"
---
# <a name="strstr-wcsstr-_mbsstr-_mbsstr_l"></a>strstr, wcsstr, _mbsstr, _mbsstr_l

Retourne un pointeur désignant la première occurrence d’une chaîne de recherche dans une chaîne.

> [!IMPORTANT]
> `_mbsstr` et `_mbsstr_l` ne peuvent pas être utilisées dans les applications qui s'exécutent dans Windows Runtime. Pour plus d’informations, consultez [Fonctions CRT non prises en charge dans les applications de la plateforme Windows universelle](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntaxe

```C
char *strstr(
   const char *str,
   const char *strSearch
); // C only
char *strstr(
   char *str,
   const char *strSearch
); // C++ only
const char *strstr(
   const char *str,
   const char *strSearch
); // C++ only
wchar_t *wcsstr(
   const wchar_t *str,
   const wchar_t *strSearch
); // C only
wchar_t *wcsstr(
   wchar_t *str,
   const wchar_t *strSearch
); // C++ only
const wchar_t *wcsstr(
   const wchar_t *str,
   const wchar_t *strSearch
); // C++ only
unsigned char *_mbsstr(
   const unsigned char *str,
   const unsigned char *strSearch
); // C only
unsigned char *_mbsstr(
   unsigned char *str,
   const unsigned char *strSearch
); // C++ only
const unsigned char *_mbsstr(
   const unsigned char *str,
   const unsigned char *strSearch
); // C++ only
unsigned char *_mbsstr_l(
   const unsigned char *str,
   const unsigned char *strSearch,
   _locale_t locale
); // C only
unsigned char *_mbsstr_l(
   unsigned char *str,
   const unsigned char *strSearch,
   _locale_t locale
); // C++ only
const unsigned char *_mbsstr_l(
   const unsigned char *str,
   const unsigned char *strSearch,
   _locale_t locale
); // C++ only
```

### <a name="parameters"></a>Paramètres

*str*<br/>
Chaîne terminée par Null à trouver.

*strSearch*<br/>
Chaîne se terminant par un caractère Null à rechercher.

*locale*<br/>
Paramètres régionaux à utiliser.

## <a name="return-value"></a>Valeur renvoyée

Retourne un pointeur désignant la première occurrence de *strSearch* dans *Str*, ou null si *strSearch* n’apparaît pas dans *Str*. Si *strSearch* pointe vers une chaîne de longueur nulle, la fonction retourne *Str*.

## <a name="remarks"></a>Notes

La `strstr` fonction retourne un pointeur vers la première occurrence de *strSearch* dans *Str*. La recherche n’inclut pas les caractères Null de fin. `wcsstr` est la version à caractères larges de `strstr` et `_mbsstr` est la version à caractères multioctets. Les arguments et la valeur de retour de `wcsstr` sont des chaînes de caractères larges ; ceux de `_mbsstr` sont des chaînes de caractères multioctets. `_mbsstr` valide ses paramètres. Si *Str* ou *strSearch* a la valeur null, le gestionnaire de paramètres non valides est appelé, comme décrit dans [validation de paramètre](../../c-runtime-library/parameter-validation.md) . Si l’exécution est autorisée à se poursuivre, `_mbsstr` affecte à la valeur `errno` EINVAL et retourne 0. `strstr` et `wcsstr` ne vérifient pas leurs paramètres. Ces trois fonctions se comportent sinon de façon identique.

> [!IMPORTANT]
> Ces fonctions peuvent être exposées à un risque lié à un dépassement de mémoire tampon. Les dépassements de mémoire tampon peuvent être exploités dans le cadre d’une attaque de système, car ils permettent d’exécuter du code arbitraire, ce qui peut entraîner une élévation injustifiée des privilèges. Pour plus d’informations, consultez [Solutions contre les dépassements de mémoire tampon](/windows/win32/SecBP/avoiding-buffer-overruns).

En C, ces fonctions acceptent un **`const`** pointeur pour le premier argument. En C++, deux surcharges sont disponibles. La surcharge qui prend un pointeur vers **`const`** retourne un pointeur vers **`const`** ; la version qui accepte un pointeur vers non- **`const`** retourne un pointeur vers non- **`const`** . La macro _CRT_CONST_CORRECT_OVERLOADS est définie si les **`const`** versions et non- **`const`** de ces fonctions sont disponibles. Si vous avez besoin du non- **`const`** comportement pour les deux surcharges C++, définissez le symbole _CONST_RETURN.

La valeur de sortie est affectée par le paramètre de catégorie de paramètres régionaux de LC_CTYPE ; Pour plus d’informations, consultez [setlocale, _wsetlocale](setlocale-wsetlocale.md). Les versions de ces fonctions qui n’ont pas le suffixe **_L** utilisent les paramètres régionaux actuels pour ce comportement dépendant des paramètres régionaux ; les versions qui ont le suffixe **_L** sont identiques, sauf qu’elles utilisent à la place les paramètres régionaux qui sont passés. Pour plus d’informations, consultez [Locale](../../c-runtime-library/locale.md).

Par défaut, l’état global de cette fonction est limité à l’application. Pour modifier cette valeur, consultez [état global dans le CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine TCHAR.H|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|------------------------------------|--------------------|-----------------------|
|`_tcsstr`|`strstr`|`_mbsstr`|`wcsstr`|
|**n/a**|**n/a**|`_mbsstr_l`|**n/a**|

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|`strstr`|\<string.h>|
|`wcsstr`|\<string.h> ou \<wchar.h>|
|`_mbsstr`, `_mbsstr_l`|\<mbstring.h>|

Pour plus d’informations sur la compatibilité, consultez [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

```C
// crt_strstr.c

#include <string.h>
#include <stdio.h>

char str[] =    "lazy";
char string[] = "The quick brown dog jumps over the lazy fox";
char fmt1[] =   "         1         2         3         4         5";
char fmt2[] =   "12345678901234567890123456789012345678901234567890";

int main( void )
{
   char *pdest;
   int  result;
   printf( "String to be searched:\n   %s\n", string );
   printf( "   %s\n   %s\n\n", fmt1, fmt2 );
   pdest = strstr( string, str );
   result = (int)(pdest - string + 1);
   if ( pdest != NULL )
      printf( "%s found at position %d\n", str, result );
   else
      printf( "%s not found\n", str );
}
```

```Output
String to be searched:
   The quick brown dog jumps over the lazy fox
            1         2         3         4         5
   12345678901234567890123456789012345678901234567890

lazy found at position 36
```

## <a name="see-also"></a>Voir aussi

[Manipulation de chaînes](../../c-runtime-library/string-manipulation-crt.md)<br/>
[Paramètres régionaux](../../c-runtime-library/locale.md)<br/>
[Interprétation des séquences de Multibyte-Character](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[strcspn, wcscspn, _mbscspn, _mbscspn_l](strcspn-wcscspn-mbscspn-mbscspn-l.md)<br/>
[strcmp, wcscmp, _mbscmp](strcmp-wcscmp-mbscmp.md)<br/>
[strpbrk, wcspbrk, _mbspbrk, _mbspbrk_l](strpbrk-wcspbrk-mbspbrk-mbspbrk-l.md)<br/>
[strrchr, wcsrchr, _mbsrchr, _mbsrchr_l](strrchr-wcsrchr-mbsrchr-mbsrchr-l.md)<br/>
[strspn, wcsspn, _mbsspn, _mbsspn_l](strspn-wcsspn-mbsspn-mbsspn-l.md)<br/>
[basic_string :: find](../../standard-library/basic-string-class.md#find)<br/>
