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
ms.openlocfilehash: cc3b50e3d3f65bee83b8df83aa0adb5c8694e35a
ms.sourcegitcommit: 8adabe177d557c74566c13145196c11cef5d10d4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/10/2019
ms.locfileid: "66821644"
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

Retourne un handle de fichier du système d’exploitation si *fd* est valide. Sinon, le gestionnaire de paramètres non valides est appelé, comme décrit dans [Validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, elle retourne **INVALID_HANDLE_VALUE** (-1). Il définit également **errno** à **EBADF**, indiquant un handle de fichier non valide. Pour éviter un avertissement lorsque le résultat est utilisé comme un descripteur de fichier Win32, effectuer un cast en un **gérer** type.

> [!NOTE]
> Lorsque **stdin**, **stdout**, et **stderr** ne sont pas associé à un flux (par exemple, dans une application Windows sans fenêtre de console), les valeurs du descripteur de fichier pour Ces flux est retournés à partir de [_fileno](fileno.md) comme spéciale, valeur -2. De même, si vous utilisez un 0, 1 ou 2 en tant que le paramètre de descripteur de fichier au lieu du résultat d’un appel à **_fileno**, **_get_osfhandle** retourne également la valeur spéciale -2 lorsque le descripteur de fichier n’est pas associé avec un flux de données et ne définit pas **errno**. Toutefois, cela n’est pas une valeur de handle de fichier valide, et qui tentent d’utiliser les appels suivants sont susceptibles d’échouer.

Pour plus d’informations sur **EBADF** et autres codes d’erreur, consultez [_doserrno, errno, _sys_errlist et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Notes

Pour fermer un fichier dont handle de fichier du système d’exploitation (se) est obtenu en **_get_osfhandle**, appelez [_close](close.md) sur le descripteur de fichier *fd*. Ne jamais appeler **CloseHandle** sur la valeur de retour de cette fonction. Le handle de fichier du système d’exploitation sous-jacent est détenu par le *fd* descripteur de fichier et est fermé lorsque [_close](close.md) est appelée sur *fd*. Si le descripteur de fichier est détenu par un `FILE *` flux, puis en appelant [fclose](fclose-fcloseall.md) sur qui `FILE *` flux ferme le descripteur de fichier et le handle de fichier du système d’exploitation sous-jacent. Dans ce cas, n’appelez pas [_close](close.md) sur le descripteur de fichier.

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
[\_open_osfhandle](open-osfhandle.md)
