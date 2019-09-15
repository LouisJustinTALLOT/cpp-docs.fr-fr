---
title: wcstombs_s, _wcstombs_s_l
ms.date: 11/04/2016
api_name:
- _wcstombs_s_l
- wcstombs_s
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
- wcstombs_s
- _wcstombs_s_l
helpviewer_keywords:
- wcstombs_s function
- string conversion, wide characters
- wide characters, converting
- _wcstombs_s_l function
- wcstombs_s_l function
- characters, converting
- string conversion, multibyte character strings
ms.assetid: 105f2d33-221a-4f6d-864c-23c1865c42af
ms.openlocfilehash: 135bcb90e6a82591bf05e56b60575719f4c7d45c
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70945027"
---
# <a name="wcstombs_s-_wcstombs_s_l"></a>wcstombs_s, _wcstombs_s_l

Convertit une séquence de caractères larges en une séquence correspondante de caractères multioctets. Version de [wctombs, _wctombs_l](wcstombs-wcstombs-l.md) assortie des améliorations de sécurité décrites dans [Fonctionnalités de sécurité dans le CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Syntaxe

```C
errno_t wcstombs_s(
   size_t *pReturnValue,
   char *mbstr,
   size_t sizeInBytes,
   const wchar_t *wcstr,
   size_t count
);

errno_t _wcstombs_s_l(
   size_t *pReturnValue,
   char *mbstr,
   size_t sizeInBytes,
   const wchar_t *wcstr,
   size_t count,
   _locale_t locale
);

template <size_t size>
errno_t wcstombs_s(
   size_t *pReturnValue,
   char (&mbstr)[size],
   const wchar_t *wcstr,
   size_t count
); // C++ only

template <size_t size>
errno_t _wcstombs_s_l(
   size_t *pReturnValue,
   char (&mbstr)[size],
   const wchar_t *wcstr,
   size_t count,
   _locale_t locale
); // C++ only
```

### <a name="parameters"></a>Paramètres

*pReturnValue*<br/>
Taille en octets de la chaîne convertie, y compris la marque de fin null.

*mbstr*<br/>
Adresse d'une mémoire tampon pour la chaîne de caractères multioctets convertie résultante.

*sizeInBytes*<br/>
Taille en octets de la mémoire tampon *mbstr* .

*wcstr*<br/>
Pointe vers la chaîne de caractères larges à convertir.

*count*<br/>
Nombre maximal d’octets à stocker dans la mémoire tampon *mbstr* , à l’exclusion du caractère null de fin, ou [_TRUNCATE](../../c-runtime-library/truncate.md).

*locale*<br/>
Paramètres régionaux à utiliser.

## <a name="return-value"></a>Valeur de retour

Zéro si l'opération a réussi, un code d'erreur en cas d'échec.

|Condition d'erreur|Valeur de retour et **errno**|
|---------------------|------------------------------|
|*mbstr* a la **valeur NULL** et *sizeInBytes* > 0|**EINVAL**|
|*wcstr* a la **valeur null**|**EINVAL**|
|La mémoire tampon de destination est trop petite pour contenir la chaîne convertie (sauf si *Count* est **_TRUNCATE**; consultez les remarques ci-dessous)|**ERANGE**|

Si l’une de ces conditions se présente, l’exception de paramètre non valide est appelée, comme décrit dans [Validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, la fonction retourne un code d’erreur et définit **errno** comme indiqué dans le tableau.

## <a name="remarks"></a>Notes

La fonction **wcstombs_s** convertit une chaîne de caractères larges pointée par *wcstr* en caractères multioctets stockés dans la mémoire tampon pointée par *mbstr*. La conversion se poursuit pour chaque caractère jusqu'à ce qu'une des conditions suivantes soit remplie :

- Un caractère large null est rencontré

- Un caractère large qui ne peut pas être converti est rencontré

- Le nombre d’octets stockés dans la mémoire tampon *mbstr* est égal à *Count*.

La chaîne de destination est toujours terminée par null (même en cas d'erreur).

Si *Count* est la valeur spéciale [_TRUNCATE](../../c-runtime-library/truncate.md), **wcstombs_s** convertit le plus possible la chaîne telle qu’elle est contenue dans la mémoire tampon de destination, tout en laissant de l’espace pour une marque de fin null. Si la chaîne est tronquée, la valeur de retour est **STRUNCATE**, et la conversion est considérée comme réussie.

Si **wcstombs_s** convertit correctement la chaîne source, elle place la taille en octets de la chaîne convertie, y compris la marque de fin null, dans  *&#42;pReturnValue* (le *pReturnValue* fourni n’est pas **null**). Cela se produit même si l’argument *mbstr* est **null** et fournit un moyen de déterminer la taille de mémoire tampon requise. Notez que si *mbstr* a la **valeur null**, *Count* est ignoré.

Si **wcstombs_s** rencontre un caractère étendu qu’il ne peut pas convertir en caractère multioctet, il place 0 dans  *&#42;pReturnValue*, définit la mémoire tampon de destination sur une chaîne vide, définit **errno** sur **EILSEQ**et retourne **EILSEQ**.

Si les séquences pointées par *wcstr* et *mbstr* se chevauchent, le comportement de **wcstombs_s** n’est pas défini.

> [!IMPORTANT]
> Assurez-vous que *wcstr* et *mbstr* ne se chevauchent pas, et que ce *nombre* reflète correctement le nombre de caractères larges à convertir.

**wcstombs_s** utilise les paramètres régionaux actuels pour tout comportement dépendant des paramètres régionaux ; **_wcstombs_s_l** est identique à **wcstombs** , à ceci près qu’il utilise à la place les paramètres régionaux transmis. Pour plus d’informations, consultez [Locale](../../c-runtime-library/locale.md).

En C++, l’utilisation de ces fonctions est simplifiée par les surcharges de modèle ; les surcharges peuvent déduire la longueur de la mémoire tampon automatiquement (ce qui évite d’avoir à spécifier un argument taille) et peuvent remplacer automatiquement les fonctions plus anciennes et non sécurisées par leurs équivalentes plus récentes et sécurisées. Pour plus d'informations, consultez [Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md).

## <a name="requirements"></a>Configuration requise

|Routine|En-tête requis|
|-------------|---------------------|
|**wcstombs_s**|\<stdlib.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemples

Ce programme illustre le comportement de la fonction **wcstombs_s** .

```C
// crt_wcstombs_s.c
// This example converts a wide character
// string to a multibyte character string.
#include <stdio.h>
#include <stdlib.h>
#include <assert.h>

#define BUFFER_SIZE 100

int main( void )
{
    size_t   i;
    char      *pMBBuffer = (char *)malloc( BUFFER_SIZE );
    wchar_t*pWCBuffer = L"Hello, world.";

    printf( "Convert wide-character string:\n" );

    // Conversion
    wcstombs_s(&i, pMBBuffer, (size_t)BUFFER_SIZE,
               pWCBuffer, (size_t)BUFFER_SIZE );

    // Output
    printf("   Characters converted: %u\n", i);
    printf("    Multibyte character: %s\n\n",
     pMBBuffer );

    // Free multibyte character buffer
    if (pMBBuffer)
    {
    free(pMBBuffer);
    }
}
```

```Output
Convert wide-character string:
   Characters converted: 14
    Multibyte character: Hello, world.
```

## <a name="see-also"></a>Voir aussi

[Conversion de données](../../c-runtime-library/data-conversion.md)<br/>
[Paramètres régionaux](../../c-runtime-library/locale.md)<br/>
[_mbclen, mblen, _mblen_l](mbclen-mblen-mblen-l.md)<br/>
[mbstowcs, _mbstowcs_l](mbstowcs-mbstowcs-l.md)<br/>
[mbtowc, _mbtowc_l](mbtowc-mbtowc-l.md)<br/>
[wctomb_s, _wctomb_s_l](wctomb-s-wctomb-s-l.md)<br/>
[WideCharToMultiByte](/windows/win32/api/stringapiset/nf-stringapiset-widechartomultibyte)<br/>
