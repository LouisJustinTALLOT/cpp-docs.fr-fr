---
title: wctomb, _wctomb_l
ms.date: 4/2/2020
api_name:
- _wctomb_l
- wctomb
- _o__wctomb_l
- _o_wctomb
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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: 162585ea866b4fb26cfaae3bc94345dadaba0baa
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367399"
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

*mbchar (en)*<br/>
Adresse d’un caractère multioctet.

*wchar (wchar)*<br/>
Caractère large.

## <a name="return-value"></a>Valeur de retour

Si **wctomb** convertit le caractère large en un caractère multioctet, il renvoie le nombre d’octets (qui n’est jamais plus grand que **MB_CUR_MAX)** dans le caractère large. Si *wchar* est le caractère nul à caractère large (L'0'), **wctomb** revient 1. Si le pointeur cible *mbchar* est **NULL**, **wctomb** retourne 0. Si la conversion n’est pas possible dans le lieu actuel, **wctomb** retourne -1 et **errno** est réglé à **EILSEQ**.

## <a name="remarks"></a>Notes

La fonction **wctomb** convertit son argument *wchar* au caractère multioctet correspondant et stocke le résultat à *mbchar*. Vous pouvez appeler la fonction de n’importe quel endroit dans n’importe quel programme. **wctomb** utilise le lieu actuel pour tout comportement local-dépendant; **_wctomb_l** est identique à **wctomb,** sauf qu’il utilise le lieu passé à la place. Pour plus d’informations, consultez [Locale](../../c-runtime-library/locale.md).

**wctomb** valide ses paramètres. Si *mbchar* est **NULL**, le gestionnaire de paramètre invalide est invoqué, tel que décrit dans [La validation de paramètres](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, **errno** est réglé sur **EINVAL** et la fonction renvoie -1.

Par défaut, l’état global de cette fonction est étendue à l’application. Pour changer cela, voir [Global State dans le CRT](../global-state.md).

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**wctomb**|\<stdlib.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

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
[Local](../../c-runtime-library/locale.md)<br/>
[_mbclen, mblen, _mblen_l](mbclen-mblen-mblen-l.md)<br/>
[mbstowcs, _mbstowcs_l](mbstowcs-mbstowcs-l.md)<br/>
[mbtowc, _mbtowc_l](mbtowc-mbtowc-l.md)<br/>
[wcstombs, _wcstombs_l](wcstombs-wcstombs-l.md)<br/>
[WideCharToMultiByte](/windows/win32/api/stringapiset/nf-stringapiset-widechartomultibyte)<br/>
