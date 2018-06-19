---
title: fgetpos | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- fgetpos
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
- fgetpos
dev_langs:
- C++
helpviewer_keywords:
- fgetpos function
- streams, file position indicator
ms.assetid: bfa05c38-1135-418c-bda1-d41be51acb62
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b111a911083354c8d9478b2c914a0a5f7dfe7725
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32397383"
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

*Flux de données*<br/>
Flux cible.

*bons de commande*<br/>
Stockage de l’indicateur de position.

## <a name="return-value"></a>Valeur de retour

En cas de réussite, **fgetpos** retourne 0. En cas d’échec, elle retourne une valeur différente de zéro et définit **errno** à un des éléments suivants du manifeste de constantes (définies dans STDIO. (H) : **EBADF**, ce qui signifie que le flux de données spécifié n’est pas un pointeur de fichier valide ou n’est pas accessible, ou **EINVAL**, ce qui signifie que la *flux* valeur ou la valeur de *pos* est non valide, telle qu’if est un pointeur null. Si *flux* ou *pos* est un **NULL** pointeur, la fonction appelle le Gestionnaire de paramètre non valide, comme décrit dans [Validation de paramètre](../../c-runtime-library/parameter-validation.md).

## <a name="remarks"></a>Notes

Le **fgetpos** fonction obtient la valeur actuelle de la *flux* indicateur de position de fichier et le stocke dans l’objet désigné par l’argument *pos*. Le **fsetpos** fonction peut ensuite utiliser les informations stockées dans *pos* pour réinitialiser le *flux* pointeur d’argument à sa position en temps **fgetpos** a été appelée. Le *pos* valeur est stockée dans un format interne et est destinée uniquement par **fgetpos** et **fsetpos**.

## <a name="requirements"></a>Spécifications

|Fonction|En-tête requis|
|--------------|---------------------|
|**fgetpos**|\<stdio.h>|

Pour plus d’informations sur la compatibilité, voir consultez [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

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

## <a name="input-crtfgetpostxt"></a>Entrée : crt_fgetpos.txt

```Input
fgetpos gets a stream's file-position indicator.
```

### <a name="output-crtfgetpostxt"></a>Sortie : crt_fgetpos.txt

```Output
after fgetpos: gets a stream
after fsetpos: gets a stream
```

## <a name="see-also"></a>Voir aussi

[E/S de flux](../../c-runtime-library/stream-i-o.md)<br/>
[fsetpos](fsetpos.md)<br/>
