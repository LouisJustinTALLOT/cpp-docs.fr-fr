---
title: mbtowc, _mbtowc_l
ms.date: 4/2/2020
api_name:
- mbtowc
- _mbtowc_l
- _o__mbtowc_l
- _o_mbtowc
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
- ucrtbase.dll
- api-ms-win-crt-convert-l1-1-0.dll
- api-ms-win-crt-multibyte-l1-1-0.dll
- ntoskrnl.exe
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- mbtowc
helpviewer_keywords:
- mbtowc function
- _mbtowc_l function
- mbtowc_l function
ms.assetid: dfd1c8a7-e73a-4307-9353-53b70b45d4d1
ms.openlocfilehash: 54e50da06fbe009184894edc60b6267e372aefc1
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2020
ms.locfileid: "82915417"
---
# <a name="mbtowc-_mbtowc_l"></a>mbtowc, _mbtowc_l

Convertir un caractère multioctet en un caractère large correspondant.

## <a name="syntax"></a>Syntaxe

```C
int mbtowc(
   wchar_t *wchar,
   const char *mbchar,
   size_t count
);
int _mbtowc_l(
   wchar_t *wchar,
   const char *mbchar,
   size_t count,
   _locale_t locale
);
```

### <a name="parameters"></a>Paramètres

*WCHAR*<br/>
Adresse d’un caractère élargi (type **wchar_t**).

*mbchar*<br/>
Adresse d'une séquence d'octets (un caractère multioctet).

*count*<br/>
Nombre d'octets à vérifier.

*locale*<br/>
Paramètres régionaux à utiliser.

## <a name="return-value"></a>Valeur de retour

Si **mbchar** n’a pas la **valeur null** et que l’objet qui *mbchar* pointe vers forme un caractère multioctet valide, **mbtowc** retourne la longueur, en octets, du caractère multioctet. Si *mbchar* a la **valeur null** ou que l’objet vers lequel il pointe est un caractère null à caractères larges (L' \ 0 '), la fonction retourne 0. Si l’objet vers lequel pointe *mbchar* ne forme pas un caractère multioctet valide dans les premiers *caractères,* elle retourne-1.

## <a name="remarks"></a>Notes 

La fonction **mbtowc** convertit le *nombre* ou moins d’octets pointés par *mbchar*, si *mbchar* n’est pas **null**, en un caractère élargi correspondant. **mbtowc** stocke le caractère élargi résultant à *WCHAR,* si *WCHAR* n’est pas **null**. **mbtowc** n’examine pas plus de **MB_CUR_MAX** octets. **mbtowc** utilise les paramètres régionaux actuels pour le comportement dépendant des paramètres régionaux ; **_mbtowc_l** est identique, à ceci près qu’il utilise à la place les paramètres régionaux transmis. Pour plus d’informations, consultez [Locale](../../c-runtime-library/locale.md).

Par défaut, l’état global de cette fonction est limité à l’application. Pour modifier cette valeur, consultez [état global dans le CRT](../global-state.md).

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**mbtowc**|\<stdlib.h>|
|**_mbtowc_l**|\<stdlib.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Bibliothèques

Toutes les versions des [bibliothèques Runtime C](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a>Exemple

```C
// crt_mbtowc.c
// Illustrates the behavior of the mbtowc function

#include <stdlib.h>
#include <stdio.h>

int main( void )
{
    int      i;
    char    *pmbc    = (char *)malloc( sizeof( char ) );
    wchar_t  wc      = L'a';
    wchar_t *pwcnull = NULL;
    wchar_t *pwc     = (wchar_t *)malloc( sizeof( wchar_t ) );
    printf( "Convert a wide character to multibyte character:\n" );
    wctomb_s( &i, pmbc, sizeof(char), wc );
    printf( "  Characters converted: %u\n", i );
    printf( "  Multibyte character: %x\n\n", *pmbc );

    printf( "Convert multibyte character back to a wide "
            "character:\n" );
    i = mbtowc( pwc, pmbc, MB_CUR_MAX );
    printf( "   Bytes converted: %u\n", i );
    printf( "   Wide character: %x\n\n", *pwc );
    printf( "Attempt to convert when target is NULL\n" );
    printf( "   returns the length of the multibyte character:\n" );
    i = mbtowc( pwcnull, pmbc, MB_CUR_MAX );
    printf( "   Length of multibyte character: %u\n\n", i );

    printf( "Attempt to convert a NULL pointer to a" );
    printf( " wide character:\n" );
    pmbc = NULL;
    i = mbtowc( pwc, pmbc, MB_CUR_MAX );
    printf( "   Bytes converted: %u\n", i );
}
```

```Output
Convert a wide character to multibyte character:
   Characters converted: 1
   Multibyte character: 61

Convert multibyte character back to a wide character:
   Bytes converted: 1
   Wide character: 61

Attempt to convert when target is NULL
   returns the length of the multibyte character:
   Length of multibyte character: 1

Attempt to convert a NULL pointer to a wide character:
   Bytes converted: 0
```

## <a name="see-also"></a>Voir aussi

[Conversion de données](../../c-runtime-library/data-conversion.md)<br/>
[MultiByteToWideChar](/windows/win32/api/stringapiset/nf-stringapiset-multibytetowidechar)<br/>
[Paramètres régionaux](../../c-runtime-library/locale.md)<br/>
[Interprétation des séquences de caractères multioctets](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[_mbclen, mblen, _mblen_l](mbclen-mblen-mblen-l.md)<br/>
[wcstombs, _wcstombs_l](wcstombs-wcstombs-l.md)<br/>
[wctomb, _wctomb_l](wctomb-wctomb-l.md)<br/>
