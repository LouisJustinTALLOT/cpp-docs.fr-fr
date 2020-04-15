---
title: wcrtomb
ms.date: 4/2/2020
api_name:
- wcrtomb
- _o_wcrtomb
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
- wcrtomb
helpviewer_keywords:
- wide characters, converting
- wcrtomb function
- multibyte characters
- characters, converting
ms.assetid: 717f1b21-2705-4b7f-b6d0-82adc5224340
ms.openlocfilehash: eda857b80404aebe46b090741e0b56d4fe692f34
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328095"
---
# <a name="wcrtomb"></a>wcrtomb

Convertit un caractère large dans sa représentation de caractère multioctet. Il existe une version plus sécurisée de cette fonction. Consultez [wcrtomb_s](wcrtomb-s.md).

## <a name="syntax"></a>Syntaxe

```C
size_t wcrtomb(
   char *mbchar,
   wchar_t wchar,
   mbstate_t *mbstate
);
template <size_t size>
size_t wcrtomb(
   char (&mbchar)[size],
   wchar_t wchar,
   mbstate_t *mbstate
); // C++ only
```

### <a name="parameters"></a>Paramètres

*mbchar (en)*<br/>
Résultat de la conversion du caractère multioctet.

*wchar (wchar)*<br/>
Caractère large à convertir.

*mbstate (en)*<br/>
Un pointeur à un objet **mbstate_t.**

## <a name="return-value"></a>Valeur de retour

Retourne le nombre d’octets nécessaire pour représenter le caractère multioctet converti ou -1 si une erreur se produit.

## <a name="remarks"></a>Notes

La fonction **wcrtomb** convertit un caractère large, commençant dans l’état de conversion spécifié contenu dans *mbstate*, de la valeur contenue dans *wchar*, dans l’adresse représentée par *mbchar*. La valeur de retour est le nombre d’octets requis pour représenter le caractère multioctet correspondant, mais il ne retournera pas plus de **MB_CUR_MAX** octets.

Si *le mbstate* est nul, l’objet interne **mbstate_t** contenant l’état de conversion de *mbchar* est utilisé. Si la séquence de caractère *wchar* n’a pas une représentation de caractère multioctet correspondante, un -1 est retourné et **l’errno** est réglé à **EILSEQ**.

La fonction **wcrtomb** diffère de [wctomb, _wctomb_l](wctomb-wctomb-l.md) par sa redémarrabilité. L’état de conversion est stocké dans *mbstate* pour les appels ultérieurs vers les mêmes fonctions ou d’autres fonctions redémarrées. Les résultats ne sont pas définis quand l'utilisation de fonctions redémarrables est combinée avec l'utilisation de fonctions non redémarrables. Par exemple, une application utiliserait **wcsrlen** plutôt que **wcsnlen**, si un appel ultérieur à **wcsrtombs** ont été utilisés au lieu de **wcstombs**.

En C++, cette fonction a une surcharge de modèle qui appelle les équivalents plus récents et sécurisés de cette fonction. Pour plus d’informations, consultez [Sécuriser les surcharges de modèle](../../c-runtime-library/secure-template-overloads.md).

Par défaut, l’état global de cette fonction est étendue à l’application. Pour changer cela, voir [Global State dans le CRT](../global-state.md).

## <a name="exceptions"></a>Exceptions

La fonction **wcrtomb** est multimarque aussi longtemps qu’aucune fonction dans le thread actuel appelle **setlocale** pendant que cette fonction est l’exécution et tandis que le *mbstate* est nul.

## <a name="example"></a>Exemple

```C
// crt_wcrtomb.c
// compile with: /W3
// This program converts a wide character
// to its corresponding multibyte character.

#include <string.h>
#include <stdio.h>
#include <wchar.h>

int main( void )
{
    size_t      sizeOfCovertion = 0;
    mbstate_t   mbstate;
    char        mbStr = 0;
    wchar_t*    wcStr = L"Q";

    // Reset to initial conversion state
    memset(&mbstate, 0, sizeof(mbstate));

    sizeOfCovertion = wcrtomb(&mbStr, *wcStr, &mbstate); // C4996
    // Note: wcrtomb is deprecated; consider using wcrtomb_s instead
    if (sizeOfCovertion > 0)
    {
        printf("The corresponding wide character \"");
        wprintf(L"%s\"", wcStr);
        printf(" was converted to the \"%c\" ", mbStr);
        printf("multibyte character.\n");
    }
    else
    {
        printf("No corresponding multibyte character "
               "was found.\n");
    }
}
```

```Output
The corresponding wide character "Q" was converted to the "Q" multibyte character.
```

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**wcrtomb**|\<wchar.h>|

## <a name="see-also"></a>Voir aussi

[Conversion de données](../../c-runtime-library/data-conversion.md)<br/>
[Local](../../c-runtime-library/locale.md)<br/>
[Interprétation des séquences multioctets-caractères](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[mbsinit](mbsinit.md)<br/>
