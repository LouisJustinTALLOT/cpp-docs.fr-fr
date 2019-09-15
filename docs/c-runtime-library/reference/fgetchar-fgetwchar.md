---
title: _fgetchar, _fgetwchar
ms.date: 11/04/2016
api_name:
- _fgetchar
- _fgetwchar
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
- fgetwchar
- _fgettchar
- _fgetchar
- _fgetwchar
- fgettchar
helpviewer_keywords:
- fgetwchar function
- _fgetchar function
- fgettchar function
- _fgetwchar function
- _fgettchar function
- standard input, reading from
- fgetchar function
ms.assetid: 8bce874c-701a-41a3-b1b2-feff266fb5b9
ms.openlocfilehash: 90a97308b8c60776d52e58feb84c5398456f26d5
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70940861"
---
# <a name="_fgetchar-_fgetwchar"></a>_fgetchar, _fgetwchar

Lit un caractère à partir de **stdin**.

## <a name="syntax"></a>Syntaxe

```C
int _fgetchar( void );
wint_t _fgetwchar( void );
```

## <a name="return-value"></a>Valeur de retour

fgetchar retourne le caractère lu en tant que **int** ou `EOF` retourne pour indiquer une erreur ou la fin du fichier.  **\_** fgetwchar retourne, sous la forme d’un [wint_t](../../c-runtime-library/standard-types.md), le caractère élargi qui correspond au caractère lu `WEOF` ou retourne pour indiquer une erreur ou la fin du fichier.  **\_** Pour les deux fonctions, utilisez feof **ou un** pour faire la distinction entre une erreur et une condition de fin de fichier.

## <a name="remarks"></a>Notes

Ces fonctions lisent un caractère unique à partir de **stdin**. Ensuite, la fonction incrémente le pointeur de fichier associé (si défini) pour désigner le caractère suivant. Si le flux est à la fin du fichier, l’indicateur de fin de fichier pour le flux est défini.

**_fgetchar** est équivalent à `fgetc( stdin )`. Elle est également équivalente à **GetChar**, mais est implémentée uniquement comme une fonction, plutôt que comme une fonction et une macro. **_fgetwchar** est la version à caractères larges de **_fgetchar**.

Ces fonctions ne sont pas compatibles avec la norme ANSI.

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine Tchar.h|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_fgettchar**|**_fgetchar**|**_fgetchar**|**_fgetwchar**|

## <a name="requirements"></a>Configuration requise

|Fonction|En-tête requis|
|--------------|---------------------|
|**_fgetchar**|\<stdio.h>|
|**_fgetwchar**|\<stdio.h> ou \<wchar.h>|

La console n’est pas prise en charge dans les applications de plateforme Windows universelle (UWP). Les handles de flux standard associés à la console (**stdin**, **stdout**et **stderr**) doivent être redirigés pour que les fonctions runtime C puissent les utiliser dans les applications UWP. Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

```C
// crt_fgetchar.c
// This program uses _fgetchar to read the first
// 80 input characters (or until the end of input)
// and place them into a string named buffer.
//

#include <stdio.h>
#include <stdlib.h>

int main( void )
{
   char buffer[81];
   int  i, ch;

   // Read in first 80 characters and place them in "buffer":
   ch = _fgetchar();
   for( i=0; (i < 80 ) && ( feof( stdin ) == 0 ); i++ )
   {
      buffer[i] = (char)ch;
      ch = _fgetchar();
   }

   // Add null to end string
   buffer[i] = '\0';
   printf( "%s\n", buffer );
}
```

```Output

      Line one.
Line two.Line one.
Line two.
```

## <a name="see-also"></a>Voir aussi

[E/S de flux](../../c-runtime-library/stream-i-o.md)<br/>
[fputc, fputwc](fputc-fputwc.md)<br/>
[getc, getwc](getc-getwc.md)<br/>
