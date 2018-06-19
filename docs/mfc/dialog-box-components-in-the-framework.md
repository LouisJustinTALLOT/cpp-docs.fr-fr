---
title: Composants de boîte de dialogue dans le Framework | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC dialog boxes [MFC], creating
- dialog classes [MFC], dialog box components
- MFC dialog boxes [MFC], about MFC dialog boxes
- dialog templates [MFC], MFC framework
- MFC dialog boxes [MFC], dialog resource
ms.assetid: 592db160-0a8a-49be-ac72-ead278aca53f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a92846dc1d7b950d1eccfa4cd42b01ac84d96b34
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33343965"
---
# <a name="dialog-box-components-in-the-framework"></a>Composants de boîte de dialogue dans le Framework
Dans l’infrastructure MFC, une boîte de dialogue comporte deux composants :  
  
-   Une ressource de modèle de boîte de dialogue qui spécifie les contrôles de la boîte de dialogue et leur emplacement.  
  
     La ressource de boîte de dialogue stocke un modèle de boîte de dialogue à partir duquel Windows crée la fenêtre de dialogue et l’affiche. Le modèle spécifie les caractéristiques de la boîte de dialogue, y compris sa taille, emplacement, style et les types et les positions des contrôles de la boîte de dialogue. Vous utiliserez généralement un modèle de boîte de dialogue stocké en tant que ressource, mais vous pouvez également créer votre propre modèle en mémoire.  
  
-   Une classe de boîte de dialogue, dérivée de [CDialog](../mfc/reference/cdialog-class.md), pour fournir une interface de programmation pour la gestion de la boîte de dialogue.  
  
     Une boîte de dialogue est une fenêtre et sera attachée à une fenêtre Windows lorsqu’elle est visible. Lors de la création de la boîte de dialogue, la ressource de modèle de boîte de dialogue est utilisée en tant que modèle pour créer des contrôles de fenêtre pour la boîte de dialogue enfants.  
  
## <a name="see-also"></a>Voir aussi  
 [Boîtes de dialogue](../mfc/dialog-boxes.md)   
 [Cycle de vie d’une boîte de dialogue](../mfc/life-cycle-of-a-dialog-box.md)

