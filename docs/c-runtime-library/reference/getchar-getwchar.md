---
description: 'En savoir plus sur : GetChar, getwchar'
title: getchar, getwchar
ms.date: 06/23/2020
api_name:
- getchar
- getwchar
- _o_getchar
- _o_getwchar
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
- api-ms-win-crt-stdio-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- getwchar
- GetChar
helpviewer_keywords:
- gettchar function
- characters, reading
- getwchar function
- _gettchar function
- standard input, reading from
ms.assetid: 19fda588-3e33-415c-bb60-dd73c028086a
ms.openlocfilehash: d8480d179cc31d30d68c07fbe92bf389226ccd53
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97256755"
---
# <a name="getchar-getwchar"></a>getchar, getwchar

Lit un caractère à partir d’une entrée standard.

## <a name="syntax"></a>Syntaxe

```C
int getchar();
wint_t getwchar();
```

## <a name="return-value"></a>Valeur de retour

Retourne le caractère lu. Ces fonctions attendent une entrée et ne retournent pas tant que l’entrée n’est pas disponible.

Pour indiquer une erreur de lecture ou une condition de fin de fichier, **GetChar** retourne **EOF** et **getwchar** retourne **WEOF**. Pour **GetChar**, utilisez l’option **feof** ou pour rechercher une **erreur ou la** fin du fichier.

## <a name="remarks"></a>Notes

Chaque routine lit un caractère unique à partir de **stdin** et incrémente le pointeur de fichier associé pour pointer vers le caractère suivant. **GetChar** est identique à [_fgetchar](fgetc-fgetwc.md), mais il est implémenté en tant que fonction et en tant que macro.

Ces fonctions verrouillent également le thread appelant et sont thread-safe. Pour une version sans verrouillage, consultez [_getchar_nolock, _getwchar_nolock](getchar-nolock-getwchar-nolock.md).

Par défaut, l’état global de cette fonction est limité à l’application. Pour modifier cette valeur, consultez [état global dans le CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine TCHAR.H|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_gettchar**|**GetChar**|**GetChar**|**getwchar**|

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**GetChar**|\<stdio.h>|
|**getwchar**|\<stdio.h> ou \<wchar.h>|

La console n’est pas prise en charge dans les applications de plateforme Windows universelle (UWP). Les handles de flux standard associés à la console, **stdin**, **stdout** et **stderr**, doivent être redirigés pour que les fonctions runtime C puissent les utiliser dans les applications UWP. Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

```C
// crt_getchar.c
// Use getchar to read a line from stdin.

#include <stdio.h>

int main()
{
    char buffer[81];
    int i, ch;

    for (i = 0; (i < 80) && ((ch = getchar()) != EOF)
                         && (ch != '\n'); i++)
    {
        buffer[i] = (char) ch;
    }

    // Terminate string with a null character
    buffer[i] = '\0';
    printf( "Input was: %s\n", buffer);
}
```

```Output

This textInput was: This text
```

## <a name="see-also"></a>Voir aussi

[E/S de flux](../../c-runtime-library/stream-i-o.md)<br/>
[getc, getwc](getc-getwc.md)<br/>
[fgetc, fgetwc](fgetc-fgetwc.md)<br/>
[_getch, _getwch](getch-getwch.md)<br/>
[putc, putwc](putc-putwc.md)<br/>
[ungetc, ungetwc](ungetc-ungetwc.md)<br/>
