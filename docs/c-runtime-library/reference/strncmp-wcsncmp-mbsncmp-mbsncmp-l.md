---
title: strncmp, wcsncmp, _mbsncmp, _mbsncmp_l
ms.date: 11/04/2016
apiname:
- strncmp
- _mbsncmp
- wcsncmp
- _mbsncmp_l
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
apitype: DLLExport
f1_keywords:
- _ftcsnccmp
- _ftcsncmp
- _tcsncmp
- _tcsnccmp
- strncmp
- _mbsncmp
- wcsncmp
helpviewer_keywords:
- _tcsnccmp function
- ftcsncmp function
- wcsncmp function
- _ftcsncmp function
- _mbsncmp function
- tcsncmp function
- mbsncmp function
- _mbsncmp_l function
- mbsncmp_l function
- strncmp function
- strings [C++], comparing characters of
- string comparison [C++], strncmp function
- _tcsncmp function
- tcsnccmp function
- ftcsnccmp function
- characters [C++], comparing
- _ftcsnccmp function
ms.assetid: 2fdbf4e6-77da-4b59-9086-488f6066b8af
ms.openlocfilehash: b8b5472289bacc940bb0cbea7876f246243660bf
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50523762"
---
# <a name="strncmp-wcsncmp-mbsncmp-mbsncmpl"></a>strncmp, wcsncmp, _mbsncmp, _mbsncmp_l

Compare jusqu'au nombre spécifié de caractères de deux chaînes.

