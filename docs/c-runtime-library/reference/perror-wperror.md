---
title: perror, _wperror
ms.date: 4/2/2020
api_name:
- _wperror
- perror
- _o__wperror
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
- api-ms-win-crt-runtime-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _wperror
- _tperror
- perror
helpviewer_keywords:
- _tperror function
- tperror function
- wperror function
- error messages, printing
- printing error messages
- _wperror function
- perror function
ms.assetid: 34fce792-16fd-4673-9849-cd88b54b6cd5
ms.openlocfilehash: 0c50e77863b4b136ac59b6f79d8e529691032609
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81338536"
---
# <a name="perror-_wperror"></a>perror, _wperror

Imprime un message d’erreur.

## <a name="syntax"></a>Syntaxe

```C
void perror(
   const char *message
);
void _wperror(
   const wchar_t *message
);
```

### <a name="parameters"></a>Paramètres

*Message*<br/>
Message de type chaîne à imprimer.

## <a name="remarks"></a>Notes

La fonction **perror** imprime un message d’erreur à **stderr**. **_wperror** est une version à caractère large de **_perror**; l’argument du *message* à **_wperror** est une chaîne de caractère large. **_wperror** et **_perror** se comportent de façon identique autrement.

Par défaut, l’état global de cette fonction est étendue à l’application. Pour changer cela, voir [Global State dans le CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine TCHAR.H|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tperror**|**perror**|**perror**|**_wperror**|

*message* est imprimé d’abord, suivi d’un côlon, puis par le message d’erreur du système pour le dernier appel de bibliothèque qui a produit l’erreur, et enfin par un caractère newline. Si *le message* est un pointeur nul ou un pointeur à une corde nulle, **perror** imprime uniquement le message d’erreur du système.

Le numéro d’erreur est stocké dans la variable [errno](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) (définie dans ERRNO.H). Les messages d’erreur système sont accessibles via la variable [_sys_errlist](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md), qui est un tableau de messages classés par numéro d’erreur. **perror** imprime le message d’erreur approprié en utilisant la valeur **errno** comme un index pour **_sys_errlist**. La valeur de la [_sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) variable est définie comme le nombre maximal d’éléments dans le **tableau _sys_errlist.**

Pour obtenir des résultats précis, appelez **perror** immédiatement après qu’une routine de bibliothèque revient avec une erreur. Sinon, les appels ultérieurs peuvent dépasser la valeur **errno.**

Dans le système d’exploitation Windows, certaines valeurs **errno** énumérées dans ERRNO. H sont inutilisés. Ces valeurs sont réservées au système d’exploitation UNIX. Voir [_doserrno, errno, _sys_errlist, et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) pour une liste des valeurs **errno** utilisés par le système d’exploitation Windows. **perror** imprime une chaîne vide pour toute valeur **errno** non utilisée par ces plates-formes.

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**perror**|\<stdio.h > ou \<stdlib.h >|
|**_wperror**|\<stdio.h> ou \<wchar.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Bibliothèques

Toutes les versions des [bibliothèques Runtime C](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a>Exemple

```C
// crt_perror.c
// compile with: /W3
/* This program attempts to open a file named
* NOSUCHF.ILE. Because this file probably doesn't exist,
* an error message is displayed. The same message is
* created using perror, strerror, and _strerror.
*/

#include <fcntl.h>
#include <sys/types.h>
#include <sys/stat.h>
#include <io.h>
#include <stdlib.h>
#include <stdio.h>
#include <string.h>
#include <share.h>

int main( void )
{
   int  fh;

   if( _sopen_s( &fh, "NOSUCHF.ILE", _O_RDONLY, _SH_DENYNO, 0 ) != 0 )
   {
      /* Three ways to create error message: */
      perror( "perror says open failed" );
      printf( "strerror says open failed: %s\n",
         strerror( errno ) ); // C4996
      printf( _strerror( "_strerror says open failed" ) ); // C4996
      // Note: strerror and _strerror are deprecated; consider
      // using strerror_s and _strerror_s instead.
   }
   else
   {
      printf( "open succeeded on input file\n" );
      _close( fh );
   }
}
```

```Output
perror says open failed: No such file or directory
strerror says open failed: No such file or directory
_strerror says open failed: No such file or directory
```

## <a name="see-also"></a>Voir aussi

[Contrôle des processus et de l’environnement](../../c-runtime-library/process-and-environment-control.md)<br/>
[clearerr](clearerr.md)<br/>
[ferror](ferror.md)<br/>
[strerror, _strerror, _wcserror, \__wcserror](strerror-strerror-wcserror-wcserror.md)<br/>
