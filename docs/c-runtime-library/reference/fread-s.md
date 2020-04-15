---
title: fread_s
ms.date: 4/2/2020
api_name:
- fread_s
- _o_fread_s
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
- fread_s
- stdio/fread_s
ms.assetid: ce735de0-f005-435d-a8f2-6f4b80ac775e
ms.openlocfilehash: 97f7ca80d4b458b952393a5b1f72bebe0bdb0d9f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81346128"
---
# <a name="fread_s"></a>fread_s

Lit les données d’un flux. Cette version de [fread](fread.md) est assortie des améliorations de sécurité décrites dans [Fonctionnalités de sécurité dans le CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Syntaxe

```C
size_t fread_s(
   void *buffer,
   size_t bufferSize,
   size_t elementSize,
   size_t count,
   FILE *stream
);
```

### <a name="parameters"></a>Paramètres

*buffer*<br/>
Emplacement de stockage des données.

*tamponSize*<br/>
Taille de la mémoire tampon de destination en octets.

*élémentsSize*<br/>
Taille de l’élément à lire en octets.

*count*<br/>
Nombre maximal d’éléments à lire.

*Flux*<br/>
Pointeur désignant la structure **FILE**.

## <a name="return-value"></a>Valeur de retour

**fread_s** renvoie le nombre d’éléments (entiers) qui ont été lus dans le tampon, ce qui peut être inférieur au *compte* si une erreur de lecture ou la fin du fichier est rencontrée avant que le *compte* soit atteint. Utilisez la fonction **feof** ou **ferror** pour distinguer une erreur d’une condition de fin de fichier. Si *la taille* ou le *nombre* est de 0, **fread_s** retourne 0 et le contenu tampon est inchangé. Si *le flux* ou le *tampon* est un pointeur nul, **fread_s** invoque le gestionnaire de paramètres invalide, tel que décrit dans la validation [des paramètres](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, cette fonction définit **errno** à **EINVAL** et renvoie 0.

Pour plus d’informations sur les codes d’erreur, consultez [_doserrno, errno, _sys_errlist et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Notes

La fonction **fread_s** se lit jusqu’à *compter* les éléments des *octets* de taille du *flux* d’entrée et les stocke dans *le tampon*.  Le pointeur de fichier qui est associé au *flux* (s’il y en a un) est augmenté par le nombre d’octets réellement lus. Si le flux donné est ouvert en mode texte, les paires d’alimentation de la ligne de retour de transport sont remplacées par des caractères d’alimentation en ligne unique. Le remplacement n’a aucun effet sur le pointeur de fichier ou la valeur de retour. La position du pointeur de fichier est indéterminée si une erreur se produit. La valeur d’un élément partiellement lu ne peut pas être déterminée.

Cette fonction verrouille les autres threads. Si vous avez besoin d’une version non verrouillée, utilisez **_fread_nolock**.

Par défaut, l’état global de cette fonction est étendue à l’application. Pour changer cela, voir [Global State dans le CRT](../global-state.md).

## <a name="requirements"></a>Spécifications

|Fonction|En-tête requis|
|--------------|---------------------|
|**fread_s**|\<stdio.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

```cpp
// crt_fread_s.c
// Command line: cl /EHsc /nologo /W4 crt_fread_s.c
//
// This program opens a file that's named FREAD.OUT and
// writes characters to the file. It then tries to open
// FREAD.OUT and read in characters by using fread_s. If the attempt succeeds,
// the program displays the number of actual items read.

#include <stdio.h>

#define BUFFERSIZE 30
#define DATASIZE 22
#define ELEMENTCOUNT 2
#define ELEMENTSIZE (DATASIZE/ELEMENTCOUNT)
#define FILENAME "FREAD.OUT"

int main( void )
{
   FILE *stream;
   char list[30];
   int  i, numread, numwritten;

   for ( i = 0; i < DATASIZE; i++ )
      list[i] = (char)('z' - i);
   list[DATASIZE] = '\0'; // terminal null so we can print it

   // Open file in text mode:
   if( fopen_s( &stream, FILENAME, "w+t" ) == 0 )
   {
      // Write DATASIZE characters to stream
      printf( "Contents of buffer before write/read:\n\t%s\n\n", list );
      numwritten = fwrite( list, sizeof( char ), DATASIZE, stream );
      printf( "Wrote %d items\n\n", numwritten );
      fclose( stream );
   } else {
      printf( "Problem opening the file\n" );
      return -1;
   }

   if( fopen_s( &stream, FILENAME, "r+t" ) == 0 )   {
      // Attempt to read in characters in 2 blocks of 11
      numread = fread_s( list, BUFFERSIZE, ELEMENTSIZE, ELEMENTCOUNT, stream );
      printf( "Number of %d-byte elements read = %d\n\n", ELEMENTSIZE, numread );
      printf( "Contents of buffer after write/read:\n\t%s\n", list );
      fclose( stream );
   } else {
      printf( "File could not be opened\n" );
      return -1;
   }
}
```

```Output
Contents of buffer before write/read:
        zyxwvutsrqponmlkjihgfe

Wrote 22 items

Number of 11-byte elements read = 2

Contents of buffer after write/read:
        zyxwvutsrqponmlkjihgfe
```

## <a name="see-also"></a>Voir aussi

[E/S de flux](../../c-runtime-library/stream-i-o.md)<br/>
[fwrite](fwrite.md)<br/>
[_read](read.md)<br/>
