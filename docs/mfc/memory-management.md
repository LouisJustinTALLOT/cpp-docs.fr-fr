---
title: Gestion de la mémoire
ms.date: 11/04/2016
helpviewer_keywords:
- memory [MFC]
- MFC, memory management
- memory allocation [MFC]
- memory [MFC], managing
- memory allocation [MFC], MFC
ms.assetid: 934ac81b-d630-4232-88e5-ea74f7187987
ms.openlocfilehash: 5d81bd0a8bdd24059951cba5c8b69751b3d1db86
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69508271"
---
# <a name="memory-management"></a>Gestion de la mémoire

Ce groupe d’articles explique comment tirer parti des services à usage général du bibliothèque MFC (Microsoft Foundation Class) (MFC) relatifs à la gestion de la mémoire. L’allocation de mémoire peut être divisée en deux catégories principales: les allocations de frame et les allocations de tas.

L’une des principales différences entre les deux techniques d’allocation est qu’avec l’allocation de frame, vous travaillez généralement avec le bloc de mémoire réel proprement dit, tandis que avec l’allocation de tas, vous recevez toujours un pointeur vers le bloc de mémoire. Une autre différence majeure entre les deux schémas est que les objets Frame sont automatiquement supprimés, tandis que les objets Heap doivent être supprimés explicitement par le programmeur.

Pour obtenir des informations non-MFC sur la gestion de la mémoire dans les programmes pour Windows, consultez Gestion de la [mémoire](/windows/win32/memory/memory-management) dans le SDK Windows.

## <a name="what-do-you-want-to-know-more-about"></a>Que voulez-vous en savoir plus sur

- [Allocation de frame](../mfc/memory-management-frame-allocation.md)

- [Allocation du tas](../mfc/memory-management-heap-allocation.md)

- [Allocation de mémoire pour un tableau](../mfc/memory-management-examples.md)

- [Libération de la mémoire pour un tableau à partir du tas](../mfc/memory-management-examples.md)

- [Allocation de mémoire pour une structure de données](../mfc/memory-management-examples.md)

- [Allocation de mémoire pour un objet](../mfc/memory-management-examples.md)

- [Blocs de mémoire redimensionnables](../mfc/memory-management-resizable-memory-blocks.md)

## <a name="see-also"></a>Voir aussi

[Concepts](../mfc/mfc-concepts.md)<br/>
[Rubriques MFC générales](../mfc/general-mfc-topics.md)
