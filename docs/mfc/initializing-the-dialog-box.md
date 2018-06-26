---
title: Initialisation de la boîte de dialogue | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- initializing dialog boxes [MFC]
- OnInitDialog method [MFC]
- modal dialog boxes [MFC], initializing
- modeless dialog boxes [MFC], initializing
- MFC dialog boxes [MFC], initializing
ms.assetid: 968142f5-19f9-4b34-a1d4-8e6412d4379b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1c4bc280c57998b23082f11f4ebe42b660177d3c
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2018
ms.locfileid: "36929619"
---
# <a name="initializing-the-dialog-box"></a>Initialisation de la boîte de dialogue
Une fois la boîte de dialogue zone et tous ses contrôles sont créés mais juste avant la boîte de dialogue boîte (de quelque type) s’affiche sur l’écran, l’objet de la boîte de dialogue [OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog) fonction membre est appelée. Pour une boîte de dialogue modale, cela se produit pendant la `DoModal` appeler. Pour une boîte de dialogue non modales `OnInitDialog` est appelée lorsque `Create` est appelée. En règle générale, vous substituez `OnInitDialog` pour initialiser les contrôles de la boîte de dialogue, par exemple définir le texte initial d’une zone d’édition. Vous devez appeler la `OnInitDialog` fonction membre de la classe de base `CDialog`, à partir de votre `OnInitDialog` remplacer.  
  
 Si vous souhaitez définir la couleur d’arrière-plan de votre boîte de dialogue (et que tous les autres boîtes de dialogue dans votre application), consultez [définissant la couleur d’arrière-plan de la boîte de dialogue](../mfc/setting-the-dialog-boxs-background-color.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Cycle de vie d’une boîte de dialogue](../mfc/life-cycle-of-a-dialog-box.md)

