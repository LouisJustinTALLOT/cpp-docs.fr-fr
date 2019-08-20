---
title: Gestion de fichiers
ms.date: 11/04/2016
f1_keywords:
- c.files
helpviewer_keywords:
- files [C++], handling
- files [C++], opening
- files [C++], manipulating
ms.assetid: 48119e2e-e94f-4602-b08b-b72440f731d8
ms.openlocfilehash: e5e43fe2cfcdfe067833d02bda511e8c9cb944ad
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69500112"
---
# <a name="file-handling"></a>Gestion de fichiers

Ces routines vous permettent de créer, supprimer et manipuler des fichiers et de définir et vérifier les autorisations d'accès aux fichiers.

Les bibliothèques Runtime C limitent à 512 le nombre de fichiers pouvant être ouverts simultanément. Toute tentative visant à ouvrir plus de descripteurs de fichiers ou de flux de fichiers que le nombre maximal autorisé entraîne un échec du programme. Utilisez [_setmaxstdio](../c-runtime-library/reference/setmaxstdio.md) pour modifier ce nombre.

## <a name="file-handling-routines-file-descriptor"></a>Routines de gestion de fichiers (descripteur de fichier)

Ces routines fonctionnent sur les fichiers désignés par un descripteur de fichier.

|Routine|Utilisez|
|-------------|---------|
|[_chsize](../c-runtime-library/reference/chsize.md),[_chsize_s](../c-runtime-library/reference/chsize-s.md)|Modifier la taille de fichier|
|[_filelength, _filelengthi64](../c-runtime-library/reference/filelength-filelengthi64.md)|Obtenir la longueur de fichier|
|[_fstat, _fstat32, _fstat64, _fstati64, _fstat32i64, _fstat64i32](../c-runtime-library/reference/fstat-fstat32-fstat64-fstati64-fstat32i64-fstat64i32.md)|Obtenir des informations d’état de fichier sur le descripteur|
|[_get_osfhandle](../c-runtime-library/reference/get-osfhandle.md)|Retourne le descripteur de fichier de système d’exploitation associé au descripteur de fichier Runtime C existant.|
|[_isatty](../c-runtime-library/reference/isatty.md)|Rechercher un périphérique de caractères|
|[_locking](../c-runtime-library/reference/locking.md)|Verrouiller des zones de fichier|
|[_open_osfhandle](../c-runtime-library/reference/open-osfhandle.md)|Associer un descripteur de fichier Runtime C à un descripteur de fichier de système d’exploitation existant|
|[_setmode](../c-runtime-library/reference/setmode.md)|Définir le mode de traduction de fichiers|

## <a name="file-handling-routines-path-or-filename"></a>Routines de gestion de fichiers (chemin ou nom de fichier)

Ces routines fonctionnent sur les fichiers spécifiés par un chemin ou un nom de fichier.

|Routine|Utilisez|
|-------------|---------|
|[_access, _waccess](../c-runtime-library/reference/access-waccess.md), [_access_s, _waccess_s](../c-runtime-library/reference/access-s-waccess-s.md)|Vérifier le paramètre d’autorisation de fichier|
|[_chmod, _wchmod](../c-runtime-library/reference/chmod-wchmod.md)|Modifier le paramètre d’autorisation de fichier|
|[_fullpath, _wfullpath](../c-runtime-library/reference/fullpath-wfullpath.md)|Développer un chemin d’accès relatif vers son nom de chemin d’accès absolu|
|[_makepath, _wmakepath](../c-runtime-library/reference/makepath-wmakepath.md), [_makepath_s, _wmakepath_s](../c-runtime-library/reference/makepath-s-wmakepath-s.md)|Fusionner des composants de chemin d’accès en un seul chemin d’accès complet|
|[_mktemp, _wmktemp](../c-runtime-library/reference/mktemp-wmktemp.md), [_mktemp_s, _wmktemp_s](../c-runtime-library/reference/mktemp-s-wmktemp-s.md)|Créer un nom de fichier unique|
|[remove, _wremove](../c-runtime-library/reference/remove-wremove.md)|Supprimer le fichier|
|[rename, _wrename](../c-runtime-library/reference/rename-wrename.md)|Renommer un fichier|
|[_splitpath, _wsplitpath](../c-runtime-library/reference/splitpath-wsplitpath.md), [_splitpath_s, _wsplitpath_s](../c-runtime-library/reference/splitpath-s-wsplitpath-s.md)|Analyser un chemin d’accès en composants|
|[_stat, _stat64, _stati64, _wstat, _wstat64, _wstati64](../c-runtime-library/reference/stat-functions.md)|Obtenir des informations d’état de fichier sur un fichier nommé|
|[_umask](../c-runtime-library/reference/umask.md), [_umask_s](../c-runtime-library/reference/umask-s.md)|Définir le masque d’autorisation par défaut pour les nouveaux fichiers créés par programme|
|[_unlink, _wunlink](../c-runtime-library/reference/unlink-wunlink.md)|Supprimer le fichier|

