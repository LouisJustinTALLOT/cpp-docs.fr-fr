---
title: _read
ms.date: 4/2/2020
api_name:
- _read
- _o__read
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
- _read
helpviewer_keywords:
- data [CRT]
- _read function
- read function
- data [C++], reading
- reading data [C++]
- files [C++], reading
ms.assetid: 2ce9c433-57ad-47fe-9ac1-4a7d4c883d30
ms.openlocfilehash: db3726b85bb4ba7c8e9a691bef3fb063ec5709c9
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81338134"
---
# <a name="_read"></a>_read

Lit les données d’un fichier.

## <a name="syntax"></a>Syntaxe

```C
int _read(
   int const fd,
   void * const buffer,
   unsigned const buffer_size
);
```

### <a name="parameters"></a>Paramètres

*Fd*<br/>
Descripteur de fichier faisant référence au fichier ouvert.

*buffer*<br/>
Emplacement de stockage des données.

*buffer_size*<br/>
Nombre maximum d’octets à lire.

## <a name="return-value"></a>Valeur de retour

**_read** renvoie le nombre d’octets lus, ce qui pourrait être inférieur *à buffer_size* s’il reste moins *de buffer_size* octets dans le fichier, ou si le fichier a été ouvert en mode texte. En mode texte, chaque paire `\r\n` d’alimentation de retour `\n`de transport est remplacée par un caractère d’alimentation en ligne unique. Seul le caractère d’alimentation en ligne unique est compté dans la valeur de retour. Le remplacement n’a pas de conséquence sur le pointeur de fichier.

Si la fonction tente de lire à la fin du fichier, elle retourne 0. Si *le fd* n’est pas valide, que le fichier n’est pas ouvert à la lecture ou que le fichier est verrouillé, le gestionnaire de paramètres invalide est invoqué, tel que décrit dans [La validation de paramètres](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, la fonction renvoie -1 et définit **errno** à **EBADF**.

Si *le tampon* est **NULL**, ou si *buffer_size* > **INT_MAX,** le gestionnaire de paramètres invalide est invoqué. Si l’exécution est autorisée à se poursuivre, la fonction renvoie -1 et **errno** est réglé à **EINVAL**.

Pour plus d’informations sur ce code de retour et sur les autres codes, consultez [_doserrno, errno, _sys_errlist et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Notes

La fonction **_read** lit un maximum de *buffer_size* octets dans le *tampon* du fichier associé à *fd*. L’opération de lecture commence à la position actuelle du pointeur de fichier associé au fichier donné. À la fin de la l’opération de lecture, le pointeur de fichier pointe vers le caractère non lu suivant.

Si le fichier a été ouvert en mode texte, la lecture se termine lorsque **_read** rencontre un personnage CTRL-Z, qui est traité comme un indicateur de fin de fichier. Utilisez [_lseek](lseek-lseeki64.md) pour effacer l’indicateur de fin de fichier.

Par défaut, l’état global de cette fonction est étendue à l’application. Pour changer cela, voir [Global State dans le CRT](../global-state.md).

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**_read**|\<io.h>|

Pour plus d’informations sur la compatibilité, consultez [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Bibliothèques

Toutes les versions des [bibliothèques Runtime C](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a>Exemple

```C
// crt_read.c
/* This program opens a file named crt_read.txt
* and tries to read 60,000 bytes from
* that file using _read. It then displays the
* actual number of bytes read.
*/

#include <fcntl.h>      /* Needed only for _O_RDWR definition */
#include <io.h>
#include <stdlib.h>
#include <stdio.h>
#include <share.h>

char buffer[60000];

int main( void )
{
   int fh, bytesread;
   unsigned int nbytes = 60000;

   /* Open file for input: */
   if ( _sopen_s( &fh, "crt_read.txt", _O_RDONLY, _SH_DENYNO, 0 ))
   {
      perror( "open failed on input file" );
      exit( 1 );
   }

   /* Read in input: */
   if (( bytesread = _read( fh, buffer, nbytes )) <= 0 )
      perror( "Problem reading file" );
   else
      printf( "Read %u bytes from file\n", bytesread );

   _close( fh );
}
```

### <a name="input-crt_readtxt"></a>Entrée : crt_read.txt

```Input
Line one.
Line two.
```

### <a name="output"></a>Output

```Output
Read 19 bytes from file
```

## <a name="see-also"></a>Voir aussi

[E/S niveau bas](../../c-runtime-library/low-level-i-o.md)<br/>
[_creat, _wcreat](creat-wcreat.md)<br/>
[fread](fread.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
[_write](write.md)<br/>
