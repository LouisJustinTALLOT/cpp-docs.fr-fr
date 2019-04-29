---
title: _get_osfhandle
ms.date: 05/29/2018
apiname:
- _get_osfhandle
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
- get_osfhandle
- _get_osfhandle
helpviewer_keywords:
- operating systems, getting file handles
- get_osfhandle function
- _get_osfhandle function
- file handles [C++], operating system
ms.assetid: 0bdd728a-4fd8-410b-8c9f-01a121135196
ms.openlocfilehash: beab4e4308bc7bcde287366b78671f61a89f8827
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62332206"
---
# <a name="getosfhandle"></a>_get_osfhandle

Récupère le handle de fichier du système d’exploitation qui est associé au descripteur de fichier spécifié.

## <a name="syntax"></a>Syntaxe

```C
intptr_t _get_osfhandle(
   int fd
);
```

### <a name="parameters"></a>Paramètres

*fd*<br/>
Descripteur de fichier existant.

## <a name="return-value"></a>Valeur de retour

Retourne un handle de fichier du système d’exploitation si *fd* est valide. Sinon, le gestionnaire de paramètres non valides est appelé, comme décrit dans [Validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, cette fonction retourne **INVALID_HANDLE_VALUE** (-1) et définit **errno** à **EBADF**, indiquant un handle de fichier non valide. Pour éviter un avertissement du compilateur lorsque le résultat est utilisé dans les routines qui attendent un descripteur de fichier Win32, effectuer un cast en un **gérer** type.

## <a name="remarks"></a>Notes

Pour fermer un fichier dont handle de fichier du système d’exploitation (se) est obtenu en **_get_osfhandle**, appelez [_close](close.md) sur le descripteur de fichier *fd*. N’appelez pas **CloseHandle** sur la valeur de retour de cette fonction. Le handle de fichier du système d’exploitation sous-jacent est détenu par le *fd* descripteur de fichier et est fermé lorsque [_close](close.md) est appelée sur *fd*. Si le descripteur de fichier est détenu par un `FILE *` flux, puis en appelant [fclose](fclose-fcloseall.md) sur qui `FILE *` flux ferme le descripteur de fichier et le handle de fichier du système d’exploitation sous-jacent. Dans ce cas, n’appelez pas [_close](close.md) sur le descripteur de fichier.

## <a name="requirements"></a>Configuration requise

|Routine|En-tête requis|
|-------------|---------------------|
|**_get_osfhandle**|\<io.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[Gestion de fichiers](../../c-runtime-library/file-handling.md)<br/>
[_close](close.md)<br/>
[_creat, _wcreat](creat-wcreat.md)<br/>
[_dup, _dup2](dup-dup2.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
