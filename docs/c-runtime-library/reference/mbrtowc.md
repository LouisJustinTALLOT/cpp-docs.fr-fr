---
description: 'En savoir plus sur : mbrtowc'
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
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- mbrtowc
helpviewer_keywords:
- mbrtowc function
ms.assetid: a1e87fcc-6de0-4ca1-bf26-508d28490286
ms.openlocfilehash: f00c9fd01826a80cb729bfe10af242db8dec2414
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97271159"
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

*wchar*<br/>
Adresse d’un caractère élargi devant recevoir la chaîne de caractères larges convertie (type **`wchar_t`** ). Cette valeur peut être un pointeur null si un caractère large n'est pas requis en retour.

*mbchar*<br/>
Adresse d'une séquence d'octets (un caractère multioctet).

*count*<br/>
Nombre d'octets à vérifier.

*mbstate*<br/>
Pointeur vers un objet d'état de conversion. Si cette valeur est un pointeur null, la fonction utilise un objet d'état de conversion interne statique. Étant donné que l’objet **mbstate_t** interne n’est pas thread-safe, nous vous recommandons de toujours passer votre propre argument *mbstate* .

## <a name="return-value"></a>Valeur renvoyée

Une des valeurs suivantes :

0 le *nombre* suivant ou moins d’octets termine le caractère multioctet qui représente le caractère élargi null, qui est stocké dans *WCHAR*, si *WCHAR* n’est pas un pointeur null.

1 à *compter*, inclus le *nombre* suivant ou un nombre d’octets inférieur termine un caractère multioctet valide. La valeur retournée est le nombre d'octets qui terminent le caractère multioctet. L’équivalent en caractères larges est stocké dans *WCHAR*, si *WCHAR* n’est pas un pointeur null.

(size_t) (-1) Une erreur d’encodage s’est produite. Le *nombre* suivant ou un nombre d’octets inférieur ne contribue pas à un caractère multioctet complet et valide. Dans ce cas, **errno** a la valeur EILSEQ et l’état de décalage de la conversion dans *mbstate* n’est pas spécifié.

(size_t) (-2) Les octets *suivants contribuent* à un caractère multioctet incomplet mais potentiellement valide, et tous les octets de *nombre* ont été traités. Aucune valeur n’est stockée dans *WCHAR*, mais *mbstate* est mis à jour pour redémarrer la fonction.

## <a name="remarks"></a>Notes

Si *mbchar* est un pointeur null, la fonction est équivalente à l’appel :

`mbrtowc(NULL, "", 1, &mbstate)`

Dans ce cas, la valeur des arguments *WCHAR* et *Count* est ignorée.

Si *mbchar* n’est pas un pointeur null, la fonction examine *le nombre d’octets à* partir de *mbchar* pour déterminer le nombre d’octets requis pour terminer le caractère multioctet suivant. Si le caractère suivant est valide, le caractère multioctet correspondant est stocké dans *WCHAR* s’il ne s’agit pas d’un pointeur null. Si le caractère est le caractère null étendu correspondant, l’état résultant de *mbstate* est l’état de conversion initial.

La fonction **mbrtowc** diffère de [mbtowc, _mbtowc_l](mbtowc-mbtowc-l.md) par son redémarrage. L’état de conversion est stocké dans *mbstate* pour les appels suivants à la même ou à d’autres fonctions redémarrables. Les résultats ne sont pas définis quand l'utilisation de fonctions redémarrables est combinée avec l'utilisation de fonctions non redémarrables.  Par exemple, une application doit utiliser **wcsrlen** au lieu de **wcslen** si un appel ultérieur à **wcsrtombs** est utilisé à la place de **wcstombs**.

Par défaut, l’état global de cette fonction est limité à l’application. Pour modifier cette valeur, consultez [état global dans le CRT](../global-state.md).

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
[Paramètres régionaux](../../c-runtime-library/locale.md)<br/>
[Interprétation des séquences de Multibyte-Character](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
