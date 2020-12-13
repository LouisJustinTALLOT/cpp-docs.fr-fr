---
description: 'En savoir plus sur : _chdrive'
title: _chdrive
ms.date: 4/2/2020
api_name:
- _chdrive
- _o__chdrive
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
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- chdrive
- _chdrive
helpviewer_keywords:
- drives, changing
- _chdrive function
- chdrive function
ms.assetid: 212a1a4b-4fa8-444e-9677-7fca4c8c47e3
ms.openlocfilehash: d3935c64d8ae67c72f8516e4c2d21a7a0aa6e21b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97186686"
---
# <a name="_chdrive"></a>_chdrive

Change le lecteur de travail actif.

> [!IMPORTANT]
> Cette API ne peut pas être utilisée dans les applications qui s'exécutent dans le Windows Runtime. Pour plus d’informations, consultez [Fonctions CRT non prises en charge dans les applications de la plateforme Windows universelle](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntaxe

```C
int _chdrive(
   int drive
);
```

### <a name="parameters"></a>Paramètres

*unités*<br/>
Entier compris entre 1 et 26 qui spécifie le lecteur de travail actif (1=A, 2=B et ainsi de suite).

## <a name="return-value"></a>Valeur renvoyée

Zéro (0) si le lecteur de travail actif a été correctement changé ; Sinon, -1.

## <a name="remarks"></a>Notes

Si le *lecteur* n’est pas dans la plage comprise entre 1 et 26, le gestionnaire de paramètre non valide est appelé, comme décrit dans [validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, la fonction **_chdrive** retourne-1, **errno** a la valeur **EACCES** et **_doserrno** a la valeur **ERROR_INVALID_DRIVE**.

La fonction **_chdrive** n’est pas thread-safe, car elle dépend de la fonction **SetCurrentDirectory**, qui elle-même n’est pas thread-safe. Pour utiliser **_chdrive** en toute sécurité dans une application multithread, vous devez fournir votre propre synchronisation de thread. Pour plus d’informations, consultez [SetCurrentDirectory](/windows/win32/api/winbase/nf-winbase-setcurrentdirectory).

La fonction **_chdrive** change uniquement le lecteur travail actif ; **_chdir** change le répertoire de travail actif.

Par défaut, l’état global de cette fonction est limité à l’application. Pour modifier cette valeur, consultez [état global dans le CRT](../global-state.md).

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**_chdrive**|\<direct.h>|

Pour plus d’informations, consultez [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

Consultez l’exemple relatif à [_getdrive](getdrive.md).

## <a name="see-also"></a>Voir aussi

[Contrôle de répertoire](../../c-runtime-library/directory-control.md)<br/>
[_chdir, _wchdir](chdir-wchdir.md)<br/>
[_fullpath, _wfullpath](fullpath-wfullpath.md)<br/>
[_getcwd, _wgetcwd](getcwd-wgetcwd.md)<br/>
[_getdrive](getdrive.md)<br/>
[_mkdir, _wmkdir](mkdir-wmkdir.md)<br/>
[_rmdir, _wrmdir](rmdir-wrmdir.md)<br/>
[system, _wsystem](system-wsystem.md)<br/>
