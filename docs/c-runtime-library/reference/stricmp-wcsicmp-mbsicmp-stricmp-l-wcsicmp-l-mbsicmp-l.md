---
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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: 315a86c5cf7e58219bad25f2b6633dd91275c09f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81320468"
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

*string1*, *string2*<br/>
Chaîne terminée par Null à comparer.

*locale*<br/>
Paramètres régionaux à utiliser.

## <a name="return-value"></a>Valeur de retour

La valeur de retour indique la relation de *la chaîne1* à *la chaîne2* comme suit.

|Valeur retournée|Description|
|------------------|-----------------|
|< 0|*string1* moins que *string2*|
|0|*string1* identique à *string2*|
|> 0|*string1* plus grand que *string2*|

Sur une erreur, **_mbsicmp** retourne **_NLSCMPERROR**, qui est \<définie en string.h \<> et mbstring.h>.

## <a name="remarks"></a>Notes

La fonction **_stricmp** compare habituellement *la chaîne1* et *la ficelle2* après avoir converti chaque personnage en minuscule, et retourne une valeur indiquant leur relation. **_stricmp** diffère de **_stricoll** en ce que la comparaison **_stricmp** n’est affectée que par **LC_CTYPE**, qui détermine quels caractères sont supérieurs et minuscules. La fonction **_stricoll** compare les chaînes selon les catégories **LC_CTYPE** et **LC_COLLATE** du lieu, qui comprend à la fois le boîtier et l’ordre de collation. Pour plus d’informations sur la catégorie **LC_COLLATE,** voir [setlocale](setlocale-wsetlocale.md) et [Local Categories](../../c-runtime-library/locale-categories.md). Les versions de ces fonctions sans le **suffixe _l** utilisent le lieu actuel pour un comportement local-dépendant. Les versions avec le suffixe sont identiques, sauf qu'elles utilisent à la place les paramètres régionaux passés en entrée. Si les paramètres régionaux n'ont pas été définis, les paramètres régionaux C sont utilisés. Pour plus d’informations, consultez [Locale](../../c-runtime-library/locale.md).

> [!NOTE]
> **_stricmp** équivaut à **_strcmpi**. Ils peuvent être utilisés de manière interchangeable, mais **_stricmp** est la norme préférée.

La fonction **_strcmpi** est équivalente à **_stricmp** et est fournie pour la compatibilité vers l’arrière seulement.

Parce **que _stricmp** fait des comparaisons minuscules, il peut entraîner un comportement inattendu.

Pour illustrer quand **la** conversion de cas par _stricmp affecte le résultat d’une comparaison, supposons que vous avez les deux cordes JOHNSTON et JOHN_HENRY. La chaîne JOHN_HENRY est considérée comme inférieure à JOHNSTON, car le caractère « _ » a une valeur ASCII inférieure à un S minuscule. En fait, tout caractère dont la valeur ASCII est comprise entre 91 et 96 est considérée comme inférieure à n’importe quelle lettre.

Si la fonction [de strcmp](strcmp-wcscmp-mbscmp.md) est utilisée au lieu de **_stricmp,** JOHN_HENRY sera plus grande que JOHNSTON.

**_wcsicmp** et **_mbsicmp** sont des versions à caractère large et multioctets de **_stricmp**. Les arguments et **la** valeur de retour de _wcsicmp sont des chaînes de caractère large; ceux de **_mbsicmp** sont des cordes multioctets-caractères. **_mbsicmp** reconnaît les séquences multioctets en fonction de la page de code multioctet actuelle et renvoie **_NLSCMPERROR** sur une erreur. Pour plus d’informations, consultez [Pages de codes](../../c-runtime-library/code-pages.md). Ces trois fonctions se comportent sinon de façon identique.

**_wcsicmp** et **wcscmp** se comportent de la même façon, sauf que **le wcscmp** ne convertit pas ses arguments en minuscules avant de les comparer. **_mbsicmp** et **_mbscmp** se comportent de la même façon, sauf que **_mbscmp** ne convertit pas ses arguments en minuscules avant de les comparer.

Vous devrez appeler [setlocale](setlocale-wsetlocale.md) pour **_wcsicmp** de travailler avec les personnages latin 1. Les paramètres régionaux C sont appliqués par défaut et par exemple, « ä » n'est pas considéré comme étant égal à « Ä ». Appel **setlocale** avec n’importe quel endroit autre que le local C avant l’appel à **_wcsicmp**. L’échantillon suivant montre comment **_wcsicmp** est sensible à la localisation :

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

Une alternative est d’appeler [_create_locale, _wcreate_locale](create-locale-wcreate-locale.md) et de passer l’objet local retourné comme un paramètre pour **_wcsicmp_l**.

Toutes ces fonctions valident leurs paramètres. Si *la chaîne1* ou *la chaîne2* sont des pointeurs nuls, le gestionnaire de paramètres invalide est invoqué, tel que décrit dans [La validation de paramètres](../../c-runtime-library/parameter-validation.md) . Si l’exécution est autorisée à se poursuivre, ces fonctions renvoient **_NLSCMPERROR** et mettent **errno** à **EINVAL**.

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

[Manipulation des cordes](../../c-runtime-library/string-manipulation-crt.md)<br/>
[memcmp, wmemcmp](memcmp-wmemcmp.md)<br/>
[_memicmp, _memicmp_l](memicmp-memicmp-l.md)<br/>
[strcmp, wcscmp, _mbscmp](strcmp-wcscmp-mbscmp.md)<br/>
[fonctions strcoll](../../c-runtime-library/strcoll-functions.md)<br/>
[strncmp, wcsncmp, _mbsncmp, _mbsncmp_l](strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)<br/>
[_strnicmp, _wcsnicmp, _mbsnicmp, _strnicmp_l, _wcsnicmp_l, _mbsnicmp_l](strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md)<br/>
[strrchr, wcsrchr, _mbsrchr, _mbsrchr_l](strrchr-wcsrchr-mbsrchr-mbsrchr-l.md)<br/>
[_strset, _strset_l, _wcsset, _wcsset_l, _mbsset, _mbsset_l](strset-strset-l-wcsset-wcsset-l-mbsset-mbsset-l.md)<br/>
[strspn, wcsspn, _mbsspn, _mbsspn_l](strspn-wcsspn-mbsspn-mbsspn-l.md)<br/>
