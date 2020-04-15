---
title: mbstowcs, _mbstowcs_l
ms.date: 4/2/2020
api_name:
- mbstowcs
- _mbstowcs_l
- _o__mbstowcs_l
- _o_mbstowcs
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
- api-ms-win-crt-multibyte-l1-1-0.dll
- api-ms-win-crt-convert-l1-1-0.dll
- ntoskrnl.exe
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- mbstowcs
helpviewer_keywords:
- _mbstowcs_l function
- mbstowcs_l function
- mbstowcs function
ms.assetid: 96696b27-e068-4eeb-8006-3f7a0546ae6d
ms.openlocfilehash: 11ff6920ea5f1dad2925a8010c9202e012fad87a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81338846"
---
# <a name="mbstowcs-_mbstowcs_l"></a>mbstowcs, _mbstowcs_l

Convertit une séquence de caractères multioctets en séquence correspondante de caractères larges. Des versions plus sécurisées de ces fonctions sont disponibles. Consultez [mbstowcs_s, _mbstowcs_s_l](mbstowcs-s-mbstowcs-s-l.md).

## <a name="syntax"></a>Syntaxe

```C
size_t mbstowcs(
   wchar_t *wcstr,
   const char *mbstr,
   size_t count
);
size_t _mbstowcs_l(
   wchar_t *wcstr,
   const char *mbstr,
   size_t count,
   _locale_t locale
);
template <size_t size>
size_t mbstowcs(
   wchar_t (&wcstr)[size],
   const char *mbstr,
   size_t count
); // C++ only
template <size_t size>
size_t _mbstowcs_l(
   wchar_t (&wcstr)[size],
   const char *mbstr,
   size_t count,
   _locale_t locale
); // C++ only
```

### <a name="parameters"></a>Paramètres

*wcstr*<br/>
Adresse d’une séquence de caractères larges.

*mbstr*<br/>
Adresse d’une séquence de caractères multioctets se terminant par un caractère Null.

*count*<br/>
Nombre maximal de caractères multioctets à convertir.

*locale*<br/>
Paramètres régionaux à utiliser.

## <a name="return-value"></a>Valeur de retour

Si **mbstowcs** convertit avec succès la chaîne source, il renvoie le nombre de caractères multioctets convertis. Si l’argument *du wcstr* est **NULL**, la fonction renvoie la taille requise (en caractères larges) de la chaîne de destination. Si **les mbstowcs** rencontrent un caractère multioctet invalide, il revient -1. Si la valeur de retour est *comptée,* la corde à caractère large n’est pas annulée.

> [!IMPORTANT]
> Assurez-vous que *le wcstr* et *le mbstr* ne se chevauchent pas, et ce *nombre* reflète correctement le nombre de caractères multioctets à convertir.

## <a name="remarks"></a>Notes

La fonction **mbstowcs** convertit jusqu’à un nombre maximum de caractères multioctets *de comptage* pointés par *mbstr* à une chaîne de caractères larges correspondants qui sont déterminés par le lieu actuel. Il stocke la chaîne de caractère large résultant à l’adresse représentée par *wcstr*. Le résultat est similaire à une série d’appels à [mbtowc](mbtowc-mbtowc-l.md). Si **les mbstowcs** rencontrent le caractère nul uni-byte ('0') avant ou quand *le nombre* se produit, il convertit le caractère nul en un caractère nul de caractère large (L'0') et s’arrête. Ainsi, la corde de caractère large à *wcstr* n’est annulée que si un caractère nul est rencontré lors de la conversion. Si les séquences pointées par *le wcstr* et le *mbstr* se chevauchent, le comportement n’est pas défini.

Si l’argument *wcstr* est **NULL**, **mbstowcs** retourne le nombre de caractères larges qui résulteraient de la conversion, sans compter un terminateur nul. La chaîne source doit se terminer par un caractère Null pour que la valeur correcte soit retournée. S’il est nécessaire que la chaîne de caractères larges résultante se termine par un caractère Null, ajoutez un à la valeur retournée.

Si l’argument *du mbstr* est **NULL**, ou si le *nombre* est > **INT_MAX**, le gestionnaire de paramètres invalides est invoqué, tel que décrit dans la validation [de paramètres](../../c-runtime-library/parameter-validation.md) . Si l’exécution est autorisée à se poursuivre, errno est réglé sur **EINVAL** et la fonction renvoie -1.

**mbstowcs** utilise le lieu actuel pour tout comportement local-dépendant; **_mbstowcs_l** est identique, sauf qu’il utilise le lieu passé à la place. Pour plus d’informations, consultez [Locale](../../c-runtime-library/locale.md).

