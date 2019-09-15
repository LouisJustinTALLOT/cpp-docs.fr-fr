---
title: wctomb_s, _wctomb_s_l
ms.date: 11/04/2016
api_name:
- _wctomb_s_l
- wctomb_s
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
- wctomb_s
- _wctomb_s_l
helpviewer_keywords:
- wctomb_s function
- wctomb_s_l function
- string conversion, wide characters
- wide characters, converting
- _wctomb_s_l function
- characters, converting
- string conversion, multibyte character strings
ms.assetid: 7e94a888-deed-4dbd-b5e9-d4a0455538b8
ms.openlocfilehash: 329724ca0196e07397d4f0337a2bf0aa2db05c84
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70957890"
---
# <a name="wctomb_s-_wctomb_s_l"></a>wctomb_s, _wctomb_s_l

Convertit un caractère large en caractère multioctet correspondant. Version de [wctomb, _wctomb_l](wctomb-wctomb-l.md) assortie des améliorations de sécurité décrites dans [Fonctionnalités de sécurité dans le CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Syntaxe

```C
errno_t wctomb_s(
   int *pRetValue,
   char *mbchar,
   size_t sizeInBytes,
   wchar_t wchar
);
errno_t _wctomb_s_l(
   int *pRetValue,
   char *mbchar,
   size_t sizeInBytes,
   wchar_t wchar,
   _locale_t locale
);
```

### <a name="parameters"></a>Paramètres

*pRetValue*<br/>
Nombre d’octets ou code indiquant le résultat.

*mbchar*<br/>
Adresse d’un caractère multioctet.

*sizeInBytes*<br/>
Taille de la mémoire tampon *mbchar*.

*wchar*<br/>
Caractère large.

*locale*<br/>
Paramètres régionaux à utiliser.

## <a name="return-value"></a>Valeur de retour

Zéro si l'opération a réussi, un code d'erreur en cas d'échec.

Conditions d’erreur

|*mbchar*|*sizeInBytes*|Valeur de retour|*pRetValue*|
|--------------|-------------------|------------------|-----------------|
|**NULL**|>0|**EINVAL**|non modifié|
|any|>**INT_MAX**|**EINVAL**|non modifié|
|any|trop petit|**EINVAL**|non modifié|

Si l’une des conditions d’erreur ci-dessus se présente, le gestionnaire de paramètre non valide est appelé, comme décrit dans [Validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, **wctomb** retourne **EINVAL** et définit **errno** sur **EINVAL**.

## <a name="remarks"></a>Notes

La fonction **wctomb_s** convertit son argument *WCHAR* en caractère multioctet correspondant et stocke le résultat sur *mbchar*. Vous pouvez appeler la fonction de n’importe quel endroit dans n’importe quel programme.

Si **wctomb_s** convertit le caractère élargi en caractère multioctet, il place le nombre d’octets (qui n’est jamais supérieur à **MB_CUR_MAX**) dans le caractère élargi dans l’entier désigné par *pretvalue*. Si *WCHAR* est le caractère null à caractères larges (L' \ 0 '), **Wctomb_s** remplit *pretvalue* avec 1. Si le pointeur cible *mbchar* est **null**, **Wctomb_s** place 0 dans *pretvalue*. Si la conversion n’est pas possible dans les paramètres régionaux actuels, **wctomb_s** place-1 dans *pretvalue*.

**wctomb_s** utilise les paramètres régionaux actuels pour les informations dépendantes des paramètres régionaux ; **_wctomb_s_l** est identique, à ceci près qu’il utilise à la place les paramètres régionaux transmis. Pour plus d’informations, consultez [Locale](../../c-runtime-library/locale.md).

## <a name="requirements"></a>Configuration requise

|Routine|En-tête requis|
|-------------|---------------------|
|**wctomb_s**|\<stdlib.h>|
|**_wctomb_s_l**|\<stdlib.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

Ce programme illustre le comportement de la fonction **wctomb** .

```cpp
// crt_wctomb_s.cpp
#include <stdio.h>
#include <stdlib.h>

int main( void )
{
    int i;
    wchar_t wc = L'a';
    char *pmb = (char *)malloc( MB_CUR_MAX );

    printf_s( "Convert a wide character:\n" );
    wctomb_s( &i, pmb, MB_CUR_MAX, wc );
    printf_s( "   Characters converted: %u\n", i );
    printf_s( "   Multibyte character: %.1s\n\n", pmb );
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
