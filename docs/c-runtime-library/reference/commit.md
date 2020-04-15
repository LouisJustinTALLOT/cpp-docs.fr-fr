---
title: _commit
ms.date: 4/2/2020
api_name:
- _commit
- _o__commit
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
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _commit
- commit
helpviewer_keywords:
- files [C++], flushing
- flushing files to disk
- commit function
- _commit function
- committing files to disk
ms.assetid: d0c74d3a-4f2d-4fb0-b140-2d687db3d233
ms.openlocfilehash: f8e13e7fc197c66395556d518ecbd1cd20ac1f77
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81348619"
---
# <a name="_commit"></a>_commit

Vide un fichier directement sur le disque.

## <a name="syntax"></a>Syntaxe

```C
int _commit(
   int fd
);
```

### <a name="parameters"></a>Paramètres

*Fd*<br/>
Descripteur de fichier faisant référence au fichier ouvert.

## <a name="return-value"></a>Valeur de retour

**_commit** renvoie 0 si le fichier a été rincé avec succès sur disque. Une valeur de rendement de -1 indique une erreur.

## <a name="remarks"></a>Notes

La fonction **_commit** oblige le système d’exploitation à écrire le fichier associé au *fd* au disque. Grâce à cet appel, le fichier spécifié est vidé immédiatement, et non quand le système d’exploitation le souhaite.

Si *fd* est un descripteur de fichier invalide, le gestionnaire de paramètres invalide est invoqué, tel que décrit dans [La validation de paramètres](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, la fonction renvoie -1 et **errno** est réglé sur **EBADF**.

Par défaut, l’état global de cette fonction est étendue à l’application. Pour changer cela, voir [Global State dans le CRT](../global-state.md).

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|En-têtes facultatifs|
|-------------|---------------------|----------------------|
|**_commit**|\<io.h>|\<errno.h>|

Pour plus d’informations sur la compatibilité, consultez [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[E/S niveau bas](../../c-runtime-library/low-level-i-o.md)<br/>
[_creat, _wcreat](creat-wcreat.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
[_read](read.md)<br/>
[_write](write.md)<br/>
