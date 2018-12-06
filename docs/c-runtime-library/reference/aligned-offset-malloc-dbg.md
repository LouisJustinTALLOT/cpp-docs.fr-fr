---
title: _aligned_offset_malloc_dbg
ms.date: 11/04/2016
apiname:
- _aligned_offset_malloc_dbg
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
- _aligned_offset_malloc_dbg
- aligned_offset_malloc_dbg
helpviewer_keywords:
- _aligned_offset_malloc_dbg function
- aligned_offset_malloc_dbg function
ms.assetid: 6c242307-c59e-4d63-aae5-d8cbec8e021c
ms.openlocfilehash: 96fe9e7fda0d0cdfdbfa5462e4f601e3649e2233
ms.sourcegitcommit: beeb77b2976e997debc55b1af35024cc62e62799
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/06/2018
ms.locfileid: "52977717"
---
# <a name="alignedoffsetmallocdbg"></a>_aligned_offset_malloc_dbg

Alloue de la mémoire sur une limite d’alignement spécifiée (version de débogage uniquement).

## <a name="syntax"></a>Syntaxe

```C
void * _aligned_offset_malloc_dbg(
   size_t size,
   size_t alignment,
   size_t offset,
   const char *filename,
   int linenumber
);
```

### <a name="parameters"></a>Paramètres

*size*<br/>
Taille de l'allocation de mémoire demandée.

*Alignement*<br/>
Valeur d'alignement, qui doit être un entier à puissance 2.

*offset*<br/>
Décalage dans l'allocation de mémoire pour forcer l'alignement.

*filename*<br/>
Pointeur vers le nom du fichier source qui a demandé l’opération d’allocation ou **NULL**.

*linenumber*<br/>
Numéro de ligne dans le fichier source où l’opération d’allocation a été demandée ou **NULL**.

## <a name="return-value"></a>Valeur de retour

Un pointeur vers le bloc de mémoire qui a été alloué ou **NULL** si l’opération a échoué.

## <a name="remarks"></a>Notes

**_aligned_offset_malloc_dbg** est une version debug de la [_aligned_offset_malloc](aligned-offset-malloc.md) (fonction). Lorsque [_DEBUG](../../c-runtime-library/debug.md) n’est pas défini, chaque appel à **_aligned_offset_malloc_dbg** est réduite à un appel à **_aligned_offset_malloc**. Les deux **_aligned_offset_malloc** et **_aligned_offset_malloc_dbg** allouer un bloc de mémoire dans le tas de base, mais **_aligned_offset_malloc_dbg** offre plusieurs fonctionnalités de débogage : mémoires tampons de chaque côté de la partie utilisateur du bloc pour vérifier la présence de fuites, et *filename*/*linenumber* informations pour déterminer l’origine de demandes d’allocation. Suivi des types d’allocation spécifiques avec un paramètre de type de bloc ne sont pas une fonctionnalité de débogage pris en charge pour les allocations alignées. Allocations alignées apparaîtra comme un type de bloc _NORMAL_BLOCK.

**_aligned_offset_malloc_dbg** alloue le bloc de mémoire avec un peu plus d’espace que demandé *taille*. L'espace supplémentaire est utilisé par le gestionnaire de tas de débogage pour lier les blocs de mémoire de débogage et pour fournir à l'application des informations sur les en-têtes de débogage et les mémoires tampons de remplacement. Quand le bloc est alloué, la partie utilisateur du bloc est renseignée avec la valeur 0xCD et chaque mémoire tampon de remplacement est renseignée avec la valeur 0xFD.

**_aligned_offset_malloc_dbg** est utile dans les situations où l’alignement est nécessaire sur un élément imbriqué ; par exemple, si l’alignement était nécessaire sur une classe imbriquée.

**_aligned_offset_malloc_dbg** repose sur **malloc**; pour plus d’informations, consultez [malloc](malloc.md).

Cette fonction affecte **errno** à **ENOMEM** si l’allocation de mémoire a échoué ou si la taille demandée était supérieure à **_HEAP_MAXREQ**. Pour plus d’informations sur **errno**, consultez [errno, _doserrno, _sys_errlist et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md). En outre, **_aligned_offset_malloc** valide ses paramètres. Si *alignement* n’est pas une puissance de 2 ou si *décalage* est supérieur ou égal à *taille* et différent de zéro, cette fonction appelle le Gestionnaire de paramètre non valide, comme décrit dans [ Validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, cette fonction retourne **NULL** et définit **errno** à **EINVAL**.

Pour plus d’informations sur la façon dont les blocs de mémoire sont alloués, initialisés et gérés dans la version de débogage du tas de base, voir [CRT Debug Heap Details](/visualstudio/debugger/crt-debug-heap-details).

Pour plus d’informations sur les types de blocs d’allocation et sur leur utilisation, consultez [Types de bloc sur le tas de débogage](/visualstudio/debugger/crt-debug-heap-details).

## <a name="requirements"></a>Configuration requise

|Routine|En-tête requis|
|-------------|---------------------|
|**_aligned_offset_malloc_dbg**|\<crtdbg.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Bibliothèques

Uniquement les versions de débogage des [bibliothèques Runtime C](../../c-runtime-library/crt-library-features.md).

## <a name="see-also"></a>Voir aussi

[Routines de débogage](../../c-runtime-library/debug-routines.md)<br/>
