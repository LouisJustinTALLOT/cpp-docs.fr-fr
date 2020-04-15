---
title: mbrtowc
ms.date: 4/2/2020
api_name:
- mbrtowc
- _o_mbrtowc
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
- mbrtowc
helpviewer_keywords:
- mbrtowc function
ms.assetid: a1e87fcc-6de0-4ca1-bf26-508d28490286
ms.openlocfilehash: be46c3f3c728b70c7cbf060572acc24662637a81
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81340931"
---
# <a name="mbrtowc"></a>mbrtowc

Convertir un caractère multioctet dans les paramètres régionaux actuels en un caractère large équivalent, avec la possibilité de redémarrer au milieu d'un caractère multioctet.

## <a name="syntax"></a>Syntaxe

```C
size_t mbrtowc(
   wchar_t *wchar,
   const char *mbchar,
   size_t count,
   mbstate_t *mbstate
);
```

### <a name="parameters"></a>Paramètres

*wchar (wchar)*<br/>
Adresse d’un caractère large pour recevoir la chaîne de caractère large converti (type **wchar_t**). Cette valeur peut être un pointeur null si un caractère large n'est pas requis en retour.

*mbchar (en)*<br/>
Adresse d'une séquence d'octets (un caractère multioctet).

*count*<br/>
Nombre d'octets à vérifier.

*mbstate (en)*<br/>
Pointeur vers un objet d'état de conversion. Si cette valeur est un pointeur null, la fonction utilise un objet d'état de conversion interne statique. Parce que l’objet interne **mbstate_t** n’est pas sans fil, nous vous recommandons de toujours passer votre propre argument *mbstate.*

## <a name="return-value"></a>Valeur de retour

L’une des valeurs suivantes :

0 Le *nombre* suivant ou moins d’octets complètent le caractère multioctet qui représente le caractère large nul, qui est stocké dans *wchar*, si *wchar n’est* pas un pointeur nul.

1 à *compter,* inclusive Le *nombre* suivant ou moins d’octets complètent un caractère multioctet valide. La valeur retournée est le nombre d'octets qui terminent le caractère multioctet. L’équivalent de caractère large est stocké dans *wchar*, si *wchar n’est* pas un pointeur nul.

(size_t) (-1) Une erreur d’encodage s’est produite. Le *nombre* suivant ou moins d’octets ne contribuent pas à un caractère multioctet complet et valide. Dans ce cas, **errno** est réglé à EILSEQ et l’état de changement de conversion dans *mbstate* n’est pas spécifié.

(size_t) (-2) Les *octets de comptage* suivants contribuent à un caractère multioctet incomplet mais potentiellement valide, et tous les *octets de comptage* ont été traités. Aucune valeur n’est stockée dans *wchar*, mais *mbstate* est mis à jour pour redémarrer la fonction.

## <a name="remarks"></a>Notes

Si *mbchar* est un pointeur nul, la fonction est équivalente à l’appel :

`mbrtowc(NULL, "", 1, &mbstate)`

Dans ce cas, la valeur des arguments *wchar* et *le compte* sont ignorés.

Si *mbchar* n’est pas un pointeur nul, la fonction examine les octets de *comptage* de *mbchar* pour déterminer le nombre requis d’octets qui sont nécessaires pour compléter le caractère multioctet suivant. Si le personnage suivant est valide, le caractère multioctet correspondant est stocké dans *wchar* s’il n’est pas un pointeur nul. Si le personnage est le caractère nul large correspondant, l’état résultant de *mbstate* est l’état de conversion initial.

La fonction **mbrtowc** diffère de [mbtowc, _mbtowc_l](mbtowc-mbtowc-l.md) par sa redémarrabilité. L’état de conversion est stocké dans *mbstate* pour les appels ultérieurs vers les mêmes fonctions ou d’autres fonctions redémarrées. Les résultats ne sont pas définis quand l'utilisation de fonctions redémarrables est combinée avec l'utilisation de fonctions non redémarrables.  Par exemple, une application doit utiliser **wcsrlen** au lieu de **wcslen** si un appel ultérieur à **wcsrtombs** est utilisé au lieu de **wcstombs**.

