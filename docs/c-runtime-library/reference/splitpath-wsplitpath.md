---
title: _splitpath, _wsplitpath
ms.date: 4/2/2020
api_name:
- _wsplitpath
- _splitpath
- _o__splitpath
- _o__wsplitpath
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
- wsplitpath
- _splitpath
- splitpath
- _wsplitpath
- _tsplitpath
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
ms.openlocfilehash: 6798f93b2d1bc18a190b3b015bf8c882a3fa8a37
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81355610"
---
# <a name="_splitpath-_wsplitpath"></a>_splitpath, _wsplitpath

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

*path*<br/>
Chemin complet.

*Disque*<br/>
Lettre de conduite, suivie d’un côlon (**: ).** Vous pouvez passer **NULL** pour ce paramètre si vous n’avez pas besoin de la lettre d’entraînement.

*Dir*<br/>
Chemin de répertoire incluant une barre oblique de fin. Les barres **/** obliques avant **\\** (), les barres obliques inverses (), ou les deux peuvent être utilisées. Vous pouvez passer **NULL** pour ce paramètre si vous n’avez pas besoin du chemin d’annuaire.

*Fname*<br/>
Nom de fichier de base (sans extension). Vous pouvez passer **NULL** pour ce paramètre si vous n’avez pas besoin du nom de fichier.

*Poste*<br/>
Extension du nom de fichier, y compris la période de tête (**. .**. Vous pouvez passer **NULL** pour ce paramètre si vous n’avez pas besoin de l’extension du nom de fichier.

## <a name="remarks"></a>Notes

La fonction **_splitpath** brise un chemin dans ses quatre composants. **_splitpath** gère automatiquement les arguments de chaîne multioctets, le cas échéant, en reconnaissant les séquences multioctets-caractères selon la page de code multioctet actuellement en service. **_wsplitpath** est une version à caractère large de **_splitpath**; les arguments à **_wsplitpath** sont des chaînes de caractère large. Ces fonctions se comportent sinon de façon identique.

**Remarque relative à la sécurité** Ces fonctions sont exposées à une menace potentielle liée à un problème de dépassement de mémoire tampon. Les dépassements de mémoire tampon sont une méthode fréquente d'attaque du système, ce qui provoque une élévation des privilèges injustifiée. Pour plus d’informations, consultez [Solutions contre les dépassements de mémoire tampon](/windows/win32/SecBP/avoiding-buffer-overruns). Des versions plus sécurisées de ces fonctions sont disponibles; voir [_splitpath_s, _wsplitpath_s](splitpath-s-wsplitpath-s.md).

Par défaut, l’état global de cette fonction est étendue à l’application. Pour changer cela, voir [Global State dans le CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine TCHAR.H|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tsplitpath**|**_splitpath**|**_splitpath**|**_wsplitpath**|

Chaque composant du chemin complet est stocké dans un tampon distinct; les constantes manifestes **_MAX_DRIVE**, **_MAX_DIR**, **_MAX_FNAME**, et **_MAX_EXT** (définie dans STDLIB. H) spécifiez la taille maximale pour chaque composant de fichier. Les composants de fichier dont la taille dépasse celle des constantes manifestes correspondantes occasionnent une altération du tas.

Chaque mémoire tampon doit être aussi volumineuse que sa constante manifeste correspondante pour éviter un possible dépassement de mémoire tampon.

Le tableau suivant répertorie les valeurs des constantes manifestes.

|Nom|Valeur|
|----------|-----------|
|**_MAX_DRIVE**|3|
|**_MAX_DIR**|256|
|**_MAX_FNAME**|256|
|**_MAX_EXT**|256|

Si le chemin complet ne contient pas de composant (par exemple, un nom de fichier), **_splitpath** attribue des chaînes vides aux tampons correspondants.

Vous pouvez passer **NULL** à **_splitpath** pour tout paramètre autre que *le chemin* dont vous n’avez pas besoin.

Si *le chemin* est **NULL**, le gestionnaire de paramètre invalide est invoqué, tel que décrit dans La validation [de paramètres](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, **errno** est réglé sur **EINVAL** et la fonction renvoie **EINVAL**.

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
