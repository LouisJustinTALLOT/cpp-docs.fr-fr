---
title: _makepath, _wmakepath | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _makepath
- _wmakepath
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
- _wmakepath
- _tmakepath
- makepath
- tmakepath
- wmakepath
- _makepath
dev_langs:
- C++
helpviewer_keywords:
- _makepath function
- wmakepath function
- makepath function
- _tmakepath function
- paths
- _wmakepath function
- tmakepath function
ms.assetid: 5930b197-a7b8-46eb-8519-2841a58cd026
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c339ce6ad67186dc7a4f43d7006c5beb047c8f90
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="makepath-wmakepath"></a>_makepath, _wmakepath

Créent un nom de chemin à partir des composants. Des versions plus sécurisées de ces fonctions sont disponibles ; consultez [_makepath_s, _wmakepath_s](makepath-s-wmakepath-s.md).

## <a name="syntax"></a>Syntaxe

```C
void _makepath(
   char *path,
   const char *drive,
   const char *dir,
   const char *fname,
   const char *ext
);
void _wmakepath(
   wchar_t *path,
   const wchar_t *drive,
   const wchar_t *dir,
   const wchar_t *fname,
   const wchar_t *ext
);
```

### <a name="parameters"></a>Paramètres

*chemin d’accès* mémoire tampon du chemin d’accès complet.

*lecteur* contient une lettre (A, B et ainsi de suite) correspondant au lecteur souhaité et un signe deux-points de fin facultatif. **_makepath** insère automatiquement le signe deux-points dans le chemin d’accès composite s’il est manquant. Si *lecteur* est **NULL** ou pointe vers une chaîne vide, aucune lettre de lecteur s’affiche dans la composition *chemin d’accès* chaîne.

*dir* contient le chemin d’accès des répertoires, sans l’indicateur de lecteur ou le nom de fichier réel. La barre oblique est facultative et une barre oblique (/) ou une barre oblique inverse (\\) ou les deux peuvent être utilisées dans un seul *dir* argument. Si aucune barre oblique finale (/ ou \\) n’est spécifiée, elle est insérée automatiquement. Si *dir* est **NULL** ou pointe vers une chaîne vide, aucun chemin d’accès du répertoire est inséré dans la composition *chemin d’accès* chaîne.

*fname* contient le nom de fichier de base sans les extensions de nom de fichier. Si *fname* est **NULL** ou pointe vers une chaîne vide, aucun nom de fichier est inséré dans la composition *chemin d’accès* chaîne.

*Ext* contient l’extension de nom de fichier réelle, avec ou sans point initial (.). **_makepath** insère automatiquement le point si elle n’apparaît pas dans *ext*. Si *ext* est **NULL** ou pointe vers une chaîne vide, aucune extension n’est inséré dans la composition *chemin d’accès* chaîne.

## <a name="remarks"></a>Notes

Le **_makepath** fonction crée une chaîne de chemin d’accès composite à partir de chaque composant, en stockant le résultat dans *chemin d’accès*. Le *chemin d’accès* peut inclure une lettre de lecteur, le chemin d’accès de répertoire, le nom de fichier et l’extension de nom de fichier. **_wmakepath** est une version à caractères larges de **_makepath**; les arguments de **_wmakepath** sont des chaînes à caractères larges. **_wmakepath** et **_makepath** comportent de façon identique.

**Remarque relative à la sécurité** Utilisez une chaîne se terminant par un caractère Null. Pour éviter les dépassements de mémoire tampon, la chaîne se terminant par null ne doit pas dépasser la taille de la *chemin d’accès* mémoire tampon. **_makepath** ne garantit pas que la longueur de la chaîne de chemin d’accès composite ne dépasse pas **_MAX_PATH**. Pour plus d’informations, consultez [Solutions contre les dépassements de mémoire tampon](http://msdn.microsoft.com/library/windows/desktop/ms717795).

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine Tchar.h|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tmakepath**|**_makepath**|**_makepath**|**_wmakepath**|

Le *chemin d’accès* argument doit pointer vers une mémoire tampon vide suffisamment grande pour contenir le chemin d’accès complet. Composite *chemin d’accès* doit pas être supérieur à la **_MAX_PATH** constante, définie dans Stdlib.h.

Si le chemin d’accès est **NULL**, le Gestionnaire de paramètre non valide est appelé, comme décrit dans [Validation de paramètre](../../c-runtime-library/parameter-validation.md). En outre, **errno** a la valeur **EINVAL**. **NULL** valeurs autorisées pour tous les autres paramètres.

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**_makepath**|\<stdlib.h>|
|**_wmakepath**|\<stdlib.h> ou \<wchar.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

```C
// crt_makepath.c
#include <stdlib.h>
#include <stdio.h>

int main( void )
{
   char path_buffer[_MAX_PATH];
   char drive[_MAX_DRIVE];
   char dir[_MAX_DIR];
   char fname[_MAX_FNAME];
   char ext[_MAX_EXT];

   _makepath( path_buffer, "c", "\\sample\\crt\\", "makepath", "c" ); // C4996
   // Note: _makepath is deprecated; consider using _makepath_s instead
   printf( "Path created with _makepath: %s\n\n", path_buffer );
   _splitpath( path_buffer, drive, dir, fname, ext ); // C4996
   // Note: _splitpath is deprecated; consider using _splitpath_s instead
   printf( "Path extracted with _splitpath:\n" );
   printf( "   Drive: %s\n", drive );
   printf( "   Dir: %s\n", dir );
   printf( "   Filename: %s\n", fname );
   printf( "   Ext: %s\n", ext );
}
```

```Output
Path created with _makepath: c:\sample\crt\makepath.c

Path extracted with _splitpath:
   Drive: c:
   Dir: \sample\crt\
   Filename: makepath
   Ext: .c
```

## <a name="see-also"></a>Voir aussi

[Gestion de fichiers](../../c-runtime-library/file-handling.md)<br/>
[_fullpath, _wfullpath](fullpath-wfullpath.md)<br/>
[_splitpath, _wsplitpath](splitpath-wsplitpath.md)<br/>
[_makepath_s, _wmakepath_s](makepath-s-wmakepath-s.md)<br/>
