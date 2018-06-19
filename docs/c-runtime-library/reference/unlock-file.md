---
title: _unlock_file | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- files [C++], unlocking
- unlock_file function
- _unlock_file function
- unlocking files
ms.assetid: cf380a51-6d3a-4f38-bd64-2d4fb57b4369
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d000dce4c0009341c787a211ed8ef41d1728b51b
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32407770"
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

*fichier* descripteur de fichier.

## <a name="remarks"></a>Notes

Le **_unlock_file** fonction déverrouille le fichier spécifié par *fichier*. Le déverrouillage d’un fichier autorise d’autres processus à y accéder. Cette fonction ne doit pas être appelée, sauf si **_lock_file** a été appelée précédemment sur le *fichier* pointeur. Appel de **_unlock_file** sur un fichier qui n’est pas verrouillé peut provoquer un blocage. Pour obtenir un exemple, consultez [_lock_file](lock-file.md).

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**_unlock_file**|\<stdio.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[Gestion de fichiers](../../c-runtime-library/file-handling.md)<br/>
[_creat, _wcreat](creat-wcreat.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
[_lock_file](lock-file.md)<br/>
