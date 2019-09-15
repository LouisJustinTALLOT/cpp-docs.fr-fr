---
title: rewind
ms.date: 11/04/2016
api_name:
- rewind
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
- rewind
helpviewer_keywords:
- rewind function
- repositioning file pointers
- file pointers [C++], repositioning
- file pointers [C++]
ms.assetid: 1a460ce1-28d8-4b5e-83a6-633dca29c28a
ms.openlocfilehash: 084a6f3d7e817498bffb510d865f4a32021e4ce8
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70949274"
---
# <a name="rewind"></a>rewind

Repositionne le pointeur de fichier au début d’un fichier.

## <a name="syntax"></a>Syntaxe

```C
void rewind(
   FILE *stream
);
```

### <a name="parameters"></a>Paramètres

*stream*<br/>
Pointeur désignant la structure **FILE**.

## <a name="remarks"></a>Notes

La fonction **rembobiner** repositionne le pointeur de fichier associé au *flux* au début du fichier. Un appel à **rewind** produit les mêmes effets que

**(void) fseek (** _Stream_ **, 0L, SEEK_SET);**

Toutefois, contrairement à [fseek](fseek-fseeki64.md), le **rembobinage** efface les indicateurs d’erreur pour le flux, ainsi que l’indicateur de fin de fichier. En outre, contrairement à [fseek](fseek-fseeki64.md), **Rewind** ne retourne pas de valeur pour indiquer si le pointeur a été déplacé avec succès.

Pour effacer la mémoire tampon du clavier, utilisez **rembobiner** avec le flux **stdin**, qui est associé au clavier par défaut.

Si Stream est un pointeur **null** , le gestionnaire de paramètres non valides est appelé, comme décrit dans [validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, cette fonction retourne et **errno** a la valeur **EINVAL**.

Pour plus d’informations sur ces codes d’erreur et les autres, consultez [_doserrno, errno, _sys_errlist et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="requirements"></a>Configuration requise

|Routine|En-tête requis|
|-------------|---------------------|
|**rewind**|\<stdio.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Bibliothèques

Toutes les versions des [bibliothèques Runtime C](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a>Exemple

```C
// crt_rewind.c
/* This program first opens a file named
* crt_rewind.out for input and output and writes two
* integers to the file. Next, it uses rewind to
* reposition the file pointer to the beginning of
* the file and reads the data back in.
*/
#include <stdio.h>

int main( void )
{
   FILE *stream;
   int data1, data2;

   data1 = 1;
   data2 = -37;

   fopen_s( &stream, "crt_rewind.out", "w+" );
   if( stream != NULL )
   {
      fprintf( stream, "%d %d", data1, data2 );
      printf( "The values written are: %d and %d\n", data1, data2 );
      rewind( stream );
      fscanf_s( stream, "%d %d", &data1, &data2 );
      printf( "The values read are: %d and %d\n", data1, data2 );
      fclose( stream );
   }
}
```

### <a name="output"></a>Sortie

```Output
The values written are: 1 and -37
The values read are: 1 and -37
```

## <a name="see-also"></a>Voir aussi

[E/S de flux](../../c-runtime-library/stream-i-o.md)<br/>
