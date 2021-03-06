---
description: 'En savoir plus sur : _locking'
title: _locking
ms.date: 4/2/2020
api_name:
- _locking
- _o__locking
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
- _locking
helpviewer_keywords:
- locking function
- bytes [C++], locking file
- files [C++], locking bytes
- files [C++], locking
- _locking function
ms.assetid: 099aaac1-d4ca-4827-aed6-24dff9844150
ms.openlocfilehash: 087fc65edbb30bdb6e36b7410f29cf165b119d38
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97198802"
---
# <a name="_locking"></a>_locking

Verrouille ou déverrouille les octets d’un fichier.

## <a name="syntax"></a>Syntaxe

```C
int _locking(
   int fd,
   int mode,
   long nbytes
);
```

### <a name="parameters"></a>Paramètres

*FD*<br/>
Descripteur de fichier.

*mode*<br/>
Action de verrouillage à exécuter.

*nbytes*<br/>
Nombre d’octets à verrouiller.

## <a name="return-value"></a>Valeur renvoyée

**_locking** retourne 0 en cas de réussite. Une valeur de retour de-1 indique un échec, auquel cas [errno](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) est défini sur l’une des valeurs suivantes.

|Valeur de la variable errno|Condition|
|-|-|
| **EACCES** | Violation de verrouillage (fichier déjà verrouillé ou déverrouillé). |
| **EBADF** | Descripteur de fichier non valide. |
| **EDEADLOCK** | Violation de verrouillage. Renvoyé lorsque l’indicateur **_LK_LOCK** ou **_LK_RLCK** est spécifié et que le fichier ne peut pas être verrouillé après 10 tentatives. |
| **EINVAL** | Un argument non valide a été fourni à **_locking**. |

Si l’échec est dû à un paramètre incorrect, tel qu’un descripteur de fichier non valide, le gestionnaire de paramètres non valides est appelé, comme décrit dans [Validation de paramètre](../../c-runtime-library/parameter-validation.md).

## <a name="remarks"></a>Notes

La fonction **_locking** verrouille ou déverrouille les octets *nbytes* du fichier spécifié par *FD*. Le verrouillage d’octets dans un fichier empêche l’accès à ces octets par d’autres processus. Tout verrouillage ou déverrouillage commence à la position actuelle du pointeur de fichier et se poursuit sur les *nbytes* octets suivants. Il est possible de verrouiller des octets au-delà de la fin du fichier.

*mode* doit être une des constantes manifestes suivantes, qui sont définies dans Locking.h.

|valeur du *mode*|Résultat|
|-|-|
| **_LK_LOCK** | Verrouille les octets spécifiés. Si les octets ne peuvent pas être verrouillés, le programme réessaie après 1 seconde. Si, après 10 tentatives, les octets ne peuvent pas être verrouillés, la constante retourne une erreur. |
| **_LK_NBLCK** | Verrouille les octets spécifiés. Si les octets ne peuvent pas être verrouillés, la constante retourne une erreur. |
| **_LK_NBRLCK** | Identique à **_LK_NBLCK**. |
| **_LK_RLCK** | Identique à **_LK_LOCK**. |
| **_LK_UNLCK** | Déverrouille les octets spécifiés, qui doivent avoir été verrouillés auparavant. |

Vous ne pouvez pas verrouiller plusieurs zones d’un fichier qui ne se chevauchent pas. Une zone ne peut être déverrouillée que si elle a été verrouillée. **_locking** ne fusionne pas les régions adjacentes ; Si deux régions verrouillées sont adjacentes, chaque région doit être déverrouillée séparément. Le verrouillage des zones doit être de courte durée et celles-ci doivent être déverrouillées avant de fermer un fichier ou de quitter le programme.

Par défaut, l’état global de cette fonction est limité à l’application. Pour modifier cette valeur, consultez [état global dans le CRT](../global-state.md).

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|En-tête facultatif|
|-------------|---------------------|---------------------|
|**_locking**|\<io.h> et \<sys/locking.h>|\<errno.h>|

Pour plus d’informations sur la compatibilité, consultez [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Bibliothèques

Toutes les versions des [bibliothèques Runtime C](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a>Exemple

```C
// crt_locking.c
/* This program opens a file with sharing. It locks
* some bytes before reading them, then unlocks them. Note that the
* program works correctly only if the file exists.
*/

#include <sys/types.h>
#include <sys/stat.h>
#include <sys/locking.h>
#include <share.h>
#include <fcntl.h>
#include <stdio.h>
#include <stdlib.h>
#include <io.h>

int main( void )
{
   int  fh, numread;
   char buffer[40];

   /* Quit if can't open file or system doesn't
    * support sharing.
    */
   errno_t err = _sopen_s( &fh, "crt_locking.txt", _O_RDONLY, _SH_DENYNO,
                          _S_IREAD | _S_IWRITE );
   printf( "%d %d\n", err, fh );
   if( err != 0 )
      exit( 1 );

   /* Lock some bytes and read them. Then unlock. */
   if( _locking( fh, LK_NBLCK, 30L ) != -1 )
   {
      long lseek_ret;
      printf( "No one can change these bytes while I'm reading them\n" );
      numread = _read( fh, buffer, 30 );
      buffer[30] = '\0';
      printf( "%d bytes read: %.30s\n", numread, buffer );
      lseek_ret = _lseek( fh, 0L, SEEK_SET );
      _locking( fh, LK_UNLCK, 30L );
      printf( "Now I'm done. Do what you will with them\n" );
   }
   else
      perror( "Locking failed\n" );

   _close( fh );
}
```

### <a name="input-crt_lockingtxt"></a>Entrée : crt_locking.txt

```Input
The first thirty bytes of this file will be locked.
```

## <a name="sample-output"></a>Exemple de sortie

```Output
No one can change these bytes while I'm reading them
30 bytes read: The first thirty bytes of this
Now I'm done. Do what you will with them
```

## <a name="see-also"></a>Voir aussi

[Gestion de fichiers](../../c-runtime-library/file-handling.md)<br/>
[_creat, _wcreat](creat-wcreat.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
