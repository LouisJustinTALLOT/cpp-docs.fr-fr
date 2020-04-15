---
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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: 06fb79ac050f4e1c357a76a782730cd72cbdadec
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81316942"
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

*Str*<br/>
Chaîne terminée par Null à trouver.

*strSearch*<br/>
Chaîne se terminant par un caractère Null à rechercher.

*locale*<br/>
Paramètres régionaux à utiliser.

## <a name="return-value"></a>Valeur de retour

Retourne un pointeur à la première occurrence de *strSearch* dans *str*, ou NULL si *strSearch* n’apparaît pas dans *str*. Si *strSearch* pointe vers une chaîne de longueur zéro, la fonction retourne *str*.

## <a name="remarks"></a>Notes

La `strstr` fonction renvoie un pointeur à la première occurrence de *strSearch* dans *str*. La recherche n’inclut pas les caractères Null de fin. `wcsstr` est la version à caractères larges de `strstr` et `_mbsstr` est la version à caractères multioctets. Les arguments et la valeur de retour de `wcsstr` sont des chaînes de caractères larges ; ceux de `_mbsstr` sont des chaînes de caractères multioctets. `_mbsstr` valide ses paramètres. Si *strSearch ou strSearch* est NULL, le gestionnaire de paramètre invalide est invoqué, tel que décrit dans [La validation de paramètres](../../c-runtime-library/parameter-validation.md) . *str* Si l’exécution est `_mbsstr` `errno` autorisée à se poursuivre, se fixe à EINVAL et renvoie 0. `strstr` et `wcsstr` ne vérifient pas leurs paramètres. Ces trois fonctions se comportent sinon de façon identique.

> [!IMPORTANT]
> Ces fonctions peuvent être exposées à un risque lié à un dépassement de mémoire tampon. Les dépassements de mémoire tampon peuvent être exploités dans le cadre d’une attaque de système, car ils permettent d’exécuter du code arbitraire, ce qui peut entraîner une élévation injustifiée des privilèges. Pour plus d’informations, consultez [Solutions contre les dépassements de mémoire tampon](/windows/win32/SecBP/avoiding-buffer-overruns).

Dans C, ces fonctions prennent un pointeur **const** pour le premier argument. En C++, deux surcharges sont disponibles. La surcharge qui prend un pointeur pour **const** retourne un pointeur à **const;** la version qui prend un pointeur à**non-const** retourne un pointeur à**non-const**. Le macro _CRT_CONST_CORRECT_OVERLOADS est défini si les versions **const** et non**const** de ces fonctions sont disponibles. Si vous avez besoin du comportement non**const** pour les deux surcharges de C, définissez le symbole _CONST_RETURN.

La valeur de production est affectée par l’établissement de catégorie locale de LC_CTYPE; pour plus d’informations, voir [setlocale, _wsetlocale](setlocale-wsetlocale.md). Les versions de ces fonctions qui n’ont pas le **suffixe _l** utilisent le lieu actuel pour ce comportement local-dépendant; les versions qui ont le **suffixe _l** sont identiques, sauf qu’ils utilisent plutôt le paramètre local qui est passé en. Pour plus d’informations, consultez [Locale](../../c-runtime-library/locale.md).

Par défaut, l’état global de cette fonction est étendue à l’application. Pour changer cela, voir [Global State dans le CRT](../global-state.md).

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

[Manipulation des cordes](../../c-runtime-library/string-manipulation-crt.md)<br/>
[Local](../../c-runtime-library/locale.md)<br/>
[Interprétation des séquences multioctets-caractères](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[strcspn, wcscspn, _mbscspn, _mbscspn_l](strcspn-wcscspn-mbscspn-mbscspn-l.md)<br/>
[strcmp, wcscmp, _mbscmp](strcmp-wcscmp-mbscmp.md)<br/>
[strpbrk, wcspbrk, _mbspbrk, _mbspbrk_l](strpbrk-wcspbrk-mbspbrk-mbspbrk-l.md)<br/>
[strrchr, wcsrchr, _mbsrchr, _mbsrchr_l](strrchr-wcsrchr-mbsrchr-mbsrchr-l.md)<br/>
[strspn, wcsspn, _mbsspn, _mbsspn_l](strspn-wcsspn-mbsspn-mbsspn-l.md)<br/>
[basic_string::trouver](../../standard-library/basic-string-class.md#find)<br/>
