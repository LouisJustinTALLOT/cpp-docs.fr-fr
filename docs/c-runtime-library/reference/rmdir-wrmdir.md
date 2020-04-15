---
title: _rmdir, _wrmdir
ms.date: 4/2/2020
api_name:
- _wrmdir
- _rmdir
- _o__rmdir
- _o__wrmdir
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
ms.openlocfilehash: dc9406371da950eb76207d8ddb4a1be8c732098e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81338066"
---
# <a name="_rmdir-_wrmdir"></a>_rmdir, _wrmdir

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

*Dirname*<br/>
Chemin du répertoire à supprimer.

## <a name="return-value"></a>Valeur de retour

Chacune de ces fonctions retourne 0 si le répertoire est bien supprimé. Une valeur de rendement de -1 indique une erreur et **errno** est réglé à l’une des valeurs suivantes:

|Valeur de la variable errno|Condition|
|-|-|
| **ENOTEMPTY** | Le chemin indiqué n’est pas un répertoire, le répertoire n’est pas vide ou le répertoire est soit le répertoire de travail actif, soit le répertoire racine. |
| **ENOENT (ENOENT)** | Le chemin n’est pas valide. |
| **LES EACCES** | Un programme a un descripteur ouvert désignant le répertoire. |

Pour plus d’informations sur ces codes de retour et les autres, consultez [_doserrno, errno, _sys_errlist et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Notes

La fonction **_rmdir** supprime l’annuaire spécifié par *dirname*. Le répertoire doit être vide et ne doit pas être le répertoire de travail actif ou le répertoire racine.

**_wrmdir** est une version à caractère large de **_rmdir**; *l’argument dirname* pour **_wrmdir** est une chaîne de caractère large. **_wrmdir** et **_rmdir** se comportent de façon identique autrement.

Par défaut, l’état global de cette fonction est étendue à l’application. Pour changer cela, voir [Global State dans le CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine Tchar.h|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_trmdir**|**_rmdir**|**_rmdir**|**_wrmdir**|

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**_rmdir**|\<direct.h>|
|**_wrmdir**|\<direct.h> ou \<wchar.h>|

Pour plus d’informations sur la compatibilité, consultez [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Bibliothèques

Toutes les versions des [bibliothèques Runtime C](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a>Exemple

Consultez l’exemple relatif à [_mkdir](mkdir-wmkdir.md).

## <a name="see-also"></a>Voir aussi

[Contrôle de répertoire](../../c-runtime-library/directory-control.md)<br/>
[_chdir, _wchdir](chdir-wchdir.md)<br/>
[_mkdir, _wmkdir](mkdir-wmkdir.md)<br/>
