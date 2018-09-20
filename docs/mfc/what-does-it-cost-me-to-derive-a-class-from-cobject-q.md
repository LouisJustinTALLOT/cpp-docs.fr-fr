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
ms.openlocfilehash: e41f9060ce24b89a0a7faae54ca6207c740475f3
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46443239"
---
# <a name="what-does-it-cost-me-to-derive-a-class-from-cobject"></a>Comment dériver une classe de CObject ?

La surcharge de dérivation de classe [CObject](../mfc/reference/cobject-class.md) est minime. Votre classe dérivée hérite uniquement quatre fonctions virtuelles et un seul [CRuntimeClass](../mfc/reference/cruntimeclass-structure.md) objet.

## <a name="see-also"></a>Voir aussi

[Classe CObject : Forum Aux Questions](../mfc/cobject-class-frequently-asked-questions.md)
