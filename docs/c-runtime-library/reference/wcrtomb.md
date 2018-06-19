---
title: wcrtomb | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- wcrtomb
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
- wcrtomb
dev_langs:
- C++
helpviewer_keywords:
- wide characters, converting
- wcrtomb function
- multibyte characters
- characters, converting
ms.assetid: 717f1b21-2705-4b7f-b6d0-82adc5224340
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: eca27e81cbb1df26d04059974cdc1ce5313bafa3
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32412675"
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

*mbchar*<br/>
Résultat de la conversion du caractère multioctet.

*wchar*<br/>
Caractère large à convertir.

*mbstate*<br/>
Un pointeur vers un **mbstate_t** objet.

## <a name="return-value"></a>Valeur de retour

Retourne le nombre d’octets nécessaire pour représenter le caractère multioctet converti ou -1 si une erreur se produit.

## <a name="remarks"></a>Notes

Le **wcrtomb** fonction convertit un caractère large, à compter de l’état de la conversion spécifiée contenue dans *mbstate*, à partir de la valeur contenue dans *wchar*, dans le adresse représentée par *mbchar*. La valeur de retour est le nombre d’octets requis pour représenter le caractère multioctet correspondant, mais il ne renvoie pas plus de **MB_CUR_MAX** octets.

Si *mbstate* est null, le texte interne **mbstate_t** objet contenant l’état de conversion de *mbchar* est utilisé. Si la séquence de caractères *wchar* n’a pas multioctets correspondant représentation sous forme de caractère, une valeur -1 est retournée et le **errno** a la valeur **EILSEQ**.

Le **wcrtomb** diffère de la fonction [wctomb, _wctomb_l](wctomb-wctomb-l.md) par sa capacité à redémarrer. L’état de conversion est stocké dans *mbstate* pour les appels suivants à la même ou d’autres fonctions redémarrables. Les résultats ne sont pas définis quand l'utilisation de fonctions redémarrables est combinée avec l'utilisation de fonctions non redémarrables. Par exemple, utilisez une application **wcsrlen** plutôt que **wcsnlen**, si un appel ultérieur à **wcsrtombs** ont été utilisés au lieu de **wcstombs**.

En C++, cette fonction a une surcharge de modèle qui appelle les équivalents plus récents et sécurisés de cette fonction. Pour plus d'informations, consultez [Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md).

## <a name="exceptions"></a>Exceptions

Le **wcrtomb** fonction est multithread-safe tant qu’aucune fonction dans le thread actuel n’appelle **setlocale** pendant l’exécution de cette fonction et lors de la *mbstate* a la valeur null.

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
[Paramètres régionaux](../../c-runtime-library/locale.md)<br/>
[Interprétation des séquences de caractères multi-octets](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[mbsinit](mbsinit.md)<br/>
