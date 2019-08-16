---
title: wcstombs, _wcstombs_l
ms.date: 11/04/2016
apiname:
- wcstombs
- _wcstombs_l
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
- ntoskrnl.exe
apitype: DLLExport
f1_keywords:
- wcstombs
- _wcstombs_l
helpviewer_keywords:
- _wcstombs_l function
- wcstombs function
- string conversion, wide characters
- wide characters, converting
- wcstombs_l function
- characters, converting
- string conversion, multibyte character strings
ms.assetid: 91234252-9ea1-423a-af99-e9d0ce4a40e3
ms.openlocfilehash: b5ee2a0e5636e9c1d1f3fc204b2b6cbf8b733d45
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69498982"
---
# <a name="wcstombs-_wcstombs_l"></a>wcstombs, _wcstombs_l

Convertit une séquence de caractères larges en une séquence correspondante de caractères multioctets. Il existe des versions plus sécurisées de ces fonctions. Consultez [wcstombs_s, _wcstombs_s_l](wcstombs-s-wcstombs-s-l.md).

## <a name="syntax"></a>Syntaxe

```C
size_t wcstombs(
   char *mbstr,
   const wchar_t *wcstr,
   size_t count
);
size_t _wcstombs_l(
   char *mbstr,
   const wchar_t *wcstr,
   size_t count,
   _locale_t locale
);
template <size_t size>
size_t wcstombs(
   char (&mbstr)[size],
   const wchar_t *wcstr,
   size_t count
); // C++ only
template <size_t size>
size_t _wcstombs_l(
   char (&mbstr)[size],
   const wchar_t *wcstr,
   size_t count,
   _locale_t locale
); // C++ only
```

### <a name="parameters"></a>Paramètres

*mbstr*<br/>
Adresse d’une séquence de caractères multioctets.

*wcstr*<br/>
Adresse d’une séquence de caractères larges.

*count*<br/>
Nombre maximal d’octets pouvant être stockés dans la chaîne de sortie multioctet.

*locale*<br/>
Paramètres régionaux à utiliser.

## <a name="return-value"></a>Valeur de retour

Si **wcstombs** convertit correctement la chaîne multioctets, elle retourne le nombre d’octets écrits dans la chaîne de sortie multioctet, à l’exclusion de la valeur null de fin (le cas échéant). Si l’argument *mbstr* a la **valeur null**, **wcstombs** retourne la taille requise en octets de la chaîne de destination. Si **wcstombs** rencontre un caractère étendu qu’il ne peut pas convertir en caractère multioctet, elle retourne-1 cast en type **size_t** et définit **errno** sur **EILSEQ**.

## <a name="remarks"></a>Notes

La fonction **wcstombs** convertit la chaîne de caractères larges pointée par *wcstr* en caractères multioctets correspondants et stocke les résultats dans le tableau *mbstr* . Le paramètre *Count* indique le nombre maximal d’octets qui peuvent être stockés dans la chaîne de sortie multioctet (autrement dit, la taille de *mbstr*). En général, le nombre d’octets exigé au moment de la conversion d’une chaîne de caractères larges n’est pas connu. Certains caractères larges peuvent en exiger un seul dans la chaîne de sortie, alors que d’autres peuvent en exiger deux. S’il y a deux octets dans la chaîne de sortie multioctet pour chaque caractère élargi dans la chaîne d’entrée (y compris le caractère de largeur null), le résultat est garanti.

Si **wcstombs** rencontre le caractère null à caractères larges (L' \ 0 ') avant ou quand *Count* se produit, il le convertit en un 0 8 bits et s’arrête. Ainsi, la chaîne de caractères multioctets sur *mbstr* est terminée par un caractère NULL uniquement si **wcstombs** rencontre un caractère null à caractères larges pendant la conversion. Si les séquences pointées par *wcstr* et *mbstr* se chevauchent, le comportement de **wcstombs** n’est pas défini.

Si l’argument *mbstr* a la **valeur null**, **wcstombs** retourne la taille requise en octets de la chaîne de destination.

**wcstombs** valide ses paramètres. Si *wcstr* a la **valeur null**, ou si *Count* est supérieur à **INT_MAX**, cette fonction appelle le gestionnaire de paramètre non valide, comme décrit dans [validation de paramètre](../../c-runtime-library/parameter-validation.md) . Si l’exécution est autorisée à se poursuivre, la fonction affecte à **errno** la valeur **EINVAL** et retourne-1.

**wcstombs** utilise les paramètres régionaux actuels pour tout comportement dépendant des paramètres régionaux; **_wcstombs_l** est identique, à ceci près qu’il utilise à la place les paramètres régionaux transmis. Pour plus d’informations, consultez [Locale](../../c-runtime-library/locale.md).

En C++, ces fonctions ont des surcharges de modèle qui appellent les équivalents plus récents et sécurisés de ces fonctions. Pour plus d'informations, consultez [Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md).

## <a name="requirements"></a>Configuration requise

|Routine|En-tête requis|
|-------------|---------------------|
|**wcstombs**|\<stdlib.h>|
|**_wcstombs_l**|\<stdlib.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemples

Ce programme illustre le comportement de la fonction **wcstombs** .

```C
// crt_wcstombs.c
// compile with: /W3
// This example demonstrates the use
// of wcstombs, which converts a string
// of wide characters to a string of
// multibyte characters.

#include <stdlib.h>
#include <stdio.h>

#define BUFFER_SIZE 100

int main( void )
{
    size_t  count;
    char    *pMBBuffer = (char *)malloc( BUFFER_SIZE );
    wchar_t *pWCBuffer = L"Hello, world.";

    printf("Convert wide-character string:\n" );

    count = wcstombs(pMBBuffer, pWCBuffer, BUFFER_SIZE ); // C4996
    // Note: wcstombs is deprecated; consider using wcstombs_s instead
    printf("   Characters converted: %u\n",
            count );
    printf("    Multibyte character: %s\n\n",
           pMBBuffer );

    free(pMBBuffer);
}
```

```Output
Convert wide-character string:
   Characters converted: 13
    Multibyte character: Hello, world.
```

## <a name="see-also"></a>Voir aussi

[Conversion de données](../../c-runtime-library/data-conversion.md)<br/>
[Paramètres régionaux](../../c-runtime-library/locale.md)<br/>
[_mbclen, mblen, _mblen_l](mbclen-mblen-mblen-l.md)<br/>
[mbstowcs, _mbstowcs_l](mbstowcs-mbstowcs-l.md)<br/>
[mbtowc, _mbtowc_l](mbtowc-mbtowc-l.md)<br/>
[wctomb, _wctomb_l](wctomb-wctomb-l.md)<br/>
[WideCharToMultiByte](/windows/win32/api/stringapiset/nf-stringapiset-widechartomultibyte)<br/>
