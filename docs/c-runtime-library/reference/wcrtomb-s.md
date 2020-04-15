---
title: wcrtomb_s
ms.date: 4/2/2020
api_name:
- wcrtomb_s
- _o_wcrtomb_s
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
- wcrtomb_s
helpviewer_keywords:
- wide characters, converting
- wcrtomb_s function
- multibyte characters
- characters, converting
ms.assetid: 9a8a1bd0-1d60-463d-a3a2-d83525eaf656
ms.openlocfilehash: ee25b18bfbb86b34e46c8c6776e8ab83157613e8
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328181"
---
# <a name="wcrtomb_s"></a>wcrtomb_s

Convertit un caractère large dans sa représentation de caractère multioctet. Version de [wcrtomb](wcrtomb.md) assortie des améliorations de sécurité décrites dans [Fonctionnalités de sécurité dans le CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Syntaxe

```C
errno_t wcrtomb_s(
   size_t *pReturnValue,
   char *mbchar,
   size_t sizeOfmbchar,
   wchar_t *wchar,
   mbstate_t *mbstate
);
template <size_t size>
errno_t wcrtomb_s(
   size_t *pReturnValue,
   char (&mbchar)[size],
   wchar_t *wchar,
   mbstate_t *mbstate
); // C++ only
```

### <a name="parameters"></a>Paramètres

*pReturnValue*<br/>
Retourne le nombre de caractères écrits ou -1 si une erreur s’est produite.

*mbchar (en)*<br/>
Résultat de la conversion du caractère multioctet.

*tailleOfmbchar*<br/>
La taille de la variable *mbchar* dans les octets.

*wchar (wchar)*<br/>
Caractère large à convertir.

*mbstate (en)*<br/>
Un pointeur à un objet **mbstate_t.**

## <a name="return-value"></a>Valeur de retour

Retourne zéro ou une valeur **d’errno** si une erreur se produit.

## <a name="remarks"></a>Notes

La fonction **wcrtomb_s** convertit un caractère large, à partir de l’état de conversion spécifié contenu dans *mbstate*, de la valeur contenue dans *wchar*, dans l’adresse représentée par *mbchar*. La valeur *pReturnValue* sera le nombre d’octets convertis, mais pas plus de **MB_CUR_MAX** octets, ou un -1 en cas d’erreur.

Si *le mbstate* est nul, l’état de conversion interne **mbstate_t** est utilisé. Si le personnage contenu dans *wchar* n’a pas de caractère multioctet correspondant, la valeur de *pReturnValue* sera de -1 et la fonction retournera la valeur **errno** de **EILSEQ**.

La fonction **wcrtomb_s** diffère de [wctomb_s, _wctomb_s_l](wctomb-s-wctomb-s-l.md) par sa redémarrabilité. L’état de conversion est stocké dans *mbstate* pour les appels ultérieurs vers les mêmes fonctions ou d’autres fonctions redémarrées. Les résultats ne sont pas définis quand l'utilisation de fonctions redémarrables est combinée avec l'utilisation de fonctions non redémarrables. Par exemple, une application utiliserait **wcsrlen** plutôt que **wcslen**, si un appel ultérieur à **wcsrtombs_s** ont été utilisés au lieu de **wcstombs_s**.

En C++, l’utilisation de cette fonction est simplifiée par les surcharges de modèle ; les surcharges peuvent déduire la longueur de la mémoire tampon automatiquement (ce qui évite d’avoir à spécifier un argument de taille) et peuvent remplacer automatiquement les fonctions plus anciennes et non sécurisées par leurs équivalents plus récents et sécurisés. Pour plus d’informations, consultez [Sécuriser les surcharges de modèle](../../c-runtime-library/secure-template-overloads.md).

Par défaut, l’état global de cette fonction est étendue à l’application. Pour changer cela, voir [Global State dans le CRT](../global-state.md).

## <a name="exceptions"></a>Exceptions

La fonction **wcrtomb_s** est multimarque aussi longtemps qu’aucune fonction dans le thread actuel appelle **setlocale** pendant que cette fonction est l’exécution et le *mbstate* est nul.

## <a name="example"></a>Exemple

```C
// crt_wcrtomb_s.c
// This program converts a wide character
// to its corresponding multibyte character.
//

#include <string.h>
#include <stdio.h>
#include <wchar.h>

int main( void )
{
    errno_t     returnValue;
    size_t      pReturnValue;
    mbstate_t   mbstate;
    size_t      sizeOfmbStr = 1;
    char        mbchar = 0;
    wchar_t*    wchar = L"Q\0";

    // Reset to initial conversion state
    memset(&mbstate, 0, sizeof(mbstate));

    returnValue = wcrtomb_s(&pReturnValue, &mbchar, sizeof(char),
                            *wchar, &mbstate);
    if (returnValue == 0) {
        printf("The corresponding wide character \"");
        wprintf(L"%s\"", wchar);
        printf(" was converted to a the \"%c\" ", mbchar);
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
The corresponding wide character "Q" was converted to a the "Q" multibyte character.
```

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**wcrtomb_s**|\<wchar.h>|

## <a name="see-also"></a>Voir aussi

[Conversion de données](../../c-runtime-library/data-conversion.md)<br/>
[Local](../../c-runtime-library/locale.md)<br/>
[Interprétation des séquences multioctets-caractères](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[mbsinit](mbsinit.md)<br/>