> [!IMPORTANT]
> **_mbsncmp** et **_mbsncmp_l** ne peut pas être utilisé dans les applications qui s’exécutent dans le Windows Runtime. Pour plus d’informations, consultez [Fonctions CRT non prises en charge dans les applications de la plateforme Windows universelle](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntaxe

```C
int strncmp(
   const char *string1,
   const char *string2,
   size_t count
);
int wcsncmp(
   const wchar_t *string1,
   const wchar_t *string2,
   size_t count
);
int _mbsncmp(
   const unsigned char *string1,
   const unsigned char *string2,
   size_t count
);
int _mbsncmp_l(
   const unsigned char *string1,
   const unsigned char *string2,
   size_t count,
   _locale_t locale
);int _mbsnbcmp(
   const unsigned char *string1,
   const unsigned char *string2,
   size_t count
);
```

### <a name="parameters"></a>Paramètres

*string1*, *chaîne2*<br/>
Chaînes à comparer.

*count*<br/>
Nombre de caractères à comparer.

*locale*<br/>
Paramètres régionaux à utiliser.

## <a name="return-value"></a>Valeur de retour

La valeur de retour indique la relation entre les sous-chaînes de *string1* et *string2* comme suit.

|Valeur de retour|Description|
|------------------|-----------------|
|< 0|*string1* sous-chaîne inférieure à *string2* sous-chaîne|
|0|*string1* sous-chaîne identique à *string2* sous-chaîne|
|> 0|*string1* sous-chaîne supérieur *string2* sous-chaîne|

Une erreur de validation de paramètre, **_mbsncmp** et **_mbsncmp_l** retourner **_NLSCMPERROR**, qui est défini dans \<string.h > et \< Mbstring.h >.

## <a name="remarks"></a>Notes

Le **strncmp** fonction effectue une comparaison ordinale du premier au maximum *nombre* les caractères de *string1* et *string2* et Retourne une valeur qui indique la relation entre les sous-chaînes. **strncmp** est une version de la casse de **_strnicmp**. **wcsncmp** et **_mbsncmp** sont des versions respectant la casse de **_wcsnicmp** et **_mbsnicmp**.

**wcsncmp** et **_mbsncmp** sont des versions à caractères larges et à caractères multioctets de **strncmp**. Les arguments de **wcsncmp** sont des caractères larges chaînes ; ceux de **_mbsncmp** sont des chaînes de caractères multioctets. **_mbsncmp** reconnaît les séquences de caractères multioctets en fonction d’une page de codes multioctets et retourne **_NLSCMPERROR** en cas d’erreur.

En outre, **_mbsncmp** et **_mbsncmp_l** valider les paramètres. Si *string1* ou *string2* est un pointeur null, le Gestionnaire de paramètre non valide est appelé, comme décrit dans [Validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, **_mbsncmp** et **_mbsncmp_l** retourner **_NLSCMPERROR** et définissez **errno** à  **EINVAL**. **strncmp** et **wcsncmp** ne valident pas leurs paramètres. Ces fonctions se comportent sinon de façon identique.

Le comportement de comparaison de **_mbsncmp** et **_mbsncmp_l** est affectée par la valeur de la **LC_CTYPE** paramètre de catégorie de paramètres régionaux. Ce paramètre contrôle la détection des octets de début et de fin des caractères multioctets. Pour plus d’informations, consultez [setlocale](setlocale-wsetlocale.md). Le **_mbsncmp** fonction utilise les paramètres régionaux actuels pour ce comportement dépendant des paramètres régionaux. Le **_mbsncmp_l** fonction est identique, sauf qu’elle utilise le *paramètres régionaux* paramètre à la place. Pour plus d’informations, consultez [Locale](../../c-runtime-library/locale.md). Si les paramètres régionaux sont des paramètres régionaux d’un octet, le comportement de ces fonctions est identique à **strncmp**.

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine TCHAR.H|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcsnccmp**|**strncmp**|**_mbsncmp**|**wcsncmp**|
|**_tcsncmp**|**strncmp**|**_mbsnbcmp**|**wcsncmp**|
|**_tccmp**|Mappe à la macro ou à la fonction inline|**_mbsncmp**|Mappe à la macro ou à la fonction inline|
|**non applicable**|**non applicable**|**_mbsncmp_l**|**non applicable**|

## <a name="requirements"></a>Configuration requise

|Routine|En-tête requis|
|-------------|---------------------|
|**strncmp**|\<string.h>|
|**wcsncmp**|\<string.h> ou \<wchar.h>|
|**_mbsncmp**, **_mbsncmp_l**|\<mbstring.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

```C
// crt_strncmp.c
#include <string.h>
#include <stdio.h>

char string1[] = "The quick brown dog jumps over the lazy fox";
char string2[] = "The QUICK brown fox jumps over the lazy dog";

int main( void )
{
   char tmp[20];
   int result;
   printf( "Compare strings:\n      %s\n      %s\n\n",
           string1, string2 );
   printf( "Function:   strncmp (first 10 characters only)\n" );
   result = strncmp( string1, string2 , 10 );
   if( result > 0 )
      strcpy_s( tmp, sizeof(tmp), "greater than" );
   else if( result < 0 )
      strcpy_s( tmp, sizeof(tmp), "less than" );
   else
      strcpy_s( tmp, sizeof(tmp), "equal to" );
   printf( "Result:      String 1 is %s string 2\n\n", tmp );
   printf( "Function:   strnicmp _strnicmp (first 10 characters only)\n" );
   result = _strnicmp( string1, string2, 10 );
   if( result > 0 )
      strcpy_s( tmp, sizeof(tmp), "greater than" );
   else if( result < 0 )
      strcpy_s( tmp, sizeof(tmp), "less than" );
   else
      strcpy_s( tmp, sizeof(tmp), "equal to" );
   printf( "Result:      String 1 is %s string 2\n", tmp );
}
```

```Output
Compare strings:
      The quick brown dog jumps over the lazy fox
      The QUICK brown fox jumps over the lazy dog

Function:   strncmp (first 10 characters only)
Result:      String 1 is greater than string 2

Function:   strnicmp _strnicmp (first 10 characters only)
Result:      String 1 is equal to string 2
```

## <a name="see-also"></a>Voir aussi

[Manipulation de chaînes](../../c-runtime-library/string-manipulation-crt.md)<br/>
[Paramètres régionaux](../../c-runtime-library/locale.md)<br/>
[Interprétation des séquences de caractères multi-octets](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[_mbsnbcmp, _mbsnbcmp_l](mbsnbcmp-mbsnbcmp-l.md)<br/>
[_mbsnbicmp, _mbsnbicmp_l](mbsnbicmp-mbsnbicmp-l.md)<br/>
[strcmp, wcscmp, _mbscmp](strcmp-wcscmp-mbscmp.md)<br/>
[strcoll, fonctions](../../c-runtime-library/strcoll-functions.md)<br/>
[_strnicmp, _wcsnicmp, _mbsnicmp, _strnicmp_l, _wcsnicmp_l, _mbsnicmp_l](strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md)<br/>
[strrchr, wcsrchr, _mbsrchr, _mbsrchr_l](strrchr-wcsrchr-mbsrchr-mbsrchr-l.md)<br/>
[_strset, _strset_l, _wcsset, _wcsset_l, _mbsset, _mbsset_l](strset-strset-l-wcsset-wcsset-l-mbsset-mbsset-l.md)<br/>
[strspn, wcsspn, _mbsspn, _mbsspn_l](strspn-wcsspn-mbsspn-mbsspn-l.md)<br/>
