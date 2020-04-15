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
ms.openlocfilehash: b048b60a5512ecc54750cb980ca67e2373e2c837
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364777"
---
# <a name="memory-management-resizable-memory-blocks"></a>Gestion de la mémoire : blocs de mémoire redimensionnables

Les **nouveaux** opérateurs et **supprimer,** décrits dans l’article [Memory Management: Exemples](../mfc/memory-management-examples.md), sont bons pour l’attribution et l’attribution de blocs de mémoire fixes et d’objets. De temps en temps, votre application peut avoir besoin de blocs de mémoire resizables. Vous devez utiliser les fonctions standard de bibliothèque C run-time [malloc](../c-runtime-library/reference/malloc.md), [réaffecter](../c-runtime-library/reference/realloc.md), et [libre](../c-runtime-library/reference/free.md) de gérer les blocs de mémoire résizables sur le tas.

> [!IMPORTANT]
> Mélanger les **nouveaux** opérateurs et **supprimer** les fonctions resizables d’allocation de mémoire sur le même bloc de mémoire se traduira par une mémoire corrompue dans la version Debug de MFC. Vous ne devez pas utiliser **réaffectation** sur un bloc de mémoire alloué avec **de nouveaux**. De même, vous ne devez pas allouer un bloc mémoire avec le **nouvel** opérateur et le supprimer **gratuitement**, ou utiliser l’opérateur de **suppression** sur un bloc de mémoire alloué avec **malloc**.

## <a name="see-also"></a>Voir aussi

[Gestion de la mémoire : allocation de tas](../mfc/memory-management-heap-allocation.md)
