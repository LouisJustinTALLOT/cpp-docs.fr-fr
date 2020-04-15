---
title: fsetpos
ms.date: 4/2/2020
api_name:
- fsetpos
- _o_fsetpos
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
- fsetpos
helpviewer_keywords:
- streams, setting position indicators
- fsetpos function
ms.assetid: 6d19ff48-1a2b-47b3-9f23-ed0a47b5a46e
ms.openlocfilehash: 22b8cebd0154c0dbfc3d21843380ebc9a139059a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81345717"
---
# <a name="fsetpos"></a>fsetpos

Définit l’indicateur de position de flux.

## <a name="syntax"></a>Syntaxe

```C
int fsetpos(
   FILE *stream,
   const fpos_t *pos
);
```

### <a name="parameters"></a>Paramètres

*Flux*<br/>
Pointeur désignant la structure **FILE**.

*Pos*<br/>
Stockage de l’indicateur de position.

## <a name="return-value"></a>Valeur de retour

En cas de succès, **fsetpos** retourne 0. Lors de l’échec, la fonction renvoie une valeur non zéro et définit **errno** à l’une des constantes manifestes suivantes (définie dans ERRNO. H) : **EBADF**, ce qui signifie que le fichier n’est pas accessible ou que l’objet auquel le *flux indique* n’est pas une structure de fichier valide; **ou EINVAL**, ce qui signifie qu’une valeur invalide pour *le flux* ou le *pos* a été adoptée. Si un paramètre non valide est passé, ces fonctions appellent le gestionnaire de paramètres non valides, comme décrit dans [Validation de paramètre](../../c-runtime-library/parameter-validation.md).

Voir [_doserrno, errno, _sys_errlist, et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) pour plus d’informations sur ces codes de retour, et d’autres.

## <a name="remarks"></a>Notes

La fonction **fsetpos** définit l’indicateur de position de fichier pour le *flux* à la valeur de *pos*, qui est obtenu dans un appel antérieur à **fgetpos** contre *le flux*. La fonction efface l’indicateur de fin de fichier et annule tout effet de [nongetc](ungetc-ungetwc.md) sur *le flux*. Après avoir appelé **fsetpos**, la prochaine opération sur *le flux* peut être soit entrée ou sortie.

Par défaut, l’état global de cette fonction est étendue à l’application. Pour changer cela, voir [Global State dans le CRT](../global-state.md).

## <a name="requirements"></a>Spécifications

|Fonction|En-tête requis|
|--------------|---------------------|
|**fsetpos**|\<stdio.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

Consultez l’exemple relatif à [fgetpos](fgetpos.md).

## <a name="see-also"></a>Voir aussi

[E/S de flux](../../c-runtime-library/stream-i-o.md)<br/>
[fgetpos](fgetpos.md)<br/>
