---
description: 'En savoir plus sur : _aligned_realloc'
title: _aligned_realloc
ms.date: 4/2/2020
api_name:
- _aligned_realloc
- _o__aligned_realloc
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
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _aligned_realloc
- aligned_realloc
helpviewer_keywords:
- aligned_realloc function
- _aligned_realloc function
ms.assetid: 80ce96e8-6087-416f-88aa-4dbb8cb1d218
ms.openlocfilehash: 305610f7eed8be180c9324f0e1e56e4af2f6a79b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97312486"
---
# <a name="_aligned_realloc"></a>_aligned_realloc

Modifie la taille d’un bloc de mémoire qui a été alloué avec [_aligned_malloc](aligned-malloc.md) ou [_aligned_offset_malloc](aligned-offset-malloc.md).

## <a name="syntax"></a>Syntaxe

```C
void * _aligned_realloc(
   void *memblock,
   size_t size,
   size_t alignment
);
```

### <a name="parameters"></a>Paramètres

*memblock*<br/>
Pointeur de bloc de mémoire actif.

*size*<br/>
Taille de l'allocation de mémoire demandée.

*repère*<br/>
Valeur d'alignement, qui doit être un entier à puissance 2.

## <a name="return-value"></a>Valeur renvoyée

**_aligned_realloc** retourne un pointeur void vers le bloc de mémoire réalloué (et éventuellement déplacé). La valeur de retour est **null** si la taille est égale à zéro et l’argument de mémoire tampon n’est pas **null**, ou s’il n’y a pas assez de mémoire disponible pour développer le bloc à la taille donnée. Dans le premier cas, le bloc d'origine est libéré. Dans le second cas, le bloc d'origine est inchangé. La valeur de retour pointe vers un espace de stockage qui est obligatoirement aligné correctement pour le stockage de tout type d'objet. Pour obtenir un pointeur vers un type autre que void, utilisez un cast de type sur la valeur de retour.

Le fait de réallouer la mémoire et de modifier l'alignement d'un bloc constitue une erreur.

## <a name="remarks"></a>Notes

**_aligned_realloc** est basé sur **malloc**. Pour plus d’informations sur l’utilisation de **_aligned_offset_malloc**, consultez [malloc](malloc.md).

Cette fonction affecte à **errno** la valeur **ENOMEM** si l’allocation de mémoire a échoué ou si la taille demandée était supérieure à **_HEAP_MAXREQ**. Pour plus d’informations sur **errno**, consultez [errno, _doserrno, _sys_errlist et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md). De plus, **_aligned_realloc** valide ses paramètres. Si *alignment* n’est pas une puissance de 2, cette fonction appelle le gestionnaire de paramètre non valide, comme décrit dans [validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, cette fonction retourne la **valeur null** et définit **errno** sur **EINVAL**.

Par défaut, l’état global de cette fonction est limité à l’application. Pour modifier cette valeur, consultez [état global dans le CRT](../global-state.md).

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**_aligned_realloc**|\<malloc.h>|

## <a name="example"></a>Exemple

Pour plus d’informations, consultez [_aligned_malloc](aligned-malloc.md).

## <a name="see-also"></a>Voir aussi

[Alignement des données](../../c-runtime-library/data-alignment.md)<br/>
