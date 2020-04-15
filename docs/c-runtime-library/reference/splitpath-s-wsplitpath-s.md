---
title: _splitpath_s, _wsplitpath_s
ms.date: 4/2/2020
api_name:
- _wsplitpath_s
- _splitpath_s
- _o__splitpath_s
- _o__wsplitpath_s
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
- ntoskrnl.exe
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _wsplitpath_s
- splitpath_s
- _splitpath_s
- wsplitpath_s
helpviewer_keywords:
- splitpath_s function
- pathnames
- _splitpath_s function
- _wsplitpath_s function
- path names
- wsplitpath_s function
ms.assetid: 30fff3e2-cd00-4eb6-b5a2-65db79cb688b
ms.openlocfilehash: 364544a9423668494747405e801d59b73de4e6c6
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81355621"
---
# <a name="_splitpath_s-_wsplitpath_s"></a>_splitpath_s, _wsplitpath_s

Divise un nom de chemin en composants. Ces versions de [_splitpath, _wsplitpath](splitpath-wsplitpath.md) intègrent les améliorations de sécurité décrites dans [Fonctionnalités de sécurité dans le CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Syntaxe

```C
errno_t _splitpath_s(
   const char * path,
   char * drive,
   size_t driveNumberOfElements,
   char * dir,
   size_t dirNumberOfElements,
   char * fname,
   size_t nameNumberOfElements,
   char * ext,
   size_t extNumberOfElements
);
errno_t _wsplitpath_s(
   const wchar_t * path,
   wchar_t * drive,
   size_t driveNumberOfElements,
   wchar_t *dir,
   size_t dirNumberOfElements,
   wchar_t * fname,
   size_t nameNumberOfElements,
   wchar_t * ext,
   size_t extNumberOfElements
);
template <size_t drivesize, size_t dirsize, size_t fnamesize, size_t extsize>
errno_t _splitpath_s(
   const char *path,
   char (&drive)[drivesize],
   char (&dir)[dirsize],
   char (&fname)[fnamesize],
   char (&ext)[extsize]
); // C++ only
template <size_t drivesize, size_t dirsize, size_t fnamesize, size_t extsize>
errno_t _wsplitpath_s(
   const wchar_t *path,
   wchar_t (&drive)[drivesize],
   wchar_t (&dir)[dirsize],
   wchar_t (&fname)[fnamesize],
   wchar_t (&ext)[extsize]
); // C++ only
```

### <a name="parameters"></a>Paramètres

*path*<br/>
Chemin complet.

*Disque*<br/>
Lettre de conduite, suivie d’un côlon (**: ).** Vous pouvez passer **NULL** pour ce paramètre si vous n’avez pas besoin de la lettre d’entraînement.

*driveNumberOfElements*<br/>
La taille du tampon *d’entraînement* en caractères simples ou larges. Si *le lecteur* est **NULL**, cette valeur doit être de 0.

*Dir*<br/>
Chemin de répertoire incluant une barre oblique de fin. Les barres **/** obliques avant **\\** (), les barres obliques inverses (), ou les deux peuvent être utilisées. Vous pouvez passer **NULL** pour ce paramètre si vous n’avez pas besoin du chemin d’annuaire.

*dirNumberOfElements*<br/>
La taille du tampon *dir* en caractères simples ou larges. Si *dir* est **NULL**, cette valeur doit être de 0.

*Fname*<br/>
Nom de fichier de base (sans extension). Vous pouvez passer **NULL** pour ce paramètre si vous n’avez pas besoin du nom de fichier.

*nomNumberOfElements*<br/>
La taille du tampon *de fname* en caractères simples ou larges. Si *la fname* est **NULL**, cette valeur doit être de 0.

*Poste*<br/>
Extension du nom de fichier, y compris la période de tête (**. .**. Vous pouvez passer **NULL** pour ce paramètre si vous n’avez pas besoin de l’extension du nom de fichier.

*extNumberOfElements*<br/>
La taille du tampon *ext* en caractères simples ou larges. Si *ext* est **NULL**, cette valeur doit être de 0.

## <a name="return-value"></a>Valeur de retour

Zéro si l'opération a réussi ; code d'erreur en cas de échec.

### <a name="error-conditions"></a>Conditions d'erreur

|Condition|Valeur de retour|
|---------------|------------------|
|*chemin* est **NULL**|**EINVAL (EN)**|
|*lecteur* est **NULL**, *driveNumberOfElements* est non-zéro|**EINVAL (EN)**|
|*lecteur* est**non-NULL**, *driveNumberOfElements* est zéro|**EINVAL (EN)**|
|*dir* est **NULL**, *dirNumberOfElements* est non-zéro|**EINVAL (EN)**|
|*dir* est**non-NULL**, *dirNumberOfElements* est zéro|**EINVAL (EN)**|
|*fname* est **NULL**, *nameNumberOfElements* est non-zéro|**EINVAL (EN)**|
|*fname* est**non-NULL**, *nameNumberOfElements* est zéro|**EINVAL (EN)**|
|*ext* est **NULL**, *extNumberOfElements* est non-zéro|**EINVAL (EN)**|
|*ext* est**non-NULL**, *extNumberOfElements* est zéro|**EINVAL (EN)**|

Si l’une des conditions ci-dessus se présente, le gestionnaire de paramètre non valide est appelé, comme décrit dans [Validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, ces fonctions **définies errno** à **EINVAL** et retourner **EINVAL**.

Si l’un des tampons est trop court pour contenir le résultat, ces fonctions effacer tous les tampons à des chaînes vides, définir **errno** à **ERANGE**, et retourner **ERANGE**.

## <a name="remarks"></a>Notes

La fonction **_splitpath_s** brise un chemin dans ses quatre composants. **_splitpath_s** gère automatiquement les arguments de chaîne multioctets, le cas échéant, en reconnaissant les séquences multioctets-caractères selon la page de code multioctet actuellement en service. **_wsplitpath_s** est une version à caractère large de **_splitpath_s**; les arguments à **_wsplitpath_s** sont des chaînes de caractère large. Sinon, ces fonctions se comportent de façon identique.

Par défaut, l’état global de cette fonction est étendue à l’application. Pour changer cela, voir [Global State dans le CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine TCHAR.H|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tsplitpath_s**|**_splitpath_s**|**_splitpath_s**|**_wsplitpath_s**|

Chaque composant du chemin complet est stocké dans un tampon distinct; les constantes manifestes **_MAX_DRIVE**, **_MAX_DIR**, **_MAX_FNAME**, et **_MAX_EXT** (définie dans STDLIB. H) spécifiez la taille maximale autorisée pour chaque composant de fichier. Les composants de fichier dont la taille dépasse celle des constantes manifestes correspondantes occasionnent une altération du tas.

Le tableau suivant répertorie les valeurs des constantes manifestes.

|Nom|Valeur|
|----------|-----------|
|_MAX_DRIVE|3|
|_MAX_DIR|256|
|_MAX_FNAME|256|
|_MAX_EXT|256|

Si le chemin complet ne contient pas de composant (par exemple, un nom de fichier), **_splitpath_s** attribue une chaîne vide au tampon correspondant.

En C++, l’utilisation de ces fonctions est simplifiée par les surcharges de modèle ; celles-ci peuvent déduire automatiquement la longueur de la mémoire tampon, ce qui évite d’avoir à spécifier un argument de taille. Pour plus d’informations, consultez [Sécuriser les surcharges de modèle](../../c-runtime-library/secure-template-overloads.md).

Les versions de bibliothèque de débogé de ces fonctions remplissent d’abord le tampon avec 0xFE. Pour désactiver ce comportement, utilisez [_CrtSetDebugFillThreshold](crtsetdebugfillthreshold.md).

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**_splitpath_s**|\<stdlib.h>|
|**_wsplitpath_s**|\<stdlib.h> ou \<wchar.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

Consultez l’exemple relatif à [_makepath_s, _wmakepath_s](makepath-s-wmakepath-s.md).

## <a name="see-also"></a>Voir aussi

[Gestion de fichiers](../../c-runtime-library/file-handling.md)<br/>
[_splitpath, _wsplitpath](splitpath-wsplitpath.md)<br/>
[_fullpath, _wfullpath](fullpath-wfullpath.md)<br/>
[_getmbcp](getmbcp.md)<br/>
[_makepath, _wmakepath](makepath-wmakepath.md)<br/>
[_setmbcp](setmbcp.md)<br/>
