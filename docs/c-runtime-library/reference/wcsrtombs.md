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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: af22a7d55c5f4958db6962e98f212fb5bb89e61e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328058"
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

*mbstate (en)*<br/>
Un pointeur vers un objet d’état de conversion **mbstate_t.**

## <a name="return-value"></a>Valeur de retour

Retourne le nombre d’octets correctement convertis, sans l’octet Null de fin (le cas échéant) ou -1 si une erreur s’est produite.

## <a name="remarks"></a>Notes

La fonction **wcsrtombs** convertit une chaîne de caractères larges, à partir de l’état de conversion spécifié contenu dans *mbstate*, des valeurs indirectes pointées dans *wcstr*, dans l’adresse de *mbstr*. La conversion se poursuivra pour chaque personnage jusqu’à ce qu’après une fin nulle grand caractère est rencontré, quand un personnage non correspondant est rencontré ou quand le personnage suivant dépasserait la limite contenue dans le *compte*. Si **les wcsrtombs** rencontrent le caractère nul à caractère large (L'0') avant ou quand *le compte* se produit, il le convertit en 8 bits 0 et s’arrête.

Ainsi, la chaîne de caractère multioctet à *mbstr* n’est annulée que si **wcsrtombs** rencontre un caractère nul de caractère large pendant la conversion. Si les séquences pointées par *le wcstr* et le *mbstr* se chevauchent, le comportement des **wcsrtombs** n’est pas défini. **wcsrtombs** est affecté par la catégorie LC_TYPE de la localisation actuelle.

La fonction **wcsrtombs** diffère des [wcstombs, _wcstombs_l](wcstombs-wcstombs-l.md) par sa redémarrabilité. L’état de conversion est stocké dans *mbstate* pour les appels ultérieurs vers les mêmes fonctions ou d’autres fonctions redémarrées. Les résultats ne sont pas définis quand l'utilisation de fonctions redémarrables est combinée avec l'utilisation de fonctions non redémarrables.  Par exemple, une application utiliserait **wcsrlen** plutôt que **wcsnlen**, si un appel ultérieur à **wcsrtombs** ont été utilisés au lieu de **wcstombs**.

Si l’argument *mbstr* est **NULL**, **wcsrtombs** retourne la taille requise dans les octets de la chaîne de destination. Si *le mbstate* est nul, l’état de conversion interne **mbstate_t** est utilisé. Si la séquence de caractère *wchar* n’a pas une représentation de caractère multioctet correspondante, un -1 est retourné et **l’errno** est réglé à **EILSEQ**.

En C++, cette fonction a une surcharge de modèle qui appelle l'équivalent plus récent et sécurisé de cette fonction. Pour plus d’informations, consultez [Sécuriser les surcharges de modèle](../../c-runtime-library/secure-template-overloads.md).

Par défaut, l’état global de cette fonction est étendue à l’application. Pour changer cela, voir [Global State dans le CRT](../global-state.md).

## <a name="exceptions"></a>Exceptions

La fonction **wcsrtombs** est multithread sûr tant que aucune fonction dans le thread actuel appelle **setlocale** pendant que cette fonction est l’exécution et le *mbstate n’est* pas nul.

## <a name="example"></a>Exemple

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
[Local](../../c-runtime-library/locale.md)<br/>
[Interprétation des séquences multioctets-caractères](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[wcrtomb](wcrtomb.md)<br/>
[wcrtomb_s](wcrtomb-s.md)<br/>
[wctomb, _wctomb_l](wctomb-wctomb-l.md)<br/>
[wcstombs, _wcstombs_l](wcstombs-wcstombs-l.md)<br/>
[mbsinit](mbsinit.md)<br/>
