---
title: perror, _wperror
ms.date: 11/04/2016
apiname:
- _wperror
- perror
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
- api-ms-win-crt-runtime-l1-1-0.dll
apitype: DLLExport
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
ms.openlocfilehash: c9026a96ecc74640eb2bcd7004d5d1e0fc287e38
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50474475"
---
# <a name="perror-wperror"></a>perror, _wperror

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

*message*<br/>
Message de type chaîne à imprimer.

## <a name="remarks"></a>Notes

Le **perror** fonction imprime un message d’erreur à **stderr**. **_wperror** est une version à caractères larges de **_perror**; le *message* l’argument de **_wperror** est une chaîne de caractères larges. **_wperror** et **_perror** se comportent de façon identique dans le cas contraire.

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine TCHAR.H|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tperror**|**perror**|**perror**|**_wperror**|

*message* est imprimé en premier, suivi par un signe deux-points, puis par le message d’erreur système pour le dernier appel de bibliothèque qui a généré l’erreur et enfin par un caractère de saut de ligne. Si *message* est un pointeur null ou un pointeur vers une chaîne null, **perror** imprime uniquement le message d’erreur système.

Le numéro d’erreur est stocké dans la variable [errno](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) (définie dans ERRNO.H). Les messages d’erreur système sont accessibles via la variable [_sys_errlist](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md), qui est un tableau de messages classés par numéro d’erreur. **pError** imprime le message d’erreur approprié à l’aide du **errno** valeur en tant qu’index pour **_sys_errlist**. La valeur de la variable [_sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) est défini comme le nombre maximal d’éléments dans le **_sys_errlist** tableau.

Pour obtenir des résultats précis, appelez **perror** immédiatement après le retour de la routine de bibliothèque avec une erreur. Dans le cas contraire, les appels suivants peuvent remplacer la **errno** valeur.

Dans le Windows système d’exploitation, certaines **errno** valeurs répertoriées dans ERRNO. H sont inutilisés. Ces valeurs sont réservées au système d’exploitation UNIX. Consultez [_doserrno, errno, _sys_errlist et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) pour obtenir la liste de **errno** valeurs utilisées par le système d’exploitation Windows. **pError** imprime une chaîne vide pour toute **errno** valeur non utilisée par ces plateformes.

## <a name="requirements"></a>Configuration requise

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

[Contrôle de processus et d’environnement](../../c-runtime-library/process-and-environment-control.md)<br/>
[clearerr](clearerr.md)<br/>
[ferror](ferror.md)<br/>
[strerror, _strerror, _wcserror, \__wcserror](strerror-strerror-wcserror-wcserror.md)<br/>
