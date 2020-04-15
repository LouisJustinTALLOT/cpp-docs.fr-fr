---
title: strcmp, wcscmp, _mbscmp, _mbscmp_l
ms.date: 4/2/2020
api_name:
- wcscmp
- _mbscmp
- _mbscmp_l
- strcmp
- _o__mbscmp
- _o__mbscmp_l
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
- api-ms-win-crt-string-l1-1-0.dll
- ntoskrnl.exe
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _mbscmp
- _mbscmp_l
- wcscmp
- strcmp
- _tcscmp
- _ftcscmp
helpviewer_keywords:
- tcscmp function
- strcmp function
- strings [C++], comparing
- mbscmp function
- string comparison [C++]
- _mbscmp function
- _mbscmp_l function
- wcscmp function
- _tcscmp function
- _ftcscmp function
- ftcscmp function
ms.assetid: 5d216b57-7a5c-4cb3-abf0-0f4facf4396d
ms.openlocfilehash: 16bb294f7bbdc0b95b59b845d7b714f823f9d962
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81357286"
---
# <a name="strcmp-wcscmp-_mbscmp-_mbscmp_l"></a>strcmp, wcscmp, _mbscmp, _mbscmp_l

Comparer des chaînes.

> [!IMPORTANT]
> **_mbscmp** et **_mbscmp_l** ne peuvent pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime. Pour plus d’informations, consultez [Fonctions CRT non prises en charge dans les applications de la plateforme Windows universelle](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntaxe

```C
int strcmp(
   const char *string1,
   const char *string2
);
int wcscmp(
   const wchar_t *string1,
   const wchar_t *string2
);
int _mbscmp(
   const unsigned char *string1,
   const unsigned char *string2
);
int _mbscmp_l(
   const unsigned char *string1,
   const unsigned char *string2,
   _locale_t locale
);
```

### <a name="parameters"></a>Paramètres

*string1*, *string2*<br/>
Chaîne terminée par Null à comparer.

*locale*<br/>
Paramètres régionaux à utiliser.

## <a name="return-value"></a>Valeur de retour

La valeur de retour pour chacune de ces fonctions indique la relation ordinaire de *la chaîne1* à *la chaîne2*.

|Value|Relation de chaîne1 à chaîne2|
|-----------|----------------------------------------|
|< 0|*string1* est inférieur à *la chaîne2*|
|0|*string1* est identique à *string2*|
|> 0|*string1* est plus grand que *la chaîne2*|

Sur une erreur de validation de paramètres, **_mbscmp** et **_mbscmp_l** retour \< **_NLSCMPERROR**, qui est définie en string.h> et \<mbstring.h>.

## <a name="remarks"></a>Notes

La fonction **de strcmp** effectue une comparaison ordinaire de *la chaîne1* et *de la chaîne2* et renvoie une valeur qui indique leur relation. **wcscmp** et **_mbscmp** sont, respectivement, des versions à caractère large et multioctets de **strcmp**. **_mbscmp** reconnaît les séquences multioctets en fonction de la page de code multioctet actuelle et renvoie **_NLSCMPERROR** sur une erreur. **_mbscmp_l** a le même comportement, mais utilise le paramètre local qui est passé au lieu de la localisation actuelle. Pour plus d’informations, consultez [Pages de codes](../../c-runtime-library/code-pages.md). En outre, si *string1* ou *string2* est un pointeur nul, **_mbscmp** invoque le gestionnaire de paramètres invalides, tel que décrit dans [La validation de paramètres](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, **_mbscmp** et **_mbscmp_l** retourner **_NLSCMPERROR** et mettre **errno** à **EINVAL**. **strcmp** et **wcscmp** ne valident pas leurs paramètres. Ces fonctions se comportent sinon de façon identique.

Par défaut, l’état global de cette fonction est étendue à l’application. Pour changer cela, voir [Global State dans le CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine TCHAR.H|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcscmp**|**strcmp**|**_mbscmp**|**wcscmp**|

Les fonctions **de strcmp** diffèrent des fonctions **de strcoll** dans ce que les comparaisons **de strcmp** sont ordinaires, et ne sont pas affectées par le lieu. **strcoll** compare les cordes lexicographiquement en utilisant la catégorie **LC_COLLATE** de l’endroit actuel. Pour plus d’informations sur la catégorie **LC_COLLATE,** voir [setlocale, _wsetlocale](setlocale-wsetlocale.md).

Dans les paramètres régionaux "C", l'ordre des caractères du jeu de caractères (jeu de caractères ASCII) est le même que l'ordre lexicographique des caractères. Cependant, dans d'autres paramètres régionaux, l'ordre des caractères du jeu de caractères peut différer de l'ordre lexicographique. Par exemple, dans certains paramètres régionaux européens, le caractère « a » (valeur 0 x 61) se trouve avant le caractère « ä » (valeur 0xE4) dans le jeu de caractères, mais le caractère « ä » se trouve avant le caractère « a » d'un point de vue lexicographique.

Dans les endroits pour lesquels l’ensemble de caractère et l’ordre de caractère lexicographique diffèrent, vous pouvez employer **strcoll** au lieu de **strcmp** pour la comparaison lexicographique des cordes. Alternativement, vous pouvez utiliser **du strxfrm** sur les cordes d’origine, puis utiliser **le strcmp** sur les cordes qui en résultent.

Les fonctions **de strcmp** sont sensibles aux cas. stricmp ** \_, wcsicmp**, et ** \_mbsicmp** comparer les cordes en les convertissant d’abord à leurs formes inférieures. ** \_** Deux chaînes qui contiennent des caractères qui se trouvent entre 'Z' et 'a' dans la table ASCII ('', '',',',\\''', ''', ''', '', et ')\`comparent différemment, selon leur cas. Par exemple, les deux chaînes "ABCDE" et "ABCD" comparer d’une façon si la comparaison est inférieure ("abcde" > "abcd") et de l’autre façon ("ABCDE" < "ABCD") si la comparaison est majuscule.

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**strcmp**|\<string.h>|
|**wcscmp**|\<string.h> ou \<wchar.h>|
|**_mbscmp**|\<mbstring.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Bibliothèques

Toutes les versions des [bibliothèques Runtime C](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a>Exemple

```C
// crt_strcmp.c

#include <string.h>
#include <stdio.h>
#include <stdlib.h>

char string1[] = "The quick brown dog jumps over the lazy fox";
char string2[] = "The QUICK brown dog jumps over the lazy fox";

int main( void )
{
   char tmp[20];
   int result;

   // Case sensitive
   printf( "Compare strings:\n   %s\n   %s\n\n", string1, string2 );
   result = strcmp( string1, string2 );
   if( result > 0 )
      strcpy_s( tmp, _countof(tmp), "greater than" );
   else if( result < 0 )
      strcpy_s( tmp, _countof (tmp), "less than" );
   else
      strcpy_s( tmp, _countof (tmp), "equal to" );
   printf( "   strcmp:   String 1 is %s string 2\n", tmp );

   // Case insensitive (could use equivalent _stricmp)
   result = _stricmp( string1, string2 );
   if( result > 0 )
      strcpy_s( tmp, _countof (tmp), "greater than" );
   else if( result < 0 )
      strcpy_s( tmp, _countof (tmp), "less than" );
   else
      strcpy_s( tmp, _countof (tmp), "equal to" );
   printf( "   _stricmp:  String 1 is %s string 2\n", tmp );
}
```

```Output
Compare strings:
   The quick brown dog jumps over the lazy fox
   The QUICK brown dog jumps over the lazy fox

   strcmp:   String 1 is greater than string 2
   _stricmp:  String 1 is equal to string 2
```

## <a name="see-also"></a>Voir aussi

[Manipulation des cordes](../../c-runtime-library/string-manipulation-crt.md)<br/>
[memcmp, wmemcmp](memcmp-wmemcmp.md)<br/>
[_memicmp, _memicmp_l](memicmp-memicmp-l.md)<br/>
[fonctions strcoll](../../c-runtime-library/strcoll-functions.md)<br/>
[_stricmp, _wcsicmp, _mbsicmp, _stricmp_l, _wcsicmp_l, _mbsicmp_l](stricmp-wcsicmp-mbsicmp-stricmp-l-wcsicmp-l-mbsicmp-l.md)<br/>
[strncmp, wcsncmp, _mbsncmp, _mbsncmp_l](strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)<br/>
[_strnicmp, _wcsnicmp, _mbsnicmp, _strnicmp_l, _wcsnicmp_l, _mbsnicmp_l](strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md)<br/>
[strrchr, wcsrchr, _mbsrchr, _mbsrchr_l](strrchr-wcsrchr-mbsrchr-mbsrchr-l.md)<br/>
[strspn, wcsspn, _mbsspn, _mbsspn_l](strspn-wcsspn-mbsspn-mbsspn-l.md)<br/>
[strxfrm, wcsxfrm, _strxfrm_l, _wcsxfrm_l](strxfrm-wcsxfrm-strxfrm-l-wcsxfrm-l.md)<br/>
