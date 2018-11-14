---
title: mbrlen
ms.date: 11/04/2016
apiname:
- mbrlen
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
- api-ms-win-crt-string-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- mbrlen
helpviewer_keywords:
- mbrlen function
ms.assetid: dde8dee9-e091-4c4c-81b3-639808885ae1
ms.openlocfilehash: ec9079b9b164e2b609a956ddf3a75cd42923bafc
ms.sourcegitcommit: afd6fac7c519dbc47a4befaece14a919d4e0a8a2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/10/2018
ms.locfileid: "51518331"
---
# <a name="mbrlen"></a>mbrlen

Déterminer le nombre d'octets requis pour terminer un caractère multioctet dans les paramètres régionaux actuels, avec la capacité de redémarrer au milieu d'un caractère multioctet.

## <a name="syntax"></a>Syntaxe

```C
size_t mbrlen(
   const char * str,
   size_t count,
   mbstate_t * mbstate
);
```

### <a name="parameters"></a>Paramètres

*str*<br/>
Pointeur vers l'octet suivant à examiner dans une chaîne de caractères multioctets.

*count*<br/>
Nombre maximal d'octets à examiner.

*mbstate*<br/>
Pointeur vers l’état actuel du décalage de l’octet initial de *str*.

## <a name="return-value"></a>Valeur de retour

Une des valeurs suivantes :

|||
|-|-|
0|La prochaine *nombre* ou moins d’octets terminent le caractère multioctet qui représente le caractère null large.
1 à *nombre*inclus,|La prochaine *nombre* ou moins d’octets terminent un caractère multioctet valide. La valeur retournée est le nombre d'octets qui terminent le caractère multioctet.
(size_t)(-2)|La prochaine *nombre* octets suivants contribuent à un caractère multioctets incomplet mais potentiellement valide et que tous les *nombre* octets ont été traités.
(size_t)(-1)|Une erreur d'encodage s'est produite. La prochaine *nombre* ou moins d’octets ne contribuent pas à un caractère multioctet complet et valid. Dans ce cas, **errno** est défini à EILSEQ et l’état de conversion dans *mbstate* n’est pas spécifié.

## <a name="remarks"></a>Notes

Le **mbrlen** fonction examine au plus *nombre* octets à partir de l’octet vers lequel pointe *str* pour déterminer le nombre d’octets qui sont requis pour terminer la prochaine caractère multioctet, y compris les séquences de décalage. Il est équivalent à l’appel `mbrtowc(NULL, str, count, &mbstate)` où *mbstate* est soit un fourni par l’utilisateur **mbstate_t** objet ou un objet interne statique fournie par la bibliothèque.

Le **mbrlen** fonction enregistre et utilise l’état du décalage d’un caractère multioctet incomplet dans le *mbstate* paramètre. Cela donne **mbrlen** la capacité de redémarrer au milieu d’un caractère multioctet si besoin est, en examinant au plus *nombre* octets. Si *mbstate* est un pointeur null, **mbrlen** utilise un statique interne **mbstate_t** objet à stocker l’état du décalage. Étant donné que le texte interne **mbstate_t** objet n’est pas thread-safe, nous vous recommandons de toujours allouez et passez votre propre *mbstate* paramètre.

Le **mbrlen** diffère de la fonction [_mbclen, mblen, _mblen_l](mbclen-mblen-mblen-l.md) par sa capacité à redémarrer. L’état du décalage est stocké dans *mbstate* pour les appels suivants à la même ou d’autres fonctions redémarrables. Les résultats ne sont pas définis quand l'utilisation de fonctions redémarrables est combinée avec l'utilisation de fonctions non redémarrables.  Par exemple, une application doit utiliser **wcsrlen** au lieu de **wcslen** si un appel ultérieur à **wcsrtombs** est utilisé au lieu de **wcstombs**.

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine TCHAR.H|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|------------------------------------|--------------------|-----------------------|
|non applicable|non applicable|**mbrlen**|non applicable|

## <a name="requirements"></a>Configuration requise

|Routine|En-tête requis|
|-------------|---------------------|
|**mbrlen**|\<wchar.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

Cet exemple montre comment l’interprétation des caractères multioctets dépend de la page de codes actuelle et illustre la capacité de reprise de **mbrlen**.

```C
// crt_mbrlen.c
// Compile by using: cl crt_mbrlen.c
#include <stdlib.h>
#include <stdio.h>
#include <string.h>
#include <locale.h>
#include <wchar.h>

size_t Example(const char * pStr)
{
    size_t      charLen = 0;
    size_t      charCount = 0;
    mbstate_t   mbState = {0};

    while ((charLen = mbrlen(pStr++, 1, &mbState)) != 0 &&
            charLen != (size_t)-1)
    {
        if (charLen != (size_t)-2) // if complete mbcs char,
        {
            charCount++;
        }
    }
    return (charCount);
}

int main( void )
{
    int         cp;
    size_t      charCount = 0;
    const char  *pSample =
        "\x82\xD0\x82\xE7\x82\xAA\x82\xC8: Shift-jis hiragana.";

    cp = _getmbcp();
    charCount = Example(pSample);
    printf("\nCode page: %d\n%s\nCharacter count: %d\n",
        cp, pSample, charCount);

    setlocale(LC_ALL, "ja-JP"); // Set Japanese locale
    _setmbcp(932); // and Japanese multibyte code page
    cp = _getmbcp();
    charCount = Example(pSample);
    printf("\nCode page: %d\n%s\nCharacter count: %d\n",
        cp, pSample, charCount);
}
```

```Output

Code page: 0
é╨éτé¬é╚: Shift-jis hiragana.
Character count: 29

Code page: 932
????: Shift-jis hiragana.
Character count: 25
```

## <a name="see-also"></a>Voir aussi

[Manipulation de chaînes](../../c-runtime-library/string-manipulation-crt.md)<br/>
[Paramètres régionaux](../../c-runtime-library/locale.md)<br/>
