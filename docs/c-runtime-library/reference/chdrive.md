---
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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: 0c19fefcf6a766842ee2e25cbe6bdb61bbf48e7d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81333346"
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

*Disque*<br/>
Entier compris entre 1 et 26 qui spécifie le lecteur de travail actif (1=A, 2=B et ainsi de suite).

## <a name="return-value"></a>Valeur de retour

Zéro (0) si le lecteur de travail actif a été correctement changé ; Sinon, -1.

## <a name="remarks"></a>Notes

Si *le lecteur* n’est pas dans la plage de 1 à 26, le gestionnaire de paramètres invalides est invoqué comme décrit dans La validation de [paramètres](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, la fonction **_chdrive** renvoie -1, **errno** est réglé sur **EACCES**, et **_doserrno** est mis à **ERROR_INVALID_DRIVE**.

La fonction **_chdrive** n’est pas thread-safe, car elle dépend de la fonction **SetCurrentDirectory**, qui elle-même n’est pas thread-safe. Pour utiliser **_chdrive** en toute sécurité dans une application multithread, vous devez fournir votre propre synchronisation de thread. Pour plus d’informations, voir [SetCurrentDirectory](/windows/win32/api/winbase/nf-winbase-setcurrentdirectory).

La fonction **_chdrive** change uniquement le lecteur travail actif ; **_chdir** change le répertoire de travail actif.

Par défaut, l’état global de cette fonction est étendue à l’application. Pour changer cela, voir [Global State dans le CRT](../global-state.md).

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
