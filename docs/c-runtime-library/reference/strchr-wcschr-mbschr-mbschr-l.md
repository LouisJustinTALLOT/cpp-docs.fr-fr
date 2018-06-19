---
title: strchr, wcschr, _mbschr, _mbschr_l | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- strchr
- wcschr
- _mbschr_l
- _mbschr
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
- ntdll.dll
- ucrtbase.dll
- api-ms-win-crt-multibyte-l1-1-0.dll
- ntoskrnl.exe
apitype: DLLExport
f1_keywords:
- _ftcschr
- strchr
- wcschr
- _tcschr
- _mbschr
dev_langs:
- C++
helpviewer_keywords:
- strings [C++], searching
- mbschr function
- _ftcschr function
- _mbschr function
- characters [C++], finding in strings
- _mbschr_l function
- ftcschr function
- wcschr function
- strchr function
- _tcschr function
- tcschr function
- mbschr_l function
ms.assetid: 2639905d-e983-43b7-b885-abef32cfac43
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6d83407efee1da2bc1c59cf0d869f54f6022a4eb
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32415522"
---
# <a name="strchr-wcschr-mbschr-mbschrl"></a>strchr, wcschr, _mbschr, _mbschr_l
Recherche un caractère dans une chaîne en utilisant les paramètres régionaux actifs ou une catégorie d’état de conversion LC_CTYPE spécifiée.

