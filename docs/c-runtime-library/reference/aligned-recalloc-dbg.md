---
title: _aligned_recalloc_dbg
ms.date: 11/04/2016
apiname:
- _aligned_recalloc_dbg
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
apitype: DLLExport
f1_keywords:
- _aligned_recalloc_dbg
- aligned_recalloc_dbg
helpviewer_keywords:
- aligned_recalloc_dbg function
- _aligned_recalloc_dbg function
ms.assetid: 55c3c27e-561c-4d6b-9bf9-1e34cc556e4b
ms.openlocfilehash: c0f0cacc5efa5e63cbe05b481f922b35742e3924
ms.sourcegitcommit: 180f63704f6ddd07a4172a93b179cf0733fd952d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70740045"
---
# <a name="_aligned_recalloc_dbg"></a>_aligned_recalloc_dbg

Modifie la taille d’un bloc de mémoire qui a été alloué avec [_aligned_malloc](aligned-malloc.md) ou [_aligned_offset_malloc](aligned-offset-malloc.md) et initialise la mémoire à 0 (version de débogage uniquement).

## <a name="syntax"></a>Syntaxe

```C
void * _aligned_recalloc_dbg(
   void * memblock,
   size_t num,
   size_t size,
   size_t alignment,
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
Taille en octets de chaque élément.

*alignment*<br/>
Valeur d'alignement, qui doit être un entier à puissance 2.

*filename*<br/>
Pointeur vers le nom du fichier source qui a demandé l’opération d’allocation ou **null**.

*linenumber*<br/>
Numéro de ligne dans le fichier source où l’opération d’allocation a été demandée ou **null**.

## <a name="return-value"></a>Valeur de retour

**_aligned_recalloc_dbg** retourne un pointeur void vers le bloc de mémoire réalloué (et éventuellement déplacé). La valeur de retour est **null** si la taille est égale à zéro et l’argument de mémoire tampon n’est pas **null**, ou s’il n’y a pas assez de mémoire disponible pour développer le bloc à la taille donnée. Dans le premier cas, le bloc d'origine est libéré. Dans le second cas, le bloc d'origine est inchangé. La valeur de retour pointe vers un espace de stockage qui est obligatoirement aligné correctement pour le stockage de tout type d'objet. Pour obtenir un pointeur vers un type autre que void, utilisez un cast de type sur la valeur de retour.

Le fait de réallouer la mémoire et de modifier l'alignement d'un bloc constitue une erreur.

## <a name="remarks"></a>Notes

**_aligned_recalloc_dbg** est une version de débogage de la fonction [_aligned_recalloc](aligned-recalloc.md) . Lorsque [_ DEBUG](../../c-runtime-library/debug.md) n’est pas défini, chaque appel à **_aligned_recalloc_dbg** est réduit à un appel à **_aligned_recalloc**. **_Aligned_recalloc** et **_aligned_recalloc_dbg** réallouent tous deux un bloc de mémoire dans le tas de base, mais **_aligned_recalloc_dbg** prend en charge plusieurs fonctionnalités de débogage : des mémoires tampons de chaque côté de la partie utilisateur du bloc à tester. les fuites et les informations de *nom de fichier*/*LineNumber* pour déterminer l’origine des demandes d’allocation. Le suivi de types d’allocation spécifiques avec un paramètre de type de bloc n’est pas une fonctionnalité de débogage prise en charge pour les allocations alignées. Les allocations alignées s’affichent sous la forme d’un type de bloc _NORMAL_BLOCK.

**_aligned_recalloc_dbg** réalloue le bloc de mémoire spécifié avec un peu plus d’espace que la taille demandée (*taille*de*nombre* * ), qui peut être supérieure ou inférieure à la taille du bloc de mémoire alloué initialement. L'espace supplémentaire est utilisé par le gestionnaire de tas de débogage pour lier les blocs de mémoire de débogage et pour fournir à l'application des informations sur les en-têtes de débogage et les mémoires tampons de remplacement. La réallocation peut entraîner un déplacement du bloc de mémoire initial vers un autre emplacement dans le tas, ainsi qu'une modification de la taille du bloc de mémoire. La partie utilisateur du bloc contient la valeur 0xCD et les mémoires tampons de remplacement contiennent 0xFD.

**_aligned_recalloc_dbg** définit **errno** sur **ENOMEM** si une allocation de mémoire échoue ; **EINVAL** est retourné si la quantité de mémoire nécessaire (y compris la surcharge mentionnée précédemment) dépasse **_HEAP_MAXREQ**. Pour plus d’informations sur ces codes d’erreur et les autres, consultez [errno, _doserrno, _sys_errlist et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

De plus, **_aligned_recalloc_dbg** valide ses paramètres. Si *alignment* n’est pas une puissance de 2, cette fonction appelle le gestionnaire de paramètre non valide, comme décrit dans [validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, cette fonction retourne la **valeur null** et définit **errno** sur **EINVAL**.

Pour plus d’informations sur la façon dont les blocs de mémoire sont alloués, initialisés et gérés dans la version de débogage du tas de base, voir [CRT Debug Heap Details](/visualstudio/debugger/crt-debug-heap-details). Pour plus d’informations sur les types de bloc d’allocation et sur leur utilisation, consultez [Types de bloc sur le tas de débogage](/visualstudio/debugger/crt-debug-heap-details). Pour plus d’informations sur les différences entre l’appel à une fonction de tas standard et sa version de débogage dans la build de débogage d’une application, consultez [Versions Debug des fonctions d’allocation du tas](/visualstudio/debugger/debug-versions-of-heap-allocation-functions).

## <a name="requirements"></a>Configuration requise

|Routine|En-tête requis|
|-------------|---------------------|
|**_aligned_recalloc_dbg**|\<crtdbg.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Bibliothèques

Uniquement les versions de débogage des [bibliothèques Runtime C](../../c-runtime-library/crt-library-features.md).

## <a name="see-also"></a>Voir aussi

[Routines de débogage](../../c-runtime-library/debug-routines.md)<br/>
