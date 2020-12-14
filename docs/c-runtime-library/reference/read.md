---
description: 'En savoir plus sur : _read'
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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: f814c912c9f5d5e2dc7897cb3a2dcc8099503314
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97274838"
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

*FD*<br/>
Descripteur de fichier faisant référence au fichier ouvert.

*mémoire tampon*<br/>
Emplacement de stockage des données.

*buffer_size*<br/>
Nombre maximal d’octets à lire.

## <a name="return-value"></a>Valeur renvoyée

**_read** retourne le nombre d’octets lus, qui peut être inférieur à *buffer_size* s’il y a moins de *buffer_size* octets dans le fichier, ou si le fichier a été ouvert en mode texte. En mode texte, chaque paire retour chariot-saut de ligne `\r\n` est remplacée par un caractère de saut de ligne unique `\n` . Seul le caractère de saut de ligne unique est compté dans la valeur de retour. Le remplacement n’a pas de conséquence sur le pointeur de fichier.

Si la fonction tente de lire à la fin du fichier, elle retourne 0. Si *FD* n’est pas valide, que le fichier n’est pas ouvert pour la lecture ou que le fichier est verrouillé, le gestionnaire de paramètres non valides est appelé, comme décrit dans [validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, la fonction retourne-1 et définit **errno** sur **EBADF**.

Si *buffer* a la **valeur null**, ou si *buffer_size*  >  **INT_MAX**, le gestionnaire de paramètre non valide est appelé. Si l’exécution est autorisée à se poursuivre, la fonction retourne-1 et **errno** a la valeur **EINVAL**.

Pour plus d’informations sur ce code de retour et sur les autres codes, consultez [_doserrno, errno, _sys_errlist et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Notes

La fonction **_read** lit un maximum de *buffer_size* octets dans la *mémoire tampon* à partir du fichier associé à *FD*. L’opération de lecture commence à la position actuelle du pointeur de fichier associé au fichier donné. À la fin de la l’opération de lecture, le pointeur de fichier pointe vers le caractère non lu suivant.

Si le fichier a été ouvert en mode texte, la lecture se termine lorsque **_read** rencontre un caractère Ctrl + Z, qui est traité comme un indicateur de fin de fichier. Utilisez [_lseek](lseek-lseeki64.md) pour effacer l’indicateur de fin de fichier.

Par défaut, l’état global de cette fonction est limité à l’application. Pour modifier cette valeur, consultez [état global dans le CRT](../global-state.md).

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

[E/s de bas niveau](../../c-runtime-library/low-level-i-o.md)<br/>
[_creat, _wcreat](creat-wcreat.md)<br/>
[fread](fread.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
[_write](write.md)<br/>
