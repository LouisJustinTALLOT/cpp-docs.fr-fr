---
title: _unlink, _wunlink
ms.date: 11/04/2016
apiname:
- _unlink
- _wunlink
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
- api-ms-win-crt-filesystem-l1-1-0.dll
apitype: DLLExport
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
ms.openlocfilehash: ec59a02f1302fe4a2149889cf1b48090d061d6b2
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62268770"
---
# <a name="unlink-wunlink"></a>_unlink, _wunlink

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

Chacune de ces fonctions retourne 0 en cas d’échec. Sinon, la fonction retourne -1 et définit **errno** à **EACCES**, ce qui signifie que le chemin d’accès spécifie un fichier en lecture seule ou un répertoire, ou la valeur **ENOENT**, ce qui signifie que le fichier ou le chemin d’accès est introuvable.

Pour plus d’informations sur ces codes de retour et les autres, consultez [_doserrno, errno, _sys_errlist et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Notes

Le **_unlink** fonction supprime le fichier spécifié par *filename*. **_wunlink** est une version à caractères larges de **_unlink**; le *filename* l’argument de **_wunlink** est une chaîne de caractères larges. Ces fonctions se comportent sinon de façon identique.

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

### <a name="input-crtunlinktxt"></a>Entrée : crt_unlink.txt

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
