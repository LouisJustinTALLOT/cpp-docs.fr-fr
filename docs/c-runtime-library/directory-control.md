---
title: Contrôle de répertoire
ms.date: 11/04/2016
f1_keywords:
- c.programs
helpviewer_keywords:
- controls [C++], directory
- directory control routines
ms.assetid: a72dcf6f-f366-4d20-8850-0e19cc53ca18
ms.openlocfilehash: 327647ee2eee7e149ec0e9ebfc71883a8a3643d5
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/11/2019
ms.locfileid: "57748578"
---
# <a name="directory-control"></a>Contrôle de répertoire

Ces routines accèdent à des informations, les modifient et obtiennent des informations sur la structure de répertoires.

## <a name="directory-control-routines"></a>Routines de contrôle de répertoire

|Routine|Utilisez|
|-------------|---------|
|[_chdir, _wchdir](../c-runtime-library/reference/chdir-wchdir.md)|Modifier le répertoire de travail actuel|
|[_chdrive](../c-runtime-library/reference/chdrive.md)|Modifier le lecteur actuel|
|[_getcwd, _wgetcwd](../c-runtime-library/reference/getcwd-wgetcwd.md)|Obtenir le répertoire de travail actuel pour le lecteur par défaut|
|[_getdcwd, _wgetdcwd](../c-runtime-library/reference/getdcwd-wgetdcwd.md)|Obtenir le répertoire de travail actuel pour le lecteur spécifié|
|[_getdiskfree](../c-runtime-library/reference/getdiskfree.md)|Remplit une structure **_diskfree_t** avec des informations relatives à un lecteur de disque.|
|[_getdrive](../c-runtime-library/reference/getdrive.md)|Obtenir le lecteur actuel (par défaut)|
|[_getdrives](../c-runtime-library/reference/getdrives.md)|Retourne un masque de bits qui représente les lecteurs de disque actuellement disponibles.|
|[_mkdir, _wmkdir](../c-runtime-library/reference/mkdir-wmkdir.md)|Créer un répertoire|
|[_rmdir, _wrmdir](../c-runtime-library/reference/rmdir-wrmdir.md)|Supprimer un répertoire|
|[_searchenv, _wsearchenv](../c-runtime-library/reference/searchenv-wsearchenv.md), [_searchenv_s, _wsearchenv_s](../c-runtime-library/reference/searchenv-s-wsearchenv-s.md)|Rechercher un fichier donné dans les chemins spécifiés|

## <a name="see-also"></a>Voir aussi

[Routines du runtime C universel par catégorie](../c-runtime-library/run-time-routines-by-category.md)<br/>
[Gestion de fichiers](../c-runtime-library/file-handling.md)<br/>
[Appels système](../c-runtime-library/system-calls.md)<br/>
