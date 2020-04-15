---
title: _chsize
ms.date: 4/2/2020
api_name:
- _chsize
- _o__chsize
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
- _chsize
helpviewer_keywords:
- size
- _chsize function
- size, changing file
- files [C++], changing size
- chsize function
ms.assetid: b3e881c5-7b27-4837-a3d4-c51591ab10ff
ms.openlocfilehash: bb2d72e40796a1dd2253361626042486490c77d9
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81350062"
---
# <a name="_chsize"></a>_chsize

Modifie la taille d’un fichier. Une version plus sécurisée est disponible. Consultez [_chsize_s](chsize-s.md).

## <a name="syntax"></a>Syntaxe

```C
int _chsize(
   int fd,
   long size
);
```

### <a name="parameters"></a>Paramètres

*Fd*<br/>
Descripteur de fichier qui fait référence à un fichier ouvert.

*Taille*<br/>
Nouvelle longueur, en octets, du fichier.

## <a name="return-value"></a>Valeur de retour

**_chsize** retourne la valeur 0 si la taille du fichier est modifiée avec succès. Une valeur de retour de -1 indique une erreur : **errno** est réglé sur **EACCES** si le fichier spécifié est lu uniquement ou si le fichier spécifié est verrouillé contre l’accès, à **EBADF** si le descripteur est invalide, **ENOSPC** si aucun espace n’est laissé sur l’appareil, ou **EINVAL** si la *taille* est inférieure à zéro.

Voir [_doserrno, errno, _sys_errlist, et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) pour plus d’informations sur ces codes de retour, et d’autres.

## <a name="remarks"></a>Notes

La fonction **_chsize** étend ou tronque le fichier associé à *fd* à la longueur spécifiée par *la taille*. Le fichier doit être ouvert dans un mode qui permet l’écriture. Des caractères Null (« \0 ») sont ajoutés si le fichier est étendu. Si le fichier est tronqué, toutes les données depuis la fin du fichier raccourci jusqu’à la longueur d’origine du fichier sont perdues.

Cette fonction valide ses paramètres. Si *la taille* est inférieure à zéro ou *fd* est un mauvais descripteur de fichier, le gestionnaire de paramètres invalides est invoqué, tel que décrit dans La validation de [paramètres](../../c-runtime-library/parameter-validation.md).

Par défaut, l’état global de cette fonction est étendue à l’application. Pour changer cela, voir [Global State dans le CRT](../global-state.md).

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|En-tête facultatif|
|-------------|---------------------|---------------------|
|**_chsize**|\<io.h>|\<errno.h>|

Pour plus d’informations sur la compatibilité, consultez [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

```C
// crt_chsize.c
// This program uses _filelength to report the size
// of a file before and after modifying it with _chsize.

#include <io.h>
#include <fcntl.h>
#include <sys/types.h>
#include <sys/stat.h>
#include <stdio.h>
#include <share.h>

int main( void )
{
   int fh, result;
   unsigned int nbytes = BUFSIZ;

   // Open a file
   if( _sopen_s( &fh, "data", _O_RDWR | _O_CREAT, _SH_DENYNO,
                 _S_IREAD | _S_IWRITE ) == 0 )
   {
      printf( "File length before: %ld\n", _filelength( fh ) );
      if( ( result = _chsize( fh, 329678 ) ) == 0 )
         printf( "Size successfully changed\n" );
      else
         printf( "Problem in changing the size\n" );
      printf( "File length after:  %ld\n", _filelength( fh ) );
      _close( fh );
   }
}
```

```Output
File length before: 0
Size successfully changed
File length after:  329678
```

## <a name="see-also"></a>Voir aussi

[Gestion de fichiers](../../c-runtime-library/file-handling.md)<br/>
[_close](close.md)<br/>
[_sopen, _wsopen](sopen-wsopen.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
