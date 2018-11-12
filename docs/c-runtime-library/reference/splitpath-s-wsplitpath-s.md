---
title: _splitpath_s, _wsplitpath_s
ms.date: 11/04/2016
apiname:
- _wsplitpath_s
- _splitpath_s
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
ms.openlocfilehash: 5a6770b7f5f0f8ee82cf86757d14e03b33c1f5d1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50602902"
---
# <a name="splitpaths-wsplitpaths"></a>_splitpath_s, _wsplitpath_s

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

*Lecteur*<br/>
Lecteur de lettre, suivie par un signe deux-points (**:**). Vous pouvez transmettre **NULL** pour ce paramètre si vous n’avez pas besoin de la lettre de lecteur.

*driveNumberOfElements*<br/>
La taille de la *lecteur* mémoire tampon en caractères larges ou codés sur un octet. Si *lecteur* est **NULL**, cette valeur doit être 0.

*dir*<br/>
Chemin de répertoire incluant une barre oblique de fin. Barres obliques ( **/** ), barres obliques inverses ( **\\** ), ou les deux peuvent être utilisés. Vous pouvez transmettre **NULL** pour ce paramètre si vous n’avez pas besoin du chemin du répertoire.

*dirNumberOfElements*<br/>
La taille de la *dir* mémoire tampon en caractères larges ou codés sur un octet. Si *dir* est **NULL**, cette valeur doit être 0.

*fname*<br/>
Nom de fichier de base (sans extension). Vous pouvez transmettre **NULL** pour ce paramètre si vous n’avez pas besoin du nom de fichier.

*nameNumberOfElements*<br/>
La taille de la *fname* mémoire tampon en caractères larges ou codés sur un octet. Si *fname* est **NULL**, cette valeur doit être 0.

*Ext*<br/>
Extension de nom de fichier, y compris le point de début (**.**). Vous pouvez transmettre **NULL** pour ce paramètre si vous n’avez pas besoin de l’extension de nom de fichier.

*extNumberOfElements*<br/>
La taille de *ext* mémoire tampon en caractères larges ou codés sur un octet. Si *ext* est **NULL**, cette valeur doit être 0.

## <a name="return-value"></a>Valeur de retour

Zéro si l'opération a réussi ; code d'erreur en cas de échec.

### <a name="error-conditions"></a>Conditions d’erreur

|Condition|Valeur de retour|
|---------------|------------------|
|*chemin d’accès* est **NULL**|**EINVAL**|
|*lecteur* est **NULL**, *driveNumberOfElements* est différente de zéro|**EINVAL**|
|*lecteur* est non -**NULL**, *driveNumberOfElements* est égal à zéro|**EINVAL**|
|*dir* est **NULL**, *dirNumberOfElements* est différente de zéro|**EINVAL**|
|*dir* est non -**NULL**, *dirNumberOfElements* est égal à zéro|**EINVAL**|
|*fname* est **NULL**, *nameNumberOfElements* est différente de zéro|**EINVAL**|
|*fname* est non -**NULL**, *nameNumberOfElements* est égal à zéro|**EINVAL**|
|*Ext* est **NULL**, *extNumberOfElements* est différente de zéro|**EINVAL**|
|*Ext* est non -**NULL**, *extNumberOfElements* est égal à zéro|**EINVAL**|

Si l’une des conditions ci-dessus se présente, le gestionnaire de paramètre non valide est appelé, comme décrit dans [Validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, ces fonctions définissent **errno** à **EINVAL** et retourner **EINVAL**.

Si une des mémoires tampons est trop court pour contenir le résultat, ces fonctions effacer toutes les mémoires tampons pour des chaînes vides, définissez **errno** à **ERANGE**et retourner **ERANGE**.

## <a name="remarks"></a>Notes

Le **_splitpath_s** fonction divise un chemin en quatre composants. **_splitpath_s** gère automatiquement les arguments de chaîne de caractères multioctets comme il convient, en identifiant les séquences de caractères multioctets en fonction de la page de codes multioctets en cours d’utilisation. **_wsplitpath_s** est une version à caractères larges de **_splitpath_s**; les arguments de **_wsplitpath_s** sont des chaînes à caractères larges. Sinon, ces fonctions se comportent de façon identique.

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine TCHAR.H|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tsplitpath_s**|**_splitpath_s**|**_splitpath_s**|**_wsplitpath_s**|

Chaque composant du chemin complet est stocké dans une mémoire tampon distincte ; les constantes manifestes **_MAX_DRIVE**, **_MAX_DIR**, **_MAX_FNAME**, et **_MAX_EXT** (défini dans STDLIB. (H) spécifiez la taille maximale autorisée pour chaque composant de fichier. Les composants de fichier dont la taille dépasse celle des constantes manifestes correspondantes occasionnent une altération du tas.

Le tableau suivant répertorie les valeurs des constantes manifestes.

|Name|Value|
|----------|-----------|
|_MAX_DRIVE|3|
|_MAX_DIR|256|
|_MAX_FNAME|256|
|_MAX_EXT|256|

Si le chemin d’accès complet ne contient pas d’un composant (par exemple, un nom de fichier), **_splitpath_s** assigne une chaîne vide à la mémoire tampon correspondante.

En C++, l’utilisation de ces fonctions est simplifiée par les surcharges de modèle ; celles-ci peuvent déduire automatiquement la longueur de la mémoire tampon, ce qui évite d’avoir à spécifier un argument de taille. Pour plus d'informations, consultez [Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md).

Les versions debug de ces fonctions remplissent d'abord la mémoire tampon avec 0xFD. Pour désactiver ce comportement, utilisez [_CrtSetDebugFillThreshold](crtsetdebugfillthreshold.md).

## <a name="requirements"></a>Configuration requise

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
