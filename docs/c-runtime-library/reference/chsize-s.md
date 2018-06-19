---
title: _chsize_s | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _chsize_s
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
- chsize_s
- _chsize_s
dev_langs:
- C++
helpviewer_keywords:
- files [C++], changing size
- chsize_s function
- _chsize_s function
ms.assetid: d88d2e94-6e3b-42a5-8631-16ac4d82fa38
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d131f5e21fa4980e77cfb9dc858d5329b94e2b93
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32395109"
---
# <a name="chsizes"></a>_chsize_s

Modifie la taille d’un fichier. Il s’agit d’une version de [_chsize](chsize.md) assortie des améliorations de sécurité décrites dans [Fonctionnalités de sécurité dans le CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Syntaxe

```C
errno_t _chsize_s(
   int fd,
   __int64 size
);
```

### <a name="parameters"></a>Paramètres

*fd*<br/>
Descripteur de fichier qui fait référence à un fichier ouvert.

*size*<br/>
Nouvelle longueur, en octets, du fichier.

## <a name="return-value"></a>Valeur de retour

**_chsize_s** renvoie la valeur 0 si la taille du fichier est modifiée avec succès. Une valeur de retour différente de zéro indique une erreur : la valeur de retour est **EACCES** si le fichier spécifié est verrouillé contre tout accès, **EBADF** si le fichier spécifié est en lecture seule ou si le descripteur n’est pas valide, **ENOSPC** si aucun espace n’est pas sur l’appareil, ou **EINVAL** si la taille est inférieure à zéro. **errno** est définie sur la même valeur.

Pour plus d'informations sur ces codes de retour et autres, consultez [_doserrno, errno, _sys_errlist et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Notes

Le **_chsize_s** fonction étend ou tronque le fichier associé *fd* à la longueur spécifiée par *taille*. Le fichier doit être ouvert dans un mode qui permet l’écriture. Des caractères Null (« \0 ») sont ajoutés si le fichier est étendu. Si le fichier est tronqué, toutes les données depuis la fin du fichier raccourci jusqu’à la longueur d’origine du fichier sont perdues.

**_chsize_s** accepte un entier 64 bits en tant que la taille du fichier et par conséquent, peut gérer des tailles de fichiers supérieures à 4 Go. **_chsize** est limité aux tailles de fichiers 32 bits.

Cette fonction valide ses paramètres. Si *fd* n’est pas un descripteur de fichier valide ou la taille est inférieure à zéro, le Gestionnaire de paramètre non valide est appelé, comme décrit dans [Validation de paramètre](../../c-runtime-library/parameter-validation.md).

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|En-tête facultatif|
|-------------|---------------------|---------------------|
|**_chsize_s**|\<io.h>|\<errno.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[Gestion de fichiers](../../c-runtime-library/file-handling.md)<br/>
[_chsize](chsize.md)<br/>
[_close](close.md)<br/>
[_creat, _wcreat](creat-wcreat.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
