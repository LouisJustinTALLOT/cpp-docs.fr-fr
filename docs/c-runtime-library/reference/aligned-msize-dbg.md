---
title: _aligned_msize_dbg
ms.date: 11/04/2016
apiname:
- _aligned_msize_dbg
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
- _aligned_msize_dbg
helpviewer_keywords:
- _aligned_msize_dbg
ms.assetid: f1c44af0-3f66-4033-81d1-d71d3afecba0
ms.openlocfilehash: 054f7b88f93eef37a9a88fbb7895452f7c158716
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62342029"
---
# <a name="alignedmsizedbg"></a>_aligned_msize_dbg

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

Le *alignement* et *décalage* valeurs doivent être le même que les valeurs passées à la fonction que le bloc alloué.

**_aligned_msize_dbg** est une version debug de la [_aligned_msize](aligned-msize.md) (fonction). Lorsque [_DEBUG](../../c-runtime-library/debug.md) n’est pas défini, chaque appel à **_aligned_msize_dbg** est réduite à un appel à **_aligned_msize**. Les deux **_aligned_msize** et **_aligned_msize_dbg** calculer la taille d’un bloc de mémoire dans le tas de base, mais **_aligned_msize_dbg** ajoute une fonctionnalité de débogage : Il inclut les mémoires tampons de chaque côté de la partie utilisateur du bloc de mémoire dans la taille retournée.

Cette fonction valide son paramètre. Si *memblock* est un pointeur null ou *alignement* n’est pas une puissance de 2, **_msize** appelle un gestionnaire de paramètre non valide, comme décrit dans [Validation de paramètre ](../../c-runtime-library/parameter-validation.md). Si l’erreur est gérée, la fonction définit **errno** à **EINVAL** et retourne -1.

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
