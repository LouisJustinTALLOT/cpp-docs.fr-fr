---
title: tmpfile | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- tmpfile
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
- tmpfile
dev_langs:
- C++
helpviewer_keywords:
- temporary files
- tmpfile function
- temporary files, creating
ms.assetid: c4a4dc24-70da-438d-ae4e-98352d88e375
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ebcad2a25af2f2acb0056d882c4191f1a51293d3
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32409067"
---
# <a name="tmpfile"></a>tmpfile

Crée un fichier temporaire. Cette fonction est dépréciée, car il en existe une version plus sécurisée. Consultez [tmpfile_s](tmpfile-s.md).

## <a name="syntax"></a>Syntaxe

```C
FILE *tmpfile( void );
```

## <a name="return-value"></a>Valeur de retour

En cas de réussite, **tmpfile** retourne un pointeur de flux de données. Sinon, elle retourne un **NULL** pointeur.

## <a name="remarks"></a>Notes

Le **tmpfile** fonction crée un fichier temporaire et retourne un pointeur vers ce flux de données. Le fichier temporaire est créé dans le répertoire racine. Pour créer un fichier temporaire dans un répertoire autre que la racine, utilisez [tmpnam](tempnam-wtempnam-tmpnam-wtmpnam.md) ou [tempnam](tempnam-wtempnam-tmpnam-wtmpnam.md) en association avec [fopen](fopen-wfopen.md).

Si le fichier ne peut pas être ouvert, **tmpfile** retourne un **NULL** pointeur. Ce fichier temporaire est automatiquement supprimé quand le fichier est fermé lorsque le programme se termine normalement, ou lorsque **_rmtmp** est appelée, en supposant que le répertoire de travail en cours ne change pas. Le fichier temporaire est ouvert dans **w + b** mode (lecture/écriture binaire).

Échec peut se produire si vous essayez de plus de TMP_MAX (voir STDIO. H) appels avec **tmpfile**.

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**tmpfile**|\<stdio.h>|

Pour plus d’informations sur la compatibilité, voir consultez [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

> [!NOTE]
> L’exécution de cet exemple sur Windows Vista nécessite des privilèges d’administrateur.

```C
// crt_tmpfile.c
// compile with: /W3
// This program uses tmpfile to create a
// temporary file, then deletes this file with _rmtmp.
#include <stdio.h>

int main( void )
{
   FILE *stream;
   int  i;

   // Create temporary files.
   for( i = 1; i <= 3; i++ )
   {
      if( (stream = tmpfile()) == NULL ) // C4996
      // Note: tmpfile is deprecated; consider using tmpfile_s instead
         perror( "Could not open new temporary file\n" );
      else
         printf( "Temporary file %d was created\n", i );
   }

   // Remove temporary files.
   printf( "%d temporary files deleted\n", _rmtmp() );
}
```

```Output
Temporary file 1 was created
Temporary file 2 was created
Temporary file 3 was created
3 temporary files deleted
```

## <a name="see-also"></a>Voir aussi

[E/S de flux](../../c-runtime-library/stream-i-o.md)<br/>
[_rmtmp](rmtmp.md)<br/>
[_tempnam, _wtempnam, tmpnam, _wtmpnam](tempnam-wtempnam-tmpnam-wtmpnam.md)<br/>
