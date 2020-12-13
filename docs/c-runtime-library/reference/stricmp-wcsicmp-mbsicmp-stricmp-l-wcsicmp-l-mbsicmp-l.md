---
description: 'En savoir plus sur : _stricmp, _wcsicmp, _mbsicmp, _stricmp_l, _wcsicmp_l, _mbsicmp_l'
title: _stricmp, _wcsicmp, _mbsicmp, _stricmp_l, _wcsicmp_l, _mbsicmp_l
ms.date: 4/2/2020
api_name:
- _stricmp_l
- _mbsicmp
- _wcsicmp
- _mbsicmp_l
- _stricmp
- _wcsicmp_l
- _o__mbsicmp
- _o__mbsicmp_l
- _o__stricmp
- _o__stricmp_l
- _o__wcsicmp
- _o__wcsicmp_l
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
- ntoskrnl.exe
- ucrtbase.dll
- api-ms-win-crt-multibyte-l1-1-0.dll
- api-ms-win-crt-string-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _ftcsicmp
- _stricmp
- wcsicmp_l
- _wcsicmp
- _tcsicmp
- _strcmpi
- stricmp_l
- _mbsicmp
- _fstricmp
- mbsicmp_l
- mbsicmp
helpviewer_keywords:
- _wcsicmp function
- _stricmp_l function
- fstricmp function
- _tcsicmp function
- ftcsicmp function
- string comparison [C++], lowercase
- _wcsicmp_l function
- _fstricmp function
- strings [C++], comparing
- mbsicmp function
- _ftcsicmp function
- _mbsicmp_l function
- wcsicmp_l function
- _stricmp function
- _mbsicmp function
- tcsicmp function
- stricmp_l function
- mbsicmp_l function
- _strcmpi function
ms.assetid: 0e1ee515-0d75-435a-a445-8875d4669b50
ms.openlocfilehash: 07ec1b2f53ae299c1c9622422cdf22e7f07ad330
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97338879"
---
# <a name="_stricmp-_wcsicmp-_mbsicmp-_stricmp_l-_wcsicmp_l-_mbsicmp_l"></a>_stricmp, _wcsicmp, _mbsicmp, _stricmp_l, _wcsicmp_l, _mbsicmp_l

Effectue une comparaison de chaînes sans tenir compte de la casse.

