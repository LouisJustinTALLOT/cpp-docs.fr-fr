---
title: _makepath, _wmakepath
ms.date: 11/04/2016
api_name:
- _makepath
- _wmakepath
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
- _wmakepath
- _tmakepath
- makepath
- tmakepath
- wmakepath
- _makepath
helpviewer_keywords:
- _makepath function
- wmakepath function
- makepath function
- _tmakepath function
- paths
- _wmakepath function
- tmakepath function
ms.assetid: 5930b197-a7b8-46eb-8519-2841a58cd026
ms.openlocfilehash: aafde0aeeebb7b773d3f96ca66ae65762dcdebdf
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70952926"
---
# <a name="_makepath-_wmakepath"></a>_makepath, _wmakepath

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

*path*<br/>
Mémoire tampon du chemin d’accès complet.

*drive*<br/>
Contient une lettre (A, B, etc.) correspondant au lecteur souhaité et un signe deux-points de fin facultatif. **_makepath** insère le signe deux-points automatiquement dans le chemin d’accès composite s’il est manquant. Si le *lecteur* est **null** ou pointe vers une chaîne vide, aucune lettre de lecteur ne s’affiche dans la chaîne du *chemin d’accès* composite.

*dir*<br/>
Contient le chemin d’accès des répertoires, sans l’indicateur de lecteur ou le nom de fichier réel. La barre oblique finale est facultative, et une barre oblique (/) ou une barre oblique inverse\\() ou les deux peuvent être utilisées dans un seul argument *dir* . Si aucune barre oblique finale (/ ou \\) n’est spécifiée, elle est insérée automatiquement. Si *dir* a la **valeur null** ou pointe vers une chaîne vide, aucun chemin d’accès de répertoire n’est inséré dans la chaîne du *chemin d’accès* composite.

*fname*<br/>
Contient le nom de fichier de base sans les extensions du nom de fichier. Si *fname* a la **valeur null** ou pointe vers une chaîne vide, aucun nom de fichier n’est inséré dans la chaîne du *chemin d’accès* composite.

*ext*<br/>
Contient l’extension de nom de fichier réelle, avec ou sans point initial (.). **_makepath** insère automatiquement le point s’il n’apparaît pas dans *ext*. Si *ext* a la **valeur null** ou pointe vers une chaîne vide, aucune extension n’est insérée dans la chaîne du *chemin d’accès* composite.

## <a name="remarks"></a>Notes

La fonction **_makepath** crée une chaîne de chemin d’accès composite à partir de composants individuels, en stockant le résultat dans le *chemin d’accès*. Le *chemin d’accès* peut inclure une lettre de lecteur, un chemin d’accès de répertoire, un nom de fichier et une extension de nom de fichier. **_wmakepath** est une version à caractères larges de **_makepath**; les arguments de **_wmakepath** sont des chaînes à caractères larges. dans le cas contraire, **_wmakepath** et **_makepath** se comportent de la même façon.

**Remarque relative à la sécurité** Utilisez une chaîne se terminant par un caractère Null. Pour éviter une saturation de la mémoire tampon, la chaîne se terminant par NULL ne doit pas dépasser la taille de la mémoire tampon du *chemin d’accès* . **_makepath** ne garantit pas que la longueur de la chaîne de chemin d’accès composite ne dépasse pas _ **MAX_PATH**. Pour plus d’informations, consultez [Solutions contre les dépassements de mémoire tampon](/windows/win32/SecBP/avoiding-buffer-overruns).

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine Tchar.h|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tmakepath**|**_makepath**|**_makepath**|**_wmakepath**|

L’argument *path* doit pointer vers une mémoire tampon vide suffisamment grande pour contenir le chemin d’accès complet. Le *chemin d’accès* composite ne doit pas être supérieur à la constante _ **MAX_PATH** , définie dans stdlib. h.

Si path a la **valeur null**, le gestionnaire de paramètres non valides est appelé, comme décrit dans [validation de paramètre](../../c-runtime-library/parameter-validation.md). En outre, **errno** a la valeur **EINVAL**. Les valeurs **null** sont autorisées pour tous les autres paramètres.

## <a name="requirements"></a>Configuration requise

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
