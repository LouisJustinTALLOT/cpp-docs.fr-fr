---
description: 'En savoir plus sur : _splitpath_s, _wsplitpath_s'
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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: f14ea8a31d241abae3a214067cae1e4d34e97861
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97292342"
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

*unités*<br/>
Lettre de lecteur, suivie d’un signe deux-points (**:**). Vous pouvez passer la **valeur null** pour ce paramètre si vous n’avez pas besoin de la lettre de lecteur.

*driveNumberOfElements*<br/>
Taille de la mémoire tampon du *lecteur* en caractères codés sur un octet ou larges. Si le *lecteur* est **null**, cette valeur doit être 0.

*dir*<br/>
Chemin de répertoire incluant une barre oblique de fin. Les barres obliques ( **/** ), les barres obliques inverses ( **\\** ) ou les deux peuvent être utilisées. Vous pouvez passer la **valeur null** pour ce paramètre si vous n’avez pas besoin du chemin d’accès au répertoire.

*dirNumberOfElements*<br/>
Taille de la mémoire tampon de *répertoire* en caractères codés sur un octet ou larges. Si *dir* est **null**, cette valeur doit être 0.

*fname*<br/>
Nom de fichier de base (sans extension). Vous pouvez passer la **valeur null** pour ce paramètre si vous n’avez pas besoin du nom de fichier.

*nameNumberOfElements*<br/>
Taille de la mémoire tampon *fname* en caractères codés sur un octet ou larges. Si *fname* a la valeur **null**, cette valeur doit être 0.

*ext*<br/>
Extension de nom de fichier, y compris le point de début (**.**). Vous pouvez passer la **valeur null** pour ce paramètre si vous n’avez pas besoin de l’extension de nom de fichier.

*extNumberOfElements*<br/>
Taille de la mémoire tampon *ext* en caractères codés sur un octet ou larges. Si *ext* a la valeur **null**, cette valeur doit être 0.

## <a name="return-value"></a>Valeur renvoyée

Zéro si l'opération a réussi ; code d'erreur en cas de échec.

### <a name="error-conditions"></a>Conditions d'erreur

|Condition|Valeur de retour|
|---------------|------------------|
|le *chemin d’accès* est **null**|**EINVAL**|
|le *lecteur* est **null**, *driveNumberOfElements* est différent de zéro|**EINVAL**|
|le *lecteur* n’est pas **null**, *driveNumberOfElements* est égal à zéro|**EINVAL**|
|*dir* est **null**, *dirNumberOfElements* est différent de zéro|**EINVAL**|
|*dir* est non **null**, *dirNumberOfElements* est égal à zéro|**EINVAL**|
|*fname* est **null**, *nameNumberOfElements* est différent de zéro|**EINVAL**|
|*fname* est non **null**, *nameNumberOfElements* est égal à zéro|**EINVAL**|
|*ext* a la **valeur null**, *extNumberOfElements* est différent de zéro|**EINVAL**|
|*ext* est non **null**, *extNumberOfElements* est égal à zéro|**EINVAL**|

Si l’une des conditions ci-dessus se présente, le gestionnaire de paramètre non valide est appelé, comme décrit dans [Validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, ces fonctions définissent **errno** sur **EINVAL** et retournent **EINVAL**.

Si l’une des mémoires tampons est trop petite pour contenir le résultat, ces fonctions effacent toutes les mémoires tampons de chaînes vides, attribuent à **errno** la valeur **ERANGE** et retournent **ERANGE**.

## <a name="remarks"></a>Notes

La fonction **_splitpath_s** divise un chemin d’accès en quatre composants. **_splitpath_s** gère automatiquement les arguments de chaîne de caractères multioctets si nécessaire, en identifiant les séquences de caractères multioctets en fonction de la page de codes multioctets en cours d’utilisation. **_wsplitpath_s** est une version à caractères larges de **_splitpath_s**; les arguments de **_wsplitpath_s** sont des chaînes à caractères larges. Sinon, ces fonctions se comportent de façon identique.

Par défaut, l’état global de cette fonction est limité à l’application. Pour modifier cette valeur, consultez [état global dans le CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine TCHAR.H|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tsplitpath_s**|**_splitpath_s**|**_splitpath_s**|**_wsplitpath_s**|

Chaque composant du chemin d’accès complet est stocké dans une mémoire tampon distincte ; les constantes de manifeste **_MAX_DRIVE**, **_MAX_DIR**, **_MAX_FNAME** et **_MAX_EXT** (définies dans stdlib. H) spécifiez la taille maximale autorisée pour chaque composant de fichier. Les composants de fichier dont la taille dépasse celle des constantes manifestes correspondantes occasionnent une altération du tas.

Le tableau suivant répertorie les valeurs des constantes manifestes.

|Nom|Valeur|
|----------|-----------|
|_MAX_DRIVE|3|
|_MAX_DIR|256|
|_MAX_FNAME|256|
|_MAX_EXT|256|

Si le chemin d’accès complet ne contient pas de composant (par exemple, un nom de fichier), **_splitpath_s** affecte une chaîne vide à la mémoire tampon correspondante.

En C++, l’utilisation de ces fonctions est simplifiée par les surcharges de modèle ; celles-ci peuvent déduire automatiquement la longueur de la mémoire tampon, ce qui évite d’avoir à spécifier un argument de taille. Pour plus d’informations, consultez [Sécuriser les surcharges de modèle](../../c-runtime-library/secure-template-overloads.md).

Les versions de la bibliothèque de débogage de ces fonctions remplissent d’abord la mémoire tampon avec 0xFE. Pour désactiver ce comportement, utilisez [_CrtSetDebugFillThreshold](crtsetdebugfillthreshold.md).

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
