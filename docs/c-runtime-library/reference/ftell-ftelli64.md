---
description: 'En savoir plus sur : ftell, _ftelli64'
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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: f3fec98cb9d90c8b63072a8e618f58246a6b0147
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97334243"
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

*train*<br/>
Structure du **fichier** cible.

## <a name="return-value"></a>Valeur renvoyée

**ftell** et **_ftelli64** retournent la position actuelle du fichier. La valeur retournée par **ftell** et **_ftelli64** peut ne pas refléter l’offset d’octet physique pour les flux ouverts en mode texte, car le mode texte provoque la traduction du saut de ligne de retour chariot. Utilisez **ftell** avec [fseek](fseek-fseeki64.md) ou **_ftelli64** avec [_fseeki64](fseek-fseeki64.md) pour revenir correctement aux emplacements de fichiers. En cas d’erreur, **ftell** et **_ftelli64** appeler le gestionnaire de paramètre non valide, comme décrit dans [validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, ces fonctions retournent-1L et définissent **errno** sur l’une des deux constantes définies dans errno. H. La constante **EBADF** signifie que l’argument de *flux* n’est pas une valeur de pointeur de fichier valide ou ne fait pas référence à un fichier ouvert. **EINVAL** signifie qu’un argument de *flux* non valide a été passé à la fonction. Sur les appareils qui ne sont pas en mesure de rechercher (tels que les terminaux et les imprimantes) ou lorsque le *flux* ne fait pas référence à un fichier ouvert, la valeur de retour n’est pas définie.

Pour plus d’informations sur ces codes de retour et autres, consultez [_doserrno, errno, _sys_errlist et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) .

## <a name="remarks"></a>Notes

Les fonctions **ftell** et **_ftelli64** récupèrent la position actuelle du pointeur de fichier (le cas échéant) associé au *flux*. La position est exprimée sous la forme d’un décalage par rapport au début du flux.

Notez que quand un fichier est ouvert pour un ajout de données, la position de fichier actuelle est déterminée par la dernière opération d’E/S, pas par l’emplacement auquel l’écriture suivante se produirait. Par exemple, si un fichier est ouvert pour un ajout et que la dernière opération était une lecture, la position de fichier est le point où l’opération de lecture suivante commencerait, pas celui où l’écriture suivante démarrerait. (Lorsqu’un fichier est ouvert pour l’ajout, la position de fichier est déplacée vers la fin du fichier avant toute opération d’écriture.) Si aucune opération d’e/s n’a encore été effectuée sur un fichier ouvert pour l’ajout, la position de fichier correspond au début du fichier.

En mode texte, Ctrl+Z est interprété comme un caractère de fin de fichier en entrée. Dans les fichiers ouverts en lecture/écriture, **fopen** et toutes les routines associées vérifient la disponibilité d’un Ctrl + Z à la fin du fichier et le suppriment si possible. Cela est dû au fait que l’utilisation de la combinaison de **ftell** et [fseek](fseek-fseeki64.md) ou **_ftelli64** et [_fseeki64](fseek-fseeki64.md), pour se déplacer dans un fichier qui se termine par un Ctrl + Z peut provoquer un comportement incorrect de **ftell** ou de **_ftelli64** vers la fin du fichier.

Cette fonction verrouille le thread appelant pendant l’exécution et est donc thread-safe. Pour une version sans verrouillage, consultez **_ftell_nolock**.

Par défaut, l’état global de cette fonction est limité à l’application. Pour modifier cette valeur, consultez [état global dans le CRT](../global-state.md).

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
