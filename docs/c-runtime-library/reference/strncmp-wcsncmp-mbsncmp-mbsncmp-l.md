---
title: strncmp, wcsncmp, _mbsncmp, _mbsncmp_l
ms.date: 4/2/2020
api_name:
- strncmp
- _mbsncmp
- wcsncmp
- _mbsncmp_l
- _o__mbsncmp
- _o__mbsncmp_l
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
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
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
ms.openlocfilehash: deae95f8cf7d538dfe22ebbe0e86524765d9d234
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2020
ms.locfileid: "82919317"
---
# <a name="strncmp-wcsncmp-_mbsncmp-_mbsncmp_l"></a>strncmp, wcsncmp, _mbsncmp, _mbsncmp_l

Compare jusqu'au nombre spécifié de caractères de deux chaînes.

> [!IMPORTANT]
> **_mbsncmp** et **_mbsncmp_l** ne peuvent pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime. Pour plus d’informations, consultez [Fonctions CRT non prises en charge dans les applications de la plateforme Windows universelle](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

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

*Chaîne1*, *Chaîne2*<br/>
Chaînes à comparer.

*count*<br/>
Nombre de caractères à comparer.

*locale*<br/>
Paramètres régionaux à utiliser.

## <a name="return-value"></a>Valeur de retour

La valeur de retour indique la relation des sous-chaînes de *Chaîne1* et *Chaîne2* comme suit.

|Valeur retournée|Description|
|------------------|-----------------|
|< 0|*Chaîne1* sous-chaîne inférieure à *Chaîne2* sous-chaîne|
|0|*Chaîne1* sous-chaîne identique à la sous-chaîne *Chaîne2*|
|> 0|*Chaîne1* sous-chaîne supérieure à la sous-chaîne *Chaîne2*|

Dans le cas d’une erreur de validation de paramètre, **_mbsncmp** et **_mbsncmp_l** retournent **_NLSCMPERROR**, qui est défini dans \<string. h> et \<mbstring. h>.

## <a name="remarks"></a>Notes 

La fonction **strncmp** effectue une comparaison ordinale d’au plus les *premiers caractères* dans *Chaîne1* et *Chaîne2* et retourne une valeur indiquant la relation entre les sous-chaînes. **strncmp** est une version de **_strnicmp**qui respecte la casse. **wcsncmp** et **_mbsncmp** sont des versions de **_wcsnicmp** et **_mbsnicmp**qui respectent la casse.

**wcsncmp** et **_mbsncmp** sont des versions à caractères larges et à caractères multioctets de **strncmp**. Les arguments de **wcsncmp** sont des chaînes à caractères larges ; ceux de **_mbsncmp** sont des chaînes de caractères multioctets. **_mbsncmp** reconnaît les séquences de caractères multioctets en fonction d’une page de codes multioctets et retourne **_NLSCMPERROR** en cas d’erreur.

En outre, **_mbsncmp** et **_mbsncmp_l** valider les paramètres. Si *Chaîne1* ou *string2* est un pointeur null, le gestionnaire de paramètres non valides est appelé, comme décrit dans [validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, **_mbsncmp** et **_mbsncmp_l** retournent **_NLSCMPERROR** et attribuent à **errno** la valeur **EINVAL**. **strncmp** et **wcsncmp** ne valident pas leurs paramètres. Ces fonctions se comportent sinon de façon identique.

Le comportement de comparaison de **_mbsncmp** et **_mbsncmp_l** est affecté par le paramètre du paramètre de catégorie **LC_CTYPE** des paramètres régionaux. Ce paramètre contrôle la détection des octets de début et de fin des caractères multioctets. Pour plus d’informations, consultez [setlocale](setlocale-wsetlocale.md). La fonction **_mbsncmp** utilise les paramètres régionaux actuels pour ce comportement dépendant des paramètres régionaux. La fonction **_mbsncmp_l** est identique, à ceci près qu’elle utilise à la place les paramètres *régionaux* . Pour plus d’informations, consultez [Locale](../../c-runtime-library/locale.md). Si les paramètres régionaux sont des paramètres régionaux codés sur un octet, le comportement de ces fonctions est identique à celui de **strncmp**.

Par défaut, l’état global de cette fonction est limité à l’application. Pour modifier cette valeur, consultez [état global dans le CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine TCHAR.H|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcsnccmp**|**strncmp**|**_mbsncmp**|**wcsncmp**|
|**_tcsncmp**|**strncmp**|**_mbsnbcmp**|**wcsncmp**|
|**_tccmp**|Mappe à la macro ou à la fonction inline|**_mbsncmp**|Mappe à la macro ou à la fonction inline|
|**non applicable**|**non applicable**|**_mbsncmp_l**|**non applicable**|

## <a name="requirements"></a>Spécifications

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
[Interprétation des séquences de caractères multioctets](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[_mbsnbcmp, _mbsnbcmp_l](mbsnbcmp-mbsnbcmp-l.md)<br/>
[_mbsnbicmp, _mbsnbicmp_l](mbsnbicmp-mbsnbicmp-l.md)<br/>
[strcmp, wcscmp, _mbscmp](strcmp-wcscmp-mbscmp.md)<br/>
[strcoll, fonctions](../../c-runtime-library/strcoll-functions.md)<br/>
[_strnicmp, _wcsnicmp, _mbsnicmp, _strnicmp_l, _wcsnicmp_l, _mbsnicmp_l](strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md)<br/>
[strrchr, wcsrchr, _mbsrchr, _mbsrchr_l](strrchr-wcsrchr-mbsrchr-mbsrchr-l.md)<br/>
[_strset, _strset_l, _wcsset, _wcsset_l, _mbsset, _mbsset_l](strset-strset-l-wcsset-wcsset-l-mbsset-mbsset-l.md)<br/>
[strspn, wcsspn, _mbsspn, _mbsspn_l](strspn-wcsspn-mbsspn-mbsspn-l.md)<br/>
