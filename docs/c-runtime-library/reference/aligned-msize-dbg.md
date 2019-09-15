---
title: _aligned_msize_dbg
ms.date: 11/04/2016
api_name:
- _aligned_msize_dbg
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
- _aligned_msize_dbg
helpviewer_keywords:
- _aligned_msize_dbg
ms.assetid: f1c44af0-3f66-4033-81d1-d71d3afecba0
ms.openlocfilehash: f2a0ceab906dccacb2e1c78a8789d524b608a4ff
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70939867"
---
# <a name="_aligned_msize_dbg"></a>_aligned_msize_dbg

Retourne la taille d’un bloc de mémoire alloué dans le tas (version de débogage uniquement).

## <a name="syntax"></a>Syntaxe

```C
size_t _aligned_msize_dbg(
   void *memblock,
   size_t alignment,
   size_t offset
);
```

### <a name="parameters"></a>Paramètres

*memblock*<br/>
Pointeur désignant le bloc de mémoire.

*alignment*<br/>
Valeur d'alignement, qui doit être un entier à puissance 2.

*offset*<br/>
Décalage dans l'allocation de mémoire pour forcer l'alignement.

## <a name="return-value"></a>Valeur de retour

Retourne la taille (en octets) sous la forme d’un entier non signé.

## <a name="remarks"></a>Notes

L' *alignement* et les valeurs de *décalage* doivent être les mêmes que les valeurs passées à la fonction qui a alloué le bloc.

**_aligned_msize_dbg** est une version de débogage de la fonction [_aligned_msize](aligned-msize.md) . Lorsque [_ DEBUG](../../c-runtime-library/debug.md) n’est pas défini, chaque appel à **_aligned_msize_dbg** est réduit à un appel à **_aligned_msize**. **_Aligned_msize** et **_aligned_msize_dbg** calculent tous les deux la taille d’un bloc de mémoire dans le tas de base, mais **_aligned_msize_dbg** ajoute une fonctionnalité de débogage : Il comprend les mémoires tampons de chaque côté de la partie utilisateur du bloc de mémoire dans la taille retournée.

Cette fonction valide son paramètre. Si *memblock* est un pointeur null ou si l' *alignement* n’est pas une puissance de 2, **_msize** appelle un gestionnaire de paramètres non valides, comme décrit dans [validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’erreur est gérée, la fonction affecte à **errno** la valeur **EINVAL** et retourne-1.

Pour plus d’informations sur la façon dont les blocs de mémoire sont alloués, initialisés et gérés dans la version de débogage du tas de base, voir [CRT Debug Heap Details](/visualstudio/debugger/crt-debug-heap-details). Pour plus d’informations sur les types de bloc d’allocation et sur leur utilisation, consultez [Types de bloc sur le tas de débogage](/visualstudio/debugger/crt-debug-heap-details). Pour plus d’informations sur les différences entre l’appel à une fonction de tas standard et sa version de débogage dans la build de débogage d’une application, consultez [Versions Debug des fonctions d’allocation du tas](/visualstudio/debugger/debug-versions-of-heap-allocation-functions).

## <a name="requirements"></a>Configuration requise

|Routine|En-tête requis|
|-------------|---------------------|
|**_aligned_msize_dbg**|\<crtdbg.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Bibliothèques

Uniquement les versions de débogage des [bibliothèques Runtime C](../../c-runtime-library/crt-library-features.md).

## <a name="see-also"></a>Voir aussi

[Allocation de mémoire](../../c-runtime-library/memory-allocation.md)<br/>
