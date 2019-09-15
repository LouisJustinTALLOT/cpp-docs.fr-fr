---
title: getc, getwc
ms.date: 11/04/2016
api_name:
- getwc
- getc
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _gettc
- getwc
- _gettchar
- getc
helpviewer_keywords:
- characters, reading
- _gettc function
- getwchar function
- streams, reading characters from
- reading characters from streams
- getc function
- getwc function
- gettc function
ms.assetid: 354ef514-d0c7-404b-92f5-995f6a834bb3
ms.openlocfilehash: ceb3ca117271e7074c6cb72c9c1f9e74ebe3bc10
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70955490"
---
# <a name="getc-getwc"></a>getc, getwc

Lisent un caractère d’un flux.

## <a name="syntax"></a>Syntaxe

```C
int getc(
   FILE *stream
);
wint_t getwc(
   FILE *stream
);
```

### <a name="parameters"></a>Paramètres

*stream*<br/>
Flux d’entrée.

## <a name="return-value"></a>Valeur de retour

Retourne le caractère lu. Pour indiquer une erreur de lecture ou une condition de fin de fichier, **GETC** retourne **EOF**et **getwc** retourne **WEOF**. Pour **GETC**, utilisez l’option **ferror** ou **feof** pour rechercher une erreur ou la fin du fichier. Si *Stream* a la **valeur null**, **GETC** et **getwc** appellent le gestionnaire de paramètres non valides, comme décrit dans [validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, ces fonctions retournent **EOF** (ou **WEOF** pour **getwc**) et attribuent à **errno** la valeur **EINVAL**.

Pour plus d’informations sur ces codes d’erreur et les autres, consultez [_doserrno, errno, _sys_errlist et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Notes

Chaque routine lit un caractère à partir d’un fichier à la position actuelle et incrémente le pointeur de fichier associé (si défini) pour qu’il désigne le caractère suivant. Le fichier est associé au *flux*.

Ces fonctions verrouillent le thread appelant et sont donc thread-safe. Pour une version sans verrouillage, consultez [_getc_nolock, _getwc_nolock](getc-nolock-getwc-nolock.md).

Voici une série de notes spécifiques aux routines.

|Routine|Notes|
|-------------|-------------|
|**getc**|Identique à **fgetc**, mais implémenté en tant que fonction et en tant que macro.|
|**getwc**|Version à caractères larges de **GETC**. Lit un caractère multioctet ou un caractère élargi selon que le *flux* est ouvert en mode texte ou binaire.|

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine TCHAR.H|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_gettc**|**getc**|**getc**|**getwc**|

## <a name="requirements"></a>Configuration requise

|Routine|En-tête requis|
|-------------|---------------------|
|**getc**|\<stdio.h>|
|**getwc**|\<stdio.h> ou \<wchar.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemples

```C
// crt_getc.c
// Use getc to read a line from a file.

#include <stdio.h>

int main()
{
    char buffer[81];
    int i, ch;
    FILE* fp;

    // Read a single line from the file "crt_getc.txt".

    fopen_s(&fp, "crt_getc.txt", "r");
    if (!fp)
    {
       printf("Failed to open file crt_getc.txt.\n");
       exit(1);
    }

    for (i = 0; (i < 80) && ((ch = getc(fp)) != EOF)
                         && (ch != '\n'); i++)
    {
        buffer[i] = (char) ch;
    }

    // Terminate string with a null character
    buffer[i] = '\0';
    printf( "Input was: %s\n", buffer);

    fclose(fp);
}
```

### <a name="input-crt_getctxt"></a>Entrée : crt_getc.txt

```Input
Line one.
Line two.
```

### <a name="output"></a>Sortie

```Output
Input was: Line one.
```

## <a name="see-also"></a>Voir aussi

[E/S de flux](../../c-runtime-library/stream-i-o.md)<br/>
[fgetc, fgetwc](fgetc-fgetwc.md)<br/>
[_getch, _getwch](getch-getwch.md)<br/>
[putc, putwc](putc-putwc.md)<br/>
[ungetc, ungetwc](ungetc-ungetwc.md)<br/>
