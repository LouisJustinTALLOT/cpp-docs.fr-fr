---
title: wcrtomb_s
ms.date: 11/04/2016
api_name:
- wcrtomb_s
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
- wcrtomb_s
helpviewer_keywords:
- wide characters, converting
- wcrtomb_s function
- multibyte characters
- characters, converting
ms.assetid: 9a8a1bd0-1d60-463d-a3a2-d83525eaf656
ms.openlocfilehash: c1612e7fc4e40e05c46f06d8a29b69534c359421
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70945843"
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

*mbchar*<br/>
Résultat de la conversion du caractère multioctet.

*sizeOfmbchar*<br/>
Taille de la variable *mbchar* en octets.

*wchar*<br/>
Caractère large à convertir.

*mbstate*<br/>
Pointeur vers un objet **mbstate_t** .

## <a name="return-value"></a>Valeur de retour

Retourne zéro ou une valeur **errno** si une erreur se produit.

## <a name="remarks"></a>Notes

La fonction **wcrtomb_s** convertit un caractère élargi, en commençant dans l’état de conversion spécifié dans *mbstate*, à partir de la valeur contenue dans *WCHAR*, dans l’adresse représentée par *mbchar*. La valeur *pReturnValue* est le nombre d’octets convertis, mais pas plus de **MB_CUR_MAX** octets, ou-1 si une erreur s’est produite.

Si *mbstate* a la valeur null, l’état de conversion **mbstate_t** interne est utilisé. Si le caractère contenu dans *WCHAR* n’a pas de caractère multioctet correspondant, la valeur de *pReturnValue* est-1 et la fonction retourne la valeur **errno** de **EILSEQ**.

La fonction **wcrtomb_s** diffère de [wctomb_s, _wctomb_s_l](wctomb-s-wctomb-s-l.md) par son redémarrage. L’état de conversion est stocké dans *mbstate* pour les appels suivants à la même ou à d’autres fonctions redémarrables. Les résultats ne sont pas définis quand l'utilisation de fonctions redémarrables est combinée avec l'utilisation de fonctions non redémarrables. Par exemple, une application utilise **wcsrlen** plutôt que **wcslen**, si un appel ultérieur à **wcsrtombs_s** était utilisé à la place de **wcstombs_s**.

En C++, l’utilisation de cette fonction est simplifiée par les surcharges de modèle ; les surcharges peuvent déduire la longueur de la mémoire tampon automatiquement (ce qui évite d’avoir à spécifier un argument de taille) et peuvent remplacer automatiquement les fonctions plus anciennes et non sécurisées par leurs équivalents plus récents et sécurisés. Pour plus d'informations, consultez [Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md).

## <a name="exceptions"></a>Exceptions

La fonction **wcrtomb_s** est multithread Safe tant qu’aucune fonction dans le thread actuel n’appelle **setlocale** pendant que cette fonction s’exécute et que *mbstate* a la valeur null.

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

## <a name="requirements"></a>Configuration requise

|Routine|En-tête requis|
|-------------|---------------------|
|**wcrtomb_s**|\<wchar.h>|

## <a name="see-also"></a>Voir aussi

[Conversion de données](../../c-runtime-library/data-conversion.md)<br/>
[Paramètres régionaux](../../c-runtime-library/locale.md)<br/>
[Interprétation des séquences de caractères multi-octets](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[mbsinit](mbsinit.md)<br/>
