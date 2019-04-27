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
ms.openlocfilehash: 1c7f901009d5e1e7f0af20d493bb748b46b18480
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62219127"
---
# <a name="memory-management"></a>Gestion de la mémoire

Ce groupe d’articles décrit comment tirer parti des services à usage général de la MFC Microsoft Foundation Class Library () associés à la gestion de la mémoire. Allocation de mémoire peut être divisée en deux catégories principales : allocations de frame et les allocations de tas.

Une des principales différences entre les deux techniques d’allocation est qu’avec l’allocation de frame que vous travaillez généralement avec la mémoire réelle bloc lui-même, alors qu’avec l’allocation de tas, vous disposez d’un pointeur désignant le bloc de mémoire. Une autre différence importante entre ces deux modèles est que les objets frame sont automatiquement supprimés, tandis que les objets du tas doivent être explicitement supprimés par le programmeur.

Pour plus d’informations non-MFC sur la gestion de mémoire dans les programmes pour Windows, consultez [gestion de la mémoire](/windows/desktop/memory/memory-management) dans le SDK Windows.

## <a name="what-do-you-want-to-know-more-about"></a>Ce que vous souhaitez en savoir plus sur

- [Allocation de frame](../mfc/memory-management-frame-allocation.md)

- [Allocation de tas](../mfc/memory-management-heap-allocation.md)

- [Allocation de mémoire pour un tableau](../mfc/memory-management-examples.md)

- [Désallocation de mémoire pour un tableau à partir du tas](../mfc/memory-management-examples.md)

- [Allocation de mémoire pour une structure de données](../mfc/memory-management-examples.md)

- [Allocation de mémoire pour un objet](../mfc/memory-management-examples.md)

- [Blocs de mémoire redimensionnables](../mfc/memory-management-resizable-memory-blocks.md)

## <a name="see-also"></a>Voir aussi

[Concepts](../mfc/mfc-concepts.md)<br/>
[Rubriques MFC générales](../mfc/general-mfc-topics.md)
