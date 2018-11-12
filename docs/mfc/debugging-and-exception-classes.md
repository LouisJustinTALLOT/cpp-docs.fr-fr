---
title: Débogage et classes d'exceptions
ms.date: 11/04/2016
f1_keywords:
- vc.classes.debug
helpviewer_keywords:
- debugging [MFC], exception classes
- debugging [MFC], classes for debugging
ms.assetid: 0d158efd-2e62-452e-9d2a-d3c30dfee7f9
ms.openlocfilehash: 5549ea3e67f06e82e441c1ca5afc4a1b859dd410
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50587968"
---
# <a name="debugging-and-exception-classes"></a>Débogage et classes d'exceptions

Ces classes fournissent la prise en charge pour le débogage d’allocation de mémoire dynamique et pour passer des informations sur les exceptions à partir de la fonction où l’exception est levée à la fonction où elle est interceptée.

Utilisez les classes [CDumpContext](../mfc/reference/cdumpcontext-class.md) et [CMemoryState](../mfc/reference/cmemorystate-structure.md) pendant le développement pour aider au débogage, comme décrit dans [débogage des Applications MFC](/visualstudio/debugger/mfc-debugging-techniques). Utilisez [CRuntimeClass](../mfc/reference/cruntimeclass-structure.md) pour déterminer la classe de n’importe quel objet en cours d’exécution, comme décrit dans l’article [l’accès aux informations sur la classe runtime](../mfc/accessing-run-time-class-information.md). L’infrastructure utilise `CRuntimeClass` pour créer dynamiquement des objets d’une classe particulière.

## <a name="see-also"></a>Voir aussi

[Vue d’ensemble de la classe](../mfc/class-library-overview.md)

