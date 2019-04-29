---
title: _stricmp, _wcsicmp, _mbsicmp, _stricmp_l, _wcsicmp_l, _mbsicmp_l
ms.date: 11/04/2016
apiname:
- _stricmp_l
- _mbsicmp
- _wcsicmp
- _mbsicmp_l
- _stricmp
- _wcsicmp_l
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
- ntoskrnl.exe
- ucrtbase.dll
- api-ms-win-crt-multibyte-l1-1-0.dll
- api-ms-win-crt-string-l1-1-0.dll
apitype: DLLExport
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
ms.openlocfilehash: d27b2128d79d7ff3ab0150e182d494fed52d46ca
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62353833"
---
# <a name="stricmp-wcsicmp-mbsicmp-stricmpl-wcsicmpl-mbsicmpl"></a>_stricmp, _wcsicmp, _mbsicmp, _stricmp_l, _wcsicmp_l, _mbsicmp_l

Effectue une comparaison de chaînes sans tenir compte de la casse.

> [!IMPORTANT]
> **_mbsicmp** et **_mbsicmp_l** ne peut pas être utilisé dans les applications qui s’exécutent dans le Windows Runtime. Pour plus d’informations, consultez [Fonctions CRT non prises en charge dans les applications de la plateforme Windows universelle](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

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

La valeur de retour indique la relation de *string1* à *string2* comme suit.

|Valeur de retour|Description|
|------------------|-----------------|
|< 0|*string1* inférieure à *chaîne2*|
|0|*string1* identique à *chaîne2*|
|> 0|*string1* supérieur *chaîne2*|

En cas d’erreur, **_mbsicmp** retourne **_NLSCMPERROR**, qui est défini dans \<string.h > et \<mbstring.h >.

## <a name="remarks"></a>Notes

Le **_stricmp** fonction ordinale compare *string1* et *string2* après la conversion de chaque caractère en minuscule et retourne une valeur qui indique leur relation. **_stricmp** diffère **_stricoll** car le **_stricmp** comparaison est uniquement affectée par **LC_CTYPE**, qui détermine quels caractères sont supérieures et en minuscules. Le **_stricoll** fonction compare les chaînes d’après les deux le **LC_CTYPE** et **LC_COLLATE** catégories des paramètres régionaux, qui inclut le cas et le classement commande. Pour plus d’informations sur la **LC_COLLATE** catégorie, consultez [setlocale](setlocale-wsetlocale.md) et [catégories de paramètres régionaux](../../c-runtime-library/locale-categories.md). Les versions de ces fonctions sans le **_l** suffixe utiliser les paramètres régionaux actuels pour le comportement dépendant des paramètres régionaux. Les versions avec le suffixe sont identiques, sauf qu'elles utilisent à la place les paramètres régionaux passés en entrée. Si les paramètres régionaux n'ont pas été définis, les paramètres régionaux C sont utilisés. Pour plus d’informations, consultez [Locale](../../c-runtime-library/locale.md).

> [!NOTE]
> **_stricmp** équivaut à **_strcmpi**. Ils peuvent être utilisés indifféremment, mais **_stricmp** est la norme préférée.

Le **_strcmpi** fonction est équivalente à **_stricmp** et n’est fourni pour la compatibilité descendante uniquement.

Étant donné que **_stricmp** comparaisons de minuscules, cela peut entraîner un comportement inattendu.

Pour illustrer la conversion par de la casse **_stricmp** affecte le résultat d’une comparaison, supposons que vous disposez des deux chaînes JOHNSTON et JOHN_HENRY. La chaîne JOHN_HENRY est considérée comme inférieure à JOHNSTON, car le caractère « _ » a une valeur ASCII inférieure à un S minuscule. En fait, tout caractère dont la valeur ASCII est comprise entre 91 et 96 est considérée comme inférieure à n’importe quelle lettre.

Si le [strcmp](strcmp-wcscmp-mbscmp.md) fonction est utilisée au lieu de **_stricmp**, JOHN_HENRY sera supérieur à JOHNSTON.

**_wcsicmp** et **_mbsicmp** sont des versions à caractères larges et à caractères multioctets de **_stricmp**. Les arguments et la valeur de retour de **_wcsicmp** sont des caractères larges chaînes ; ceux de **_mbsicmp** sont des chaînes de caractères multioctets. **_mbsicmp** reconnaît les séquences de caractères multioctets en fonction de la page de codes multioctets actuelle et retourne **_NLSCMPERROR** en cas d’erreur. Pour plus d’informations, consultez [Pages de codes](../../c-runtime-library/code-pages.md). Ces trois fonctions se comportent sinon de façon identique.

**_wcsicmp** et **wcscmp** ont un comportement identique, sauf que **wcscmp** ne convertit pas ses arguments en minuscules avant de les comparer. **_mbsicmp** et **_mbscmp** ont un comportement identique, sauf que **_mbscmp** ne convertit pas ses arguments en minuscules avant de les comparer.

Vous devez appeler [setlocale](setlocale-wsetlocale.md) pour **_wcsicmp** pour travailler avec des caractères Latin 1. Les paramètres régionaux C sont appliqués par défaut et par exemple, « ä » n'est pas considéré comme étant égal à « Ä ». Appelez **setlocale** avec tous les paramètres régionaux autres que les paramètres régionaux C avant l’appel à **_wcsicmp**. L’exemple suivant montre comment **_wcsicmp** est sensible aux paramètres régionaux :

```C
// crt_stricmp_locale.c
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

Une alternative consiste à appeler [_create_locale, _wcreate_locale](create-locale-wcreate-locale.md) et passez l’objet de paramètres régionaux retourné en tant que paramètre à **_wcsicmp_l**.

Toutes ces fonctions valident leurs paramètres. Si *string1* ou *string2* sont des pointeurs null, le Gestionnaire de paramètre non valide est appelé, comme décrit dans [Validation de paramètre](../../c-runtime-library/parameter-validation.md) . Si l’exécution est autorisée à se poursuivre, ces fonctions retournent **_NLSCMPERROR** et définissez **errno** à **EINVAL**.

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine TCHAR.H|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcsicmp**|**_stricmp**|**_mbsicmp**|**_wcsicmp**|

## <a name="requirements"></a>Configuration requise

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
