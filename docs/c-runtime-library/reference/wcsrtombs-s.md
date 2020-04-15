---
title: wcsrtombs_s
ms.date: 4/2/2020
api_name:
- wcsrtombs_s
- _o_wcsrtombs_s
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
- wcsrtombs_s
helpviewer_keywords:
- string conversion, wide characters
- wcsrtombs_s function
- wide characters, strings
ms.assetid: 9dccb766-113c-44bb-9b04-07a634dddec8
ms.openlocfilehash: 71a2206df9d3afb64fcaf62848988cf116d9071f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328109"
---
# <a name="wcsrtombs_s"></a>wcsrtombs_s

Convertit une chaîne de caractères larges dans sa représentation de chaîne de caractères multioctets. Version de [wcsrtombs](wcsrtombs.md) assortie des améliorations de sécurité décrites dans [Fonctionnalités de sécurité dans le CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Syntaxe

```C
errno_t wcsrtombs_s(
   size_t *pReturnValue,
   char *mbstr,
   size_t sizeInBytes,
   const wchar_t **wcstr,
   sizeof count,
   mbstate_t *mbstate
);
template <size_t size>
errno_t wcsrtombs_s(
   size_t *pReturnValue,
   char (&mbstr)[size],
   const wchar_t **wcstr,
   sizeof count,
   mbstate_t *mbstate
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
Le nombre maximum d’octets à stocker dans le tampon *mbstr,* ou [_TRUNCATE](../../c-runtime-library/truncate.md).

*mbstate (en)*<br/>
Un pointeur vers un objet d’état de conversion **mbstate_t.**

## <a name="return-value"></a>Valeur de retour

Zéro si l'opération a réussi, un code d'erreur en cas d'échec.

|État d’erreur|Valeur de rendement et **errno**|
|---------------------|------------------------------|
|*mbstr* est **NULL** et *tailleInBytes* > 0|**EINVAL (EN)**|
|*wcstr* est **NULL**|**EINVAL (EN)**|
|Le tampon de destination est trop petit pour contenir la chaîne convertie (à moins que *le compte* ne **soit _TRUNCATE**; voir Remarques ci-dessous)|**ERANGE**|

Si l’une de ces conditions se présente, l’exception de paramètre non valide est appelée, comme décrit dans [Validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, la fonction renvoie un code d’erreur et définit **errno** comme indiqué dans le tableau.

## <a name="remarks"></a>Notes

La fonction **wcsrtombs_s** convertit une chaîne de caractères larges pointés par *wcstr* en caractères multioctets stockés dans le tampon pointé par *mbstr*, en utilisant l’état de conversion contenu dans *mbstate*. La conversion se poursuit pour chaque caractère jusqu'à ce qu'une des conditions suivantes soit remplie :

- Un caractère large null est rencontré

- Un caractère large qui ne peut pas être converti est rencontré

- Le nombre d’octets stockés dans le tampon *mbstr* *équivaut à compter*.

La chaîne de destination est toujours terminée par null (même en cas d'erreur).

Si *le compte* est la valeur spéciale [_TRUNCATE](../../c-runtime-library/truncate.md), puis **wcsrtombs_s** convertit autant de la chaîne que s’insérera dans le tampon de destination, tout en laissant de la place pour un terminateur nul.

Si **wcsrtombs_s** convertit avec succès la chaîne source, il met la taille dans les octets de la chaîne convertie, y compris le terminateur nul, en *&#42;pReturnValue* (fourni *pReturnValue* n’est pas **NULL**). Cela se produit même si l’argument *mbstr* est **NULL** et fournit un moyen de déterminer la taille du tampon requis. Notez que si *mbstr* est **NULL**, *le compte* est ignoré.

Si **wcsrtombs_s** rencontre un personnage large qu’il ne peut pas convertir en un personnage multioctet, il met -1 en * \*pReturnValue*, définit le tampon de destination à une chaîne vide, définit **errno** à **EILSEQ**, et retourne **EILSEQ**.

Si les séquences pointées par *le wcstr* et le *mbstr* se chevauchent, le comportement de **wcsrtombs_s** est indéfini. **wcsrtombs_s** est affectée par la LC_TYPE catégorie de l’endroit actuel.

> [!IMPORTANT]
> Assurez-vous que *le wcstr* et *le mbstr* ne se chevauchent pas, et ce *nombre* reflète correctement le nombre de caractères larges à convertir.

La fonction **wcsrtombs_s** diffère de [wcstombs_s, _wcstombs_s_l](wcstombs-s-wcstombs-s-l.md) par sa redémarrabilité. L’état de conversion est stocké dans *mbstate* pour les appels ultérieurs vers les mêmes fonctions ou d’autres fonctions redémarrées. Les résultats ne sont pas définis quand l'utilisation de fonctions redémarrables est combinée avec l'utilisation de fonctions non redémarrables. Par exemple, une application utiliserait **wcsrlen** plutôt que **wcslen**, si un appel ultérieur à **wcsrtombs_s** ont été utilisés au lieu de **wcstombs_s**.

En C++, l’utilisation de ces fonctions est simplifiée par les surcharges de modèle ; les surcharges peuvent déduire la longueur de la mémoire tampon automatiquement (ce qui évite d’avoir à spécifier un argument taille) et peuvent remplacer automatiquement les fonctions plus anciennes et non sécurisées par leurs équivalentes plus récentes et sécurisées. Pour plus d’informations, consultez [Sécuriser les surcharges de modèle](../../c-runtime-library/secure-template-overloads.md).

Par défaut, l’état global de cette fonction est étendue à l’application. Pour changer cela, voir [Global State dans le CRT](../global-state.md).

## <a name="exceptions"></a>Exceptions

La fonction **wcsrtombs_s** est multimarque aussi longtemps qu’aucune fonction dans le thread actuel appelle **setlocale** pendant que cette fonction est l’exécution et le *mbstate* est nul.

## <a name="example"></a>Exemple

```cpp
// crt_wcsrtombs_s.cpp
//
// This code example converts a wide
// character string into a multibyte
// character string.
//

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
    errno_t         err;
    mbstate_t       mbstate;

    // Reset to initial shift state
    ::memset((void*)&mbstate, 0, sizeof(mbstate));

    err = wcsrtombs_s(&countConverted, mbString, MB_BUFFER_SIZE,
                      &wcsIndirectString, MB_BUFFER_SIZE, &mbstate);
    if (err == EILSEQ)
    {
        printf( "An encoding error was detected in the string.\n" );
    }
    else
    {
        printf( "The string was successfully converted.\n" );
    }
}
```

```Output
The string was successfully converted.
```

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**wcsrtombs_s**|\<wchar.h>|

## <a name="see-also"></a>Voir aussi

[Conversion de données](../../c-runtime-library/data-conversion.md)<br/>
[Local](../../c-runtime-library/locale.md)<br/>
[Interprétation des séquences multioctets-caractères](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[wcrtomb](wcrtomb.md)<br/>
[wcrtomb_s](wcrtomb-s.md)<br/>
[wctomb, _wctomb_l](wctomb-wctomb-l.md)<br/>
[wcstombs, _wcstombs_l](wcstombs-wcstombs-l.md)<br/>
[mbsinit](mbsinit.md)<br/>
