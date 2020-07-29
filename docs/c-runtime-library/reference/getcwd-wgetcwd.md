---
title: _getcwd, _wgetcwd
description: Les fonctions de la bibliothèque Runtime C _getcwd, _wgetcwd d’accéder au répertoire de travail actuel.
ms.date: 4/2/2020
api_name:
- _wgetcwd
- _getcwd
- _o__getcwd
- _o__wgetcwd
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
- api-ms-win-crt-environment-l1-1-0.dll
- api-ms-win-crt-stdio-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _getcwd
- wgetcwd
- _wgetcwd
- tgetcwd
- _tgetcwd
helpviewer_keywords:
- getcwd function
- working directory
- _wgetcwd function
- _getcwd function
- current working directory
- wgetcwd function
- directories [C++], current working
ms.assetid: 888dc8c6-5595-4071-be55-816b38e3e739
ms.openlocfilehash: b6fb32a593a969f93a934f251f38cd50960440b0
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87221885"
---
# <a name="_getcwd-_wgetcwd"></a>_getcwd, _wgetcwd

Obtient le répertoire de travail actuel.

## <a name="syntax"></a>Syntaxe

```C
char *_getcwd(
   char *buffer,
   int maxlen
);
wchar_t *_wgetcwd(
   wchar_t *buffer,
   int maxlen
);
```

### <a name="parameters"></a>Paramètres

*mémoire tampon*\
Emplacement de stockage pour le chemin.

*MaxLen*\
Longueur maximale du chemin d’accès en caractères : **`char`** pour **_getcwd** et **`wchar_t`** pour **_wgetcwd**.

## <a name="return-value"></a>Valeur de retour

Retourne un pointeur vers la *mémoire tampon*. Une valeur de retour **null** indique une erreur, et **errno** a la valeur **ENOMEM**, ce qui indique que la mémoire est insuffisante pour allouer *MaxLen* octets (quand un argument **null** est fourni comme *buffer*) ou à **ERANGE**, ce qui indique que le chemin d’accès dépasse les caractères *MaxLen* . Si *MaxLen* est inférieur ou égal à zéro, cette fonction appelle un gestionnaire de paramètres non valides, comme décrit dans [validation de paramètre](../../c-runtime-library/parameter-validation.md).

Pour plus d’informations sur ces codes de retour et les autres, consultez [_doserrno, errno, _sys_errlist et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Notes

La fonction **_getcwd** obtient le chemin d’accès complet du répertoire de travail actuel pour le lecteur par défaut et le stocke au niveau de la *mémoire tampon*. L’argument entier *MaxLen* spécifie la longueur maximale du chemin d’accès. Une erreur se produit si la longueur du chemin d’accès (y compris le caractère null de fin) dépasse *MaxLen*. L’argument de *mémoire tampon* peut avoir la **valeur null**; une mémoire tampon d’une taille d’au moins *MaxLen* (plus uniquement si nécessaire) est allouée automatiquement, à l’aide de **malloc**, pour stocker le chemin d’accès. Cette mémoire tampon peut être libérée ultérieurement en appelant **Free** et en lui passant le **_getcwd** valeur de retour (pointeur vers la mémoire tampon allouée).

**_getcwd** retourne une chaîne qui représente le chemin d’accès du répertoire de travail actuel. Si le répertoire de travail actuel est la racine, la chaîne se termine par une barre oblique inverse ( `\` ). Si le répertoire de travail actuel est un répertoire autre que la racine, la chaîne se termine par le nom du répertoire, et non pas par une barre oblique inverse.

**_wgetcwd** est une version à caractères larges de **_getcwd**; l’argument de *mémoire tampon* et la valeur de retour de **_wgetcwd** sont des chaînes à caractères larges. dans le cas contraire, **_wgetcwd** et **_getcwd** se comportent de la même façon.

Quand **_DEBUG** et **_CRTDBG_MAP_ALLOC** sont définis, les appels à **_getcwd** et **_wgetcwd** sont remplacés par des appels à **_getcwd_dbg** et **_wgetcwd_dbg** pour permettre le débogage des allocations de mémoire. Pour plus d’informations, consultez [_getcwd_dbg, _wgetcwd_dbg](getcwd-dbg-wgetcwd-dbg.md).

Par défaut, l’état global de cette fonction est limité à l’application. Pour modifier cette valeur, consultez [état global dans le CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine Tchar.h|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tgetcwd**|**_getcwd**|**_getcwd**|**_wgetcwd**|

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**_getcwd**|\<direct.h>|
|**_wgetcwd**|\<direct.h> ou \<wchar.h>|

Pour plus d’informations sur la compatibilité, consultez [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

```C
// crt_getcwd.c
// Compile with: cl /W4 crt_getcwd.c
// This program places the name of the current directory in the
// buffer array, then displays the name of the current directory
// on the screen. Passing NULL as the buffer forces getcwd to allocate
// memory for the path, which allows the code to support file paths
// longer than _MAX_PATH, which are supported by NTFS.

#include <direct.h> // _getcwd
#include <stdlib.h> // free, perror
#include <stdio.h>  // printf
#include <string.h> // strlen

int main( void )
{
   char* buffer;

   // Get the current working directory:
   if ( (buffer = _getcwd( NULL, 0 )) == NULL )
      perror( "_getcwd error" );
   else
   {
      printf( "%s \nLength: %zu\n", buffer, strlen(buffer) );
      free(buffer);
   }
}
```

```Output
C:\Code
```

## <a name="see-also"></a>Voir aussi

[Contrôle de répertoire](../../c-runtime-library/directory-control.md)\
[_chdir, _wchdir](chdir-wchdir.md)\
[_mkdir, _wmkdir](mkdir-wmkdir.md)\
[_rmdir, _wrmdir](rmdir-wrmdir.md)
