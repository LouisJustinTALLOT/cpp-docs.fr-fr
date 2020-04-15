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
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- mbrlen
helpviewer_keywords:
- mbrlen function
ms.assetid: dde8dee9-e091-4c4c-81b3-639808885ae1
ms.openlocfilehash: 7503de22a8310335ddd678335916d3e74dab6e70
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81340988"
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

*mbstate (en)*<br/>
Pointeur à l’état de décalage actuel du byte initial de *str*.

## <a name="return-value"></a>Valeur de retour

L’une des valeurs suivantes :

|||
|-|-|
0|Le *nombre* suivant ou moins d’octets complètent le caractère multioctet qui représente le caractère nul large.
1 à *compter,* inclusivement|Le *nombre* suivant ou moins d’octets complètent un caractère multioctet valide. La valeur retournée est le nombre d'octets qui terminent le caractère multioctet.
(size_t)(-2)|Les *octets de comptage* suivants contribuent à un caractère multioctet incomplet mais potentiellement valide et tous les *octets de comptage* ont été traités.
(size_t)(-1)|Une erreur d'encodage s'est produite. Le *nombre* suivant ou moins d’octets ne contribuent pas à un caractère multioctet complet et valide. Dans ce cas, **errno** est réglé sur EILSEQ et l’état de conversion dans *mbstate* n’est pas spécifié.

## <a name="remarks"></a>Notes

La fonction **mbrlen** inspecte tout au plus les octets *de comptage* à partir du octet pointé par *str* pour déterminer le nombre d’octets qui sont nécessaires pour compléter le prochain caractère multioctet, y compris toutes les séquences de décalage. Il est équivalent `mbrtowc(NULL, str, count, &mbstate)` à l’appel où *mbstate* est soit un objet **mbstate_t** fourni par l’utilisateur, soit un objet interne statique fourni par la bibliothèque.

La fonction **mbrlen** enregistre et utilise l’état de décalage d’un caractère multioctet incomplet dans le paramètre *mbstate.* Cela donne **mbrlen** la capacité de redémarrer au milieu d’un caractère multioctet si nécessaire, l’examen de la plupart des octets *compter.* Si *mbstate* est un pointeur nul, **mbrlen** utilise un objet **interne,** statique mbstate_t pour stocker l’état de décalage. Parce que l’objet **de mbstate_t** interne n’est pas sans fil, nous vous recommandons toujours d’allouer et de passer votre propre paramètre *mbstate.*

La fonction **mbrlen** diffère de [_mbclen, mblen, _mblen_l](mbclen-mblen-mblen-l.md) par sa redémarrabilité. L’état de changement est stocké dans *mbstate* pour les appels ultérieurs vers les mêmes fonctions ou d’autres fonctions redémarrantes. Les résultats ne sont pas définis quand l'utilisation de fonctions redémarrables est combinée avec l'utilisation de fonctions non redémarrables.  Par exemple, une application doit utiliser **wcsrlen** au lieu de **wcslen** si un appel ultérieur à **wcsrtombs** est utilisé au lieu de **wcstombs**.

Par défaut, l’état global de cette fonction est étendue à l’application. Pour changer cela, voir [Global State dans le CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine TCHAR.H|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|------------------------------------|--------------------|-----------------------|
|Non applicable|Non applicable|**mbrlen**|Non applicable|

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**mbrlen**|\<wchar.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

Cet exemple montre comment l’interprétation des caractères multioctets dépend de la page de code actuelle, et démontre la capacité de reprise de **mbrlen**.

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

[Manipulation des cordes](../../c-runtime-library/string-manipulation-crt.md)<br/>
[Local](../../c-runtime-library/locale.md)<br/>
