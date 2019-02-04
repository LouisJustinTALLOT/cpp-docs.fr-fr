---
title: strcmp, wcscmp, _mbscmp, _mbscmp_l
ms.date: 01/22/2019
apiname:
- wcscmp
- _mbscmp
- _mbscmp_l
- strcmp
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
- api-ms-win-crt-string-l1-1-0.dll
- ntoskrnl.exe
apitype: DLLExport
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
ms.openlocfilehash: dae5e04809ac7312097cb418ab5ffd561fdbd1d1
ms.sourcegitcommit: e98671a4f741b69d6277da02e6b4c9b1fd3c0ae5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/04/2019
ms.locfileid: "55703153"
---
# <a name="strcmp-wcscmp-mbscmp-mbscmpl"></a>strcmp, wcscmp, _mbscmp, _mbscmp_l

Comparer des chaînes.

> [!IMPORTANT]
> **_mbscmp** et **_mbscmp_l** ne peut pas être utilisé dans les applications qui s’exécutent dans le Windows Runtime. Pour plus d’informations, consultez [Fonctions CRT non prises en charge dans les applications de la plateforme Windows universelle](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

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

La valeur de retour pour chacune de ces fonctions indique la relation ordinale de *string1* à *string2*.

|Value|Relation de chaîne1 à chaîne2|
|-----------|----------------------------------------|
|< 0|*string1* est inférieure à *chaîne2*|
|0|*string1* est identique à *chaîne2*|
|> 0|*string1* est supérieur à *chaîne2*|

Une erreur de validation de paramètre, **_mbscmp** et **_mbscmp_l** retourner **_NLSCMPERROR**, qui est défini dans \<string.h > et \< Mbstring.h >.

## <a name="remarks"></a>Notes

Le **strcmp** fonction effectue une comparaison ordinale de *string1* et *string2* et retourne une valeur qui indique leur relation. **wcscmp** et **_mbscmp** sont, respectivement, les versions de caractères larges et à caractères multioctets **strcmp**. **_mbscmp** reconnaît les séquences de caractères multioctets en fonction de la page de codes multioctets actuelle et retourne **_NLSCMPERROR** en cas d’erreur. **_mbscmp_l** a le même comportement, mais utilise les paramètres régionaux qui sont passés à la place les paramètres régionaux actuels. Pour plus d’informations, consultez [Pages de codes](../../c-runtime-library/code-pages.md). En outre, si *string1* ou *string2* est un pointeur null, **_mbscmp** appelle le Gestionnaire de paramètre non valide, comme décrit dans [Validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, **_mbscmp** et **_mbscmp_l** retourner **_NLSCMPERROR** et définissez **errno** à **EINVAL** . **strcmp** et **wcscmp** ne valident pas leurs paramètres. Ces fonctions se comportent sinon de façon identique.

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine TCHAR.H|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcscmp**|**strcmp**|**_mbscmp**|**wcscmp**|

Le **strcmp** fonctions se distinguent de la **strcoll** fonctions dans qui **strcmp** comparaisons sont ordinales et ne sont pas affectées par les paramètres régionaux. **strcoll** compare des chaînes de point de vue lexicographique à l’aide de la **LC_COLLATE** catégorie de paramètres régionaux actuels. Pour plus d’informations sur la **LC_COLLATE** catégorie, consultez [setlocale, _wsetlocale](setlocale-wsetlocale.md).

Dans les paramètres régionaux "C", l'ordre des caractères du jeu de caractères (jeu de caractères ASCII) est le même que l'ordre lexicographique des caractères. Cependant, dans d'autres paramètres régionaux, l'ordre des caractères du jeu de caractères peut différer de l'ordre lexicographique. Par exemple, dans certains paramètres régionaux européens, le caractère « a » (valeur 0 x 61) se trouve avant le caractère « ä » (valeur 0xE4) dans le jeu de caractères, mais le caractère « ä » se trouve avant le caractère « a » d'un point de vue lexicographique.

Dans les paramètres régionaux pour lesquels le jeu de caractères et l’ordre lexicographique des caractères diffèrent, vous pouvez utiliser **strcoll** au lieu de **strcmp** pour la comparaison lexicographique de chaînes. Vous pouvez également utiliser **strxfrm** sur les chaînes d’origine et utilisez puis **strcmp** sur les chaînes résultantes.

Le **strcmp** fonctions respectent la casse. **\_stricmp**,  **\_wcsicmp**, et  **\_mbsicmp** comparer des chaînes en les convertissant d’abord en minuscules. Deux chaînes qui contiennent des caractères qui se trouvent entre « Z » et « a » dans la table ASCII ('[','\\', ']', ' ^', '_', et '\`') comparent différemment, en fonction de leur casse. Par exemple, les deux chaînes « ABCDE » et « ABCD ^ « comparent différemment selon si la comparaison est en minuscule (« abcde » > « abcd ^ ») et l’autre sens (« ABCDE » < « ABCD ^ ») si la comparaison est en majuscule.

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

[Manipulation de chaînes](../../c-runtime-library/string-manipulation-crt.md)<br/>
[memcmp, wmemcmp](memcmp-wmemcmp.md)<br/>
[_memicmp, _memicmp_l](memicmp-memicmp-l.md)<br/>
[strcoll, fonctions](../../c-runtime-library/strcoll-functions.md)<br/>
[_stricmp, _wcsicmp, _mbsicmp, _stricmp_l, _wcsicmp_l, _mbsicmp_l](stricmp-wcsicmp-mbsicmp-stricmp-l-wcsicmp-l-mbsicmp-l.md)<br/>
[strncmp, wcsncmp, _mbsncmp, _mbsncmp_l](strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)<br/>
[_strnicmp, _wcsnicmp, _mbsnicmp, _strnicmp_l, _wcsnicmp_l, _mbsnicmp_l](strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md)<br/>
[strrchr, wcsrchr, _mbsrchr, _mbsrchr_l](strrchr-wcsrchr-mbsrchr-mbsrchr-l.md)<br/>
[strspn, wcsspn, _mbsspn, _mbsspn_l](strspn-wcsspn-mbsspn-mbsspn-l.md)<br/>
[strxfrm, wcsxfrm, _strxfrm_l, _wcsxfrm_l](strxfrm-wcsxfrm-strxfrm-l-wcsxfrm-l.md)<br/>
