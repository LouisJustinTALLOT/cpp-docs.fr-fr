---
title: _unlock_file
ms.date: 4/2/2020
api_name:
- _unlock_file
- _o__unlock_file
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
- _unlock_file
- unlock_file
helpviewer_keywords:
- files [C++], unlocking
- unlock_file function
- _unlock_file function
- unlocking files
ms.assetid: cf380a51-6d3a-4f38-bd64-2d4fb57b4369
ms.openlocfilehash: 46d07a8b3645ae0d68276d96271be0a246716f0b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81361222"
---
# <a name="_unlock_file"></a>_unlock_file

Déverrouille un fichier, autorisant ainsi les autres processus à y accéder.

## <a name="syntax"></a>Syntaxe

```C
void _unlock_file(
   FILE* file
);
```

### <a name="parameters"></a>Paramètres

*Fichier*<br/>
Descripteur de fichier.

## <a name="remarks"></a>Notes

La fonction **_unlock_file** déverrouille le fichier spécifié par *fichier*. Le déverrouillage d’un fichier autorise d’autres processus à y accéder. Cette fonction ne doit pas être appelée à moins **que _lock_file** a été précédemment appelé sur le pointeur *de fichier.* Appeler **_unlock_file** sur un fichier qui n’est pas verrouillé peut entraîner une impasse. Pour obtenir un exemple, consultez [_lock_file](lock-file.md).

Par défaut, l’état global de cette fonction est étendue à l’application. Pour changer cela, voir [Global State dans le CRT](../global-state.md).

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
