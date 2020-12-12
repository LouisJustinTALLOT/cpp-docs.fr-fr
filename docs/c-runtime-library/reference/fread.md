---
description: 'En savoir plus sur : fread'
title: fread
ms.date: 4/2/2020
api_name:
- fread
- _o_fread
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
- fread
helpviewer_keywords:
- reading data [C++], from input streams
- fread function
- data [C++], reading from input stream
- streams [C++], reading data from
ms.assetid: 9a3c1538-93dd-455e-ae48-77c1e23c53f0
ms.openlocfilehash: 131dacd296d4e710ea1b91d9a8578ef06b76a341
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97314046"
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

*mémoire tampon*<br/>
Emplacement de stockage des données.

*size*<br/>
Taille de l’élément en octets.

*count*<br/>
Nombre maximal d’éléments à lire.

*train*<br/>
Pointeur désignant la structure **FILE**.

## <a name="return-value"></a>Valeur renvoyée

**fread** retourne le nombre d’éléments complets réellement lus, qui peut être inférieur à *Count* si une erreur se produit ou si la fin du fichier est rencontrée avant d’atteindre le *nombre*. Utilisez la fonction **feof** ou **ferror** pour distinguer une erreur de lecture d’une condition de fin de fichier. Si la *taille* ou le *nombre* est égal à 0, **fread** retourne 0 et le contenu de la mémoire tampon n’est pas modifié. Si *Stream* ou *buffer* est un pointeur null, **fread** appelle le gestionnaire de paramètre non valide, comme décrit dans [validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, cette fonction affecte à **errno** la valeur **EINVAL** et retourne 0.

Pour plus d’informations sur ces codes d’erreur [ \_ , consultez doserrno, errno, \_ sys \_ errlist et \_ sys \_ nErr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) .

## <a name="remarks"></a>Notes

La fonction **fread** lit le *nombre* d’éléments de *taille* octets à partir du *flux* d’entrée et les stocke dans la *mémoire tampon*. Le pointeur de fichier associé au *flux* (le cas échéant) est augmenté du nombre d’octets réellement lus. Si le flux donné est ouvert en [mode texte](../../c-runtime-library/text-and-binary-mode-file-i-o.md), les nouvelles lignes de style Windows sont converties en nouvelles lignes de style UNIX. Autrement dit, les paires CRLF (retour chariot-saut de ligne) sont remplacées par des caractères de saut de ligne unique (LF). Le remplacement n’a aucun effet sur le pointeur de fichier ou la valeur de retour. La position du pointeur de fichier est indéterminée si une erreur se produit. La valeur d’un élément partiellement lu ne peut pas être déterminée.

En cas d’utilisation sur un flux en mode texte, si la quantité de données demandées (autrement dit, le nombre de *tailles* \* ) est supérieure ou égale à la taille de la mémoire tampon du **fichier** interne \* (par défaut, il s’agit de 4096 octets, configurable à l’aide de [setvbuf](../../c-runtime-library/reference/setvbuf.md)), les données de flux sont copiées directement dans la mémoire tampon fournie par l’utilisateur, et la conversion Étant donné que les données converties peuvent être plus courtes que les données de flux copiées dans la mémoire tampon, les données passées dans la *mémoire tampon* \[ *return_value* \* *taille*] (où *return_value* est la valeur de retour de **fread**) peuvent contenir des données non converties du fichier. Pour cette raison, nous vous recommandons d’arrêter les données de type caractère au niveau de la *mémoire tampon* \[ *return_value* \* *taille*] si l’objectif de la mémoire tampon est d’agir en tant que chaîne de style C. Pour plus d’informations sur les effets du mode texte et du mode binaire, consultez [fopen](fopen-wfopen.md) .

Cette fonction verrouille les autres threads. Si vous avez besoin d’une version sans verrouillage, utilisez **_fread_nolock**.

Par défaut, l’état global de cette fonction est limité à l’application. Pour modifier cette valeur, consultez [état global dans le CRT](../global-state.md).

## <a name="requirements"></a>Spécifications

|Fonction|En-tête requis|
|--------------|---------------------|
|**fread**|\<stdio.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

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
