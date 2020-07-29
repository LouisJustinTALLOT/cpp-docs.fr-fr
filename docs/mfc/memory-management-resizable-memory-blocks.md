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
ms.openlocfilehash: 308b5aa00aeb1f0e7887ad90bad79a28b361d7c7
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87217920"
---
# <a name="memory-management-resizable-memory-blocks"></a>Gestion de la mémoire : blocs de mémoire redimensionnables

Les **`new`** **`delete`** opérateurs et, décrits dans l’article [gestion de la mémoire : exemples](memory-management-examples.md), sont utiles pour l’allocation et la libération des blocs de mémoire et des objets de taille fixe. Parfois, votre application peut nécessiter des blocs de mémoire redimensionnables. Vous devez utiliser les fonctions de la bibliothèque Runtime C standard [malloc](../c-runtime-library/reference/malloc.md), [realloc](../c-runtime-library/reference/realloc.md)et [Free](../c-runtime-library/reference/free.md) pour gérer les blocs de mémoire redimensionnables sur le tas.

> [!IMPORTANT]
> La combinaison **`new`** des **`delete`** opérateurs et avec les fonctions d’allocation de mémoire redimensionnables sur le même bloc de mémoire entraîne une altération de la mémoire dans la version de débogage de MFC. Vous ne devez pas utiliser la fonction **realloc** sur un bloc de mémoire alloué avec **`new`** . De même, vous ne devez pas allouer un bloc de mémoire avec l' **`new`** opérateur et le supprimer **gratuitement**, ni utiliser l' **`delete`** opérateur sur un bloc de mémoire alloué avec **malloc**.

## <a name="see-also"></a>Voir aussi

[Gestion de la mémoire : allocation de tas](memory-management-heap-allocation.md)
