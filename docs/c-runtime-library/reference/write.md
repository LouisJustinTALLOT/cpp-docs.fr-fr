---
title: _write | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _write
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
- _write
dev_langs:
- C++
helpviewer_keywords:
- _write function
- write function
- files [C++], writing to
ms.assetid: 7b868c33-766f-4e1a-95a7-e8d25f0604c4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 917309717d72048650d2b3975fefd74a1db50949
ms.sourcegitcommit: e9ce38decc9f986edab5543de3464b11ebccb123
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/13/2018
ms.locfileid: "42572722"
---
# <a name="write"></a>_write

Écrit des données dans un fichier.

## <a name="syntax"></a>Syntaxe

```C
int _write(
   int fd,
   const void *buffer,
   unsigned int count
);
```

### <a name="parameters"></a>Paramètres

*fd*<br/>
Descripteur de fichier pour le fichier dans lequel les données sont écrites.

*buffer*<br/>
Données à écrire.

*count*<br/>
Nombre d'octets.

## <a name="return-value"></a>Valeur de retour

En cas de réussite, **_write** retourne le nombre d’octets réellement écrits. Si l’espace effectif restant sur le disque est inférieure à la taille de la mémoire tampon de la fonction tente d’écrire sur le disque, **_write** échoue et ne pas vidé du contenu de la mémoire tampon sur le disque. Une valeur de retour de -1 indique une erreur. Si des paramètres non valides sont passés, cette fonction appelle le gestionnaire de paramètre non valide, comme décrit dans [Validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, la fonction retourne -1 et **errno** est défini sur une des trois valeurs : **EBADF**, ce qui signifie que le descripteur de fichier n’est pas valide ou le fichier n’est pas ouvert pour écriture ; **ENOSPC**, ce qui signifie que ne comporte pas suffisamment d’espace disponible sur le périphérique de l’opération ; ou **EINVAL**, ce qui signifie que *tampon* était un pointeur null ou qui irrégulière. *nombre* d’octets a été passé à écrire dans un fichier en mode Unicode.

Pour plus d’informations sur ces codes de retour et les autres, consultez [errno, _doserrno, _sys_errlist et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

Si le fichier est ouvert en mode texte, chaque caractère de saut de ligne est remplacé par un retour chariot - paire de saut de ligne dans la sortie. Le remplacement n'a pas de conséquence sur la valeur de retour.

Quand le fichier est ouvert en mode de traduction Unicode, par exemple, si *fd* est ouvert en utilisant **_open** ou **_sopen** et un paramètre de mode qui inclut **_O_ WTEXT**, **_O_U16TEXT**, ou **_O_U8TEXT**, ou s’il est ouvert à l’aide de **fopen** et un paramètre de mode qui inclut **ccs = UNICODE**, **ccs = UTF-16LE**, ou **ccs = UTF-8**, ou si le mode est modifié pour un mode de traduction Unicode à l’aide de **_setmode**:*tampon* est interprété comme un pointeur vers un tableau de **wchar_t** contenant **UTF-16** données. Toute tentative d’écriture d’une quantité impaire d’octets dans ce mode provoque une erreur de validation de paramètre.

## <a name="remarks"></a>Notes

Le **_write** fonction écritures *nombre* octets à partir de *tampon* dans le fichier associé *fd*. L'opération d'écriture commence à la position actuelle du pointeur de fichier (le cas échéant) associé au fichier donné. Si le fichier est ouvert pour ajout, l'opération commence à la fin actuelle du fichier. Après l'opération d'écriture, le pointeur de fichier est augmenté du nombre d'octets réellement écrits.

Lors de l’écriture de fichiers ouverts en mode texte, **_write** traite un caractère CTRL + Z comme la fin du fichier logique. Lors de l’écriture sur un appareil, **_write** traite un caractère CTRL + Z dans la mémoire tampon comme un terminateur de sortie.

## <a name="requirements"></a>Configuration requise

|Routine|En-tête requis|
|-------------|---------------------|
|**_write**|\<io.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

```C
// crt__write.c
//
// This program opens a file for output and uses _write to write
// some bytes to the file.

#include <io.h>
#include <stdio.h>
#include <stdlib.h>
#include <fcntl.h>
#include <sys/types.h>
#include <sys/stat.h>
#include <errno.h>
#include <share.h>

char buffer[] = "This is a test of '_write' function";

int main( void )
{
   int         fileHandle = 0;
   unsigned    bytesWritten = 0;

   if ( _sopen_s(&fileHandle, "write.o", _O_RDWR | _O_CREAT,
                  _SH_DENYNO, _S_IREAD | _S_IWRITE) )
      return -1;

   if (( bytesWritten = _write( fileHandle, buffer, sizeof( buffer ))) == -1 )
   {
      switch(errno)
      {
         case EBADF:
            perror("Bad file descriptor!");
            break;
         case ENOSPC:
            perror("No space left on device!");
            break;
         case EINVAL:
            perror("Invalid parameter: buffer was NULL!");
            break;
         default:
            // An unrelated error occured
            perror("Unexpected error!");
      }
   }
   else
   {
      printf_s( "Wrote %u bytes to file.\n", bytesWritten );
   }
   _close( fileHandle );
}
```

```Output
Wrote 36 bytes to file.
```

## <a name="see-also"></a>Voir aussi

[E/S de bas niveau](../../c-runtime-library/low-level-i-o.md)<br/>
[fwrite](fwrite.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
[_read](read.md)<br/>
[_setmode](setmode.md)<br/>
