---
title: fgetc, fgetwc | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- fgetwc
- fgetc
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
- api-ms-win-crt-stdio-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _fgettc
- fgetwc
- fgetc
dev_langs:
- C++
helpviewer_keywords:
- fgettc function
- characters, reading
- _fgettc function
- fgetc function
- streams, reading characters from
- reading characters from streams
- fgetwc function
ms.assetid: 13348b7b-dc86-421c-9d6c-611ca79c8338
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f06c5c2f092932d97755a8f0cff63cde3a9682c6
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32401283"
---
# <a name="fgetc-fgetwc"></a>fgetc, fgetwc

Lisent un caractère d’un flux.

## <a name="syntax"></a>Syntaxe

```C
int fgetc(
   FILE *stream
);
wint_t fgetwc(
   FILE *stream
);
```

### <a name="parameters"></a>Paramètres

*Flux de données*<br/>
Pointeur désignant la structure **FILE**.

## <a name="return-value"></a>Valeur de retour

**fgetc** retourne le caractère lu comme un **int** ou renvoie **EOF** pour indiquer une erreur ou la fin du fichier. **fgetwc** retourne, comme un [wint_t](../../c-runtime-library/standard-types.md), le caractère large qui correspond au caractère lu ou retourne **WEOF** pour indiquer une erreur ou la fin du fichier. Pour les deux fonctions, utilisez **feof** ou **ferror** faire la distinction entre une erreur et une condition de fin de fichier. Si une erreur de lecture se produit, l’indicateur d’erreur pour le flux est défini. Si *flux* est **NULL**, **fgetc** et **fgetwc** appellent le Gestionnaire de paramètre non valide, comme décrit dans [paramètre Validation](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, ces fonctions définissent **errno** à **EINVAL** et retourner **EOF**.

## <a name="remarks"></a>Notes

Chacune de ces fonctions lit un caractère unique à partir de la position actuelle du fichier associé *flux*. Ensuite, la fonction incrémente le pointeur de fichier associé (si défini) pour désigner le caractère suivant. Si le flux est à la fin du fichier, l’indicateur de fin de fichier pour le flux est défini.

**fgetc** équivaut à **getc**, mais est implémenté uniquement en tant que fonction, plutôt que comme une fonction et une macro.

**fgetwc** est la version à caractères larges de **fgetc**; il lit **c** comme un caractère multioctet ou un caractère large selon s’il *flux* est ouvert dans mode de texte ou binaire.

Les versions avec suffixe **_nolock** sont identiques, à ceci près qu’elles ne sont pas protégées contre les interférences avec d’autres threads.

Pour plus d’informations sur le traitement des caractères larges et des caractères multioctets en modes texte et binaire, consultez [E/S de flux Unicode en modes texte et binaire](../../c-runtime-library/unicode-stream-i-o-in-text-and-binary-modes.md).

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine TCHAR.H|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_fgettc**|**fgetc**|**fgetc**|**fgetwc**|

## <a name="requirements"></a>Spécifications

|Fonction|En-tête requis|
|--------------|---------------------|
|**fgetc**|\<stdio.h>|
|**fgetwc**|\<stdio.h> ou \<wchar.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

```C
// crt_fgetc.c
// This program uses getc to read the first
// 80 input characters (or until the end of input)
// and place them into a string named buffer.

#include <stdio.h>
#include <stdlib.h>

int main( void )
{
   FILE *stream;
   char buffer[81];
   int  i, ch;

   // Open file to read line from:
   fopen_s( &stream, "crt_fgetc.txt", "r" );
   if( stream == NULL )
      exit( 0 );

   // Read in first 80 characters and place them in "buffer":
   ch = fgetc( stream );
   for( i=0; (i < 80 ) && ( feof( stream ) == 0 ); i++ )
   {
      buffer[i] = (char)ch;
      ch = fgetc( stream );
   }

   // Add null to end string
   buffer[i] = '\0';
   printf( "%s\n", buffer );
   fclose( stream );
}
```

## <a name="input-crtfgetctxt"></a>Entrée : crt_fgetc.txt

```Input
Line one.
Line two.
```

### <a name="output"></a>Sortie

```Output
Line one.
Line two.
```

## <a name="see-also"></a>Voir aussi

[E/S de flux](../../c-runtime-library/stream-i-o.md)<br/>
[fputc, fputwc](fputc-fputwc.md)<br/>
[getc, getwc](getc-getwc.md)<br/>
