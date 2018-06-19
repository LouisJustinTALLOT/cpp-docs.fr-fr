---
title: _close | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _close
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
- api-ms-win-crt-stdio-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _close
dev_langs:
- C++
helpviewer_keywords:
- _close function
- close function
- files [C++], closing
ms.assetid: 4708a329-8acf-4cd9-b7b0-a952e1897247
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: eabf084d2e4dd7e280c0ff730d1ec34d86f1ed98
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32394195"
---
# <a name="close"></a>_close

Ferme un fichier.

## <a name="syntax"></a>Syntaxe

```C
int _close(
   int fd
);
```

### <a name="parameters"></a>Paramètres

*fd*<br/>
Descripteur de fichier faisant référence au fichier ouvert.

## <a name="return-value"></a>Valeur de retour

**_close** retourne 0 si le fichier a été correctement fermé. Une valeur de retour de -1 indique une erreur.

## <a name="remarks"></a>Notes

Le **_close** fonction ferme le fichier associé *fd*.

Le descripteur de fichier et le handle de fichier du système d’exploitation sous-jacent sont fermés. Par conséquent, il n’est pas nécessaire d’appeler **CloseHandle** si le fichier a été ouvert à l’origine à l’aide de la fonction Win32 **CreateFile** et converti en un descripteur de fichier à l’aide de **_open_osfhandle**.

Cette fonction valide ses paramètres. Si *fd* est un descripteur de fichier incorrect, le Gestionnaire de paramètre non valide est appelé, comme décrit dans [Validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, les fonctions retournent -1 et **errno** a la valeur **EBADF**.

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|En-tête facultatif|
|-------------|---------------------|---------------------|
|**_close**|\<io.h>|\<errno.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

Consultez l’exemple relatif à [_open](open-wopen.md).

## <a name="see-also"></a>Voir aussi

[E/S de bas niveau](../../c-runtime-library/low-level-i-o.md)<br/>
[_chsize](chsize.md)<br/>
[_creat, _wcreat](creat-wcreat.md)<br/>
[_dup, _dup2](dup-dup2.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
[_unlink, _wunlink](unlink-wunlink.md)<br/>