En C++, ces fonctions ont des surcharges de modèle qui appellent les équivalents plus récents et sécurisés de ces fonctions. Pour plus d’informations, consultez [Sécuriser les surcharges de modèle](../../c-runtime-library/secure-template-overloads.md).

Par défaut, l’état global de cette fonction est étendue à l’application. Pour changer cela, voir [Global State dans le CRT](../global-state.md).

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**mbstowcs**|\<stdlib.h>|
|**_mbstowcs_l**|\<stdlib.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

```C
// crt_mbstowcs.c
// compile with: /W3
// illustrates the behavior of the mbstowcs function

#include <stdlib.h>
#include <stdio.h>
#include <locale.h>

int main( void )
{
    size_t size;
    int nChar = 2; // number of characters to convert
    int requiredSize;

    unsigned char    *pmbnull  = NULL;
    unsigned char    *pmbhello = NULL;
    char* localeInfo;

    wchar_t *pwchello = L"\x3042\x3043"; // 2 Hiragana characters
    wchar_t *pwc;

    /* Enable the Japanese locale and codepage */
    localeInfo = setlocale(LC_ALL, "Japanese_Japan.932");
    printf("Locale information set to %s\n", localeInfo);

    printf( "Convert to multibyte string:\n" );

    requiredSize = wcstombs( NULL, pwchello, 0); // C4996
    // Note: wcstombs is deprecated; consider using wcstombs_s
    printf("   Required Size: %d\n", requiredSize);

    /* Add one to leave room for the null terminator. */
    pmbhello = (unsigned char *)malloc( requiredSize + 1);
    if (! pmbhello)
    {
        printf("Memory allocation failure.\n");
        return 1;
    }
    size = wcstombs( pmbhello, pwchello, requiredSize + 1); // C4996
    // Note: wcstombs is deprecated; consider using wcstombs_s
    if (size == (size_t) (-1))
    {
        printf("Couldn't convert string. Code page 932 may"
                " not be available.\n");
        return 1;
    }
    printf( "   Number of bytes written to multibyte string: %u\n",
            (unsigned int) size );
    printf( "   Hex values of the" );
    printf( " multibyte characters: %#.2x %#.2x %#.2x %#.2x\n",
            pmbhello[0], pmbhello[1], pmbhello[2], pmbhello[3] );
    printf( "   Codepage 932 uses 0x81 to 0x9f as lead bytes.\n\n");

    printf( "Convert back to wide-character string:\n" );

    /* Assume we don't know the length of the multibyte string.
     Get the required size in characters, and allocate enough space. */

    requiredSize = mbstowcs(NULL, pmbhello, 0); // C4996
    /* Add one to leave room for the null terminator */
    pwc = (wchar_t *)malloc( (requiredSize + 1) * sizeof( wchar_t ));
    if (! pwc)
    {
        printf("Memory allocation failure.\n");
        return 1;
    }
    size = mbstowcs( pwc, pmbhello, requiredSize + 1); // C4996
    if (size == (size_t) (-1))
    {
       printf("Couldn't convert string--invalid multibyte character.\n");
    }
    printf( "   Characters converted: %u\n", (unsigned int)size );
    printf( "   Hex value of first 2" );
    printf( " wide characters: %#.4x %#.4x\n\n", pwc[0], pwc[1] );
    free(pwc);
    free(pmbhello);
}
```

```Output
Locale information set to Japanese_Japan.932
Convert to multibyte string:
   Required Size: 4
   Number of bytes written to multibyte string: 4
   Hex values of the  multibyte characters: 0x82 0xa0 0x82 0xa1
   Codepage 932 uses 0x81 to 0x9f as lead bytes.

Convert back to wide-character string:
   Characters converted: 2
   Hex value of first 2 wide characters: 0x3042 0x3043
```

## <a name="see-also"></a>Voir aussi

[Conversion de données](../../c-runtime-library/data-conversion.md)<br/>
[Local](../../c-runtime-library/locale.md)<br/>
[Interprétation des séquences multioctets-caractères](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[_mbclen, mblen, _mblen_l](mbclen-mblen-mblen-l.md)<br/>
[mbtowc, _mbtowc_l](mbtowc-mbtowc-l.md)<br/>
[wcstombs, _wcstombs_l](wcstombs-wcstombs-l.md)<br/>
[wctomb, _wctomb_l](wctomb-wctomb-l.md)<br/>
[MultiByteToWideChar](/windows/win32/api/stringapiset/nf-stringapiset-multibytetowidechar)<br/>
