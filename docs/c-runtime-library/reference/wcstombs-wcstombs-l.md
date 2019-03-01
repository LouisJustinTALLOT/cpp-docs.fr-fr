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
ms.openlocfilehash: d102cd74061faeb0c41823e6cf5c9a8ef335294f
ms.sourcegitcommit: e06648107065f3dea35f40c1ae5999391087b80b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/01/2019
ms.locfileid: "57210729"
---
# <a name="wcstombs-wcstombsl"></a>wcstombs, _wcstombs_l

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

Si **wcstombs** convertit correctement la chaîne multioctet, elle retourne le nombre d’octets écrits dans la chaîne de sortie multioctet, à l’exclusion du caractère null de fin (le cas échéant). Si le *mbstr* argument est **NULL**, **wcstombs** retourne la taille en octets de la chaîne de destination. Si **wcstombs** rencontre un caractère large qu’elle ne peut pas convertir en un caractère multioctet, elle retourne -1 castée en type **size_t** et définit **errno** à **EILSEQ** .

## <a name="remarks"></a>Notes

Le **wcstombs** fonction convertit la chaîne de caractères larges vers laquelle pointée *wcstr* à caractères multioctets correspondants et les stocke les résultats dans le *mbstr* tableau. Le *nombre* paramètre indique le nombre maximal d’octets qui peuvent être stockées dans la chaîne de sortie multioctet (autrement dit, la taille de *mbstr*). En général, le nombre d’octets exigé au moment de la conversion d’une chaîne de caractères larges n’est pas connu. Certains caractères larges peuvent en exiger un seul dans la chaîne de sortie, alors que d’autres peuvent en exiger deux. S’il existe deux octets dans la chaîne de sortie multioctet pour chaque caractère large dans la chaîne d’entrée (y compris la valeur null de caractère large), le résultat est assuré de s’intégrer.

Si **wcstombs** rencontre le caractère null de caractères larges (L '\0') avant ou quand *nombre* se produit, il est converti en un 0 de 8 bits et s’arrête. Par conséquent, la chaîne de caractères multioctets à *mbstr* est nul uniquement si **wcstombs** rencontre un caractère null large pendant la conversion. Si les séquences pointées par *wcstr* et *mbstr* se chevauchent, le comportement de **wcstombs** n’est pas défini.

Si le *mbstr* argument est **NULL**, **wcstombs** retourne la taille en octets de la chaîne de destination.

**wcstombs** valide ses paramètres. Si *wcstr* est **NULL**, ou si *nombre* est supérieur à **INT_MAX**, cette fonction appelle le Gestionnaire de paramètre non valide, comme décrit dans [Validation de paramètre](../../c-runtime-library/parameter-validation.md) . Si l’exécution est autorisée à se poursuivre, la fonction définit **errno** à **EINVAL** et retourne -1.

**wcstombs** utilise les paramètres régionaux actuels pour tout comportement dépendant des paramètres régionaux ; **_wcstombs_l** est identique, sauf qu’elle utilise les paramètres régionaux à la place. Pour plus d’informations, consultez [Locale](../../c-runtime-library/locale.md).

En C++, ces fonctions ont des surcharges de modèle qui appellent les équivalents plus récents et sécurisés de ces fonctions. Pour plus d'informations, consultez [Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md).

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**wcstombs**|\<stdlib.h>|
|**_wcstombs_l**|\<stdlib.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

Ce programme illustre le comportement de la **wcstombs** (fonction).

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
[WideCharToMultiByte](/windows/desktop/api/stringapiset/nf-stringapiset-widechartomultibyte)<br/>