## <a name="file-handling-routines-open-file"></a>Routines de gestion de fichiers (ouvrir un fichier)

Ces routines ouvrent des fichiers.

|Routine|Utilisez|
|-------------|---------|
|[fopen, _wfopen](../c-runtime-library/reference/fopen-wfopen.md), [fopen_s, _wfopen_s](../c-runtime-library/reference/fopen-s-wfopen-s.md)|Ouvre un fichier et retourne un pointeur vers le fichier ouvert.|
|[_fsopen, _wfsopen](../c-runtime-library/reference/fsopen-wfsopen.md)|Ouvre un flux avec le partage de fichiers et retourne un pointeur vers le fichier ouvert.|
|[_open, _wopen](../c-runtime-library/reference/open-wopen.md)|Ouvre un fichier et retourne un descripteur de fichier au fichier ouvert.|
|[_sopen, _wsopen](../c-runtime-library/reference/sopen-wsopen.md), [_sopen_s, _wsopen_s](../c-runtime-library/reference/sopen-s-wsopen-s.md)|Ouvre un fichier avec le partage de fichiers et retourne un descripteur de fichier au fichier ouvert.|
|[_pipe](../c-runtime-library/reference/pipe.md)|Crée un canal pour la lecture et l’écriture.|
|[freopen, _wfreopen](../c-runtime-library/reference/freopen-wfreopen.md), [freopen_s, _wfreopen_s](../c-runtime-library/reference/freopen-s-wfreopen-s.md)|Réaffecte un pointeur de fichier.|

Ces routines permettent de modifier la représentation du fichier entre une structure `FILE`, un descripteur de fichier et un handle de fichier Win32.

|Routine|Utilisez|
|-------------|---------|
|[_fdopen, _wfdopen](../c-runtime-library/reference/fdopen-wfdopen.md)|Associe un flux à un fichier ouvert précédemment pour une E/S de bas niveau et retourne un pointeur vers le flux ouvert.|
|[_fileno](../c-runtime-library/reference/fileno.md)|Obtient le descripteur de fichier associé à un flux.|
|[_get_osfhandle](../c-runtime-library/reference/get-osfhandle.md)|Retourne le descripteur de fichier de système d’exploitation associé au descripteur de fichier Runtime C existant.|
|[_open_osfhandle](../c-runtime-library/reference/open-osfhandle.md)|Associe un descripteur de fichier Runtime C à un descripteur de fichier de système d’exploitation existant.|

Les fonctions Win32 suivantes permettent aussi d’ouvrir des fichiers et des canaux :

- [CreateFile](/windows/win32/api/fileapi/nf-fileapi-createfilew)

- [CreatePipe](/windows/win32/api/namedpipeapi/nf-namedpipeapi-createpipe)

- [CreateNamedPipe](/windows/win32/api/winbase/nf-winbase-createnamedpipew)

## <a name="see-also"></a>Voir aussi

[Routines du runtime C universel par catégorie](../c-runtime-library/run-time-routines-by-category.md)<br/>
[Contrôle de répertoire](../c-runtime-library/directory-control.md)<br/>
[Appels système](../c-runtime-library/system-calls.md)<br/>
