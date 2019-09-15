---
title: fgetpos
ms.date: 11/04/2016
api_name:
- fgetpos
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
- fgetpos
helpviewer_keywords:
- fgetpos function
- streams, file position indicator
ms.assetid: bfa05c38-1135-418c-bda1-d41be51acb62
ms.openlocfilehash: 27d25b29f656d1df889e5f83857ca437f609a07a
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70940846"
---
# <a name="fgetpos"></a>fgetpos

Obtient l’indicateur de position de fichier d’un flux.

## <a name="syntax"></a>Syntaxe

```C
int fgetpos(
   FILE *stream,
   fpos_t *pos
);
```

### <a name="parameters"></a>Paramètres

*stream*<br/>
Flux cible.

*imprim*<br/>
Stockage de l’indicateur de position.

## <a name="return-value"></a>Valeur de retour

En cas de réussite, **fgetpos** retourne 0. En cas d’échec, elle retourne une valeur différente de zéro et définit **errno** sur l’une des constantes manifestes suivantes (définies dans stdio. H) : **EBADF**, ce qui signifie que le flux spécifié n’est pas un pointeur de fichier valide ou n’est pas accessible, ou **EINVAL**, ce qui signifie que la valeur de *flux* ou la valeur de *pos* n’est pas valide, par exemple si est un pointeur null. Si *Stream* ou *pos* est un pointeur **null** , la fonction appelle le gestionnaire de paramètre non valide, comme décrit dans [validation de paramètre](../../c-runtime-library/parameter-validation.md).

## <a name="remarks"></a>Notes

La fonction **fgetpos** obtient la valeur actuelle de l’indicateur de position de fichier de l’argument de *flux* et la stocke dans l’objet désigné par *pos*. La fonction **fsetpos** peut utiliser ultérieurement les informations stockées dans *pos* pour réinitialiser le pointeur de l’argument de *flux* à sa position au moment de l’appel de **fgetpos** . La valeur *pos* est stockée dans un format interne et est destinée à être utilisée uniquement par **fgetpos** et **fsetpos**.

## <a name="requirements"></a>Configuration requise

|Fonction|En-tête requis|
|--------------|---------------------|
|**fgetpos**|\<stdio.h>|

Pour plus d’informations sur la compatibilité, voir consultez [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemples

```C
// crt_fgetpos.c
// This program uses fgetpos and fsetpos to
// return to a location in a file.

#include <stdio.h>

int main( void )
{
   FILE   *stream;
   fpos_t pos;
   char   buffer[20];

   if( fopen_s( &stream, "crt_fgetpos.txt", "rb" ) ) {
      perror( "Trouble opening file" );
      return -1;
   }

   // Read some data and then save the position.
   fread( buffer, sizeof( char ), 8, stream );
   if( fgetpos( stream, &pos ) != 0 ) {
      perror( "fgetpos error" );
      return -1;
   }

   fread( buffer, sizeof( char ), 13, stream );
   printf( "after fgetpos: %.13s\n", buffer );

   // Restore to old position and read data
   if( fsetpos( stream, &pos ) != 0 ) {
      perror( "fsetpos error" );
      return -1;
   }

   fread( buffer, sizeof( char ), 13, stream );
   printf( "after fsetpos: %.13s\n", buffer );
   fclose( stream );
}
```

## <a name="input-crt_fgetpostxt"></a>Entrée : crt_fgetpos.txt

```Input
fgetpos gets a stream's file-position indicator.
```

### <a name="output-crt_fgetpostxt"></a>Sortie : crt_fgetpos.txt

```Output
after fgetpos: gets a stream
after fsetpos: gets a stream
```

## <a name="see-also"></a>Voir aussi

[E/S de flux](../../c-runtime-library/stream-i-o.md)<br/>
[fsetpos](fsetpos.md)<br/>
