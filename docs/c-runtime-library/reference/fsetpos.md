---
description: 'En savoir plus sur : fsetpos'
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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: e8259bcf4dba951bf6603fb5d4984db6ece0e266
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97114219"
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

*train*<br/>
Pointeur désignant la structure **FILE**.

*pos*<br/>
Stockage de l’indicateur de position.

## <a name="return-value"></a>Valeur renvoyée

En cas de réussite, **fsetpos** retourne 0. En cas d’échec, la fonction retourne une valeur différente de zéro et définit **errno** sur l’une des constantes manifestes suivantes (définies dans errno. H) : **EBADF**, ce qui signifie que le fichier n’est pas accessible ou que l’objet vers lequel pointe le *flux* n’est pas une structure de fichier valide ; ou **EINVAL**, ce qui signifie qu’une valeur non valide a été passée pour *Stream* ou *pos* . Si un paramètre non valide est passé, ces fonctions appellent le gestionnaire de paramètres non valides, comme décrit dans [Validation de paramètre](../../c-runtime-library/parameter-validation.md).

Pour plus d’informations sur ces codes de retour et autres, consultez [_doserrno, errno, _sys_errlist et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) .

## <a name="remarks"></a>Notes

La fonction **fsetpos** affecte à l’indicateur de position de fichier du *flux* la valeur *pos*, qui est obtenue dans un appel antérieur à **fgetpos** par rapport à *Stream*. La fonction efface l’indicateur de fin de fichier et annule les effets de [ungetc](ungetc-ungetwc.md) sur *Stream*. Après l’appel de **fsetpos**, l’opération suivante sur le *flux* peut être soit une entrée, soit une sortie.

Par défaut, l’état global de cette fonction est limité à l’application. Pour modifier cette valeur, consultez [état global dans le CRT](../global-state.md).

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
