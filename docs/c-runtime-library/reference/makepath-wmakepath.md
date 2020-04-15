---
title: _makepath, _wmakepath
ms.date: 4/2/2020
api_name:
- _makepath
- _wmakepath
- _o__makepath
- _o__wmakepath
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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: b92e056816183b4bbb07edb3efec4415655d655e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81341590"
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
Mémoire tampon du chemin d'accès complet.

*Disque*<br/>
Contient une lettre (A, B, etc.) correspondant au lecteur souhaité et un signe deux-points de fin facultatif. **_makepath** insère automatiquement le côlon dans la trajectoire composite s’il manque. Si *le lecteur* est **NULL** ou pointe vers une chaîne vide, aucune lettre d’entraînement n’apparaît dans la chaîne de *trajectoire* composite.

*Dir*<br/>
Contient le chemin d’accès des répertoires, sans l’indicateur de lecteur ou le nom de fichier réel. La barre oblique de fuite est facultative, et soit\\une barre oblique avant (/) ou une barre oblique inverse ( ) ou les deux pourraient être utilisés dans un seul argument *dir.* Si aucune barre oblique finale (/ ou \\) n’est spécifiée, elle est insérée automatiquement. Si *le dir* est **NULL** ou pointe vers une chaîne vide, aucun chemin de répertoire n’est inséré dans la chaîne de *chemin* composite.

*Fname*<br/>
Contient le nom de fichier de base sans les extensions du nom de fichier. Si *la fname* est **NULL** ou indique une chaîne vide, aucun nom de fichier n’est inséré dans la chaîne de *trajectoire* composite.

*Poste*<br/>
Contient l’extension de nom de fichier réelle, avec ou sans point initial (.). **_makepath** insère automatiquement la période si elle n’apparaît pas dans *ext*. Si *l’ext* est **NULL** ou pointe vers une chaîne vide, aucune extension n’est insérée dans la chaîne de *trajectoire* composite.

## <a name="remarks"></a>Notes

La fonction **_makepath** crée une chaîne de chemin composite à partir de composants individuels, le stockage du résultat dans le *chemin*. Le *chemin* peut inclure une lettre d’entraînement, un parcours d’annuaire, un nom de fichier et une extension du nom de fichier. **_wmakepath** est une version à caractère large de **_makepath**; les arguments pour **_wmakepath** sont des chaînes de caractère large. **_wmakepath** et **_makepath** se comportent de façon identique autrement.

**Remarque relative à la sécurité** Utilisez une chaîne se terminant par un caractère Null. Pour éviter le dépassement de mémoire tampon, la ficelle non terminée ne doit pas dépasser la taille du tampon de *trajectoire.* **_makepath** ne garantit pas que la longueur de la chaîne de trajectoire composite ne dépasse pas **_MAX_PATH**. Pour plus d’informations, consultez [Solutions contre les dépassements de mémoire tampon](/windows/win32/SecBP/avoiding-buffer-overruns).

Par défaut, l’état global de cette fonction est étendue à l’application. Pour changer cela, voir [Global State dans le CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine Tchar.h|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tmakepath**|**_makepath**|**_makepath**|**_wmakepath**|

*L’argument du chemin* doit indiquer un tampon vide assez grand pour maintenir le chemin complet. Le *chemin* composite ne doit pas être plus grand que la **constante _MAX_PATH,** définie dans Stdlib.h.

Si le chemin est **NULL**, le gestionnaire de paramètre invalide est invoqué, tel que décrit dans [La validation de paramètres](../../c-runtime-library/parameter-validation.md). En outre, **errno** est fixé à **EINVAL**. **Les** valeurs NULL sont autorisées pour tous les autres paramètres.

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**_makepath**|\<stdlib.h>|
|**_wmakepath**|\<stdlib.h> ou \<wchar.h>|

Pour plus d’informations sur la compatibilité, consultez [Compatibility](../../c-runtime-library/compatibility.md).

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
