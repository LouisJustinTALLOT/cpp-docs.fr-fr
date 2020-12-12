---
description: 'En savoir plus sur : _get_osfhandle'
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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: 72f6a2f695868bdc4a5d13c09d1d34152cf9e51e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97321134"
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

*FD*<br/>
Descripteur de fichier existant.

## <a name="return-value"></a>Valeur renvoyée

Retourne un descripteur de fichier de système d’exploitation si *FD* est valide. Sinon, le gestionnaire de paramètres non valides est appelé, comme décrit dans [Validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, elle retourne **INVALID_HANDLE_VALUE** (-1). Il définit également **errno** sur **EBADF**, ce qui indique un descripteur de fichier non valide. Pour éviter un avertissement lorsque le résultat est utilisé comme handle de fichier Win32, effectuez un cast de celui-ci en un type de **handle** .

> [!NOTE]
> Lorsque **stdin**, **stdout** et **stderr** ne sont pas associés à un flux (par exemple, dans une application Windows sans fenêtre de console), les valeurs de descripteur de fichier pour ces flux sont retournées à partir de [_fileno](fileno.md) comme valeur spéciale-2. De même, si vous utilisez 0, 1 ou 2 comme paramètre de descripteur de fichier au lieu du résultat d’un appel à **_fileno**, **_get_osfhandle** retourne également la valeur spéciale-2 lorsque le descripteur de fichier n’est pas associé à un flux et ne définit pas **errno**. Toutefois, il ne s’agit pas d’une valeur de descripteur de fichier valide, et les appels suivants qui tentent de l’utiliser sont susceptibles d’échouer.

Pour plus d’informations sur **EBADF** et d’autres codes d’erreur, consultez [_doserrno, errno, _sys_errlist et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Notes

Pour fermer un fichier dont le descripteur de fichier du système d’exploitation est obtenu par **_get_osfhandle**, appelez [_close](close.md) sur le descripteur de fichier *FD*. N’appelez jamais **CloseHandle** sur la valeur de retour de cette fonction. Le descripteur de fichier de système d’exploitation sous-jacent appartient au descripteur de fichier *FD* et est fermé lorsque [_close](close.md) est appelé sur *FD*. Si le descripteur de fichier appartient à un `FILE *` flux, l’appel de [fclose](fclose-fcloseall.md) sur ce `FILE *` flux ferme à la fois le descripteur de fichier et le handle de fichier du système d’exploitation sous-jacent. Dans ce cas, n’appelez pas [_close](close.md) sur le descripteur de fichier.

Par défaut, l’état global de cette fonction est limité à l’application. Pour modifier cette valeur, consultez [état global dans le CRT](../global-state.md).

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
