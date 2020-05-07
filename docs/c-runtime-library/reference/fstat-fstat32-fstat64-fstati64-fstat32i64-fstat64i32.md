---
title: _fstat, _fstat32, _fstat64, _fstati64, _fstat32i64, _fstat64i32
ms.date: 4/2/2020
api_name:
- _fstat32
- _fstat64
- _fstati64
- _fstat
- _fstat64i32
- _fstat32i64
- _o__fstat32
- _o__fstat32i64
- _o__fstat64
- _o__fstat64i32
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
- api-ms-win-crt-filesystem-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _fstat32i64
- fstat
- fstat64i32
- _fstat64
- _fstati64
- fstat64
- _fstat32
- fstat32i64
- fstati64
- _fstat
- fstat32
- _fstat64i32
helpviewer_keywords:
- _fstat64 function
- fstati64 function
- _fstat64i32 function
- _fstat32i64 function
- _fstat32 function
- file information
- fstat64i32 function
- fstat32 function
- fstat function
- fstat64 function
- _fstat function
- _fstati64 function
- fstat32i64 function
ms.assetid: 088f5e7a-9636-4cf7-ab8e-e28d2aa4280a
ms.openlocfilehash: 81c272187c681010e7b8560d43f2fad87e1e0fdc
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2020
ms.locfileid: "82910121"
---
# <a name="_fstat-_fstat32-_fstat64-_fstati64-_fstat32i64-_fstat64i32"></a>_fstat, _fstat32, _fstat64, _fstati64, _fstat32i64, _fstat64i32

Obtient des informations sur un fichier ouvert.

## <a name="syntax"></a>Syntaxe

```C
int _fstat(
   int fd,
   struct _stat *buffer
);
int _fstat32(
   int fd,
   struct __stat32 *buffer
);
int _fstat64(
   int fd,
   struct __stat64 *buffer
);
int _fstati64(
   int fd,
   struct _stati64 *buffer
);
int _fstat32i64(
   int fd,
   struct _stat32i64 *buffer
);
int _fstat64i32(
   int fd,
   struct _stat64i32 *buffer
);
```

### <a name="parameters"></a>Paramètres

*FD*<br/>
Descripteur du fichier ouvert.

*buffer*<br/>
Pointeur désignant la structure destinée à stocker les résultats.

## <a name="return-value"></a>Valeur de retour

