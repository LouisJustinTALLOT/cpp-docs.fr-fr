---
title: Débogage et Classes d’Exception | Microsoft Docs
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
ms.openlocfilehash: 4b7c88c5d12f56318bbb37a825e28c2bfcbc132d
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46418175"
---
# <a name="debugging-and-exception-classes"></a>Débogage et classes d'exceptions

Ces classes fournissent la prise en charge pour le débogage d’allocation de mémoire dynamique et pour passer des informations sur les exceptions à partir de la fonction où l’exception est levée à la fonction où elle est interceptée.

Utilisez les classes [CDumpContext](../mfc/reference/cdumpcontext-class.md) et [CMemoryState](../mfc/reference/cmemorystate-structure.md) pendant le développement pour aider au débogage, comme décrit dans [débogage des Applications MFC](/visualstudio/debugger/mfc-debugging-techniques). Utilisez [CRuntimeClass](../mfc/reference/cruntimeclass-structure.md) pour déterminer la classe de n’importe quel objet en cours d’exécution, comme décrit dans l’article [l’accès aux informations sur la classe runtime](../mfc/accessing-run-time-class-information.md). L’infrastructure utilise `CRuntimeClass` pour créer dynamiquement des objets d’une classe particulière.

## <a name="see-also"></a>Voir aussi

[Vue d’ensemble de la classe](../mfc/class-library-overview.md)

