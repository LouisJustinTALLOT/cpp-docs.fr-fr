---
title: _close
ms.date: 4/2/2020
api_name:
- _close
- _o__close
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
- _close
helpviewer_keywords:
- _close function
- close function
- files [C++], closing
ms.assetid: 4708a329-8acf-4cd9-b7b0-a952e1897247
ms.openlocfilehash: 4d8b702a10624ae80629b4ce4644c428322500cb
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81348642"
---
# <a name="_close"></a>_close

Ferme un fichier.

## <a name="syntax"></a>Syntaxe

```C
int _close(
   int fd
);
```

### <a name="parameters"></a>Paramètres

*Fd*<br/>
Descripteur de fichier faisant référence au fichier ouvert.

## <a name="return-value"></a>Valeur de retour

**_close** renvoie 0 si le fichier a été fermé avec succès. Une valeur de rendement de -1 indique une erreur.

## <a name="remarks"></a>Notes

La fonction **_close** ferme le fichier associé à *fd*.

Le descripteur de fichier et le handle de fichier du système d’exploitation sous-jacent sont fermés. Ainsi, il n’est pas nécessaire d’appeler **CloseHandle** si le fichier a été ouvert à l’origine en utilisant la fonction Win32 **CreateFile** et converti en un descripteur de fichiers en utilisant **_open_osfhandle**.

Cette fonction valide ses paramètres. Si *fd* est un mauvais descripteur de fichier, le gestionnaire de paramètre invalide est invoqué, tel que décrit dans [La validation de paramètres](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, les fonctions renvoient -1 et **errno** est réglé sur **EBADF**.

Par défaut, l’état global de cette fonction est étendue à l’application. Pour changer cela, voir [Global State dans le CRT](../global-state.md).

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|En-tête facultatif|
|-------------|---------------------|---------------------|
|**_close**|\<io.h>|\<errno.h>|

Pour plus d’informations sur la compatibilité, consultez [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

Consultez l’exemple relatif à [_open](open-wopen.md).

## <a name="see-also"></a>Voir aussi

[E/S niveau bas](../../c-runtime-library/low-level-i-o.md)<br/>
[_chsize](chsize.md)<br/>
[_creat, _wcreat](creat-wcreat.md)<br/>
[_dup, _dup2](dup-dup2.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
[_unlink, _wunlink](unlink-wunlink.md)<br/>
