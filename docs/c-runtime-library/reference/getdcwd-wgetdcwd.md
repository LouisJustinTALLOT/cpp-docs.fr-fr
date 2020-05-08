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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: 69e9d0b0eaa3a62d95ea602b68b5d1ad0df99e4a
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2020
ms.locfileid: "82919217"
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

*unités*<br/>
Entier non négatif qui spécifie le lecteur (0 = lecteur par défaut, 1 = A, 2 = B, etc.).

Si le lecteur spécifié n’est pas disponible, ou si le type de lecteur (par exemple, amovible, fixe, CD-ROM, disque RAM ou lecteur réseau) ne peut pas être déterminé, le gestionnaire de paramètre non valide est appelé. Pour plus d’informations, consultez [Validation de paramètre](../../c-runtime-library/parameter-validation.md).

*buffer*<br/>
Emplacement de stockage pour le chemin d'accès, ou **NULL**.

Si la valeur **null** est spécifiée, cette fonction alloue une mémoire tampon d’au moins la taille de *MaxLen* à l’aide de **malloc**, et la valeur de retour de **_getdcwd** est un pointeur vers la mémoire tampon allouée. La mémoire tampon peut être libérée en appelant **Free** et en lui passant le pointeur.

*maxlen*<br/>
Entier positif différent de zéro qui spécifie la longueur maximale du chemin d’accès, en caractères : **char** pour **_getdcwd** et **wchar_t** pour **_wgetdcwd**.

Si *MaxLen* est inférieur ou égal à zéro, le gestionnaire de paramètre non valide est appelé. Pour plus d’informations, consultez [Validation de paramètre](../../c-runtime-library/parameter-validation.md).

## <a name="return-value"></a>Valeur de retour

Pointeur vers une chaîne qui représente le chemin d’accès complet du répertoire de travail actuel sur le lecteur spécifié, ou **null**, qui indique une erreur.

Si *buffer* est spécifié comme **null** et que la mémoire est insuffisante pour allouer des caractères *MaxLen* , une erreur se produit et **errno** a la valeur **ENOMEM**. Si la longueur du chemin d’accès, y compris le caractère null de fin, dépasse *MaxLen*, une erreur se produit et **errno** a la valeur **ERANGE**. Pour plus d’informations sur ces codes d’erreur, consultez [errno, _doserrno, _sys_errlist et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Notes 

La fonction **_getdcwd** obtient le chemin d’accès complet du répertoire de travail actuel sur le lecteur spécifié et le stocke au niveau de la *mémoire tampon*. Si le répertoire de travail actuel est la racine, la chaîne se termine par une barre oblique inverse (\\). Si le répertoire de travail actuel est un répertoire différent de la racine, la chaîne se termine par le nom du répertoire, et non par une barre oblique inverse.

**_wgetdcwd** est une version à caractères larges de **_getdcwd**, et son paramètre de *mémoire tampon* et sa valeur de retour sont des chaînes à caractères larges. Dans le cas contraire, **_wgetdcwd** et **_getdcwd** se comportent de la même façon.

Cette fonction est thread-safe même si elle dépend de **GetFullPathName**, qui n'est pas elle-même thread-safe. Toutefois, vous pouvez enfreindre la sécurité des threads si votre application multithread appelle cette fonction et [GetFullPathName](/windows/win32/api/fileapi/nf-fileapi-getfullpathnamew).

La version de cette fonction qui a le suffixe **_nolock** se comporte de la même façon que cette fonction, sauf qu’elle n’est pas thread-safe et qu’elle n’est pas protégée contre les interférences par d’autres threads. Pour plus d'informations, consultez [_getdcwd_nolock, _wgetdcwd_nolock](getdcwd-nolock-wgetdcwd-nolock.md).

Quand **_DEBUG** et **_CRTDBG_MAP_ALLOC** sont définis, les appels à **_getdcwd** et **_wgetdcwd** sont remplacés par des appels à **_getdcwd_dbg** et **_wgetdcwd_dbg** afin que vous puissiez déboguer les allocations de mémoire. Pour plus d’informations, consultez[_getdcwd_dbg, _wgetdcwd_dbg](getdcwd-dbg-wgetdcwd-dbg.md).

Par défaut, l’état global de cette fonction est limité à l’application. Pour modifier cette valeur, consultez [état global dans le CRT](../global-state.md).

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

## <a name="example"></a> Exemple

Consultez l’exemple dans [_getdrive](getdrive.md).

## <a name="see-also"></a>Voir aussi

[Contrôle de répertoire](../../c-runtime-library/directory-control.md)<br/>
[_chdir, _wchdir](chdir-wchdir.md)<br/>
[_getcwd, _wgetcwd](getcwd-wgetcwd.md)<br/>
[_getdrive](getdrive.md)<br/>
[_mkdir, _wmkdir](mkdir-wmkdir.md)<br/>
[_rmdir, _wrmdir](rmdir-wrmdir.md)<br/>
