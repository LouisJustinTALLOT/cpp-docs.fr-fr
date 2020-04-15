---
title: ftell, _ftelli64
ms.date: 4/2/2020
api_name:
- _ftelli64
- ftell
- _o__ftelli64
- _o_ftell
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
- _ftelli64
- ftell
helpviewer_keywords:
- ftell function
- ftelli64 function
- _ftelli64 function
- file pointers [C++], getting current position
- file pointers [C++]
ms.assetid: 40149cd8-65f2-42ff-b70c-68e3e918cdd7
ms.openlocfilehash: bfe79610161a7f4032517d9f7eaa0de50be18e50
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81345617"
---
# <a name="ftell-_ftelli64"></a>ftell, _ftelli64

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

*Flux*<br/>
Structure **FILE** cible.

## <a name="return-value"></a>Valeur de retour

**ftell** et **_ftelli64** retournent la position de fichier actuelle. La valeur retournée par **ftell** et **_ftelli64** peut ne pas refléter le décalage d’ente physique pour les flux ouverts en mode texte, parce que le mode texte provoque la traduction d’alimentation en ligne de retour de transport. Utilisez **ftell** avec [fseek](fseek-fseeki64.md) ou **_ftelli64** avec [_fseeki64](fseek-fseeki64.md) pour revenir correctement aux emplacements des fichiers. Sur erreur, **ftell** et **_ftelli64** invoquent le gestionnaire de paramètres invalides, tel que décrit dans [La validation des paramètres](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, ces fonctions renvoient -1L et **placent errno** à l’une des deux constantes, définies dans ERRNO. H. La constante **EBADF** signifie que l’argument du *flux* n’est pas une valeur valide de pointeur de fichier ou ne se réfère pas à un fichier ouvert. **EINVAL** signifie qu’un argument de *flux* invalide a été transmis à la fonction. Sur les appareils incapables de rechercher (tels que les terminaux et les imprimantes), ou lorsque *le flux* ne se réfère pas à un fichier ouvert, la valeur de retour n’est pas définie.

Voir [_doserrno, errno, _sys_errlist, et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) pour plus d’informations sur ces codes de retour, et d’autres.

## <a name="remarks"></a>Notes

Les fonctions **ftell** et **_ftelli64** récupèrent la position actuelle du pointeur de fichier (le cas échéant) associée au *flux*. La position est exprimée sous la forme d’un décalage par rapport au début du flux.

Notez que quand un fichier est ouvert pour un ajout de données, la position de fichier actuelle est déterminée par la dernière opération d’E/S, pas par l’emplacement auquel l’écriture suivante se produirait. Par exemple, si un fichier est ouvert pour un ajout et que la dernière opération était une lecture, la position de fichier est le point où l’opération de lecture suivante commencerait, pas celui où l’écriture suivante démarrerait. (Lorsqu’un fichier est ouvert pour l’appending, la position du fichier est déplacée à la fin du fichier avant toute opération de rédaction.) Si aucune opération I/O n’a encore eu lieu sur un fichier ouvert pour appending, la position du fichier est le début du fichier.

En mode texte, Ctrl+Z est interprété comme un caractère de fin de fichier en entrée. Dans les fichiers ouverts pour la lecture/écriture, **fopen** et toutes les routines connexes vérifient un CTRL-Z à la fin du fichier et supprimez-le si possible. Ceci est fait parce que l’utilisation de la combinaison de **ftell** et [fseek](fseek-fseeki64.md) ou **_ftelli64** et [_fseeki64](fseek-fseeki64.md), de se déplacer dans un fichier qui se termine par un CTRL-Z peut provoquer **ftell** ou **_ftelli64** de se comporter incorrectement vers la fin du fichier.

Cette fonction verrouille le thread appelant pendant l’exécution et est donc thread-safe. Pour une version non-locking, voir **_ftell_nolock**.

Par défaut, l’état global de cette fonction est étendue à l’application. Pour changer cela, voir [Global State dans le CRT](../global-state.md).

## <a name="requirements"></a>Spécifications

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
