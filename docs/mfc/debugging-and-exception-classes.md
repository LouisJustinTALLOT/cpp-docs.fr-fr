---
title: Débogage et Classes d’Exception | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.classes.debug
dev_langs:
- C++
helpviewer_keywords:
- debugging [MFC], exception classes
- debugging [MFC], classes for debugging
ms.assetid: 0d158efd-2e62-452e-9d2a-d3c30dfee7f9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9adf6a585771336de9fb33abbebdd6bab97383ed
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33341759"
---
# <a name="debugging-and-exception-classes"></a>Débogage et classes d'exceptions
Ces classes fournissent la prise en charge pour le débogage d’allocation de mémoire dynamique, ainsi que pour passer des informations sur les exceptions à partir de la fonction où l’exception est levée à la fonction dans laquelle elle est interceptée.  
  
 Utilisez les classes [CDumpContext](../mfc/reference/cdumpcontext-class.md) et [CMemoryState](../mfc/reference/cmemorystate-structure.md) lors du développement afin de faciliter le débogage, comme décrit dans [débogage des Applications MFC](/visualstudio/debugger/mfc-debugging-techniques). Utilisez [CRuntimeClass](../mfc/reference/cruntimeclass-structure.md) pour déterminer la classe de n’importe quel objet en cours d’exécution, comme décrit dans l’article [l’accès aux informations de classe d’exécution](../mfc/accessing-run-time-class-information.md). L’infrastructure utilise `CRuntimeClass` pour créer dynamiquement des objets d’une classe particulière.  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble de la classe](../mfc/class-library-overview.md)