Retourne 0 si les informations sur l’état des fichiers sont obtenues. Une valeur de retour de-1 indique une erreur. Si le descripteur de fichier n’est pas valide ou si la *mémoire tampon* est **null**, le gestionnaire de paramètre non valide est appelé, comme décrit dans [validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, **errno** a la valeur **EBADF**, dans le cas d’un descripteur de fichier non valide, ou à **EINVAL**, si *buffer* a la **valeur null**.

## <a name="remarks"></a>Notes 

La fonction **_fstat** obtient des informations sur le fichier ouvert associé à *FD* et les stocke dans la structure vers laquelle pointe la *mémoire tampon*. La structure **_stat** , définie dans SYS\Stat.h, contient les champs suivants.

|Champ|Signification|
|-|-|
| **st_atime** | Heure du dernier accès au fichier. |
| **st_ctime** | Heure de la création du fichier. |
| **st_dev** | Si un périphérique, *FD*; Sinon, 0. |
| **st_mode** | Masque de bits pour les informations relatives au mode de fichier. Le bit de **_S_IFCHR** est défini si *FD* fait référence à un appareil. Le bit de **_S_IFREG** est défini si *FD* fait référence à un fichier ordinaire. Les bits de lecture/écriture sont définis en fonction du mode d’autorisation du fichier. **_S_IFCHR** et d’autres constantes sont définies dans SYS\Stat.h. |
| **st_mtime** | Heure de la dernière modification du fichier. |
| **st_nlink** | Toujours 1 sur les systèmes de fichiers autres que NTFS. |
| **st_rdev** | Si un périphérique, *FD*; Sinon, 0. |
| **st_size** | Taille du fichier en octets. |

Si *FD* fait référence à un périphérique, les champs **st_atime**, **st_ctime**, **st_mtime**et **st_size** ne sont pas significatifs.

Étant donné que Stat.h utilise le type [_dev_t](../../c-runtime-library/standard-types.md), qui est défini dans Types.h, vous devez inclure Types.h avant Stat.h dans votre code.

**_fstat64**, qui utilise la structure **__stat64** , permet d’exprimer les dates de création de fichiers 23:59:59 jusqu’au 31 décembre 3000, UTC ; tandis que les autres fonctions représentent uniquement les dates jusqu’au 18 janvier 2038 à 23:59:59, heure UTC. Le 1er janvier 1970 à minuit est la limite inférieure de la plage de dates pour toutes ces fonctions.

Les variantes de ces fonctions prennent en charge les types d’heures 32 bits ou 64 bits, ainsi que les longueurs de fichiers 32 bits ou 64 bits. Le premier suffixe numérique (**32** ou **64**) indique la taille du type d’heure utilisé ; le deuxième suffixe est soit **i32** , soit **I64**, indiquant si la taille du fichier est représentée sous la forme d’un entier 32 bits ou 64 bits.

**_fstat** équivaut à **_fstat64i32**et **struct** **_stat** contient une heure de 64 bits. Cela est vrai, sauf si **_USE_32BIT_TIME_T** est défini, auquel cas l’ancien comportement est appliqué. **_fstat** utilise une heure de 32 bits, et **struct** **_stat** contient une heure de 32 bits. Il en va de même pour **_fstati64**.

Par défaut, l’état global de cette fonction est limité à l’application. Pour modifier cette valeur, consultez [état global dans le CRT](../global-state.md).

### <a name="time-type-and-file-length-type-variations-of-_stat"></a>Variantes de type d’heure et de type de longueur de fichier de _stat

|Fonctions|_USE_32BIT_TIME_T défini ?|Type d’heure|Type de longueur de fichier|
|---------------|------------------------------------|---------------|----------------------|
|**_fstat**|Non défini|64 bits|32 bits|
|**_fstat**|Défini|32 bits|32 bits|
|**_fstat32**|Non affecté par la définition de macro|32 bits|32 bits|
|**_fstat64**|Non affecté par la définition de macro|64 bits|64 bits|
|**_fstati64**|Non défini|64 bits|64 bits|
|**_fstati64**|Défini|32 bits|64 bits|
|**_fstat32i64**|Non affecté par la définition de macro|32 bits|64 bits|
|**_fstat64i32**|Non affecté par la définition de macro|64 bits|32 bits|

## <a name="requirements"></a>Spécifications

|Function|En-tête requis|
|--------------|---------------------|
|**_fstat**|\<sys/stat.h> et \<sys/types.h>|
|**_fstat32**|\<sys/stat.h> et \<sys/types.h>|
|**_fstat64**|\<sys/stat.h> et \<sys/types.h>|
|**_fstati64**|\<sys/stat.h> et \<sys/types.h>|
|**_fstat32i64**|\<sys/stat.h> et \<sys/types.h>|
|**_fstat64i32**|\<sys/stat.h> et \<sys/types.h>|

Pour plus d’informations sur la compatibilité, consultez [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

```C
// crt_fstat.c
// This program uses _fstat to report
// the size of a file named F_STAT.OUT.

#include <io.h>
#include <fcntl.h>
#include <time.h>
#include <sys/types.h>
#include <sys/stat.h>
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <errno.h>
#include <share.h>

int main( void )
{
   struct _stat buf;
   int fd, result;
   char buffer[] = "A line to output";
   char timebuf[26];
   errno_t err;

   _sopen_s( &fd,
             "f_stat.out",
             _O_CREAT | _O_WRONLY | _O_TRUNC,
             _SH_DENYNO,
             _S_IREAD | _S_IWRITE );
   if( fd != -1 )
      _write( fd, buffer, strlen( buffer ) );

   // Get data associated with "fd":
   result = _fstat( fd, &buf );

   // Check if statistics are valid:
   if( result != 0 )
   {
      if (errno == EBADF)
        printf( "Bad file descriptor.\n" );
      else if (errno == EINVAL)
        printf( "Invalid argument to _fstat.\n" );
   }
   else
   {
      printf( "File size     : %ld\n", buf.st_size );
      err = ctime_s(timebuf, 26, &buf.st_mtime);
      if (err)
      {
         printf("Invalid argument to ctime_s.");
         exit(1);
      }
      printf( "Time modified : %s", timebuf );
   }
   _close( fd );
}
```

```Output
File size     : 16
Time modified : Wed May 07 15:25:11 2003
```

## <a name="see-also"></a>Voir aussi

[Gestion de fichiers](../../c-runtime-library/file-handling.md)<br/>
[_access, _waccess](access-waccess.md)<br/>
[_chmod, _wchmod](chmod-wchmod.md)<br/>
[_filelength, _filelengthi64](filelength-filelengthi64.md)<br/>
[_stat, _wstat, fonctions](stat-functions.md)<br/>
