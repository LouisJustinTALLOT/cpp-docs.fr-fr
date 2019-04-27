---
title: wctomb_s, _wctomb_s_l
ms.date: 11/04/2016
apiname:
- _wctomb_s_l
- wctomb_s
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
ms.openlocfilehash: 08e8cb0ddaac342682776600fd0fd8b3d26b8953
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62188483"
---
# <a name="wctombs-wctombsl"></a>wctomb_s, _wctomb_s_l

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

Si l’une des conditions d’erreur ci-dessus se présente, le gestionnaire de paramètre non valide est appelé, comme décrit dans [Validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, **wctomb** retourne **EINVAL** et définit **errno** à **EINVAL**.

## <a name="remarks"></a>Notes

Le **wctomb_s** fonction convertit son *wchar* l’argument de caractère multioctet correspondant et stocke le résultat au niveau *mbchar*. Vous pouvez appeler la fonction de n’importe quel endroit dans n’importe quel programme.

Si **wctomb_s** convertit le caractère large en caractère multioctet, elle place le nombre d’octets (qui n’est jamais supérieure à **MB_CUR_MAX**) dans le caractère large dans l’entier désigné par *pRetValue*. Si *wchar* est le caractère null de caractères larges (L '\0'), **wctomb_s** remplit *pRetValue* avec 1. Si le pointeur cible *mbchar* est **NULL**, **wctomb_s** affecte la valeur 0 *pRetValue*. Si la conversion n’est pas possible dans les paramètres régionaux actuels, **wctomb_s** place -1 dans *pRetValue*.

**wctomb_s** utilise les paramètres régionaux actuels pour plus d’informations dépendantes des paramètres régionaux ; **_wctomb_s_l** est identique, sauf qu’elle utilise les paramètres régionaux à la place. Pour plus d’informations, consultez [Locale](../../c-runtime-library/locale.md).

## <a name="requirements"></a>Configuration requise

|Routine|En-tête requis|
|-------------|---------------------|
|**wctomb_s**|\<stdlib.h>|
|**_wctomb_s_l**|\<stdlib.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

Ce programme illustre le comportement de la **wctomb** (fonction).

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
[WideCharToMultiByte](/windows/desktop/api/stringapiset/nf-stringapiset-widechartomultibyte)<br/>
