---
title: _tell, _telli64
ms.date: 11/04/2016
apiname:
- _telli64
- _tell
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
- tell
- telli64
- _telli64
- _tell
helpviewer_keywords:
- tell function
- file pointers [C++], getting
- _tell function
- file pointers [C++]
- telli64 function
- _telli64 function
ms.assetid: 1500e8f9-8fec-4253-9eec-ec66125dfc9b
ms.openlocfilehash: 628f37d3b8a39a75fb2329a1b2805426f15e821f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62258570"
---
# <a name="tell-telli64"></a>_tell, _telli64

Obtiennent la position du pointeur de fichier.

## <a name="syntax"></a>Syntaxe

```C
long _tell(
   int handle
);
__int64 _telli64(
   int handle
);
```

### <a name="parameters"></a>Paramètres

*handle*<br/>
Descripteur de fichier faisant référence au fichier ouvert.

## <a name="return-value"></a>Valeur de retour

Position actuelle du pointeur de fichier. Sur les appareils incapables de rechercher, la valeur de retour n’est pas définie.

Une valeur de retour de-1 L indique une erreur. Si *gérer* est un descripteur de fichier non valide, le Gestionnaire de paramètre non valide est appelé, comme décrit dans [Validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, ces fonctions définissent **errno** à **EBADF** et retournent-1 L.

Pour plus d’informations sur ce code de retour et sur les autres codes, consultez [_doserrno, errno, _sys_errlist, and _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) .

## <a name="remarks"></a>Notes

Le **_tell** fonction obtient la position actuelle du pointeur de fichier (le cas échéant) associée à la *gérer* argument. La position est exprimée en nombre d’octets à partir du début du fichier. Pour le **_telli64** (fonction), cette valeur est exprimée sous la forme d’un entier 64 bits.

## <a name="requirements"></a>Configuration requise

|Routine|En-tête requis|
|-------------|---------------------|
|**_tell**, **_telli64**|\<io.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

```C
// crt_tell.c
// This program uses _tell to tell the
// file pointer position after a file read.
//

#include <io.h>
#include <stdio.h>
#include <fcntl.h>
#include <share.h>
#include <string.h>

int main( void )
{
   int  fh;
   char buffer[500];

   if ( _sopen_s( &fh, "crt_tell.txt", _O_RDONLY, _SH_DENYNO, 0) )
   {
      char buff[50];
      _strerror_s( buff, sizeof(buff), NULL );
      printf( buff );
      exit( -1 );
   }

   if( _read( fh, buffer, 500 ) > 0 )
      printf( "Current file position is: %d\n", _tell( fh ) );
   _close( fh );
}
```

### <a name="input-crttelltxt"></a>Entrée : crt_tell.txt

```Input
Line one.
Line two.
```

### <a name="output"></a>Sortie

```Output
Current file position is: 20
```

## <a name="see-also"></a>Voir aussi

[E/S de bas niveau](../../c-runtime-library/low-level-i-o.md)<br/>
[ftell, _ftelli64](ftell-ftelli64.md)<br/>
[_lseek, _lseeki64](lseek-lseeki64.md)<br/>