Par défaut, l’état global de cette fonction est étendue à l’application. Pour changer cela, voir [Global State dans le CRT](../global-state.md).

## <a name="example"></a>Exemple

Convertit un caractère multioctet en son équivalent en caractère large.

```cpp
// crt_mbrtowc.cpp

#include <stdio.h>
#include <mbctype.h>
#include <string.h>
#include <locale.h>
#include <wchar.h>

#define BUF_SIZE 100

int Sample(char* szIn, wchar_t* wcOut, int nMax)
{
    mbstate_t   state = {0}; // Initial state
    size_t      nConvResult,
                nmbLen = 0,
                nwcLen = 0;
    wchar_t*    wcCur = wcOut;
    wchar_t*    wcEnd = wcCur + nMax;
    const char* mbCur = szIn;
    const char* mbEnd = mbCur + strlen(mbCur) + 1;
    char*       szLocal;

    // Sets all locale to French_Canada.1252
    szLocal = setlocale(LC_ALL, "French_Canada.1252");
    if (!szLocal)
    {
        printf("The fuction setlocale(LC_ALL, \"French_Canada.1252\") failed!\n");
        return 1;
    }

    printf("Locale set to: \"%s\"\n", szLocal);

    // Sets the code page associated current locale's code page
    // from a previous call to setlocale.
    if (_setmbcp(_MB_CP_SBCS) == -1)
    {
        printf("The fuction _setmbcp(_MB_CP_SBCS) failed!");
        return 1;
    }

    while ((mbCur < mbEnd) && (wcCur < wcEnd))
    {
        //
        nConvResult = mbrtowc(wcCur, mbCur, 1, &state);
        switch (nConvResult)
        {
            case 0:
            {  // done
                printf("Conversion succeeded!\nMultibyte String: ");
                printf(szIn);
                printf("\nWC String: ");
                wprintf(wcOut);
                printf("\n");
                mbCur = mbEnd;
                break;
            }

            case -1:
            {  // encoding error
                printf("The call to mbrtowc has detected an encoding error.\n");
                mbCur = mbEnd;
                break;
            }

            case -2:
            {  // incomplete character
                if   (!mbsinit(&state))
                {
                    printf("Currently in middle of mb conversion, state = %x\n", state);
                    // state will contain data regarding lead byte of mb character
                }

                ++nmbLen;
                ++mbCur;
                break;
            }

            default:
            {
                if   (nConvResult > 2) // The multibyte should never be larger than 2
                {
                    printf("Error: The size of the converted multibyte is %d.\n", nConvResult);
                }

                ++nmbLen;
                ++nwcLen;
                ++wcCur;
                ++mbCur;
            break;
            }
        }
    }

   return 0;
}

int main(int argc, char* argv[])
{
    char    mbBuf[BUF_SIZE] = "AaBbCc\x9A\x8B\xE0\xEF\xF0xXyYzZ";
    wchar_t wcBuf[BUF_SIZE] = {L''};

    return Sample(mbBuf, wcBuf, BUF_SIZE);
}
```

### <a name="sample-output"></a>Exemple de sortie

```Output
Locale set to: "French_Canada.1252"
Conversion succeeded!
Multibyte String: AaBbCcÜïα∩≡xXyYzZ
WC String: AaBbCcÜïα∩≡xXyYzZ
```

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**mbrtowc**|\<wchar.h>|

## <a name="see-also"></a>Voir aussi

[Conversion de données](../../c-runtime-library/data-conversion.md)<br/>
[Local](../../c-runtime-library/locale.md)<br/>
[Interprétation des séquences multioctets-caractères](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
