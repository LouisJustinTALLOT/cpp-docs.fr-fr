---
title: Gestion de la mémoire | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- memory [MFC]
- MFC, memory management
- memory allocation [MFC]
- memory [MFC], managing
- memory allocation [MFC], MFC
ms.assetid: 934ac81b-d630-4232-88e5-ea74f7187987
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 928a954be6a96f5026a98f724a77bebd51be27f0
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33345076"
---
# <a name="memory-management"></a>Gestion de la mémoire
Ce groupe d’articles explique comment tirer parti des services généraux de la MFC Microsoft Foundation Class Library () associés à la gestion de la mémoire. Allocation de mémoire peut être divisée en deux catégories principales : allocations de frame et les allocations de tas.  
  
 Une des principales différences entre les deux techniques d’allocation est qu’avec l’allocation de frame que vous travaillez avec la mémoire réelle bloc lui-même, alors qu’avec l’allocation de tas, vous disposez d’un pointeur vers le bloc de mémoire. Une autre différence importante entre ces deux modèles est que les objets frame sont automatiquement supprimés, tandis que les objets de tas doivent être explicitement supprimés par le programmeur.  
  
 Pour plus d’informations non-MFC sur la gestion de mémoire dans les programmes pour Windows, consultez [gestion de la mémoire](http://msdn.microsoft.com/library/windows/desktop/aa366779) dans le Kit de développement logiciel Windows.  
  
## <a name="what-do-you-want-to-know-more-about"></a>Que voulez-vous en savoir plus  
  
-   [Allocation de frame](../mfc/memory-management-frame-allocation.md)  
  
-   [Allocation des tas](../mfc/memory-management-heap-allocation.md)  
  
-   [Allocation de mémoire pour un tableau](../mfc/memory-management-examples.md)  
  
-   [Désallocation de mémoire pour un tableau à partir du tas](../mfc/memory-management-examples.md)  
  
-   [Allocation de mémoire pour une structure de données](../mfc/memory-management-examples.md)  
  
-   [Allocation de mémoire pour un objet](../mfc/memory-management-examples.md)  
  
-   [Blocs de mémoire redimensionnables](../mfc/memory-management-resizable-memory-blocks.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Concepts](../mfc/mfc-concepts.md)   
 [Rubriques MFC générales](../mfc/general-mfc-topics.md)

