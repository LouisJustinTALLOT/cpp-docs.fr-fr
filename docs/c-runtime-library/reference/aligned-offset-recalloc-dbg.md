---
title: _aligned_offset_recalloc_dbg
ms.date: 11/04/2016
api_name:
- _aligned_offset_recalloc_dbg
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- aligned_offset_recalloc_dbg
- _aligned_offset_recalloc_dbg
helpviewer_keywords:
- aligned_offset_recalloc_dbg function
- _aligned_offset_recalloc_dbg function
ms.assetid: 7ab719c3-77e0-4d2e-934f-01529d062fbf
ms.openlocfilehash: e363a1cb104db9973f5f9e9c67a5d40693d405ee
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70939749"
---
# <a name="_aligned_offset_recalloc_dbg"></a>_aligned_offset_recalloc_dbg

Modifie la taille d’un bloc de mémoire qui a été alloué avec [_aligned_malloc](aligned-malloc.md) ou [_aligned_offset_malloc](aligned-offset-malloc.md) et initialise la mémoire à 0 (version de débogage uniquement).

## <a name="syntax"></a>Syntaxe

```C
void * _aligned_offset_recalloc_dbg(
   void *memblock,
   size_t num,
   size_t size,
   size_t alignment,
   size_t offset,
   const char *filename,
   int linenumber
);
```

### <a name="parameters"></a>Paramètres

*memblock*<br/>
Pointeur de bloc de mémoire actif.

*certain*<br/>
Nombre d'éléments.

*size*<br/>
Longueur en octets de chaque élément.

*alignment*<br/>
Valeur d'alignement, qui doit être un entier à puissance 2.

*offset*<br/>
Décalage dans l'allocation de mémoire pour forcer l'alignement.

*filename*<br/>
Pointeur vers le nom du fichier source qui a demandé l’opération de réallocation ou **null**.

*linenumber*<br/>
Numéro de ligne dans le fichier source où l’opération de réallocation a été demandée ou **null**.

## <a name="return-value"></a>Valeur de retour

**_aligned_offset_recalloc_dbg** retourne un pointeur void vers le bloc de mémoire réalloué (et éventuellement déplacé). La valeur de retour est **null** si la taille est égale à zéro et l’argument de mémoire tampon n’est pas **null**, ou s’il n’y a pas assez de mémoire disponible pour développer le bloc à la taille donnée. Dans le premier cas, le bloc d'origine est libéré. Dans le second cas, le bloc d'origine est inchangé. La valeur de retour pointe vers un espace de stockage qui est obligatoirement aligné correctement pour le stockage de tout type d'objet. Pour obtenir un pointeur vers un type autre que void, utilisez un cast de type sur la valeur de retour.

## <a name="remarks"></a>Notes

**_aligned_offset_realloc_dbg** est une version de débogage de la fonction [_aligned_offset_recalloc](aligned-offset-recalloc.md) . Lorsque [_ DEBUG](../../c-runtime-library/debug.md) n’est pas défini, chaque appel à **_aligned_offset_recalloc_dbg** est réduit à un appel à **_aligned_offset_recalloc**. **_Aligned_offset_recalloc** et **_aligned_offset_recalloc_dbg** réallouent tous deux un bloc de mémoire dans le tas de base, mais **_aligned_offset_recalloc_dbg** prend en charge plusieurs fonctionnalités de débogage : des mémoires tampons de chaque côté de la partie utilisateur du bloc à tester pour détecter les fuites, et les informations de *nom de fichier*/*LineNumber* pour déterminer l’origine des demandes d’allocation. Le suivi de types d’allocation spécifiques avec un paramètre de type de bloc n’est pas une fonctionnalité de débogage prise en charge pour les allocations alignées. Les allocations alignées s’affichent sous la forme d’un type de bloc _NORMAL_BLOCK.

**_aligned_offset_realloc_dbg** réalloue le bloc de mémoire spécifié avec un peu plus d’espace que la fonction *NewSize*demandée. *NewSize* peut être supérieure ou inférieure à la taille du bloc de mémoire alloué initialement. L'espace supplémentaire est utilisé par le gestionnaire de tas de débogage pour lier les blocs de mémoire de débogage et pour fournir à l'application des informations sur les en-têtes de débogage et les mémoires tampons de remplacement. La réallocation peut entraîner un déplacement du bloc de mémoire initial vers un emplacement différent dans le tas, ainsi qu'une modification de la taille du bloc de mémoire. Si le bloc de mémoire est déplacé, son contenu d'origine est remplacé.

Cette fonction affecte à **errno** la valeur **ENOMEM** si l’allocation de mémoire a échoué ou si la taille demandée (*taille*du*nombre* * ) est supérieure à **_HEAP_MAXREQ**. Pour plus d’informations sur **errno**, consultez [errno, _doserrno, _sys_errlist et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md). De plus, **_aligned_offset_recalloc_dbg** valide ses paramètres. Si *alignment* n’est pas une puissance de 2 ou si *offset* est supérieur ou égal à la taille demandée et différent de zéro, cette fonction appelle le gestionnaire de paramètre non valide, comme décrit dans [validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, cette fonction retourne la **valeur null** et définit **errno** sur **EINVAL**.

Pour plus d’informations sur la façon dont les blocs de mémoire sont alloués, initialisés et gérés dans la version de débogage du tas de base, voir [CRT Debug Heap Details](/visualstudio/debugger/crt-debug-heap-details). Pour plus d’informations sur les types de bloc d’allocation et sur leur utilisation, consultez [Types de bloc sur le tas de débogage](/visualstudio/debugger/crt-debug-heap-details). Pour plus d’informations sur les différences entre l’appel à une fonction de tas standard et sa version de débogage dans la build de débogage d’une application, consultez [Versions Debug des fonctions d’allocation du tas](/visualstudio/debugger/debug-versions-of-heap-allocation-functions).

## <a name="requirements"></a>Configuration requise

|Routine|En-tête requis|
|-------------|---------------------|
|**_aligned_offset_recalloc_dbg**|\<malloc.h>|

## <a name="see-also"></a>Voir aussi

[Alignement des données](../../c-runtime-library/data-alignment.md)<br/>
