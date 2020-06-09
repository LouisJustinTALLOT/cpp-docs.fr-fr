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
ms.openlocfilehash: 74ae94146b1ec711b586ea1fecbbc89a47b40b5e
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84626278"
---
# <a name="memory-management-resizable-memory-blocks"></a>Gestion de la mémoire : blocs de mémoire redimensionnables

Les opérateurs **New** et **Delete** , décrits dans l’article gestion de la [mémoire : exemples](memory-management-examples.md), sont corrects pour allouer et libérer des blocs de mémoire de taille fixe et des objets. Parfois, votre application peut nécessiter des blocs de mémoire redimensionnables. Vous devez utiliser les fonctions de la bibliothèque Runtime C standard [malloc](../c-runtime-library/reference/malloc.md), [realloc](../c-runtime-library/reference/realloc.md)et [Free](../c-runtime-library/reference/free.md) pour gérer les blocs de mémoire redimensionnables sur le tas.

> [!IMPORTANT]
> La combinaison des opérateurs **New** et **Delete** avec les fonctions d’allocation de mémoire redimensionnables sur le même bloc de mémoire entraîne une altération de la mémoire dans la version Debug des MFC. Vous ne devez pas utiliser la fonction **realloc** sur un bloc de mémoire alloué avec **New**. De même, vous ne devez pas allouer un bloc de mémoire avec l’opérateur **New** et le supprimer **gratuitement**, ni utiliser l’opérateur **Delete** sur un bloc de mémoire alloué avec **malloc**.

## <a name="see-also"></a>Voir aussi

[Gestion de la mémoire : allocation de tas](memory-management-heap-allocation.md)
