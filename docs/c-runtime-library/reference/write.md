---
description: 'En savoir plus sur : _write'
title: _write
ms.date: 4/2/2020
api_name:
- _write
- _o__write
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
- _write
helpviewer_keywords:
- _write function
- write function
- files [C++], writing to
ms.assetid: 7b868c33-766f-4e1a-95a7-e8d25f0604c4
ms.openlocfilehash: 15988f803b37f9ce128a49662c2311a4aa6ca8fd
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97117157"
---
# <a name="_write"></a>_write

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

*FD*<br/>
Descripteur de fichier pour le fichier dans lequel les données sont écrites.

*mémoire tampon*<br/>
Données à écrire.

*count*<br/>
Nombre d'octets.

## <a name="return-value"></a>Valeur renvoyée

En cas de réussite, **_Write** retourne le nombre d’octets écrits. Si l’espace réel restant sur le disque est inférieur à la taille de la mémoire tampon que la fonction essaie d’écrire sur le disque, **_Write** échoue et n’efface pas le contenu de la mémoire tampon sur le disque. Une valeur de retour de-1 indique une erreur. Si des paramètres non valides sont passés, cette fonction appelle le gestionnaire de paramètre non valide, comme décrit dans [Validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, la fonction retourne-1 et **errno** a la valeur de l’une des trois valeurs suivantes : **EBADF**, ce qui signifie que le descripteur de fichier n’est pas valide ou que le fichier n’est pas ouvert en écriture. **ENOSPC**, ce qui signifie que l’espace restant sur l’appareil est insuffisant pour l’opération ; ou **EINVAL**, ce qui signifie que la *mémoire tampon* était un pointeur null ou qu’un *nombre* impair d’octets était passé à être écrit dans un fichier en mode Unicode.

Pour plus d’informations sur ces codes de retour et les autres, consultez [errno, _doserrno, _sys_errlist et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

Si le fichier est ouvert en mode texte, chaque caractère de saut de ligne est remplacé par une paire retour chariot-saut de ligne dans la sortie. Le remplacement n’affecte pas la valeur de retour.

Lorsque le fichier est ouvert en mode de traduction Unicode, par exemple, si *FD* est ouvert à l’aide de **_open** ou **_sopen** et d’un paramètre de mode qui comprend **_O_WTEXT**, **_O_U16TEXT** ou **_O_U8TEXT**, ou s’il est ouvert à l’aide de **fopen** et d’un paramètre de mode qui inclut **CCS = Unicode**, **CCS = UTF-16LE** ou **CCS = utf-8**, ou si le mode est modifié en mode de traduction Unicode à l’aide de **_setmode**, la *mémoire tampon* est interprétée comme un pointeur vers un tableau de **`wchar_t`** qui contient des données **UTF-16** . Toute tentative d'écriture d'une quantité impaire d'octets dans ce mode provoque une erreur de validation de paramètre.

## <a name="remarks"></a>Notes

La fonction **_Write** écrit le *nombre* d’octets de la *mémoire tampon* dans le fichier associé à *FD*. L'opération d'écriture commence à la position actuelle du pointeur de fichier (le cas échéant) associé au fichier donné. Si le fichier est ouvert pour ajout, l'opération commence à la fin actuelle du fichier. Après l’opération d’écriture, le pointeur de fichier est augmenté du nombre d’octets écrits.

Lors de l’écriture dans des fichiers ouverts en mode texte, **_Write** traite un caractère Ctrl + Z comme la fin logique du fichier. Lors de l’écriture sur un appareil, **_Write** traite un caractère Ctrl + Z dans la mémoire tampon comme un terminateur de sortie.

Par défaut, l’état global de cette fonction est limité à l’application. Pour modifier cette valeur, consultez [état global dans le CRT](../global-state.md).

## <a name="requirements"></a>Spécifications

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
            // An unrelated error occurred
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

[E/s de bas niveau](../../c-runtime-library/low-level-i-o.md)<br/>
[fwrite](fwrite.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
[_read](read.md)<br/>
[_setmode](setmode.md)<br/>
