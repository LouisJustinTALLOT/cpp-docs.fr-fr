---
title: 'Gestion de la mémoire : blocs de mémoire redimensionnables'
ms.date: 11/04/2016
helpviewer_keywords:
- memory blocks [MFC], resizable
- memory [MFC], corruption
- memory allocation [MFC], memory block size
- memory blocks [MFC], allocating
- blocks [MFC], memory allocation
- resizable memory blocks [MFC]
ms.assetid: f0efe6f4-a3ed-4541-9195-51ec1291967a
ms.openlocfilehash: 499e2d4a99152e08f50159c4c952eb882c9fd425
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50481144"
---
# <a name="memory-management-resizable-memory-blocks"></a>Gestion de la mémoire : blocs de mémoire redimensionnables

Le **nouveau** et **supprimer** opérateurs, décrites dans l’article [gestion de la mémoire : exemples](../mfc/memory-management-examples.md), conviennent pour l’allocation et libération des blocs de mémoire de taille fixe et objets. Parfois, votre application peut nécessiter des blocs de mémoire redimensionnables. Vous devez utiliser les fonctions de bibliothèque Runtime C standards [malloc](../c-runtime-library/reference/malloc.md), [realloc](../c-runtime-library/reference/realloc.md), et [gratuit](../c-runtime-library/reference/free.md) pour gérer les blocs de mémoire redimensionnables sur le tas.

> [!IMPORTANT]
>  Combiner la **nouveau** et **supprimer** opérateurs avec les fonctions d’allocation de mémoire redimensionnables sur le même bloc de mémoire entraîne une mémoire endommagée dans la version Debug des MFC. Vous ne devez pas utiliser **realloc** sur un bloc de mémoire alloué avec **nouveau**. De même, vous ne devez pas allouer un bloc de mémoire avec le **nouveau** opérateur et supprimez-le avec **gratuit**, ou utiliser le **supprimer** opérateur sur un bloc de mémoire allouée avec **malloc**.

## <a name="see-also"></a>Voir aussi

[Gestion de la mémoire : allocation de tas](../mfc/memory-management-heap-allocation.md)

