---
title: wcstombs, _wcstombs_l
ms.date: 4/2/2020
api_name:
- wcstombs
- _wcstombs_l
- _o__wcstombs_l
- _o_wcstombs
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
ms.openlocfilehash: fb95c6d73a3979a39995b9104a76fc42ca9e8535
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366720"
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

Si **les wcstombs** convertissent avec succès la chaîne multioctet, il renvoie le nombre d’octets inscrits dans la chaîne de sortie multioctets, à l’exclusion de la mise fin nulle (le cas échéant). Si l’argument *mbstr* est **NULL**, **wcstombs** retourne la taille requise dans les octets de la chaîne de destination. Si **wcstombs** rencontre un personnage large qu’il ne peut pas convertir en un personnage multioctet, il retourne -1 casting pour taper **size_t** et définit **errno** à **EILSEQ**.

## <a name="remarks"></a>Notes

La fonction **wcstombs** convertit la chaîne à caractère large pointée par *wcstr* aux caractères multioctets correspondants et stocke les résultats dans le tableau *mbstr.* Le *paramètre* de comptage indique le nombre maximum d’octets qui peuvent être stockés dans la chaîne de sortie multioctets (c’est-à-dire la taille de *mbstr).* En général, le nombre d’octets exigé au moment de la conversion d’une chaîne de caractères larges n’est pas connu. Certains caractères larges peuvent en exiger un seul dans la chaîne de sortie, alors que d’autres peuvent en exiger deux. S’il y a deux octets dans la chaîne de sortie multioctet pour chaque personnage large dans la chaîne d’entrée (y compris le caractère large nul), le résultat est garanti pour s’adapter.

Si **les wcstombs** rencontrent le caractère nul à caractère large (L'0') avant ou quand *le compte* se produit, il le convertit en un 0 8 bits et s’arrête. Ainsi, la chaîne de caractère multioctet à *mbstr* n’est annulée que si **wcstombs** rencontre un caractère nul à caractère large lors de la conversion. Si les séquences pointées par *le wcstr* et le *mbstr* se chevauchent, le comportement des **wcstombs** n’est pas défini.

Si l’argument *mbstr* est **NULL**, **wcstombs** retourne la taille requise dans les octets de la chaîne de destination.

**wcstombs** valide ses paramètres. Si *wcstr* est **NULL**, ou si *le nombre* est plus grand que **INT_MAX**, cette fonction invoque le gestionnaire de paramètres invalides, tel que décrit dans La validation [de paramètres](../../c-runtime-library/parameter-validation.md) . Si l’exécution est autorisée à se poursuivre, la fonction définit **errno** à **EINVAL** et renvoie -1.

**wcstombs** utilise le lieu actuel pour tout comportement local-dépendant; **_wcstombs_l** est identique, sauf qu’il utilise le lieu passé à la place. Pour plus d’informations, consultez [Locale](../../c-runtime-library/locale.md).

En C++, ces fonctions ont des surcharges de modèle qui appellent les équivalents plus récents et sécurisés de ces fonctions. Pour plus d’informations, consultez [Sécuriser les surcharges de modèle](../../c-runtime-library/secure-template-overloads.md).

Par défaut, l’état global de cette fonction est étendue à l’application. Pour changer cela, voir [Global State dans le CRT](../global-state.md).

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**wcstombs**|\<stdlib.h>|
|**_wcstombs_l**|\<stdlib.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

Ce programme illustre le comportement de la fonction **wcstombs.**

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
[Local](../../c-runtime-library/locale.md)<br/>
[_mbclen, mblen, _mblen_l](mbclen-mblen-mblen-l.md)<br/>
[mbstowcs, _mbstowcs_l](mbstowcs-mbstowcs-l.md)<br/>
[mbtowc, _mbtowc_l](mbtowc-mbtowc-l.md)<br/>
[wctomb, _wctomb_l](wctomb-wctomb-l.md)<br/>
[WideCharToMultiByte](/windows/win32/api/stringapiset/nf-stringapiset-widechartomultibyte)<br/>
