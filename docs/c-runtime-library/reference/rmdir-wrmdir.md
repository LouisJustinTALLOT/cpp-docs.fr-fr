---
title: _rmdir, _wrmdir
ms.date: 11/04/2016
apiname:
- _wrmdir
- _rmdir
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
- trmdir
- _trmdir
- wrmdir
- _rmdir
- _wrmdir
helpviewer_keywords:
- _rmdir function
- directories [C++], deleting
- rmdir function
- directories [C++], removing
- trmdir function
- _trmdir function
- _wrmdir function
- wrmdir function
ms.assetid: 652c2a5a-b0ac-4493-864e-1edf484333c5
ms.openlocfilehash: 0d0d9a25b70746174a66abbe088b297a5d9a0942
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62357458"
---
# <a name="rmdir-wrmdir"></a>_rmdir, _wrmdir

Supprime un répertoire.

## <a name="syntax"></a>Syntaxe

```C
int _rmdir(
   const char *dirname
);
int _wrmdir(
   const wchar_t *dirname
);
```

### <a name="parameters"></a>Paramètres

*dirname*<br/>
Chemin du répertoire à supprimer.

## <a name="return-value"></a>Valeur de retour

Chacune de ces fonctions retourne 0 si le répertoire est bien supprimé. Une valeur de retour de -1 indique une erreur et **errno** est défini sur l’une des valeurs suivantes :

|Valeur de la variable errno|Condition|
|-|-|
| **ENOTEMPTY** | Le chemin indiqué n’est pas un répertoire, le répertoire n’est pas vide ou le répertoire est soit le répertoire de travail actif, soit le répertoire racine. |
| **ENOENT** | Le chemin n’est pas valide. |
| **EACCES** | Un programme a un descripteur ouvert désignant le répertoire. |

Pour plus d'informations sur ces codes de retour et autres, consultez [_doserrno, errno, _sys_errlist et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Notes

Le **_rmdir** fonction supprime le répertoire spécifié par *dirname*. Le répertoire doit être vide et ne doit pas être le répertoire de travail actif ou le répertoire racine.

**_wrmdir** est une version à caractères larges de **_rmdir**; le *dirname* l’argument de **_wrmdir** est une chaîne de caractères larges. **_wrmdir** et **_rmdir** se comportent de façon identique dans le cas contraire.

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine Tchar.h|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_trmdir**|**_rmdir**|**_rmdir**|**_wrmdir**|

## <a name="requirements"></a>Configuration requise

|Routine|En-tête requis|
|-------------|---------------------|
|**_rmdir**|\<direct.h>|
|**_wrmdir**|\<direct.h> ou \<wchar.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Bibliothèques

Toutes les versions des [bibliothèques Runtime C](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a>Exemple

Consultez l’exemple relatif à [_mkdir](mkdir-wmkdir.md).

## <a name="see-also"></a>Voir aussi

[Contrôle de répertoire](../../c-runtime-library/directory-control.md)<br/>
[_chdir, _wchdir](chdir-wchdir.md)<br/>
[_mkdir, _wmkdir](mkdir-wmkdir.md)<br/>
