---
title: mbrlen
ms.date: 4/2/2020
api_name:
- mbrlen
- _o_mbrlen
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
- api-ms-win-crt-string-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- mbrlen
helpviewer_keywords:
- mbrlen function
ms.assetid: dde8dee9-e091-4c4c-81b3-639808885ae1
ms.openlocfilehash: 2e0e0ec9d92744fc904bae5ac7f91db8049de4cd
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88842115"
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

*Str*<br/>
Pointeur vers l'octet suivant à examiner dans une chaîne de caractères multioctets.

*count*<br/>
Nombre maximal d'octets à examiner.

*mbstate*<br/>
Pointeur vers l’état de décalage actuel de l’octet initial de *Str*.

## <a name="return-value"></a>Valeur renvoyée

Une des valeurs suivantes :

| Value | Description |
|--|--|
| 0 | Le *nombre* suivant ou un nombre d’octets inférieur termine le caractère multioctet qui représente le caractère null étendu. |
| 1 pour *compter*, inclusive | Le *nombre* suivant ou un nombre d’octets inférieur termine un caractère multioctet valide. La valeur retournée est le nombre d'octets qui terminent le caractère multioctet. |
| (size_t)(-2) | Les octets *suivants contribuent* à un caractère multioctet incomplet mais potentiellement valide, et tous les octets de *nombre* ont été traités. |
| (size_t)(-1) | Une erreur d'encodage s'est produite. Le *nombre* suivant ou un nombre d’octets inférieur ne contribue pas à un caractère multioctet complet et valide. Dans ce cas, **errno** a la valeur EILSEQ et l’état de conversion dans *mbstate* n’est pas spécifié. |

## <a name="remarks"></a>Notes

La fonction **mbrlen** inspecte *le nombre d’octets à* partir de l’octet pointé par *Str* pour déterminer le nombre d’octets nécessaires pour terminer le caractère multioctet suivant, y compris les séquences de décalage. Il est équivalent à l’appel `mbrtowc(NULL, str, count, &mbstate)` où *mbstate* est un objet **mbstate_t** fourni par l’utilisateur ou un objet interne statique fourni par la bibliothèque.

La fonction **mbrlen** enregistre et utilise l’état de décalage d’un caractère multioctet incomplet dans le paramètre *mbstate* . Cela donne à **mbrlen** la possibilité de redémarrer au milieu d’un caractère multioctet, le cas échéant, en examinant au maximum le *nombre* d’octets. Si *mbstate* est un pointeur null, **mbrlen** utilise un objet **mbstate_t** statique interne pour stocker l’État Shift. Étant donné que l’objet **mbstate_t** interne n’est pas thread-safe, nous vous recommandons de toujours allouer et de passer votre propre paramètre *mbstate* .

La fonction **mbrlen** diffère de [_mbclen, mblen, _mblen_l](mbclen-mblen-mblen-l.md) par son redémarrage. L’état de décalage est stocké dans *mbstate* pour les appels suivants à la même ou à d’autres fonctions redémarrables. Les résultats ne sont pas définis quand l'utilisation de fonctions redémarrables est combinée avec l'utilisation de fonctions non redémarrables.  Par exemple, une application doit utiliser **wcsrlen** au lieu de **wcslen** si un appel ultérieur à **wcsrtombs** est utilisé à la place de **wcstombs**.

Par défaut, l’état global de cette fonction est limité à l’application. Pour modifier cette valeur, consultez [état global dans le CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine TCHAR.H|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|------------------------------------|--------------------|-----------------------|
|Non applicable|Non applicable|**mbrlen**|Non applicable|

## <a name="requirements"></a>Configuration requise

|Routine|En-tête requis|
|-------------|---------------------|
|**mbrlen**|\<wchar.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

Cet exemple montre comment l’interprétation des caractères multioctets dépend de la page de codes actuelle et montre la capacité de reprise de **mbrlen**.

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
