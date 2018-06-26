---
title: 'Gestion de la mémoire : Blocs de mémoire redimensionnables | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- memory blocks [MFC], resizable
- memory [MFC], corruption
- memory allocation [MFC], memory block size
- memory blocks [MFC], allocating
- blocks [MFC], memory allocation
- resizable memory blocks [MFC]
ms.assetid: f0efe6f4-a3ed-4541-9195-51ec1291967a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ba66fb3d85d716b18486ef08f7f2025e78d6cc57
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2018
ms.locfileid: "36929328"
---
# <a name="memory-management-resizable-memory-blocks"></a>Gestion de la mémoire : blocs de mémoire redimensionnables
Le **nouveau** et **supprimer** opérateurs, décrites dans l’article [gestion de la mémoire : exemples](../mfc/memory-management-examples.md), sont correctes pour allouer et libérer des blocs de mémoire de taille fixe et objets. Parfois, votre application peut avoir besoin de blocs de mémoire redimensionnables. Vous devez utiliser les fonctions de bibliothèque Runtime C standard [malloc](../c-runtime-library/reference/malloc.md), [realloc](../c-runtime-library/reference/realloc.md), et [libre](../c-runtime-library/reference/free.md) pour gérer les blocs de mémoire redimensionnables sur le tas.  
  
> [!IMPORTANT]
>  Mélange les **nouveau** et **supprimer** opérateurs avec les fonctions d’allocation de mémoire redimensionnables sur le même bloc de mémoire entraîne une mémoire endommagée dans la version Debug des MFC. Vous ne devez pas utiliser **realloc** sur un bloc de mémoire alloué avec **nouveau**. De même, vous ne devez pas allouer un bloc de mémoire avec la **nouveau** opérateur et le supprimer avec **libre**, ou utilisez le **supprimer** opérateur sur un bloc de mémoire allouée avec **malloc**.  
  
## <a name="see-also"></a>Voir aussi  
 [Gestion de la mémoire : allocation de tas](../mfc/memory-management-heap-allocation.md)

