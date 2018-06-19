---
title: Dois-je dériver les nouvelles classes de CObject ? | Microsoft Docs
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
- derived classes [MFC], from CObject
- CObject class [MFC], when to use
ms.assetid: 26021031-feaf-424c-80d1-9547c4409d6a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 51904ac06ae6c2db5586f8dc405f85145c5b1f30
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33343058"
---
# <a name="do-i-have-to-derive-new-classes-from-cobject"></a>Dois-je dériver les nouvelles classes de CObject ?
Non, vous n’avez pas.  
  
 Dérivez une classe de [CObject](../mfc/reference/cobject-class.md) lorsque vous avez besoin des fonctionnalités qu’il fournit, telles que la sérialisation ou de la création dynamique d’objets. De nombreuses classes de données doivent être sérialisés dans des fichiers, il est souvent judicieux de les dériver de `CObject`. Pour obtenir un exemple d’une classe dérivée de `CObject`, consultez la [exemple Scribble](../visual-cpp-samples.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Classe CObject : Forum Aux Questions](../mfc/cobject-class-frequently-asked-questions.md)
