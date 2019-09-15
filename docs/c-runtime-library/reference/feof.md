---
title: feof
ms.date: 11/04/2016
api_name:
- feof
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- feof
helpviewer_keywords:
- end of file, testing for
- feof function
ms.assetid: 09081eee-7c4b-4189-861f-2fad95d3ec6d
ms.openlocfilehash: cf6cfdb63689f5d69cc45dd407ecc6b08a7a7a73
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70941137"
---
# <a name="feof"></a>feof

Teste la fin de fichier sur un flux.

## <a name="syntax"></a>Syntaxe

```C
int feof(
   FILE *stream
);
```

### <a name="parameters"></a>Paramètres

*stream*<br/>
Pointeur désignant la structure **FILE**.

## <a name="return-value"></a>Valeur de retour

La fonction **feof** retourne une valeur différente de zéro si une opération de lecture a tenté de lire au-delà de la fin du fichier ; Sinon, retourne 0. Si le pointeur de flux a la **valeur null**, la fonction appelle le gestionnaire de paramètre non valide, comme décrit dans [validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, **errno** a la valeur **EINVAL** et **feof** retourne 0.

Pour plus d’informations sur ces codes d’erreur et les autres, consultez [_doserrno, errno, _sys_errlist et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Notes

La routine **feof** (implémentée à la fois en tant que fonction et en tant que macro) détermine si la fin du *flux* a été passée. Lorsque la fin du fichier est passée, les opérations de lecture retournent un indicateur de fin de fichier jusqu’à ce que le flux soit fermé ou jusqu’à ce que [rembobine](rewind.md), **fsetpos**, [fseek](fseek-fseeki64.md)ou **clearerr** soit appelé.

Par exemple, si un fichier contient 10 octets et que vous lisez 10 octets à partir du fichier, **feof** retourne 0, car même si le pointeur de fichier se trouve à la fin du fichier, vous n’avez pas tenté de lire au-delà de la fin. Une fois que vous avez essayé de lire un onzième octet, **feof** retourne une valeur différente de zéro.

## <a name="requirements"></a>Configuration requise

|Fonction|En-tête requis|
|--------------|---------------------|
|**feof**|\<stdio.h>|

Pour plus d’informations sur la compatibilité, voir consultez [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemples

```C
// crt_feof.c
// This program uses feof to indicate when
// it reaches the end of the file CRT_FEOF.TXT. It also
// checks for errors with ferror.
//

#include <stdio.h>
#include <stdlib.h>

int main( void )
{
   int  count, total = 0;
   char buffer[100];
   FILE *stream;

   fopen_s( &stream, "crt_feof.txt", "r" );
   if( stream == NULL )
      exit( 1 );

   // Cycle until end of file reached:
   while( !feof( stream ) )
   {
      // Attempt to read in 100 bytes:
      count = fread( buffer, sizeof( char ), 100, stream );
      if( ferror( stream ) )      {
         perror( "Read error" );
         break;
      }

      // Total up actual bytes read
      total += count;
   }
   printf( "Number of bytes read = %d\n", total );
   fclose( stream );
}
```

## <a name="input-crt_feoftxt"></a>Entrée : crt_feof.txt

```Input
Line one.
Line two.
```

### <a name="output"></a>Sortie

```Output
Number of bytes read = 19
```

## <a name="see-also"></a>Voir aussi

[Gestion des erreurs](../../c-runtime-library/error-handling-crt.md)<br/>
[E/S de flux](../../c-runtime-library/stream-i-o.md)<br/>
[clearerr](clearerr.md)<br/>
[_eof](eof.md)<br/>
[ferror](ferror.md)<br/>
[perror, _wperror](perror-wperror.md)<br/>
