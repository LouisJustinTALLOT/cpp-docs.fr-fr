---
title: ftell, _ftelli64
ms.date: 11/04/2016
apiname:
- _ftelli64
- ftell
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
- _ftelli64
- ftell
helpviewer_keywords:
- ftell function
- ftelli64 function
- _ftelli64 function
- file pointers [C++], getting current position
- file pointers [C++]
ms.assetid: 40149cd8-65f2-42ff-b70c-68e3e918cdd7
ms.openlocfilehash: cc76ad0776ae82637b95d32cdc6254d3c40da5b5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62332781"
---
# <a name="ftell-ftelli64"></a>ftell, _ftelli64

Obtient la position actuelle d’un pointeur de fichier.

## <a name="syntax"></a>Syntaxe

```C
long ftell(
   FILE *stream
);
__int64 _ftelli64(
   FILE *stream
);
```

### <a name="parameters"></a>Paramètres

*stream*<br/>
Cible **fichier** structure.

## <a name="return-value"></a>Valeur de retour

**ftell** et **_ftelli64** retourner la position actuelle du fichier. La valeur retournée par **ftell** et **_ftelli64** peuvent ne pas refléter l’offset d’octet physique pour les flux ouverts en mode texte, car ce mode entraîne la traduction des sauts de ligne de transport. Utilisez **ftell** avec [fseek](fseek-fseeki64.md) ou **_ftelli64** avec [_fseeki64](fseek-fseeki64.md) vers les emplacements de fichier correctement. En cas d’erreur, **ftell** et **_ftelli64** appellent le Gestionnaire de paramètre non valide, comme décrit dans [Validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, ces fonctions retournent-1 L et un ensemble **errno** à une des suivantes constantes, définies dans ERRNO. H. Le **EBADF** constante signifie la *flux* argument n’est pas une valeur de pointeur de fichier valide ou ne fait pas référence à un fichier ouvert. **EINVAL** signifie non valide *flux* argument passé à la fonction. Sur les appareils incapables de recherche (tels que les terminaux et les imprimantes), ou lorsque *flux* ne fait pas référence à un fichier ouvert, la valeur de retour n’est pas définie.

Pour plus d’informations sur ces codes de retour et les autres, consultez [_doserrno, errno, _sys_errlist et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Notes

Le **ftell** et **_ftelli64** fonctions récupèrent la position actuelle du pointeur de fichier (le cas échéant) associée à *flux*. La position est exprimée sous la forme d’un décalage par rapport au début du flux.

Notez que quand un fichier est ouvert pour un ajout de données, la position de fichier actuelle est déterminée par la dernière opération d’E/S, pas par l’emplacement auquel l’écriture suivante se produirait. Par exemple, si un fichier est ouvert pour un ajout et que la dernière opération était une lecture, la position de fichier est le point où l’opération de lecture suivante commencerait, pas celui où l’écriture suivante démarrerait. (Quand un fichier est ouvert pour un ajout, la position de fichier est déplacée vers la fin du fichier avant toute opération d’écriture.) Si aucune opération d’E/S ne s’est produite sur un fichier ouvert pour un ajout, la position de fichier correspond au début du fichier.

En mode texte, Ctrl+Z est interprété comme un caractère de fin de fichier en entrée. Dans les fichiers ouverts en lecture/écriture, **fopen** et toutes les routines connexes recherchent un CTRL + Z à la fin du fichier et le suppriment si possible. En effet à l’aide de la combinaison de **ftell** et [fseek](fseek-fseeki64.md) ou **_ftelli64** et [_fseeki64](fseek-fseeki64.md)pour se déplacer dans un fichier qui se termine par un CTRL + Z peut provoquer **ftell** ou **_ftelli64** au comportement incorrect vers la fin du fichier.

Cette fonction verrouille le thread appelant pendant l’exécution et est donc thread-safe. Pour obtenir une version sans verrouillage, consultez **_ftell_nolock**.

## <a name="requirements"></a>Configuration requise

|Fonction|En-tête requis|En-têtes facultatifs|
|--------------|---------------------|----------------------|
|**ftell**|\<stdio.h>|\<errno.h>|
|**_ftelli64**|\<stdio.h>|\<errno.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

```C
// crt_ftell.c
// This program opens a file named CRT_FTELL.C
// for reading and tries to read 100 characters. It
// then uses ftell to determine the position of the
// file pointer and displays this position.

#include <stdio.h>

FILE *stream;

int main( void )
{
   long position;
   char list[100];
   if( fopen_s( &stream, "crt_ftell.c", "rb" ) == 0 )
   {
      // Move the pointer by reading data:
      fread( list, sizeof( char ), 100, stream );
      // Get position after read:
      position = ftell( stream );
      printf( "Position after trying to read 100 bytes: %ld\n",
              position );
      fclose( stream );
   }
}
```

```Output
Position after trying to read 100 bytes: 100
```

## <a name="see-also"></a>Voir aussi

[E/S de flux](../../c-runtime-library/stream-i-o.md)<br/>
[fopen, _wfopen](fopen-wfopen.md)<br/>
[fgetpos](fgetpos.md)<br/>
[fseek, _fseeki64](fseek-fseeki64.md)<br/>
[_lseek, _lseeki64](lseek-lseeki64.md)<br/>
