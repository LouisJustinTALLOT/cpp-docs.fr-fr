---
title: _aligned_recalloc | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _aligned_recalloc
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
- api-ms-win-crt-heap-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- aligned_recalloc
- _aligned_recalloc
dev_langs:
- C++
helpviewer_keywords:
- aligned_recalloc function
- _aligned_recalloc function
ms.assetid: d3da3dcc-79ef-4273-8af5-ac7469420142
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2792cff3c401d7710f3844bfe65640e194189586
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32393236"
---
# <a name="alignedrecalloc"></a>_aligned_recalloc

Modifie la taille d’un bloc de mémoire qui a été alloué avec [_aligned_malloc](aligned-malloc.md) ou [_aligned_offset_malloc](aligned-offset-malloc.md) et initialise la mémoire à 0.

## <a name="syntax"></a>Syntaxe

```C
void * _aligned_recalloc(
   void *memblock,
   size_t num,
   size_t size,
   size_t alignment
);
```

### <a name="parameters"></a>Paramètres

*memblock*<br/>
Pointeur de bloc de mémoire actif.

*Nombre*<br/>
Nombre d'éléments.

*size*<br/>
Taille en octets de chaque élément.

*Alignement*<br/>
Valeur d'alignement, qui doit être un entier à puissance 2.

## <a name="return-value"></a>Valeur de retour

**_aligned_recalloc** retourne un pointeur void vers le bloc de mémoire réalloué (et éventuellement déplacé). La valeur de retour est **NULL** si la taille est égale à zéro et que l’argument de la mémoire tampon n’est pas **NULL**, ou s’il n’existe pas de suffisamment de mémoire pour étendre le bloc à la taille donnée. Dans le premier cas, le bloc d'origine est libéré. Dans le second cas, le bloc d'origine est inchangé. La valeur de retour pointe vers un espace de stockage qui est obligatoirement aligné correctement pour le stockage de tout type d'objet. Pour obtenir un pointeur vers un type autre que void, utilisez un cast de type sur la valeur de retour.

Le fait de réallouer la mémoire et de modifier l'alignement d'un bloc constitue une erreur.

## <a name="remarks"></a>Notes

**_aligned_recalloc** est basée sur **malloc**. Pour plus d’informations sur l’utilisation de **_aligned_offset_malloc**, consultez [malloc](malloc.md).

Cette fonction affecte **errno** à **ENOMEM** si l’allocation de mémoire a échoué ou si la taille demandée était supérieure à **_HEAP_MAXREQ**. Pour plus d’informations sur **errno**, consultez [errno, _doserrno, _sys_errlist et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md). En outre, **_aligned_recalloc** valide ses paramètres. Si *alignement* n’est pas une puissance de 2, cette fonction appelle le Gestionnaire de paramètre non valide, comme décrit dans [Validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, cette fonction retourne **NULL** et définit **errno** à **EINVAL**.

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**_aligned_recalloc**|\<malloc.h>|

## <a name="see-also"></a>Voir aussi

[Alignement des données](../../c-runtime-library/data-alignment.md)<br/>
[_recalloc](recalloc.md)<br/>
[_aligned_offset_recalloc](aligned-offset-recalloc.md)<br/>
