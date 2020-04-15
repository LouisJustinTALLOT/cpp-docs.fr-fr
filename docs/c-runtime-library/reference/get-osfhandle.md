---
title: _get_osfhandle
ms.date: 4/2/2020
api_name:
- _get_osfhandle
- _o__get_osfhandle
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
- get_osfhandle
- _get_osfhandle
helpviewer_keywords:
- operating systems, getting file handles
- get_osfhandle function
- _get_osfhandle function
- file handles [C++], operating system
ms.assetid: 0bdd728a-4fd8-410b-8c9f-01a121135196
ms.openlocfilehash: a12c0c93ae15350a4b91a8aa905acb941f8b6a10
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81345033"
---
# <a name="_get_osfhandle"></a>_get_osfhandle

Récupère le handle de fichier du système d’exploitation qui est associé au descripteur de fichier spécifié.

## <a name="syntax"></a>Syntaxe

```C
intptr_t _get_osfhandle(
   int fd
);
```

### <a name="parameters"></a>Paramètres

*Fd*<br/>
Descripteur de fichier existant.

## <a name="return-value"></a>Valeur de retour

Renvoie une poignée de fichier système d’exploitation si *le fd* est valide. Sinon, le gestionnaire de paramètres non valides est appelé, comme décrit dans [Validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution se poursuit, elle renvoie **INVALID_HANDLE_VALUE** (-1). Il définit également **errno** à **EBADF**, indiquant une poignée de fichier invalide. Pour éviter un avertissement lorsque le résultat est utilisé comme poignée de fichier Win32, jetez-le à un type **HANDLE.**

> [!NOTE]
> Lorsque **stdin**, **stdout**, et **stderr** ne sont pas associés à un flux (par exemple, dans une application Windows sans fenêtre de console), les valeurs descripteur de fichier pour ces flux sont retournés de [_fileno](fileno.md) comme la valeur spéciale -2. De même, si vous utilisez un 0, 1 ou 2 comme paramètre descripteur de fichier au lieu du résultat d’un appel à **_fileno**, **_get_osfhandle** retourne également la valeur spéciale -2 lorsque le descripteur de fichier n’est pas associé à un flux, et ne fixe pas **errno**. Cependant, il ne s’agit pas d’une valeur valide de poignée de fichier, et les appels ultérieurs qui tentent de l’utiliser sont susceptibles d’échouer.

Pour plus d’informations sur **EBADF** et d’autres codes d’erreur, voir [_doserrno, errno, _sys_errlist, et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Notes

Pour fermer un fichier dont le système d’exploitation (OS) poignée de fichier est obtenu par **_get_osfhandle**, appelez [_close](close.md) sur le fichier descriptor *fd*. N’appelez jamais **CloseHandle** sur la valeur de retour de cette fonction. La poignée de fichier OS sous-jacente appartient au descripteur de fichiers *fd,* et est fermée lorsque [_close](close.md) est appelé sur *fd*. Si le descripteur de `FILE *` fichier est la propriété d’un flux, puis l’appel [fclose](fclose-fcloseall.md) sur ce `FILE *` flux ferme à la fois le descripteur de fichier et la poignée de fichier OS sous-jacente. Dans ce cas, n’appelez pas [_close](close.md) sur le descripteur du fichier.

Par défaut, l’état global de cette fonction est étendue à l’application. Pour changer cela, voir [Global State dans le CRT](../global-state.md).

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**_get_osfhandle**|\<io.h>|

Pour plus d’informations sur la compatibilité, consultez [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[Gestion de fichiers](../../c-runtime-library/file-handling.md)<br/>
[_close](close.md)<br/>
[_creat, _wcreat](creat-wcreat.md)<br/>
[_dup, _dup2](dup-dup2.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
[\_open_osfhandle](open-osfhandle.md)
