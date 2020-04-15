---
title: wcstombs_s, _wcstombs_s_l
ms.date: 4/2/2020
api_name:
- _wcstombs_s_l
- wcstombs_s
- _o__wcstombs_s_l
- _o_wcstombs_s
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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: c20066cddb3f28d31d2964ec720b64ed49836f65
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328048"
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
La taille dans les octets de la chaîne convertie, y compris le terminateur nul.

*mbstr*<br/>
Adresse d'une mémoire tampon pour la chaîne de caractères multioctets convertie résultante.

*sizeInBytes*<br/>
La taille dans les octets du tampon *mbstr.*

*wcstr*<br/>
Pointe vers la chaîne de caractères larges à convertir.

*count*<br/>
Le nombre maximal d’octets à stocker dans le tampon *mbstr,* sans compter le caractère null de fin, ou [_TRUNCATE](../../c-runtime-library/truncate.md).

*locale*<br/>
Paramètres régionaux à utiliser.

## <a name="return-value"></a>Valeur de retour

Zéro si l'opération a réussi, un code d'erreur en cas d'échec.

|État d’erreur|Valeur de rendement et **errno**|
|---------------------|------------------------------|
|*mbstr* est **NULL** et *tailleInBytes* > 0|**EINVAL (EN)**|
|*wcstr* est **NULL**|**EINVAL (EN)**|
|Le tampon de destination est trop petit pour contenir la chaîne convertie (à moins que *le compte* ne **soit _TRUNCATE**; voir Remarques ci-dessous)|**ERANGE**|

Si l’une de ces conditions se présente, l’exception de paramètre non valide est appelée, comme décrit dans [Validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, la fonction renvoie un code d’erreur et définit **errno** comme indiqué dans le tableau.

## <a name="remarks"></a>Notes

La fonction **wcstombs_s** convertit une chaîne de caractères larges pointés par *wcstr* en caractères multioctets stockés dans le tampon pointé vers *mbstr*. La conversion se poursuit pour chaque caractère jusqu'à ce qu'une des conditions suivantes soit remplie :

- Un caractère large null est rencontré

- Un caractère large qui ne peut pas être converti est rencontré

- Le nombre d’octets stockés dans le tampon *mbstr* *équivaut à compter*.

La chaîne de destination est toujours terminée par null (même en cas d'erreur).

Si *le compte* est la valeur spéciale [_TRUNCATE](../../c-runtime-library/truncate.md), puis **wcstombs_s** convertit autant de la chaîne que s’insérera dans le tampon de destination, tout en laissant de la place pour un terminateur nul. Si la chaîne est tronquée, la valeur de retour est **STRUNCATE**, et la conversion est considérée comme réussie.

Si **wcstombs_s** convertit avec succès la chaîne source, il met la taille dans les octets de la chaîne convertie, y compris le terminateur nul, en *&#42;pReturnValue* (fourni *pReturnValue* n’est pas **NULL**). Cela se produit même si l’argument *mbstr* est **NULL** et fournit un moyen de déterminer la taille du tampon requis. Notez que si *mbstr* est **NULL**, *le compte* est ignoré.

Si **wcstombs_s** rencontre un personnage large qu’il ne peut pas convertir en un personnage multioctet, il met 0 dans *&#42;pReturnValue*, définit le tampon de destination à une chaîne vide, définit **errno** à **EILSEQ**, et retourne **EILSEQ**.

Si les séquences pointées par *le wcstr* et le *mbstr* se chevauchent, le comportement de **wcstombs_s** est indéfini.

> [!IMPORTANT]
> Assurez-vous que *le wcstr* et *le mbstr* ne se chevauchent pas, et ce *nombre* reflète correctement le nombre de caractères larges à convertir.

**wcstombs_s** utilise le lieu actuel pour tout comportement local-dépendant; **_wcstombs_s_l** est identique aux **wcstombs,** sauf qu’il utilise le lieu passé à la place. Pour plus d’informations, consultez [Locale](../../c-runtime-library/locale.md).

En C++, l’utilisation de ces fonctions est simplifiée par les surcharges de modèle ; les surcharges peuvent déduire la longueur de la mémoire tampon automatiquement (ce qui évite d’avoir à spécifier un argument taille) et peuvent remplacer automatiquement les fonctions plus anciennes et non sécurisées par leurs équivalentes plus récentes et sécurisées. Pour plus d’informations, consultez [Sécuriser les surcharges de modèle](../../c-runtime-library/secure-template-overloads.md).

Par défaut, l’état global de cette fonction est étendue à l’application. Pour changer cela, voir [Global State dans le CRT](../global-state.md).

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**wcstombs_s**|\<stdlib.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

Ce programme illustre le comportement de la fonction **wcstombs_s.**

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
[Local](../../c-runtime-library/locale.md)<br/>
[_mbclen, mblen, _mblen_l](mbclen-mblen-mblen-l.md)<br/>
[mbstowcs, _mbstowcs_l](mbstowcs-mbstowcs-l.md)<br/>
[mbtowc, _mbtowc_l](mbtowc-mbtowc-l.md)<br/>
[wctomb_s, _wctomb_s_l](wctomb-s-wctomb-s-l.md)<br/>
[WideCharToMultiByte](/windows/win32/api/stringapiset/nf-stringapiset-widechartomultibyte)<br/>
