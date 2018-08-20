---
title: _dup, _dup2 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _dup
- _dup2
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
- _dup2
- _dup
dev_langs:
- C++
helpviewer_keywords:
- _dup2 function
- dup function
- file handles [C++], duplicating
- file handles [C++], reassigning
- dup2 function
- _dup function
ms.assetid: 4d07e92c-0d76-4832-a770-dfec0e7a0cfa
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ad477dc09ce6c8bee2d69e479f8e1615639cb14d
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32399801"
---
# <a name="dup-dup2"></a>_dup, _dup2

Crée un second descripteur de fichier pour un fichier ouvert (**_dup**), ou réaffecte un descripteur de fichier (**_dup2**).

## <a name="syntax"></a>Syntaxe

```C
int _dup( int fd );
int _dup2( int fd1, int fd2 );
```

### <a name="parameters"></a>Paramètres

*FD*, *fd1*<br/>
Descripteurs de fichier qui font référence à un fichier ouvert.

*FD2 Répartiteurs*<br/>
Un descripteur de fichier.

## <a name="return-value"></a>Valeur de retour

**_dup** retourne un nouveau descripteur de fichier. **_dup2** renvoie la valeur 0 pour indiquer une réussite. Si une erreur se produit, chaque fonction retourne -1 et les jeux de **errno** à **EBADF** si le descripteur de fichier n’est pas valide ou à **EMFILE** si plus aucun descripteur de fichier n’est disponibles. En cas de descripteur de fichier non valide, la fonction appelle également le gestionnaire de paramètres non valides, comme décrit dans [Validation de paramètre](../../c-runtime-library/parameter-validation.md).

Pour plus d'informations sur ces codes de retour et autres, consultez [_doserrno, errno, _sys_errlist et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Notes

Le **_dup** et **_dup2** fonctions associer un second descripteur de fichier à un fichier ouvert. Ces fonctions peuvent être utilisées pour associer un descripteur de fichier prédéfinie, telle que celle pour **stdout**, avec un autre fichier. Les opérations sur le fichier peuvent être effectuées à l’aide de l’un des descripteurs de fichier. Le type d’accès autorisé pour le fichier n’est pas affecté par la création d’un descripteur. **_dup** retourne le descripteur de fichier disponible suivant pour le fichier donné. **_dup2** force *FD2 Répartiteurs* pour faire référence au même fichier en tant que *fd1*. Si *FD2 Répartiteurs* est associé avec un fichier ouvert au moment de l’appel, ce fichier est fermé.

Les deux **_dup** et **_dup2** accepter des descripteurs de fichiers en tant que paramètres. Pour passer d’un flux de données (**fichier \*** ) sur l’une de ces fonctions, utilisez [_fileno](fileno.md). Le **fileno** routine retourne le descripteur de fichier actuellement associé au flux donné. L’exemple suivant montre comment associer **stderr** (défini comme **fichier \***  dans Stdio.h) avec un descripteur de fichier :

```C
int cstderr = _dup( _fileno( stderr ));
```

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**_dup**|\<io.h>|
|**_dup2**|\<io.h>|

La console n’est pas pris en charge dans les applications de plateforme Windows universelle (UWP). Les descripteurs de flux standard qui sont associés à la console, **stdin**, **stdout**, et **stderr**, doivent être redirigés avant que les fonctions d’exécution C de les utiliser dans les applications UWP . Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

```C
// crt_dup.c
// This program uses the variable old to save
// the original stdout. It then opens a new file named
// DataFile and forces stdout to refer to it. Finally, it
// restores stdout to its original state.

#include <io.h>
#include <stdlib.h>
#include <stdio.h>

int main( void )
{
   int old;
   FILE *DataFile;

   old = _dup( 1 );   // "old" now refers to "stdout"
                      // Note:  file descriptor 1 == "stdout"
   if( old == -1 )
   {
      perror( "_dup( 1 ) failure" );
      exit( 1 );
   }
   _write( old, "This goes to stdout first\n", 26 );
   if( fopen_s( &DataFile, "data", "w" ) != 0 )
   {
      puts( "Can't open file 'data'\n" );
      exit( 1 );
   }

   // stdout now refers to file "data"
   if( -1 == _dup2( _fileno( DataFile ), 1 ) )
   {
      perror( "Can't _dup2 stdout" );
      exit( 1 );
   }
   puts( "This goes to file 'data'\n" );

   // Flush stdout stream buffer so it goes to correct file
   fflush( stdout );
   fclose( DataFile );

   // Restore original stdout
   _dup2( old, 1 );
   puts( "This goes to stdout\n" );
   puts( "The file 'data' contains:" );
   _flushall();
   system( "type data" );
}
```

```Output
This goes to stdout first
This goes to stdout

The file 'data' contains:
This goes to file 'data'
```

## <a name="see-also"></a>Voir aussi

[E/S de bas niveau](../../c-runtime-library/low-level-i-o.md)<br/>
[_close](close.md)<br/>
[_creat, _wcreat](creat-wcreat.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
