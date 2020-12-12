---
description: En savoir plus sur les classes de débogage et d’exception
title: Débogage et classes d'exceptions
ms.date: 11/04/2016
f1_keywords:
- vc.classes.debug
helpviewer_keywords:
- debugging [MFC], exception classes
- debugging [MFC], classes for debugging
ms.assetid: 0d158efd-2e62-452e-9d2a-d3c30dfee7f9
ms.openlocfilehash: 2c14ea8d51fd1b63427ad1495e711a906e013ea4
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97291114"
---
# <a name="debugging-and-exception-classes"></a>Débogage et classes d'exceptions

Ces classes assurent la prise en charge du débogage de l’allocation de mémoire dynamique et du passage des informations sur les exceptions à partir de la fonction où l’exception est levée dans la fonction où elle est interceptée.

Utilisez les classes [CDumpContext](reference/cdumpcontext-class.md) et [CMemoryState](reference/cmemorystate-structure.md) pendant le développement pour faciliter le débogage, comme décrit dans [débogage d’applications MFC](/visualstudio/debugger/mfc-debugging-techniques). Utilisez [CRuntimeClass](reference/cruntimeclass-structure.md) pour déterminer la classe d’un objet au moment de l’exécution, comme décrit dans l’article [accès aux informations de classe Run-Time](accessing-run-time-class-information.md). L’infrastructure utilise `CRuntimeClass` pour créer dynamiquement des objets d’une classe particulière.

## <a name="see-also"></a>Voir aussi

[Vue d'ensemble des classes](class-library-overview.md)
