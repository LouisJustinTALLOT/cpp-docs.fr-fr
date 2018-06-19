---
title: _splitpath, _wsplitpath | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _wsplitpath
- _splitpath
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
- wsplitpath
- _splitpath
- splitpath
- _wsplitpath
- _tsplitpath
dev_langs:
- C++
helpviewer_keywords:
- _splitpath function
- pathnames
- wsplitpath function
- splitpath function
- _wsplitpath function
- tsplitpath function
- path names
- _tsplitpath function
ms.assetid: 32bd76b5-1385-4ee8-a64c-abcb541cd2e4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 220e2befc40dba342a7f8c2aa4c94294bc667ce0
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32411420"
---
# <a name="splitpath-wsplitpath"></a>_splitpath, _wsplitpath

Divisent un nom de chemin en composants. Il existe des versions plus sécurisées de ces fonctions. Consultez [_searchenv_s, _wsearchenv_s](splitpath-s-wsplitpath-s.md).

## <a name="syntax"></a>Syntaxe

```C
void _splitpath(
   const char *path,
   char *drive,
   char *dir,
   char *fname,
   char *ext
);
void _wsplitpath(
   const wchar_t *path,
   wchar_t *drive,
   wchar_t *dir,
   wchar_t *fname,
   wchar_t *ext
);
```

### <a name="parameters"></a>Paramètres

*chemin d’accès* chemin d’accès complet.

*lecteur* lettre du lecteur suivie du signe deux-points (**:**). Vous pouvez passer **NULL** pour ce paramètre, si vous n’avez pas besoin de la lettre de lecteur.

*dir* chemin d’accès de répertoire, y compris la barre oblique de fin. Barres obliques ( **/** ), les barres obliques inverses ( **\\** ), ou les deux peuvent être utilisés. Vous pouvez passer **NULL** pour ce paramètre, si vous n’avez pas besoin du chemin d’accès de répertoire.

*fname* nom de fichier (sans extension) de Base. Vous pouvez passer **NULL** pour ce paramètre, si vous n’avez pas besoin du nom de fichier.

*Ext* extension de nom de fichier, y compris le début de période (**.**). Vous pouvez passer **NULL** pour ce paramètre, si vous n’avez pas besoin de l’extension de nom de fichier.

## <a name="remarks"></a>Notes

Le **_splitpath** fonction s’arrête à un chemin d’accès en quatre composants. **_splitpath** gère automatiquement les arguments de chaîne de caractères multioctets selon le cas, le cas des séquences de caractères multioctets selon la page de codes multioctets en cours d’utilisation. **_wsplitpath** est une version à caractères larges de **_splitpath**; les arguments de **_wsplitpath** sont des chaînes à caractères larges. Ces fonctions se comportent sinon de façon identique.

**Remarque relative à la sécurité** Ces fonctions sont exposées à une menace potentielle liée à un problème de dépassement de mémoire tampon. Les dépassements de mémoire tampon sont une méthode fréquente d'attaque du système, ce qui provoque une élévation des privilèges injustifiée. Pour plus d’informations, consultez [Solutions contre les dépassements de mémoire tampon](http://msdn.microsoft.com/library/windows/desktop/ms717795). Il existe des versions plus sécurisées de ces fonctions. Consultez [_splitpath_s, _wsplitpath_s](splitpath-s-wsplitpath-s.md).

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine TCHAR.H|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tsplitpath**|**_splitpath**|**_splitpath**|**_wsplitpath**|

Chaque composant du chemin d’accès complet est stocké dans une mémoire tampon distincte ; les constantes de manifeste **_MAX_DRIVE**, **_MAX_DIR**, **_MAX_FNAME**, et **_MAX_EXT** (défini dans STDLIB. H) spécifier la taille maximale de chaque composant du fichier. Les composants de fichier dont la taille dépasse celle des constantes manifestes correspondantes occasionnent une altération du tas.

Chaque mémoire tampon doit être aussi volumineuse que sa constante manifeste correspondante pour éviter un possible dépassement de mémoire tampon.

Le tableau suivant répertorie les valeurs des constantes manifestes.

|Name|Value|
|----------|-----------|
|**_MAX_DRIVE**|3|
|**_MAX_DIR**|256|
|**_MAX_FNAME**|256|
|**_MAX_EXT**|256|

Si le chemin d’accès complet ne contient pas un composant (par exemple, un nom de fichier), **_splitpath** affecte vide des chaînes pour les mémoires tampons correspondantes.

Vous pouvez passer **NULL** à **_splitpath** pour un paramètre autre que *chemin d’accès* que vous n’avez pas besoin.

Si *chemin d’accès* est **NULL**, le Gestionnaire de paramètre non valide est appelé, comme décrit dans [Validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, **errno** a la valeur **EINVAL** et la fonction retourne **EINVAL**.

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**_splitpath**|\<stdlib.h>|
|**_wsplitpath**|\<stdlib.h> ou \<wchar.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

Consultez l’exemple relatif à [_makepath](makepath-wmakepath.md).

## <a name="see-also"></a>Voir aussi

[Gestion de fichiers](../../c-runtime-library/file-handling.md)<br/>
[_fullpath, _wfullpath](fullpath-wfullpath.md)<br/>
[_getmbcp](getmbcp.md)<br/>
[_makepath, _wmakepath](makepath-wmakepath.md)<br/>
[_setmbcp](setmbcp.md)<br/>
[_splitpath_s, _wsplitpath_s](splitpath-s-wsplitpath-s.md)<br/>
