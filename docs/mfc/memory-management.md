---
description: 'En savoir plus sur : gestion de la mémoire'
title: Gestion de la mémoire
ms.date: 11/04/2016
helpviewer_keywords:
- memory [MFC]
- MFC, memory management
- memory allocation [MFC]
- memory [MFC], managing
- memory allocation [MFC], MFC
ms.assetid: 934ac81b-d630-4232-88e5-ea74f7187987
ms.openlocfilehash: 4e274820ce82cf8b338c6a62349440e944f21f7a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97253375"
---
# <a name="memory-management"></a>Gestion de la mémoire

Ce groupe d’articles explique comment tirer parti des services à usage général du bibliothèque MFC (Microsoft Foundation Class) (MFC) relatifs à la gestion de la mémoire. L’allocation de mémoire peut être divisée en deux catégories principales : les allocations de frame et les allocations de tas.

L’une des principales différences entre les deux techniques d’allocation est qu’avec l’allocation de frame, vous travaillez généralement avec le bloc de mémoire réel proprement dit, tandis que avec l’allocation de tas, vous recevez toujours un pointeur vers le bloc de mémoire. Une autre différence majeure entre les deux schémas est que les objets Frame sont automatiquement supprimés, tandis que les objets Heap doivent être supprimés explicitement par le programmeur.

Pour obtenir des informations non-MFC sur la gestion de la mémoire dans les programmes pour Windows, consultez Gestion de la [mémoire](/windows/win32/memory/memory-management) dans le SDK Windows.

## <a name="what-do-you-want-to-know-more-about"></a>Que voulez-vous en savoir plus sur

- [Allocation d’images](memory-management-frame-allocation.md)

- [Allocation du tas](memory-management-heap-allocation.md)

- [Allocation de mémoire pour un tableau](memory-management-examples.md)

- [Libération de la mémoire pour un tableau à partir du tas](memory-management-examples.md)

- [Allocation de mémoire pour une structure de données](memory-management-examples.md)

- [Allocation de mémoire pour un objet](memory-management-examples.md)

- [Blocs de mémoire redimensionnables](memory-management-resizable-memory-blocks.md)

## <a name="see-also"></a>Voir aussi

[Concepts](mfc-concepts.md)<br/>
[Rubriques générales sur MFC](general-mfc-topics.md)
