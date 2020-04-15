---
title: _aligned_offset_recalloc
ms.date: 4/2/2020
api_name:
- _aligned_offset_recalloc
- _o__aligned_offset_recalloc
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
- api-ms-win-crt-heap-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- aligned_offset_recalloc
- _aligned_offset_recalloc
helpviewer_keywords:
- aligned_offset_recalloc function
- _aligned_offset_recalloc function
ms.assetid: a258f54e-eeb4-4853-96fc-007d710f98e9
ms.openlocfilehash: 4c710712138d07191468cdc7ef02fc75e2f46dad
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81350543"
---
# <a name="_aligned_offset_recalloc"></a>_aligned_offset_recalloc

Modifie la taille d’un bloc de mémoire qui a été alloué avec [_aligned_malloc](aligned-malloc.md) ou [_aligned_offset_malloc](aligned-offset-malloc.md) et initialise la mémoire à 0.

## <a name="syntax"></a>Syntaxe

```C
void * _aligned_offset_recalloc(
   void *memblock,
   size_t num,
   size_t size,
   size_t alignment,
   size_t offset
);
```

### <a name="parameters"></a>Paramètres

*memblock*<br/>
Pointeur de bloc de mémoire actif.

*nombre*<br/>
Nombre d'éléments.

*Taille*<br/>
Longueur en octets de chaque élément.

*Alignement*<br/>
Valeur d'alignement, qui doit être un entier à puissance 2.

*offset*<br/>
Décalage dans l'allocation de mémoire pour forcer l'alignement.

## <a name="return-value"></a>Valeur de retour

**_aligned_offset_recalloc** retourne un pointeur vide au bloc de mémoire réaffecté (et peut-être déplacé). La valeur de retour est **NULL** si la taille est nulle et l’argument tampon n’est pas **NULL**, ou s’il n’y a pas assez de mémoire disponible pour étendre le bloc à la taille donnée. Dans le premier cas, le bloc d'origine est libéré. Dans le second cas, le bloc d'origine est inchangé. La valeur de retour pointe vers un espace de stockage qui est obligatoirement aligné correctement pour le stockage de tout type d'objet. Pour obtenir un pointeur vers un type autre que void, utilisez un cast de type sur la valeur de retour.

**_aligned_offset_recalloc** est marquée `__declspec(noalias)` `__declspec(restrict)`et, ce qui signifie que la fonction est garantie de ne pas modifier les variables globales et que le pointeur retourné n’est pas alias. Pour plus d’informations, consultez [noalias](../../cpp/noalias.md) et [restrict](../../cpp/restrict.md).

## <a name="remarks"></a>Notes

Comme [_aligned_offset_malloc](aligned-offset-malloc.md), **_aligned_offset_recalloc** permet d’aligner une structure à un décalage au sein de la structure.

**_aligned_offset_recalloc** est basé sur **malloc**. Pour plus d’informations sur l’utilisation **de _aligned_offset_malloc**, voir [malloc](malloc.md). Si *memblock* est **NULL**, la fonction appelle **_aligned_offset_malloc** interne.

Cette fonction définit **errno** à **ENOMEM** si l’allocation de mémoire a échoué ou si la taille demandée *(taille**de nombre* * ) était supérieure **à _HEAP_MAXREQ**. Pour plus d’informations sur **errno**, voir [errno, _doserrno, _sys_errlist, et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md). En outre, **_aligned_offset_recalloc** valide ses paramètres. Si *l’alignement* n’est pas une puissance de 2 ou si le *décalage* est supérieur ou égal à la taille demandée et nonzero, cette fonction invoque le gestionnaire de paramètres invalide, tel que décrit dans la validation [de paramètres](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, cette fonction renvoie **NULL** et définit **errno** à **EINVAL**.

Par défaut, l’état global de cette fonction est étendue à l’application. Pour changer cela, voir [Global State dans le CRT](../global-state.md).

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**_aligned_offset_recalloc**|\<malloc.h>|

## <a name="see-also"></a>Voir aussi

[Alignement des données](../../c-runtime-library/data-alignment.md)<br/>
[_recalloc](recalloc.md)<br/>
[_aligned_recalloc](aligned-recalloc.md)<br/>
