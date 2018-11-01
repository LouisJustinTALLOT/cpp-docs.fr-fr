---
title: wcrtomb_s
ms.date: 11/04/2016
apiname:
- wcrtomb_s
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
apitype: DLLExport
f1_keywords:
- wcrtomb_s
helpviewer_keywords:
- wide characters, converting
- wcrtomb_s function
- multibyte characters
- characters, converting
ms.assetid: 9a8a1bd0-1d60-463d-a3a2-d83525eaf656
ms.openlocfilehash: 7fe7fba861eecec562928cf381973f62a4db60fb
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50522460"
---
# <a name="wcrtombs"></a>wcrtomb_s

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
La taille de la *mbchar* variable en octets.

*wchar*<br/>
Caractère large à convertir.

*mbstate*<br/>
Un pointeur vers un **mbstate_t** objet.

## <a name="return-value"></a>Valeur de retour

Retourne zéro ou un **errno** valeur si une erreur se produit.

## <a name="remarks"></a>Notes

Le **wcrtomb_s** fonction convertit un caractère large, à compter de l’état de conversion spécifié contenu dans *mbstate*, à partir de la valeur contenue dans *wchar*, dans le adresse représentée par *mbchar*. Le *pReturnValue* valeur sera le nombre d’octets convertis, mais pas plus de **MB_CUR_MAX** octets, ou -1 si une erreur s’est produite.

Si *mbstate* a la valeur null, le texte interne **mbstate_t** état de la conversion est utilisé. Si le caractère contenu dans *wchar* n’a pas un caractère multioctet correspondant, la valeur de *pReturnValue* sera -1 et la fonction retournera le **errno** valeur de **EILSEQ**.

Le **wcrtomb_s** diffère de la fonction [wctomb_s, _wctomb_s_l](wctomb-s-wctomb-s-l.md) par sa capacité à redémarrer. L’état de conversion est stocké dans *mbstate* pour les appels suivants à la même ou d’autres fonctions redémarrables. Les résultats ne sont pas définis quand l'utilisation de fonctions redémarrables est combinée avec l'utilisation de fonctions non redémarrables. Par exemple, une application utiliserait **wcsrlen** plutôt que **wcslen**, si un appel ultérieur à **wcsrtombs_s** était utilisé au lieu de **wcstombs_s**.

En C++, l’utilisation de cette fonction est simplifiée par les surcharges de modèle ; les surcharges peuvent déduire la longueur de la mémoire tampon automatiquement (ce qui évite d’avoir à spécifier un argument de taille) et peuvent remplacer automatiquement les fonctions plus anciennes et non sécurisées par leurs équivalents plus récents et sécurisés. Pour plus d'informations, consultez [Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md).

## <a name="exceptions"></a>Exceptions

Le **wcrtomb_s** fonction est multithread-safe tant qu’aucune fonction dans le thread actuel n’appelle **setlocale** pendant l’exécution de cette fonction et le *mbstate* a la valeur null.

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
