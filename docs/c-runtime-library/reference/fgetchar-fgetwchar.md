---
title: _fgetchar, _fgetwchar
ms.date: 4/2/2020
api_name:
- _fgetchar
- _fgetwchar
- _o__fgetchar
- _o__fgetwchar
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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: b9d805483395d3050a1eb0bc78afef8cd99ca984
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81346930"
---
# <a name="_fgetchar-_fgetwchar"></a>_fgetchar, _fgetwchar

Lit un personnage de **stdin**.

## <a name="syntax"></a>Syntaxe

```C
int _fgetchar( void );
wint_t _fgetwchar( void );
```

## <a name="return-value"></a>Valeur de retour

fgetchar renvoie le personnage lu `EOF` comme un **int** ou des retours pour indiquer une erreur ou une fin de fichier. ** \_** fgetwchar renvoie, comme un [wint_t](../../c-runtime-library/standard-types.md), le caractère large qui `WEOF` correspond au personnage lu ou retourne pour indiquer une erreur ou une fin de fichier. ** \_** Pour les deux fonctions, utilisez **feof** ou **ferror** pour distinguer entre une erreur et une condition de fin de fichier.

## <a name="remarks"></a>Notes

Ces fonctions lisent un seul personnage de **stdin**. Ensuite, la fonction incrémente le pointeur de fichier associé (si défini) pour désigner le caractère suivant. Si le flux est à la fin du fichier, l’indicateur de fin de fichier pour le flux est défini.

**_fgetchar** est équivalent à `fgetc( stdin )`. Il est également équivalent à **getchar**, mais mis en œuvre uniquement comme une fonction, plutôt que comme une fonction et une macro. **_fgetwchar** est la version grand caractère de **_fgetchar**.

Ces fonctions ne sont pas compatibles avec la norme ANSI.

Par défaut, l’état global de cette fonction est étendue à l’application. Pour changer cela, voir [Global State dans le CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine Tchar.h|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_fgettchar**|**_fgetchar**|**_fgetchar**|**_fgetwchar**|

## <a name="requirements"></a>Spécifications

|Fonction|En-tête requis|
|--------------|---------------------|
|**_fgetchar**|\<stdio.h>|
|**_fgetwchar**|\<stdio.h> ou \<wchar.h>|

La console n’est pas prise en charge dans les applications Universal Windows Platform (UWP). Les poignées de flux standard qui sont associées à la console -**stdin**, **stdout**, et **stderr**- doivent être redirigées avant que les fonctions C run-time peuvent les utiliser dans les applications UWP. Pour plus d’informations sur la compatibilité, consultez [Compatibility](../../c-runtime-library/compatibility.md).

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
