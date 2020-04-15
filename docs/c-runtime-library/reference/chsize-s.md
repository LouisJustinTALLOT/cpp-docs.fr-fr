---
title: _chsize_s
ms.date: 4/2/2020
api_name:
- _chsize_s
- _o__chsize_s
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
- chsize_s
- _chsize_s
helpviewer_keywords:
- files [C++], changing size
- chsize_s function
- _chsize_s function
ms.assetid: d88d2e94-6e3b-42a5-8631-16ac4d82fa38
ms.openlocfilehash: 70845124eb889d73a0f87aadd923e2d86db96c29
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81350075"
---
# <a name="_chsize_s"></a>_chsize_s

Modifie la taille d’un fichier. Il s’agit d’une version de [_chsize](chsize.md) assortie des améliorations de sécurité décrites dans [Fonctionnalités de sécurité dans le CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Syntaxe

```C
errno_t _chsize_s(
   int fd,
   __int64 size
);
```

### <a name="parameters"></a>Paramètres

*Fd*<br/>
Descripteur de fichier qui fait référence à un fichier ouvert.

*Taille*<br/>
Nouvelle longueur, en octets, du fichier.

## <a name="return-value"></a>Valeur de retour

**_chsize_s** retourne la valeur 0 si la taille du fichier est modifiée avec succès. Une valeur de retour non zéro indique une erreur : la valeur de retour est **EACCES** si le fichier spécifié est verrouillé contre l’accès, **EBADF** si le fichier spécifié est lu uniquement ou le descripteur est invalide, **ENOSPC** si aucun espace n’est laissé sur l’appareil, ou **EINVAL** si la taille est inférieure à zéro. **errno** est réglé à la même valeur.

Pour plus d’informations sur ces codes de retour et les autres, consultez [_doserrno, errno, _sys_errlist et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Notes

La fonction **_chsize_s** étend ou tronque le fichier associé à *fd* à la longueur spécifiée par *la taille*. Le fichier doit être ouvert dans un mode qui permet l’écriture. Des caractères Null (« \0 ») sont ajoutés si le fichier est étendu. Si le fichier est tronqué, toutes les données depuis la fin du fichier raccourci jusqu’à la longueur d’origine du fichier sont perdues.

**_chsize_s** prend un intégrier 64 bits que la taille du fichier, et peut donc gérer la taille des fichiers de plus de 4 Go. **_chsize** est limitée à la taille des fichiers 32 bits.

Cette fonction valide ses paramètres. Si *fd n’est* pas un descripteur de fichier valide ou la taille est inférieure à zéro, le gestionnaire de paramètres invalides est invoqué, tel que décrit dans [La validation de paramètres](../../c-runtime-library/parameter-validation.md).

Par défaut, l’état global de cette fonction est étendue à l’application. Pour changer cela, voir [Global State dans le CRT](../global-state.md).

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|En-tête facultatif|
|-------------|---------------------|---------------------|
|**_chsize_s**|\<io.h>|\<errno.h>|

Pour plus d’informations sur la compatibilité, consultez [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[Gestion de fichiers](../../c-runtime-library/file-handling.md)<br/>
[_chsize](chsize.md)<br/>
[_close](close.md)<br/>
[_creat, _wcreat](creat-wcreat.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
