---
title: wcsrtombs_s
ms.date: 11/04/2016
apiname:
- wcsrtombs_s
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
- wcsrtombs_s
helpviewer_keywords:
- string conversion, wide characters
- wcsrtombs_s function
- wide characters, strings
ms.assetid: 9dccb766-113c-44bb-9b04-07a634dddec8
ms.openlocfilehash: 9ece21737b1e0b4d157b241286638ac376843fc6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50459057"
---
# <a name="wcsrtombss"></a>wcsrtombs_s

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
Nombre de caractères convertis.

*mbstr*<br/>
Adresse d'une mémoire tampon pour la chaîne de caractères multioctets convertie résultante.

*sizeInBytes*<br/>
La taille en octets de la *mbstr* mémoire tampon.

*wcstr*<br/>
Pointe vers la chaîne de caractères larges à convertir.

*count*<br/>
Le nombre maximal d’octets à stocker dans le *mbstr* mémoire tampon, ou [_TRUNCATE](../../c-runtime-library/truncate.md).

*mbstate*<br/>
Un pointeur vers un **mbstate_t** objet d’état de conversion.

## <a name="return-value"></a>Valeur de retour

Zéro si l'opération a réussi, un code d'erreur en cas d'échec.

|Condition d'erreur|Valeur de retour et **errno**|
|---------------------|------------------------------|
|*mbstr* est **NULL** et *sizeInBytes* > 0|**EINVAL**|
|*wcstr* est **NULL**|**EINVAL**|
|La mémoire tampon de destination est trop petite pour contenir la chaîne convertie (à moins que *nombre* est **_TRUNCATE**; consultez la section Notes ci-dessous)|**ERANGE**|

Si l’une de ces conditions se présente, l’exception de paramètre non valide est appelée, comme décrit dans [Validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, la fonction retourne un code d’erreur et définit **errno** comme indiqué dans le tableau.

## <a name="remarks"></a>Notes

Le **wcsrtombs_s** fonction convertit une chaîne de caractères larges vers laquelle pointé *wcstr* en caractères multioctets stockés dans la mémoire tampon vers laquelle pointée *mbstr*, en utilisant le état de conversion contenu dans *mbstate*. La conversion se poursuit pour chaque caractère jusqu'à ce qu'une des conditions suivantes soit remplie :

- Un caractère large null est rencontré

- Un caractère large qui ne peut pas être converti est rencontré

- Le nombre d’octets stockés dans le *mbstr* mettre en mémoire tampon est égale à *nombre*.

La chaîne de destination est toujours terminée par null (même en cas d'erreur).

Si *nombre* est la valeur spéciale [_TRUNCATE](../../c-runtime-library/truncate.md), puis **wcsrtombs_s** convertit autant de caractères de la chaîne en tenir dans la mémoire tampon de destination, tout en laissant la place pour une valeur null marque de fin.

Si **wcsrtombs_s** convertit correctement la chaîne source, elle place la taille en octets de la chaîne convertie, y compris le terminateur null, en  *&#42;pReturnValue* (fourni  *pReturnValue* n’est pas **NULL**). Cela se produit même si le *mbstr* argument est **NULL** et fournit un moyen pour déterminer la taille de mémoire tampon requise. Notez que si *mbstr* est **NULL**, *nombre* est ignoré.

Si **wcsrtombs_s** rencontre un caractère large qu’elle ne peut pas convertir en un caractère multioctet, il place -1  *\*pReturnValue*, définit la mémoire tampon de destination sur une chaîne vide, définit **errno** à **EILSEQ**et retourne **EILSEQ**.

Si les séquences pointées par *wcstr* et *mbstr* se chevauchent, le comportement de **wcsrtombs_s** n’est pas défini. **wcsrtombs_s** est affectée par la catégorie LC_TYPE des paramètres régionaux actuels.

> [!IMPORTANT]
> Vérifiez que *wcstr* et *mbstr* ne se chevauchent pas et qui *nombre* reflète fidèlement le nombre de caractères larges à convertir.

Le **wcsrtombs_s** diffère de la fonction [wcstombs_s, _wcstombs_s_l](wcstombs-s-wcstombs-s-l.md) par sa capacité à redémarrer. L’état de conversion est stocké dans *mbstate* pour les appels suivants à la même ou d’autres fonctions redémarrables. Les résultats ne sont pas définis quand l'utilisation de fonctions redémarrables est combinée avec l'utilisation de fonctions non redémarrables. Par exemple, une application utiliserait **wcsrlen** plutôt que **wcslen**, si un appel ultérieur à **wcsrtombs_s** était utilisé au lieu de **wcstombs_s**.

En C++, l’utilisation de ces fonctions est simplifiée par les surcharges de modèle ; les surcharges peuvent déduire la longueur de la mémoire tampon automatiquement (ce qui évite d’avoir à spécifier un argument taille) et peuvent remplacer automatiquement les fonctions plus anciennes et non sécurisées par leurs équivalentes plus récentes et sécurisées. Pour plus d'informations, consultez [Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md).

## <a name="exceptions"></a>Exceptions

Le **wcsrtombs_s** fonction est multithread-safe tant qu’aucune fonction dans le thread actuel n’appelle **setlocale** pendant l’exécution de cette fonction et le *mbstate* a la valeur null.

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

void main()
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

## <a name="requirements"></a>Configuration requise

|Routine|En-tête requis|
|-------------|---------------------|
|**wcsrtombs_s**|\<wchar.h>|

## <a name="see-also"></a>Voir aussi

[Conversion de données](../../c-runtime-library/data-conversion.md)<br/>
[Paramètres régionaux](../../c-runtime-library/locale.md)<br/>
[Interprétation des séquences de caractères multi-octets](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[wcrtomb](wcrtomb.md)<br/>
[wcrtomb_s](wcrtomb-s.md)<br/>
[wctomb, _wctomb_l](wctomb-wctomb-l.md)<br/>
[wcstombs, _wcstombs_l](wcstombs-wcstombs-l.md)<br/>
[mbsinit](mbsinit.md)<br/>
