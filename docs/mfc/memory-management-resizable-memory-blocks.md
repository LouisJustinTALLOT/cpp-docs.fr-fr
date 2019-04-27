---
title: 'Gestion de la mémoire : Blocs de mémoire redimensionnables'
ms.date: 11/04/2016
helpviewer_keywords:
- memory blocks [MFC], resizable
- memory [MFC], corruption
- memory allocation [MFC], memory block size
- memory blocks [MFC], allocating
- blocks [MFC], memory allocation
- resizable memory blocks [MFC]
ms.assetid: f0efe6f4-a3ed-4541-9195-51ec1291967a
ms.openlocfilehash: 124a2599e1523d5393fcf6255c88de0fd8cd72cd
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62219140"
---
# <a name="memory-management-resizable-memory-blocks"></a>Gestion de la mémoire : Blocs de mémoire redimensionnables

Le **nouveau** et **supprimer** opérateurs, décrites dans l’article [gestion de la mémoire : Exemples](../mfc/memory-management-examples.md), conviennent pour l’allocation et libération des blocs de mémoire de taille fixe et des objets. Parfois, votre application peut nécessiter des blocs de mémoire redimensionnables. Vous devez utiliser les fonctions de bibliothèque Runtime C standards [malloc](../c-runtime-library/reference/malloc.md), [realloc](../c-runtime-library/reference/realloc.md), et [gratuit](../c-runtime-library/reference/free.md) pour gérer les blocs de mémoire redimensionnables sur le tas.

> [!IMPORTANT]
>  Combiner la **nouveau** et **supprimer** opérateurs avec les fonctions d’allocation de mémoire redimensionnables sur le même bloc de mémoire entraîne une mémoire endommagée dans la version Debug des MFC. Vous ne devez pas utiliser **realloc** sur un bloc de mémoire alloué avec **nouveau**. De même, vous ne devez pas allouer un bloc de mémoire avec le **nouveau** opérateur et supprimez-le avec **gratuit**, ou utiliser le **supprimer** opérateur sur un bloc de mémoire allouée avec **malloc**.

## <a name="see-also"></a>Voir aussi

[Gestion de la mémoire : Allocation des tas](../mfc/memory-management-heap-allocation.md)
