---
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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: 26ffd56072f1a5fddc3131a42cd47c145e437b60
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81346065"
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

*Taille*<br/>
Taille de l’élément en octets.

*count*<br/>
Nombre maximal d’éléments à lire.

*Flux*<br/>
Pointeur désignant la structure **FILE**.

## <a name="return-value"></a>Valeur de retour

**fread** renvoie le nombre d’éléments complets effectivement lus, qui peuvent être moins que *compter* si une erreur se produit ou si la fin du fichier est rencontrée avant d’atteindre le *compte*. Utilisez la fonction **feof** ou **ferror** pour distinguer une erreur de lecture d’une condition de fin de fichier. Si *la taille* ou le *nombre* est de 0, **fread** retourne 0 et le contenu tampon est inchangé. Si *le flux* ou le *tampon* est un pointeur nul, **fread** invoque le gestionnaire de paramètres invalide, tel que décrit dans [la validation de paramètres](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, cette fonction définit **errno** à **EINVAL** et renvoie 0.

Voir [ \_ \_doserrno, errno,\_sys \_errlist,\_et sys nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) pour plus d’informations sur ces codes d’erreur.

## <a name="remarks"></a>Notes

La fonction **fread** se lit jusqu’à *compter* les articles de *taille* octets du *flux* d’entrée et les stocke dans *le tampon*. Le pointeur de fichier associé au *flux* (s’il y en a un) est augmenté par le nombre d’octets réellement lus. Si le flux donné est ouvert en [mode texte,](../../c-runtime-library/text-and-binary-mode-file-i-o.md)les nouvelles lignes de style Windows sont converties en nouvelles lignes de style Unix. C’est-à-dire que les paires d’alimentation en ligne de retour de transport (CRLF) sont remplacées par des caractères d’alimentation en ligne unique (LF). Le remplacement n’a aucun effet sur le pointeur de fichier ou la valeur de retour. La position du pointeur de fichier est indéterminée si une erreur se produit. La valeur d’un élément partiellement lu ne peut pas être déterminée.

Lorsqu’il est utilisé sur un flux de mode texte, si la quantité de données demandées (c’est-à-dire le *nombre*de *tailles)* \* est supérieure ou égale à la taille interne du tampon **FILE** \* (par défaut, il s’agit de 4096 octets, configurables à l’aide [de setvbuf),](../../c-runtime-library/reference/setvbuf.md)les données du flux sont copiées directement dans le tampon fourni par l’utilisateur, et la conversion de nouvelle ligne est effectuée dans ce tampon. Étant donné que les données converties peuvent être plus courtes que les données du flux copiées dans le tampon, les données passées *tampon*\[*return_value* \* *taille*] (où *return_value* est la valeur de retour de **fread**) peuvent contenir des données non converties du fichier. Pour cette raison, nous vous recommandons de mettre fin à des données de caractère à la *taille**de return_value* \* *tampon*\[] si l’intention du tampon est d’agir comme une chaîne de style C. Voir [fopen](fopen-wfopen.md) pour plus de détails sur les effets du mode texte et du mode binaire.

Cette fonction verrouille les autres threads. Si vous avez besoin d’une version non verrouillée, utilisez **_fread_nolock**.

Par défaut, l’état global de cette fonction est étendue à l’application. Pour changer cela, voir [Global State dans le CRT](../global-state.md).

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
[Texte et fichier binaire I/O](../../c-runtime-library/text-and-binary-mode-file-i-o.md)<br/>
[fopen](fopen-wfopen.md)<br/>
[fwrite](fwrite.md)<br/>
[_read](read.md)<br/>
