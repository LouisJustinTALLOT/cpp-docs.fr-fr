---
title: wctomb, _wctomb_l
ms.date: 11/04/2016
api_name:
- _wctomb_l
- wctomb
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
- ntoskrnl.exe
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- wctomb
helpviewer_keywords:
- string conversion, wide characters
- wide characters, converting
- _wctomb_l function
- wctomb function
- wctomb_l function
- characters, converting
- string conversion, multibyte character strings
ms.assetid: 4a543f0e-5516-4d81-8ff2-3c5206f02ed5
ms.openlocfilehash: 195105618c75bd2a3a493f169fca4c2d3d4ebd62
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70944999"
---
# <a name="wctomb-_wctomb_l"></a>wctomb, _wctomb_l

Convertit un caractère large en caractère multioctet correspondant. Il existe des versions plus sécurisées de ces fonctions. Consultez [wctomb_s, _wctomb_s_l](wctomb-s-wctomb-s-l.md).

## <a name="syntax"></a>Syntaxe

```C
int wctomb(
   char *mbchar,
   wchar_t wchar
);
int _wctomb_l(
   char *mbchar,
   wchar_t wchar,
   _locale_t locale
);
```

### <a name="parameters"></a>Paramètres

*mbchar*<br/>
Adresse d’un caractère multioctet.

*wchar*<br/>
Caractère large.

## <a name="return-value"></a>Valeur de retour

Si **wctomb** convertit le caractère larges en caractère multioctet, il retourne le nombre d’octets (qui n’est jamais supérieur à **MB_CUR_MAX**) dans le caractère élargi. Si *WCHAR* est le caractère null à caractères larges (L' \ 0 '), **wctomb** retourne 1. Si le pointeur cible *mbchar* est **null**, **wctomb** retourne 0. Si la conversion n’est pas possible dans les paramètres régionaux actuels, **wctomb** retourne-1 et **errno** a la valeur **EILSEQ**.

## <a name="remarks"></a>Notes

La fonction **wctomb** convertit son argument *WCHAR* en caractère multioctet correspondant et stocke le résultat sur *mbchar*. Vous pouvez appeler la fonction de n’importe quel endroit dans n’importe quel programme. **wctomb** utilise les paramètres régionaux actuels pour tout comportement dépendant des paramètres régionaux ; **_wctomb_l** est identique à **wctomb** , à ceci près qu’il utilise à la place les paramètres régionaux transmis. Pour plus d’informations, consultez [Locale](../../c-runtime-library/locale.md).

**wctomb** valide ses paramètres. Si *mbchar* a la **valeur null**, le gestionnaire de paramètres non valides est appelé, comme décrit dans [validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, **errno** a la valeur **EINVAL** et la fonction retourne-1.

## <a name="requirements"></a>Configuration requise

|Routine|En-tête requis|
|-------------|---------------------|
|**wctomb**|\<stdlib.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemples

Ce programme illustre le comportement de la fonction wctomb.

```cpp
// crt_wctomb.cpp
// compile with: /W3
#include <stdio.h>
#include <stdlib.h>

int main( void )
{
   int i;
   wchar_t wc = L'a';
   char *pmb = (char *)malloc( MB_CUR_MAX );

   printf( "Convert a wide character:\n" );
   i = wctomb( pmb, wc ); // C4996
   // Note: wctomb is deprecated; consider using wctomb_s
   printf( "   Characters converted: %u\n", i );
   printf( "   Multibyte character: %.1s\n\n", pmb );
}
```

```Output
Convert a wide character:
   Characters converted: 1
   Multibyte character: a
```

## <a name="see-also"></a>Voir aussi

[Conversion de données](../../c-runtime-library/data-conversion.md)<br/>
[Paramètres régionaux](../../c-runtime-library/locale.md)<br/>
[_mbclen, mblen, _mblen_l](mbclen-mblen-mblen-l.md)<br/>
[mbstowcs, _mbstowcs_l](mbstowcs-mbstowcs-l.md)<br/>
[mbtowc, _mbtowc_l](mbtowc-mbtowc-l.md)<br/>
[wcstombs, _wcstombs_l](wcstombs-wcstombs-l.md)<br/>
[WideCharToMultiByte](/windows/win32/api/stringapiset/nf-stringapiset-widechartomultibyte)<br/>