> [!IMPORTANT]
> **_mbsicmp** et **_mbsicmp_l** ne peuvent pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime. Pour plus d’informations, consultez [Fonctions CRT non prises en charge dans les applications de la plateforme Windows universelle](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntaxe

```C
int _stricmp(
   const char *string1,
   const char *string2
);
int _wcsicmp(
   const wchar_t *string1,
   const wchar_t *string2
);
int _mbsicmp(
   const unsigned char *string1,
   const unsigned char *string2
);
int _stricmp_l(
   const char *string1,
   const char *string2,
   _locale_t locale
);
int _wcsicmp_l(
   const wchar_t *string1,
   const wchar_t *string2,
   _locale_t locale
);
int _mbsicmp_l(
   const unsigned char *string1,
   const unsigned char *string2,
   _locale_t locale
);
```

### <a name="parameters"></a>Paramètres

*Chaîne1*, *Chaîne2*<br/>
Chaîne terminée par Null à comparer.

*locale*<br/>
Paramètres régionaux à utiliser.

## <a name="return-value"></a>Valeur renvoyée

La valeur de retour indique la relation de *Chaîne1* à *Chaîne2* comme suit.

|Valeur retournée|Description|
|------------------|-----------------|
|< 0|*Chaîne1* inférieure à *Chaîne2*|
|0|*Chaîne1* identique à *Chaîne2*|
|> 0|*Chaîne1* supérieure à *Chaîne2*|

En cas d’erreur, **_mbsicmp** retourne **_NLSCMPERROR**, qui est défini dans \<string.h> et \<mbstring.h> .

## <a name="remarks"></a>Notes

La fonction **_stricmp** compare de façon ordinale *Chaîne1* et *Chaîne2* après la conversion de chaque caractère en minuscules, et retourne une valeur indiquant leur relation. **_stricmp** diffère de **_stricoll** dans le fait que la comparaison **_stricmp** est uniquement affectée par la **LC_CTYPE**, qui détermine quels caractères sont supérieurs et en minuscules. La fonction **_stricoll** compare les chaînes en fonction des catégories **LC_CTYPE** et **LC_COLLATE** des paramètres régionaux, qui incluent à la fois le cas et l’ordre de classement. Pour plus d’informations sur la catégorie **LC_COLLATE** , consultez [setlocale](setlocale-wsetlocale.md) et [catégories de paramètres régionaux](../../c-runtime-library/locale-categories.md). Les versions de ces fonctions sans le suffixe **_L** utilisent les paramètres régionaux actuels pour le comportement dépendant des paramètres régionaux. Les versions avec le suffixe sont identiques, sauf qu'elles utilisent à la place les paramètres régionaux passés en entrée. Si les paramètres régionaux n'ont pas été définis, les paramètres régionaux C sont utilisés. Pour plus d’informations, consultez [Locale](../../c-runtime-library/locale.md).

> [!NOTE]
> **_stricmp** équivaut à **_strcmpi**. Elles peuvent être utilisées indifféremment, mais **_stricmp** est la norme préférée.

La fonction **_strcmpi** est équivalente à **_stricmp** et n’est fournie qu’à des fins de compatibilité descendante.

Étant donné que **_stricmp** effectue des comparaisons en minuscules, cela peut entraîner un comportement inattendu.

Pour illustrer le moment où la conversion de casse par **_stricmp** affecte le résultat d’une comparaison, supposons que vous avez les deux chaînes JOHNSTON et JOHN_HENRY. La chaîne JOHN_HENRY est considérée comme inférieure à JOHNSTON, car le caractère « _ » a une valeur ASCII inférieure à un S minuscule. En fait, tout caractère dont la valeur ASCII est comprise entre 91 et 96 est considérée comme inférieure à n’importe quelle lettre.

Si la fonction [strcmp](strcmp-wcscmp-mbscmp.md) est utilisée à la place de **_stricmp**, JOHN_HENRY sera supérieur à Johnston.

**_wcsicmp** et **_mbsicmp** sont des versions à caractères larges et à caractères multioctets de **_stricmp**. Les arguments et la valeur de retour de **_wcsicmp** sont des chaînes à caractères larges ; ceux de **_mbsicmp** sont des chaînes de caractères multioctets. **_mbsicmp** reconnaît les séquences de caractères multioctets en fonction de la page de codes multioctets actuelle et retourne **_NLSCMPERROR** en cas d’erreur. Pour plus d’informations, consultez [Pages de codes](../../c-runtime-library/code-pages.md). Ces trois fonctions se comportent sinon de façon identique.

**_wcsicmp** et **wcscmp** se comportent de la même manière, sauf que **wcscmp** ne convertit pas ses arguments en minuscules avant de les comparer. **_mbsicmp** et **_mbscmp** se comportent de la même manière, sauf que **_mbscmp** ne convertit pas ses arguments en minuscules avant de les comparer.

Vous devrez appeler [setlocale](setlocale-wsetlocale.md) pour **_wcsicmp** pour utiliser des caractères latins 1. Les paramètres régionaux C sont appliqués par défaut et par exemple, « ä » n'est pas considéré comme étant égal à « Ä ». Appelez **setlocale** avec des paramètres régionaux autres que les paramètres régionaux C avant l’appel à **_wcsicmp**. L’exemple suivant montre comment **_wcsicmp** est sensible aux paramètres régionaux :

```C
// crt_stricmp_locale.c
By default, this function's global state is scoped to the application. To change this, see [Global state in the CRT](../global-state.md).

#include <string.h>
#include <stdio.h>
#include <locale.h>

int main() {
   setlocale(LC_ALL,"C");   // in effect by default
   printf("\n%d",_wcsicmp(L"ä", L"Ä"));   // compare fails
   setlocale(LC_ALL,"");
   printf("\n%d",_wcsicmp(L"ä", L"Ä"));   // compare succeeds
}
```

Une alternative consiste à appeler [_create_locale, _wcreate_locale](create-locale-wcreate-locale.md) et à passer l’objet de paramètres régionaux retourné en tant que paramètre à **_wcsicmp_l**.

Toutes ces fonctions valident leurs paramètres. Si *string1* ou *string2* sont des pointeurs null, le gestionnaire de paramètres non valides est appelé, comme décrit dans [validation de paramètre](../../c-runtime-library/parameter-validation.md) . Si l’exécution est autorisée à se poursuivre, ces fonctions retournent **_NLSCMPERROR** et attribuent à **errno** la valeur **EINVAL**.

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine TCHAR.H|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcsicmp**|**_stricmp**|**_mbsicmp**|**_wcsicmp**|

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**_stricmp**, **_stricmp_l**|\<string.h>|
|**_wcsicmp**, **_wcsicmp_l**|\<string.h> ou \<wchar.h>|
|**_mbsicmp**, **_mbsicmp_l**|\<mbstring.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

```C
// crt_stricmp.c

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
      strcpy_s( tmp, _countof(tmp), "less than" );
   else
      strcpy_s( tmp, _countof(tmp), "equal to" );
   printf( "   strcmp:   String 1 is %s string 2\n", tmp );

   // Case insensitive (could use equivalent _stricmp)
   result = _stricmp( string1, string2 );
   if( result > 0 )
      strcpy_s( tmp, _countof(tmp), "greater than" );
   else if( result < 0 )
      strcpy_s( tmp, _countof(tmp), "less than" );
   else
      strcpy_s( tmp, _countof(tmp), "equal to" );
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
[strcmp, wcscmp, _mbscmp](strcmp-wcscmp-mbscmp.md)<br/>
[strcoll, fonctions](../../c-runtime-library/strcoll-functions.md)<br/>
[strncmp, wcsncmp, _mbsncmp, _mbsncmp_l](strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)<br/>
[_strnicmp, _wcsnicmp, _mbsnicmp, _strnicmp_l, _wcsnicmp_l, _mbsnicmp_l](strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md)<br/>
[strrchr, wcsrchr, _mbsrchr, _mbsrchr_l](strrchr-wcsrchr-mbsrchr-mbsrchr-l.md)<br/>
[_strset, _strset_l, _wcsset, _wcsset_l, _mbsset, _mbsset_l](strset-strset-l-wcsset-wcsset-l-mbsset-mbsset-l.md)<br/>
[strspn, wcsspn, _mbsspn, _mbsspn_l](strspn-wcsspn-mbsspn-mbsspn-l.md)<br/>
