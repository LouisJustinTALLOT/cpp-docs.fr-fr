---
title: wctob
ms.date: 11/04/2016
apiname:
- wctob
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
- ucrtbase.dll
- api-ms-win-crt-convert-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- wctob
helpviewer_keywords:
- wide characters, converting
- wctob function
- characters, converting
ms.assetid: 46aec98b-c2f2-4e9d-9d89-7db99ba8a9a6
ms.openlocfilehash: 1d9dca16ca905afbc94d912a8083017ba9cc84e6
ms.sourcegitcommit: afd6fac7c519dbc47a4befaece14a919d4e0a8a2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/10/2018
ms.locfileid: "51522517"
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

Si **wctob** convertit correctement un caractère large, elle retourne sa représentation sous forme de caractère multioctet, uniquement si le caractère multioctet est un octet exactement. Si **wctob** rencontre un caractère large, elle ne peut pas convertir en un caractère multioctet ou le caractère multioctet est de pas exactement un octet, elle retourne une valeur -1.

## <a name="remarks"></a>Notes

Le **wctob** fonction convertit un caractère large contenu dans *wchar* caractère multioctet correspondant passé par la valeur de retour **int** valeur, si le multioctets caractère est un octet exactement.

Si **wctob** a échoué et qu’aucun caractère multioctet correspondant a été trouvé, la fonction définit **errno** à **EILSEQ** et retourne -1.

## <a name="requirements"></a>Configuration requise

|Routine|En-tête requis|
|-------------|---------------------|
|**wctob**|\<wchar.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

Ce programme illustre le comportement de la **wcstombs** (fonction).

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
[WideCharToMultiByte](/windows/desktop/api/stringapiset/nf-stringapiset-widechartomultibyte)<br/>
