---
title: _getcwd, _wgetcwd
description: C Runtime Library fonctionne _getcwd, _wgetcwd obtenir l’annuaire de travail actuel.
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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: bc19a416ebebeb901e8dbb435971e6d5f33e4067
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81344436"
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

*Tampon*\
Emplacement de stockage pour le chemin.

*maxlen (en)*\
Longueur maximale du chemin en caractères : **char** pour **_getcwd** et **wchar_t** pour **_wgetcwd.**

## <a name="return-value"></a>Valeur de retour

Retourne un pointeur à *tampon*. Une valeur **de** retour NULL indique une erreur, et **errno** est réglé soit à **ENOMEM**, ce qui indique qu’il n’y a pas suffisamment de mémoire pour allouer des octets *maxlen* (lorsqu’un argument **NULL** est donné comme *tampon*), ou à **ERANGE**, ce qui indique que le chemin est plus long que les caractères *maxlen.* Si *le maxlen* est inférieur ou égal à zéro, cette fonction invoque un gestionnaire de paramètres invalide, tel que décrit dans [La validation des paramètres](../../c-runtime-library/parameter-validation.md).

Pour plus d’informations sur ces codes de retour et les autres, consultez [_doserrno, errno, _sys_errlist et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Notes

La fonction **_getcwd** obtient le plein chemin de l’annuaire de travail actuel pour le lecteur par défaut et le stocke à *tampon*. L’argument *maxlen* integer spécifie la longueur maximale pour le chemin. Une erreur se produit si la longueur du chemin (y compris le caractère nul de fin) dépasse *maxlen*. L’argument *de la mémoire tampon* peut être **NULL**; un tampon d’au moins taille *maxlen* (plus seulement si nécessaire) est automatiquement alloué, en utilisant **malloc**, pour stocker le chemin. Ce tampon peut plus tard être libéré en appelant **libre** et en le passant la valeur de retour **_getcwd** (un pointeur sur le tampon alloué).

**_getcwd** retourne une chaîne qui représente le parcours de l’actuel répertoire de travail. Si le répertoire de travail actuel est la racine,`\`la chaîne se termine par un backslash ( ). Si le répertoire de travail actuel est un répertoire autre que la racine, la chaîne se termine par le nom du répertoire, et non pas par une barre oblique inverse.

**_wgetcwd** est une version à caractère large de **_getcwd**; l’argument *tampon* et la valeur de retour de **_wgetcwd** sont des chaînes de caractère large. **_wgetcwd** et **_getcwd** se comportent de façon identique autrement.

Lorsque **_DEBUG** et **_CRTDBG_MAP_ALLOC** sont définis, les appels à **_getcwd** et **_wgetcwd** sont remplacés par des appels à **_getcwd_dbg** et **_wgetcwd_dbg** pour permettre de débogage des allocations de mémoire. Pour plus d’informations, consultez [_getcwd_dbg, _wgetcwd_dbg](getcwd-dbg-wgetcwd-dbg.md).

Par défaut, l’état global de cette fonction est étendue à l’application. Pour changer cela, voir [Global State dans le CRT](../global-state.md).

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

[Contrôle de l’annuaire](../../c-runtime-library/directory-control.md)\
[_chdir, _wchdir](chdir-wchdir.md)\
[_mkdir, _wmkdir](mkdir-wmkdir.md)\
[_rmdir, _wrmdir](rmdir-wrmdir.md)
