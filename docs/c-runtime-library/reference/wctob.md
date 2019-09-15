---
title: wctob
ms.date: 11/04/2016
api_name:
- wctob
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- wctob
helpviewer_keywords:
- wide characters, converting
- wctob function
- characters, converting
ms.assetid: 46aec98b-c2f2-4e9d-9d89-7db99ba8a9a6
ms.openlocfilehash: 151325b0d66e6d57156cdf94828ca1d4b151d437
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70944932"
---
# <a name="wctob"></a>wctob

Détermine si un caractère large correspond à un caractère multioctet et retourne sa représentation de caractère multioctet.

## <a name="syntax"></a>Syntaxe

```C
int wctob(
   wint_t wchar
);
```

### <a name="parameters"></a>Paramètres

*wchar*<br/>
Valeur à traduire.

## <a name="return-value"></a>Valeur de retour

Si **wctob** convertit correctement un caractère élargi, il retourne sa représentation de caractère multioctet, uniquement si la longueur du caractère multioctet est d’un octet exactement. Si **wctob** rencontre un caractère étendu qu’il ne peut pas convertir en caractère multioctet ou si le caractère multioctet n’est pas exactement d’un octet, il retourne-1.

## <a name="remarks"></a>Notes

La fonction **wctob** convertit un caractère élargi contenu dans *WCHAR* en caractère multioctet correspondant passé par la valeur **int** de retour, si le caractère multioctet est exactement d’un octet.

Si **wctob** a échoué et qu’aucun caractère multioctet correspondant n’a été trouvé, la fonction affecte à **errno** la valeur **EILSEQ** et retourne-1.

## <a name="requirements"></a>Configuration requise

|Routine|En-tête requis|
|-------------|---------------------|
|**wctob**|\<wchar.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

Ce programme illustre le comportement de la fonction **wcstombs** .

```C
// crt_wctob.c
#include <stdio.h>
#include <wchar.h>

int main( void )
{
    int     bChar = 0;
    wint_t  wChar = 0;

    // Set the corresponding wide character to exactly one byte.
    wChar = (wint_t)'A';

    bChar = wctob( wChar );
    if (bChar == WEOF)
    {
        printf( "No corresponding multibyte character was found.\n");
    }
    else
    {
        printf( "Determined the corresponding multibyte character to"
                " be \"%c\".\n", bChar);
    }
}
```

```Output
Determined the corresponding multibyte character to be "A".
```

## <a name="see-also"></a>Voir aussi

[Conversion de données](../../c-runtime-library/data-conversion.md)<br/>
[Paramètres régionaux](../../c-runtime-library/locale.md)<br/>
[_mbclen, mblen, _mblen_l](mbclen-mblen-mblen-l.md)<br/>
[mbstowcs, _mbstowcs_l](mbstowcs-mbstowcs-l.md)<br/>
[mbtowc, _mbtowc_l](mbtowc-mbtowc-l.md)<br/>
[wctomb, _wctomb_l](wctomb-wctomb-l.md)<br/>
[WideCharToMultiByte](/windows/win32/api/stringapiset/nf-stringapiset-widechartomultibyte)<br/>
