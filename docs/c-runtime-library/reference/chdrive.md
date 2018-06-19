---
title: _chdrive | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _chdrive
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
- chdrive
- _chdrive
dev_langs:
- C++
helpviewer_keywords:
- drives, changing
- _chdrive function
- chdrive function
ms.assetid: 212a1a4b-4fa8-444e-9677-7fca4c8c47e3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8f95169f62fa2eaf9c562bff463ad84c0827db9a
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32394420"
---
# <a name="chdrive"></a>_chdrive

Change le lecteur de travail actif.

> [!IMPORTANT]
> Cette API ne peut pas être utilisée dans les applications qui s’exécutent dans le Windows Runtime. Pour plus d’informations, consultez [Fonctions CRT non prises en charge dans les applications de la plateforme Windows universelle](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntaxe

```C
int _chdrive(
   int drive
);
```

### <a name="parameters"></a>Paramètres

*Lecteur*<br/>
Entier compris entre 1 et 26 qui spécifie le lecteur de travail actif (1=A, 2=B et ainsi de suite).

## <a name="return-value"></a>Valeur de retour

Zéro (0) si le lecteur de travail actif a été correctement changé ; Sinon, -1.

## <a name="remarks"></a>Notes

Si *lecteur* est pas dans la plage comprise entre 1 et 26, le Gestionnaire de paramètres non valides est appelé, comme décrit dans [Validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, la **_chdrive** fonction retourne -1, **errno** a la valeur **EACCES**, et **_doserrno** alavaleur **ERROR_INVALID_DRIVE**.

La fonction **_chdrive** n’est pas thread-safe, car elle dépend de la fonction **SetCurrentDirectory**, qui elle-même n’est pas thread-safe. Pour utiliser **_chdrive** en toute sécurité dans une application multithread, vous devez fournir votre propre synchronisation de thread. Pour plus d’informations, accédez à [MSDN Library](http://go.microsoft.com/fwlink/p/?linkid=150542), puis recherchez **SetCurrentDirectory**.

La fonction **_chdrive** change uniquement le lecteur travail actif ; **_chdir** change le répertoire de travail actif.

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**_chdrive**|\<direct.h>|

Pour plus d'informations, voir [Compatibilité](../../c-runtime-library/compatibility.md).

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
