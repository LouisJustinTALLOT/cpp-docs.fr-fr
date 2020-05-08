---
title: wcsrtombs
ms.date: 4/2/2020
api_name:
- wcsrtombs
- _o_wcsrtombs
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
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- wcsrtombs
helpviewer_keywords:
- wcsrtombs function
- string conversion, wide characters
- wide characters, strings
ms.assetid: a8d21fec-0d36-4085-9d81-9b1c61c7259d
ms.openlocfilehash: cad31f28c5542a96eae9f144344882b71806052a
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2020
ms.locfileid: "82910623"
---
# <a name="wcsrtombs"></a>wcsrtombs

Convertit une chaîne de caractères larges dans sa représentation de chaîne de caractères multioctets. Il existe une version plus sécurisée de cette fonction. Consultez [wcsrtombs_s](wcsrtombs-s.md).

## <a name="syntax"></a>Syntaxe

```C
size_t wcsrtombs(
   char *mbstr,
   const wchar_t **wcstr,
   sizeof count,
   mbstate_t *mbstate
);
template <size_t size>
size_t wcsrtombs(
   char (&mbstr)[size],
   const wchar_t **wcstr,
   sizeof count,
   mbstate_t *mbstate
); // C++ only
```

### <a name="parameters"></a>Paramètres

*mbstr*<br/>
Emplacement adresse de la chaîne de caractères multioctets convertie obtenue.

*wcstr*<br/>
Pointe indirectement vers l’emplacement de la chaîne de caractères larges à convertir.

*count*<br/>
Nombre de caractères à convertir.

*mbstate*<br/>
Pointeur vers un objet d’état de conversion **mbstate_t** .

## <a name="return-value"></a>Valeur de retour

Retourne le nombre d’octets correctement convertis, sans l’octet Null de fin (le cas échéant) ou -1 si une erreur s’est produite.

## <a name="remarks"></a>Notes 

La fonction **wcsrtombs** convertit une chaîne de caractères larges, en commençant dans l’état de conversion spécifié contenu dans *mbstate*, à partir des valeurs indirectes pointées vers *wcstr*, dans l’adresse de *mbstr*. La conversion se poursuit pour chaque caractère jusqu’à : après la détection d’un caractère élargi de fin null, lorsqu’un caractère non correspondant est rencontré ou lorsque le caractère suivant dépasse la limite contenue dans *Count*. Si **wcsrtombs** rencontre le caractère null à caractères larges (L' \ 0 ') avant ou quand *Count* se produit, il le convertit en un 0 8 bits et s’arrête.

Par conséquent, la chaîne de caractères multioctets sur *mbstr* est terminée par un caractère NULL uniquement si **wcsrtombs** rencontre un caractère null à caractères larges au cours de la conversion. Si les séquences pointées par *wcstr* et *mbstr* se chevauchent, le comportement de **wcsrtombs** n’est pas défini. **wcsrtombs** est affecté par la catégorie LC_TYPE des paramètres régionaux actuels.

La fonction **wcsrtombs** diffère de [wcstombs, _wcstombs_l](wcstombs-wcstombs-l.md) par son redémarrage. L’état de conversion est stocké dans *mbstate* pour les appels suivants à la même ou à d’autres fonctions redémarrables. Les résultats ne sont pas définis quand l'utilisation de fonctions redémarrables est combinée avec l'utilisation de fonctions non redémarrables.  Par exemple, une application utilise **wcsrlen** plutôt que **wcsnlen**, si un appel ultérieur à **wcsrtombs** était utilisé à la place de **wcstombs**.

Si l’argument *mbstr* a la **valeur null**, **wcsrtombs** retourne la taille requise en octets de la chaîne de destination. Si *mbstate* a la valeur null, l’état de conversion **mbstate_t** interne est utilisé. Si la séquence de caractères *WCHAR* n’a pas de représentation de caractères multioctets correspondante, la valeur-1 est retournée et le **errno** est défini sur **EILSEQ**.

En C++, cette fonction a une surcharge de modèle qui appelle l'équivalent plus récent et sécurisé de cette fonction. Pour plus d’informations, consultez [Sécuriser les surcharges de modèle](../../c-runtime-library/secure-template-overloads.md).

Par défaut, l’état global de cette fonction est limité à l’application. Pour modifier cette valeur, consultez [état global dans le CRT](../global-state.md).

## <a name="exceptions"></a>Exceptions

La fonction **wcsrtombs** est multithread Safe tant qu’aucune fonction dans le thread actuel n’appelle **setlocale** pendant que cette fonction s’exécute et que *mbstate* n’a pas la valeur null.

## <a name="example"></a> Exemple

```cpp
// crt_wcsrtombs.cpp
// compile with: /W3
// This code example converts a wide
// character string into a multibyte
// character string.

#include <stdio.h>
#include <memory.h>
#include <wchar.h>
#include <errno.h>

#define MB_BUFFER_SIZE 100

int main()
{
    const wchar_t   wcString[] =
                    {L"Every good boy does fine."};
    const wchar_t   *wcsIndirectString = wcString;
    char            mbString[MB_BUFFER_SIZE];
    size_t          countConverted;
    mbstate_t       mbstate;

    // Reset to initial shift state
    ::memset((void*)&mbstate, 0, sizeof(mbstate));

    countConverted = wcsrtombs(mbString, &wcsIndirectString,
                               MB_BUFFER_SIZE, &mbstate); // C4996
    // Note: wcsrtombs is deprecated; consider using wcsrtombs_s
    if (errno == EILSEQ)
    {
        printf( "An encoding error was detected in the string.\n" );
    }
    else
    {
        printf( "The string was successfuly converted.\n" );
    }
}
```

```Output
The string was successfuly converted.
```

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**wcsrtombs**|\<wchar.h>|

## <a name="see-also"></a>Voir aussi

[Conversion de données](../../c-runtime-library/data-conversion.md)<br/>
[Paramètres régionaux](../../c-runtime-library/locale.md)<br/>
[Interprétation des séquences de caractères multioctets](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[wcrtomb](wcrtomb.md)<br/>
[wcrtomb_s](wcrtomb-s.md)<br/>
[wctomb, _wctomb_l](wctomb-wctomb-l.md)<br/>
[wcstombs, _wcstombs_l](wcstombs-wcstombs-l.md)<br/>
[mbsinit](mbsinit.md)<br/>
