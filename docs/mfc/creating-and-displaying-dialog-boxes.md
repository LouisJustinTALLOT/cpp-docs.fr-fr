---
title: Création et affichage de boîtes de dialogue | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- modal dialog boxes [MFC], creating
- opening dialog boxes
- modeless dialog boxes [MFC], creating
- MFC dialog boxes [MFC], creating
- MFC dialog boxes [MFC], displaying
ms.assetid: 1c5219ee-8b46-44bc-9708-83705d4f248b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0fcac345a572f8b33d76692d6852e2dc28698367
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33342460"
---
# <a name="creating-and-displaying-dialog-boxes"></a>Création et affichage de boîtes de dialogue
Création d’un objet de la boîte de dialogue est une opération en deux phases. Tout d’abord, construisez l’objet de la boîte de dialogue, puis de créer la fenêtre de la boîte de dialogue. Boîtes de dialogue modales et non modales diffèrent légèrement dans le processus utilisé pour créer et de les afficher. Le tableau suivant répertorie comment modales et non modales boîtes de dialogue sont normalement construites et affichées.  
  
### <a name="dialog-creation"></a>Création de la boîte de dialogue  
  
|Type de la boîte de dialogue|Méthode de création|  
|-----------------|----------------------|  
|[Non modales](../mfc/creating-modeless-dialog-boxes.md)|Construire `CDialog`, puis appelez **créer** fonction membre.|  
|[Modal](../mfc/creating-modal-dialog-boxes.md)|Construire `CDialog`, puis appelez `DoModal` fonction membre.|  
  
 Vous pouvez, si vous le souhaitez, votre boîte de dialogue Créer à partir d’un [modèle de boîte de dialogue en mémoire](../mfc/using-a-dialog-template-in-memory.md) que vous avez construit plutôt qu’à partir d’une ressource de modèle de boîte de dialogue. Il s’agit toutefois une rubrique avancée.  
  
## <a name="see-also"></a>Voir aussi  
 [Cycle de vie d’une boîte de dialogue](../mfc/life-cycle-of-a-dialog-box.md)

