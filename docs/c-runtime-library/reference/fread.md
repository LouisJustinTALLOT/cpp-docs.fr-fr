---
title: fread
ms.date: 11/28/2018
apiname:
- fread
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
- fread
helpviewer_keywords:
- reading data [C++], from input streams
- fread function
- data [C++], reading from input stream
- streams [C++], reading data from
ms.assetid: 9a3c1538-93dd-455e-ae48-77c1e23c53f0
ms.openlocfilehash: 7248eb08409b50d855dbb70c7638a856302b345b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62287874"
---
# <a name="fread"></a>fread

Lit les données d’un flux.

## <a name="syntax"></a>Syntaxe

```C
size_t fread(
   void *buffer,
   size_t size,
   size_t count,
   FILE *stream
);
```

### <a name="parameters"></a>Paramètres

*buffer*<br/>
Emplacement de stockage des données.

*size*<br/>
Taille de l’élément en octets.

*count*<br/>
Nombre maximal d’éléments à lire.

*stream*<br/>
Pointeur désignant la structure **FILE**.

## <a name="return-value"></a>Valeur de retour

**fread** retourne le nombre d’éléments complets réellement lus, qui peut être inférieur à *nombre* si une erreur se produit ou si la fin du fichier est rencontrée avant d’atteindre *nombre*. Utilisez le **feof** ou **ferror** fonction permettant de distinguer une erreur de lecture d’une condition de fin de fichier. Si *taille* ou *nombre* est 0, **fread** retourne 0 et le contenu de la mémoire tampon est identiques. Si *flux* ou *tampon* est un pointeur null, **fread** appelle le Gestionnaire de paramètre non valide, comme décrit dans [Validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, cette fonction affecte **errno** à **EINVAL** et retourne 0.

Consultez [ \_doserrno, errno, \_sys\_errlist, et \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) pour plus d’informations sur ces codes d’erreur.

## <a name="remarks"></a>Notes

Le **fread** fonction lit jusqu'à *nombre* éléments de *taille* octets à partir de l’entrée *flux* et les stocke dans *mémoire tampon* . Le pointeur de fichier associé *flux* (le cas échéant) est augmenté le nombre d’octets réellement lus. Si le flux donné est ouvert en [mode texte](../../c-runtime-library/text-and-binary-mode-file-i-o.md), sauts de ligne Windows de style sont convertis en sauts de ligne de style Unix. Autrement dit, les paires de sauts de ligne (CRLF) chariot sont remplacés par les caractères de saut de ligne (LF) unique. Le remplacement n’a aucun effet sur le pointeur de fichier ou la valeur de retour. La position du pointeur de fichier est indéterminée si une erreur se produit. La valeur d’un élément partiellement lu ne peut pas être déterminée.

Lorsqu’il est utilisé sur un flux en mode texte, si la quantité de données demandée (autrement dit, *taille* \* *nombre*) est supérieur ou égal à interne **fichier** \*taille de mémoire tampon (valeur par défaut est 4 096 octets, configurables à l’aide de [setvbuf](../../c-runtime-library/reference/setvbuf.md)), les données de flux sont copiées directement dans la mémoire tampon fournie par l’utilisateur et la conversion de saut de ligne est effectuée dans cette mémoire tampon. Dans la mesure où les données converties peuvent être plus courtes que les données de flux de données copiées dans la mémoire tampon, les données passées *tampon*\[*return_value* \* *taille*] () où *return_value* est la valeur de retour à partir de **fread**) peuvent contenir des données non converties à partir du fichier. Pour cette raison, nous vous recommandons de vous terminez les données de caractères à *tampon*\[*return_value* \* *taille*] si l’objectif de la mémoire tampon est pour agir comme une chaîne de style C. Consultez [fopen](fopen-wfopen.md) pour plus d’informations sur les effets du mode texte et le mode binaire.

Cette fonction verrouille les autres threads. Si vous avez besoin d’une version sans verrouillage, utilisez **_fread_nolock**.

## <a name="requirements"></a>Configuration requise

|Fonction|En-tête requis|
|--------------|---------------------|
|**fread**|\<stdio.h>|

Pour plus d’informations sur la compatibilité, voir consultez [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

```C
// crt_fread.c
// This program opens a file named FREAD.OUT and
// writes 25 characters to the file. It then tries to open
// FREAD.OUT and read in 25 characters. If the attempt succeeds,
// the program displays the number of actual items read.

#include <stdio.h>

int main( void )
{
   FILE *stream;
   char list[30];
   int  i, numread, numwritten;

   // Open file in text mode:
   if( fopen_s( &stream, "fread.out", "w+t" ) == 0 )
   {
      for ( i = 0; i < 25; i++ )
         list[i] = (char)('z' - i);
      // Write 25 characters to stream
      numwritten = fwrite( list, sizeof( char ), 25, stream );
      printf( "Wrote %d items\n", numwritten );
      fclose( stream );

   }
   else
      printf( "Problem opening the file\n" );

   if( fopen_s( &stream, "fread.out", "r+t" ) == 0 )
   {
      // Attempt to read in 25 characters
      numread = fread( list, sizeof( char ), 25, stream );
      printf( "Number of items read = %d\n", numread );
      printf( "Contents of buffer = %.25s\n", list );
      fclose( stream );
   }
   else
      printf( "File could not be opened\n" );
}
```

```Output
Wrote 25 items
Number of items read = 25
Contents of buffer = zyxwvutsrqponmlkjihgfedcb
```

## <a name="see-also"></a>Voir aussi

[E/S de flux](../../c-runtime-library/stream-i-o.md)<br/>
[E/s de fichier texte et binaire](../../c-runtime-library/text-and-binary-mode-file-i-o.md)<br/>
[fopen](fopen-wfopen.md)<br/>
[fwrite](fwrite.md)<br/>
[_read](read.md)<br/>
