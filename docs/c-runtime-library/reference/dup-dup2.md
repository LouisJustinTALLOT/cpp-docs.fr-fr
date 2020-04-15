---
title: _dup, _dup2
ms.date: 4/2/2020
api_name:
- _dup
- _dup2
- _o__dup
- _o__dup2
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
- _dup2
- _dup
helpviewer_keywords:
- _dup2 function
- dup function
- file handles [C++], duplicating
- file handles [C++], reassigning
- dup2 function
- _dup function
ms.assetid: 4d07e92c-0d76-4832-a770-dfec0e7a0cfa
ms.openlocfilehash: 239f857bb40c9609cb6f7ff373295a7a1f8523a9
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81348112"
---
# <a name="_dup-_dup2"></a>_dup, _dup2

Crée un deuxième descripteur de fichier pour un fichier ouvert (**_dup**), ou réaffecte un descripteur de fichier **(_dup2**).

## <a name="syntax"></a>Syntaxe

```C
int _dup( int fd );
int _dup2( int fd1, int fd2 );
```

### <a name="parameters"></a>Paramètres

*fd*, *fd1*<br/>
Descripteurs de fichier qui font référence à un fichier ouvert.

*fd2*<br/>
Un descripteur de fichier.

## <a name="return-value"></a>Valeur de retour

**_dup** renvoie un nouveau descripteur de fichiers. **_dup2 revient** 0 pour indiquer le succès. En cas d’erreur, chaque fonction renvoie -1 et définit **errno** à **EBADF** si le descripteur de fichier est invalide ou à **EMFILE** si aucun descripteur de fichier n’est disponible. En cas de descripteur de fichier non valide, la fonction appelle également le gestionnaire de paramètres non valides, comme décrit dans [Validation de paramètre](../../c-runtime-library/parameter-validation.md).

Pour plus d’informations sur ces codes de retour et les autres, consultez [_doserrno, errno, _sys_errlist et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Notes

Les fonctions **_dup** et **_dup2** associent un deuxième descripteur de fichiers à un fichier actuellement ouvert. Ces fonctions peuvent être utilisées pour associer un descripteur de fichier prédéfini, comme celui de **stdout**, avec un fichier différent. Les opérations sur le fichier peuvent être effectuées à l’aide de l’un des descripteurs de fichier. Le type d’accès autorisé pour le fichier n’est pas affecté par la création d’un descripteur. **_dup** renvoie le prochain descripteur de fichier disponible pour le fichier donné. **_dup2** forces *fd2* de se référer au même fichier que *fd1*. Si *fd2* est associé à un fichier ouvert au moment de l’appel, ce fichier est fermé.

Les **_dup** et **_dup2** acceptent les descripteurs de fichiers comme paramètres. Pour passer un`FILE *`flux ( ) à l’une ou l’autre de ces fonctions, utilisez [_fileno](fileno.md). La routine **fileno** renvoie le descripteur de fichier actuellement associé au flux donné. L’exemple suivant montre comment associer **stderr** (défini comme `FILE *` dans Stdio.h) avec un descripteur de fichier:

```C
int cstderr = _dup( _fileno( stderr ));
```

Par défaut, l’état global de cette fonction est étendue à l’application. Pour changer cela, voir [Global State dans le CRT](../global-state.md).

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**_dup**|\<io.h>|
|**_dup2**|\<io.h>|

La console n’est pas prise en charge dans les applications Universal Windows Platform (UWP). Les poignées de flux standard qui sont associées à la console, **stdin**, **stdout**, et **stderr**, doivent être redirigés avant que les fonctions C run-time peuvent les utiliser dans les applications UWP. Pour plus d’informations sur la compatibilité, consultez [Compatibility](../../c-runtime-library/compatibility.md).

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

[E/S niveau bas](../../c-runtime-library/low-level-i-o.md)<br/>
[_close](close.md)<br/>
[_creat, _wcreat](creat-wcreat.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
