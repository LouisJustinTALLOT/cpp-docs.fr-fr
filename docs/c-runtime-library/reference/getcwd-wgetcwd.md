---
title: _getcwd, _wgetcwd
ms.date: 11/04/2016
apiname:
- _wgetcwd
- _getcwd
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
- api-ms-win-crt-environment-l1-1-0.dll
- api-ms-win-crt-stdio-l1-1-0.dll
apitype: DLLExport
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
ms.openlocfilehash: 4c533f0e716cb9a13c152b9be3c46f60291118d9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62331790"
---
# <a name="getcwd-wgetcwd"></a>_getcwd, _wgetcwd

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

*buffer*<br/>
Emplacement de stockage pour le chemin.

*maxlen*<br/>
Longueur maximale du chemin en caractères : **char** pour **_getcwd** et **wchar_t** pour **_wgetcwd**.

## <a name="return-value"></a>Valeur de retour

Retourne un pointeur vers *tampon*. Un **NULL** valeur renvoyée indique une erreur, et **errno** prend la valeur **ENOMEM**, indiquant qu’il existe une mémoire insuffisante pour allouer *maxlen* octets (quand un **NULL** argument est fourni en tant que *tampon*), ou la valeur **ERANGE**, indiquant que le chemin d’accès est plus long que *maxlen*  caractères. Si *maxlen* est inférieure ou égale à zéro, cette fonction appelle un gestionnaire de paramètre non valide, comme décrit dans [Validation de paramètre](../../c-runtime-library/parameter-validation.md).

Pour plus d'informations sur ces codes de retour et autres, consultez [_doserrno, errno, _sys_errlist et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Notes

Le **_getcwd** fonction obtient le chemin complet du répertoire de travail actuel pour le lecteur par défaut et le stocke à *tampon*. L’argument entier *maxlen* spécifie la longueur maximale pour le chemin d’accès. Une erreur se produit si la longueur du chemin d’accès (y compris le caractère null de fin) dépasse *maxlen*. Le *tampon* argument peut être **NULL**; une mémoire tampon de taille d’au moins *maxlen* (plus seulement si nécessaire) est allouée automatiquement, à l’aide de **malloc**, pour stocker le chemin d’accès. Cette mémoire tampon ultérieurement peut être libéré en appelant **gratuit** et en lui passant le **_getcwd** retourner de valeur (un pointeur vers la mémoire tampon allouée).

**_getcwd** retourne une chaîne qui représente le chemin d’accès du répertoire de travail actuel. Si le répertoire de travail actuel est la racine, la chaîne se termine par une barre oblique inverse ( **\\** ). Si le répertoire de travail actuel est un répertoire autre que la racine, la chaîne se termine par le nom du répertoire, et non pas par une barre oblique inverse.

**_wgetcwd** est une version à caractères larges de **_getcwd**; le *tampon* argument et valeur de retour de **_wgetcwd** sont des chaînes à caractères larges. **_wgetcwd** et **_getcwd** se comportent de façon identique dans le cas contraire.

Lorsque **_DEBUG** et **_CRTDBG_MAP_ALLOC** sont définis, les appels à **_getcwd** et **_wgetcwd** sont remplacés par les appels à **_ getcwd_dbg** et **_wgetcwd_dbg** pour permettre le débogage des allocations de mémoire. Pour plus d’informations, consultez [_getcwd_dbg, _wgetcwd_dbg](getcwd-dbg-wgetcwd-dbg.md).

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine Tchar.h|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tgetcwd**|**_getcwd**|**_getcwd**|**_wgetcwd**|

## <a name="requirements"></a>Configuration requise

|Routine|En-tête requis|
|-------------|---------------------|
|**_getcwd**|\<direct.h>|
|**_wgetcwd**|\<direct.h> ou \<wchar.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

```C
// crt_getcwd.c
// This program places the name of the current directory in the
// buffer array, then displays the name of the current directory
// on the screen. Passing NULL as the buffer forces getcwd to allocate
// memory for the path, which allows the code to support file paths
// longer than _MAX_PATH, which are supported by NTFS.

#include <direct.h>
#include <stdlib.h>
#include <stdio.h>

int main( void )
{
   char* buffer;

   // Get the current working directory:
   if( (buffer = _getcwd( NULL, 0 )) == NULL )
      perror( "_getcwd error" );
   else
   {
      printf( "%s \nLength: %d\n", buffer, strnlen(buffer) );
      free(buffer);
   }
}
```

```Output
C:\Code
```

## <a name="see-also"></a>Voir aussi

[Contrôle de répertoire](../../c-runtime-library/directory-control.md)<br/>
[_chdir, _wchdir](chdir-wchdir.md)<br/>
[_mkdir, _wmkdir](mkdir-wmkdir.md)<br/>
[_rmdir, _wrmdir](rmdir-wrmdir.md)<br/>
