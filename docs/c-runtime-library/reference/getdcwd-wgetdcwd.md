---
title: _getdcwd, _wgetdcwd
ms.date: 4/2/2020
api_name:
- _getdcwd
- _wgetdcwd
- _o__getdcwd
- _o__wgetdcwd
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
- api-ms-win-crt-stdio-l1-1-0.dll
- api-ms-win-crt-environment-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- wgetdcwd
- getdcwd
- _getdcwd
- tgetdcwd
- _wgetdcwd
- _tgetdcwd
helpviewer_keywords:
- wgetdcwd function
- working directory
- getdcwd function
- _getdcwd function
- _wgetdcwd function
- current working directory
- directories [C++], current working
ms.assetid: 184152f5-c7b0-495b-918d-f9a6adc178bd
ms.openlocfilehash: 3a4ca8ff3f1153893282c65bc4c2becd687138ce
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81344398"
---
# <a name="_getdcwd-_wgetdcwd"></a>_getdcwd, _wgetdcwd

Obtient le chemin d'accès complet du répertoire de travail actuel sur le lecteur spécifié.

## <a name="syntax"></a>Syntaxe

```C
char *_getdcwd(
   int drive,
   char *buffer,
   int maxlen
);
wchar_t *_wgetdcwd(
   int drive,
   wchar_t *buffer,
   int maxlen
);
```

### <a name="parameters"></a>Paramètres

*Disque*<br/>
Entier non négatif qui spécifie le lecteur (0 = lecteur par défaut, 1 = A, 2 = B, etc.).

Si le lecteur spécifié n’est pas disponible, ou si le type d’entraînement (par exemple, amovible, fixe, CD-ROM, disque RAM ou lecteur réseau) ne peut pas être déterminé, le gestionnaire de paramètres invalides est invoqué. Pour plus d’informations, consultez [Validation de paramètre](../../c-runtime-library/parameter-validation.md).

*buffer*<br/>
Emplacement de stockage pour le chemin d'accès, ou **NULL**.

Si **NULL** est spécifié, cette fonction alloue un tampon d’au moins la taille *maxlen* en utilisant **malloc**, et la valeur de retour de **_getdcwd** est un pointeur à la zone tampon allouée. Le tampon peut être libéré en appelant **libre** et en le passant le pointeur.

*maxlen*<br/>
Un intégrateur positif non zéro qui spécifie la longueur maximale du chemin, en caractères : **char** pour **_getdcwd** et **wchar_t** pour **_wgetdcwd.**

Si *le maxlen* est inférieur ou égal à zéro, le gestionnaire de paramètres invalides est invoqué. Pour plus d’informations, consultez [Validation de paramètre](../../c-runtime-library/parameter-validation.md).

## <a name="return-value"></a>Valeur de retour

Pointeur vers une chaîne qui représente le chemin complet de l’annuaire de travail actuel sur le lecteur spécifié, ou **NULL**, ce qui indique une erreur.

Si *le tampon* est spécifié comme **NULL** et qu’il n’y a pas suffisamment de mémoire pour attribuer des caractères *maxlen,* une erreur se produit et **errno** est réglé sur **ENOMEM**. Si la longueur du chemin, y compris le caractère nul de fin dépasse *maxlen*, une erreur se produit, et **errno** est réglé à **ERANGE**. Pour plus d’informations sur ces codes d’erreur, consultez [errno, _doserrno, _sys_errlist et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Notes

La fonction **_getdcwd** obtient le plein chemin de l’annuaire de travail actuel sur le lecteur spécifié et le stocke à *tampon*. Si le répertoire de travail actuel est la racine, la chaîne se termine par une barre oblique inverse (\\). Si le répertoire de travail actuel est un répertoire différent de la racine, la chaîne se termine par le nom du répertoire, et non par une barre oblique inverse.

**_wgetdcwd** est une version à caractère large de **_getdcwd**, et son paramètre *tampon* et la valeur de retour sont des chaînes à caractère large. Sinon, **_wgetdcwd** et **_getdcwd** se comportent de façon identique.

Cette fonction est thread-safe même si elle dépend de **GetFullPathName**, qui n'est pas elle-même thread-safe. Toutefois, vous pouvez enfreindre la sécurité des threads si votre application multithread appelle cette fonction et [GetFullPathName](/windows/win32/api/fileapi/nf-fileapi-getfullpathnamew).

La version de cette fonction qui a le **suffixe _nolock** se comporte de la même manière à cette fonction, sauf qu’il n’est pas sans fil et n’est pas protégé contre les interférences par d’autres threads. Pour plus d'informations, consultez [_getdcwd_nolock, _wgetdcwd_nolock](getdcwd-nolock-wgetdcwd-nolock.md).

Lorsque **_DEBUG** et **_CRTDBG_MAP_ALLOC** sont définis, les appels à **_getdcwd** et **_wgetdcwd** sont remplacés par des appels à **_getdcwd_dbg** et **_wgetdcwd_dbg** afin que vous puissiez déboiffer les allocations de mémoire. Pour plus d’informations, consultez[_getdcwd_dbg, _wgetdcwd_dbg](getdcwd-dbg-wgetdcwd-dbg.md).

Par défaut, l’état global de cette fonction est étendue à l’application. Pour changer cela, voir [Global State dans le CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine Tchar.h|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tgetdcwd**|**_getdcwd**|**_getdcwd**|**_wgetdcwd**|

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**_getdcwd**|\<direct.h>|
|**_wgetdcwd**|\<direct.h> ou \<wchar.h>|

Pour plus d’informations sur la compatibilité, consultez [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

Consultez l’exemple dans [_getdrive](getdrive.md).

## <a name="see-also"></a>Voir aussi

[Contrôle de répertoire](../../c-runtime-library/directory-control.md)<br/>
[_chdir, _wchdir](chdir-wchdir.md)<br/>
[_getcwd, _wgetcwd](getcwd-wgetcwd.md)<br/>
[_getdrive](getdrive.md)<br/>
[_mkdir, _wmkdir](mkdir-wmkdir.md)<br/>
[_rmdir, _wrmdir](rmdir-wrmdir.md)<br/>