> [!IMPORTANT]
> **_mbschr** et **_mbschr_l** ne peut pas être utilisée dans les applications qui s’exécutent dans le Windows Runtime. Pour plus d’informations, consultez [Fonctions CRT non prises en charge dans les applications de la plateforme Windows universelle](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntaxe

```C
char *strchr(
   const char *str,
   int c
);  // C only
char *strchr(
   char * str,
   int c
); // C++ only
const char *strchr(
   const char * str,
   int c
); // C++ only
wchar_t *wcschr(
   const wchar_t *str,
   wchar_t c
); // C only
wchar_t *wcschr(
   wchar_t *str,
   wchar_t c
);  // C++ only
const wchar_t *wcschr(
   const wchar_t *str,
   wchar_t c
);  // C++ only
unsigned char *_mbschr(
   const unsigned char *str,
   unsigned int c
); // C only
unsigned char *_mbschr(
   unsigned char *str,
   unsigned int c
); // C++ only
const unsigned char *_mbschr(
   const unsigned char *str,
   unsigned int c
); // C++ only
unsigned char *_mbschr_l(
   const unsigned char *str,
   unsigned int c,
   _locale_t locale
); // C only
unsigned char *_mbschr_l(
   unsigned char *str,
   unsigned int c,
   _locale_t locale
); // C++ only
const unsigned char *_mbschr_l(
   const unsigned char *str,
   unsigned int c,
   _locale_t locale
); // C++ only
```

### <a name="parameters"></a>Paramètres

*str*<br/>
Chaîne source se terminant par null.

*c*<br/>
Caractère à trouver.

*locale*<br/>
Paramètres régionaux à utiliser.

## <a name="return-value"></a>Valeur de retour

Chacune de ces fonctions retourne un pointeur vers la première occurrence de *c* dans *str*, ou **NULL** si *c* est introuvable.

## <a name="remarks"></a>Notes

Le **strchr** fonction recherche la première occurrence de *c* dans *str*, ou la valeur **NULL** si *c* est introuvable. Le caractère Null de fin est inclus dans la recherche.

**wcschr**, **_mbschr** et **_mbschr_l** sont des versions à caractères larges et caractères multioctets de **strchr**. Les arguments et la valeur de retour de **wcschr** sont des caractères larges chaînes ; ceux de **_mbschr** sont des chaînes de caractères multioctets. **_mbschr** reconnaît les séquences de caractères multioctets. Également, si la chaîne est un pointeur null, **_mbschr** appelle le Gestionnaire de paramètre non valide, comme décrit dans [Validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, **_mbschr** retourne **NULL** et définit **errno** à **EINVAL**. **strchr** et **wcschr** ne vérifient pas leurs paramètres. Ces trois fonctions se comportent sinon de façon identique.

La valeur de sortie est affectée par la définition de la **LC_CTYPE** catégorie de configuration des paramètres régionaux ; pour plus d’informations, consultez [setlocale](setlocale-wsetlocale.md). Les versions de ces fonctions sans le suffixe **_l** utilisent les paramètres régionaux pour ce comportement dépendant des paramètres régionaux ; les versions avec le suffixe **_l** sont identiques, sauf qu’elles utilisent à la place les paramètres régionaux transmis. Pour plus d’informations, consultez [Locale](../../c-runtime-library/locale.md).

En C, ces fonctions acceptent un ** const ** pointeur comme premier argument. En C++, deux surcharges sont disponibles. La surcharge acceptant un pointeur vers ** const ** retourne un pointeur vers **const **; la version qui prend un pointeur vers non -** const ** retourne un pointeur vers non -** const **. La macro **_CRT_CONST_CORRECT_OVERLOADS** est défini si les deux le **const ** et non-** const ** les versions de ces fonctions sont disponibles. Si vous avez besoin non -** const ** comportement pour les deux surcharges C++, définissez le symbole **_CONST_RETURN**.

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine TCHAR.H|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcschr**|**strchr**|**_mbschr**|**wcschr**|
|**_n/a**|**n/a**|**_mbschr_l**|**n/a**|

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**strchr**|\<string.h>|
|**wcschr**|\<string.h> ou \<wchar.h>|
|**_mbschr**, **_mbschr_l**|\<mbstring.h>|

Pour plus d'informations sur la compatibilité, consultez [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

```C
// crt_strchr.c
//
// This program illustrates searching for a character
// with strchr (search forward) or strrchr (search backward).
//

#include <string.h>
#include <stdio.h>

int  ch = 'r';

char string[] = "The quick brown dog jumps over the lazy fox";
char fmt1[] =   "         1         2         3         4         5";
char fmt2[] =   "12345678901234567890123456789012345678901234567890";

int main( void )
{
   char *pdest;
   int result;

   printf_s( "String to be searched:\n      %s\n", string );
   printf_s( "      %s\n      %s\n\n", fmt1, fmt2 );
   printf_s( "Search char:   %c\n", ch );

   // Search forward.
   pdest = strchr( string, ch );
   result = (int)(pdest - string + 1);
   if ( pdest != NULL )
      printf_s( "Result:   first %c found at position %d\n",
              ch, result );
   else
      printf_s( "Result:   %c not found\n", ch );

   // Search backward.
   pdest = strrchr( string, ch );
   result = (int)(pdest - string + 1);
   if ( pdest != NULL )
      printf_s( "Result:   last %c found at position %d\n", ch, result );
   else
      printf_s( "Result:\t%c not found\n", ch );
}
```

```Output
String to be searched:
      The quick brown dog jumps over the lazy fox
               1         2         3         4         5
      12345678901234567890123456789012345678901234567890

Search char:   r
Result:   first r found at position 12
Result:   last r found at position 30
```

## <a name="see-also"></a>Voir aussi

[Manipulation de chaînes](../../c-runtime-library/string-manipulation-crt.md)<br/>
[Paramètres régionaux](../../c-runtime-library/locale.md)<br/>
[Interprétation des séquences de caractères multi-octets](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[strcspn, wcscspn, _mbscspn, _mbscspn_l](strcspn-wcscspn-mbscspn-mbscspn-l.md)<br/>
[strncat, _strncat_l, wcsncat, _wcsncat_l, _mbsncat, _mbsncat_l](strncat-strncat-l-wcsncat-wcsncat-l-mbsncat-mbsncat-l.md)<br/>
[strncmp, wcsncmp, _mbsncmp, _mbsncmp_l](strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)<br/>
[strncpy, _strncpy_l, wcsncpy, _wcsncpy_l, _mbsncpy, _mbsncpy_l](strncpy-strncpy-l-wcsncpy-wcsncpy-l-mbsncpy-mbsncpy-l.md)<br/>
[_strnicmp, _wcsnicmp, _mbsnicmp, _strnicmp_l, _wcsnicmp_l, _mbsnicmp_l](strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md)<br/>
[strpbrk, wcspbrk, _mbspbrk, _mbspbrk_l](strpbrk-wcspbrk-mbspbrk-mbspbrk-l.md)<br/>
[strrchr, wcsrchr, _mbsrchr, _mbsrchr_l](strrchr-wcsrchr-mbsrchr-mbsrchr-l.md)<br/>
[strstr, wcsstr, _mbsstr, _mbsstr_l](strstr-wcsstr-mbsstr-mbsstr-l.md)<br/>
