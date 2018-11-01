---
title: _unlock_file
ms.date: 11/04/2016
apiname:
- _unlock_file
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
- _unlock_file
- unlock_file
helpviewer_keywords:
- files [C++], unlocking
- unlock_file function
- _unlock_file function
- unlocking files
ms.assetid: cf380a51-6d3a-4f38-bd64-2d4fb57b4369
ms.openlocfilehash: e3d11cbd59ef5846b33908ae6b6c40d7ea6125e8
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50552527"
---
# <a name="unlockfile"></a>_unlock_file

Déverrouille un fichier, autorisant ainsi les autres processus à y accéder.

## <a name="syntax"></a>Syntaxe

```C
void _unlock_file(
   FILE* file
);
```

### <a name="parameters"></a>Paramètres

*fichier*<br/>
Descripteur de fichier.

## <a name="remarks"></a>Notes

Le **_unlock_file** fonction déverrouille le fichier spécifié par *fichier*. Le déverrouillage d’un fichier autorise d’autres processus à y accéder. Cette fonction ne doit pas être appelée, sauf si **_lock_file** a été appelée précédemment sur le *fichier* pointeur. Appel **_unlock_file** sur un fichier qui n’est pas verrouillé peut provoquer un interblocage. Pour obtenir un exemple, consultez [_lock_file](lock-file.md).

## <a name="requirements"></a>Configuration requise

|Routine|En-tête requis|
|-------------|---------------------|
|**_unlock_file**|\<stdio.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[Gestion de fichiers](../../c-runtime-library/file-handling.md)<br/>
[_creat, _wcreat](creat-wcreat.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
[_lock_file](lock-file.md)<br/>
