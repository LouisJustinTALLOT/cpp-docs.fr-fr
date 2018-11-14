---
title: _lseek, _lseeki64
ms.date: 11/04/2016
apiname:
- _lseeki64
- _lseek
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
- _lseeki64
- _lseek
- lseeki64
helpviewer_keywords:
- lseek function
- _lseek function
- _lseeki64 function
- lseeki64 function
- file pointers [C++], moving
- seek file pointers
ms.assetid: aba8a768-d40e-48c3-b38e-473dbd782f93
ms.openlocfilehash: 4d0320b45cb8cd99f1d9f6494b7dcb17bc545a81
ms.sourcegitcommit: 1819bd2ff79fba7ec172504b9a34455c70c73f10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2018
ms.locfileid: "51326093"
---
# <a name="lseek-lseeki64"></a>_lseek, _lseeki64

Déplace un pointeur de fichier vers l’emplacement spécifié.

## <a name="syntax"></a>Syntaxe

```C
long _lseek(
   int fd,
   long offset,
   int origin
);
__int64 _lseeki64(
   int fd,
   __int64 offset,
   int origin
);
```

### <a name="parameters"></a>Paramètres

*fd*<br/>
Descripteur de fichier qui fait référence à un fichier ouvert.

*offset*<br/>
Nombre d’octets à partir d’*origin*.

*origin*<br/>
Position initiale.

## <a name="return-value"></a>Valeur de retour

**_lseek** retourne le décalage, en octets, de la nouvelle position à partir du début du fichier. **_lseeki64** retourne le décalage en un entier 64 bits. La fonction retourne-1 L pour indiquer une erreur. Si un paramètre non valide est passé, tel qu’un descripteur de fichier incorrect, que la valeur d’*origin* n’est pas valide ou que la position spécifiée par *offset* se situe avant le début du fichier, le gestionnaire de paramètres non valides est appelé, comme décrit dans [Validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, ces fonctions définissent **errno** à **EBADF** et retournent-1 L. Sur les appareils sans fonctionnalités de recherche (tels que les terminaux et les imprimantes), la valeur de retour n’est pas définie.

Pour plus d’informations sur ces codes d’erreur et autres, consultez [_doserrno, errno, _sys_errlist et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Notes

Le **_lseek** fonction déplace le pointeur de fichier associé *fd* vers un nouvel emplacement est *décalage* octets à partir de *origine*. L’opération suivante sur le fichier se produit au nouvel emplacement. L’argument *origin* doit être une des constantes suivantes, qui sont définies dans Stdio.h.

|*origine* valeur||
|-|-|
| **SEEK_SET** | Début du fichier. |
| **SEEK_CUR** | Position actuelle du pointeur de fichier. |
| **SEEK_END** | Fin du fichier. |

Vous pouvez utiliser **_lseek** pour repositionner le pointeur n’importe où dans un fichier ou au-delà de la fin du fichier.

## <a name="requirements"></a>Configuration requise

|Routine|En-tête requis|
|-------------|---------------------|
|**_lseek**|\<io.h>|
|**_lseeki64**|\<io.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Bibliothèques

Toutes les versions des [bibliothèques Runtime C](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a>Exemple

```C
// crt_lseek.c
/* This program first opens a file named lseek.txt.
* It then uses _lseek to find the beginning of the file,
* to find the current position in the file, and to find
* the end of the file.
*/

#include <io.h>
#include <fcntl.h>
#include <stdlib.h>
#include <stdio.h>
#include <share.h>

int main( void )
{
   int fh;
   long pos;               /* Position of file pointer */
   char buffer[10];

   _sopen_s( &fh, "crt_lseek.c_input", _O_RDONLY, _SH_DENYNO, 0 );

   /* Seek the beginning of the file: */
   pos = _lseek( fh, 0L, SEEK_SET );
   if( pos == -1L )
      perror( "_lseek to beginning failed" );
   else
      printf( "Position for beginning of file seek = %ld\n", pos );

   /* Move file pointer a little */
    _read( fh, buffer, 10 );

   /* Find current position: */
   pos = _lseek( fh, 0L, SEEK_CUR );
   if( pos == -1L )
      perror( "_lseek to current position failed" );
   else
      printf( "Position for current position seek = %ld\n", pos );

   /* Set the end of the file: */
   pos = _lseek( fh, 0L, SEEK_END );
   if( pos == -1L )
      perror( "_lseek to end failed" );
   else
      printf( "Position for end of file seek = %ld\n", pos );

   _close( fh );
}
```

### <a name="input-crtlseekcinput"></a>Entrée : crt_lseek.c_input

```Input
Line one.
Line two.
Line three.
Line four.
Line five.
```

### <a name="output"></a>Sortie

```Output
Position for beginning of file seek = 0
Position for current position seek = 10
Position for end of file seek = 57
```

## <a name="see-also"></a>Voir aussi

[E/S de bas niveau](../../c-runtime-library/low-level-i-o.md)<br/>
[fseek, _fseeki64](fseek-fseeki64.md)<br/>
[_tell, _telli64](tell-telli64.md)<br/>
