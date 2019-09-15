---
title: _unlink, _wunlink
ms.date: 11/04/2016
api_name:
- _unlink
- _wunlink
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
- api-ms-win-crt-filesystem-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _tunlink
- _unlink
- wunlink
- _wunlink
helpviewer_keywords:
- files [C++], deleting
- _wunlink function
- wunlink function
- unlink function
- _unlink function
- tunlink function
- files [C++], removing
- _tunlink function
ms.assetid: 5e4f5f1b-1e99-4391-9b18-9ac63c32fae8
ms.openlocfilehash: 878a1b4aa009bc8528dfac1908ed26c7e3b269ae
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70957390"
---
# <a name="_unlink-_wunlink"></a>_unlink, _wunlink

Suppriment un fichier.

## <a name="syntax"></a>Syntaxe

```C
int _unlink(
   const char *filename
);
int _wunlink(
   const wchar_t *filename
);
```

### <a name="parameters"></a>Paramètres

*filename*<br/>
Nom du fichier à supprimer.

## <a name="return-value"></a>Valeur de retour

Chacune de ces fonctions retourne 0 en cas d’échec. Dans le cas contraire, la fonction retourne-1 et définit **errno** à **EACCES**, ce qui signifie que le chemin d’accès spécifie un fichier en lecture seule ou un répertoire, ou à **ENOENT**, ce qui signifie que le fichier ou le chemin d’accès est introuvable.

Pour plus d’informations sur ces codes de retour et les autres, consultez [_doserrno, errno, _sys_errlist et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Notes

La fonction **_unlink** supprime le fichier spécifié par *filename*. **_wunlink** est une version à caractères larges de **_unlink**; l’argument *filename* de **_wunlink** est une chaîne de caractères larges. Ces fonctions se comportent sinon de façon identique.

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine TCHAR.H|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tunlink**|**_unlink**|**_unlink**|**_wunlink**|

## <a name="requirements"></a>Configuration requise

|Routine|En-tête requis|
|-------------|---------------------|
|**_unlink**|\<io.h> et \<stdio.h>|
|**_wunlink**|\<io.h> ou \<wchar.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="code-example"></a>Exemple de code

Ce programme utilise _unlink pour supprimer CRT_UNLINK.TXT.

```C
// crt_unlink.c

#include <stdio.h>

int main( void )
{
   if( _unlink( "crt_unlink.txt" ) == -1 )
      perror( "Could not delete 'CRT_UNLINK.TXT'" );
   else
      printf( "Deleted 'CRT_UNLINK.TXT'\n" );
}
```

### <a name="input-crt_unlinktxt"></a>Entrée : crt_unlink.txt

```Input
This file will be deleted.
```

### <a name="sample-output"></a>Résultat de l'exemple

```Output
Deleted 'CRT_UNLINK.TXT'
```

## <a name="see-also"></a>Voir aussi

[Gestion de fichiers](../../c-runtime-library/file-handling.md)<br/>
[_close](close.md)<br/>
[remove, _wremove](remove-wremove.md)<br/>
