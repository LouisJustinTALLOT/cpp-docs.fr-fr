---
title: Comment dériver une classe de CObject ? | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- CObject
dev_langs:
- C++
helpviewer_keywords:
- CObject class [MFC], overhead of derived classes [MFC]
ms.assetid: 9b92c98b-b3dd-48a7-9d24-c3b8554edf90
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3ffff35cdef6cf2f730687334bbb56bc078371a7
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33381675"
---
# <a name="what-does-it-cost-me-to-derive-a-class-from-cobject"></a>Comment dériver une classe de CObject ?
La surcharge de dérivation de classe [CObject](../mfc/reference/cobject-class.md) est minime. Votre classe dérivée hérite seulement quatre fonctions virtuelles et un seul [CRuntimeClass](../mfc/reference/cruntimeclass-structure.md) objet.  
  
## <a name="see-also"></a>Voir aussi  
 [Classe CObject : Forum Aux Questions](../mfc/cobject-class-frequently-asked-questions.md)
