---
title: Ajout d’éléments au contrôle Header | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- controls [MFC], header
- CHeaderCtrl class [MFC], adding items
- header controls [MFC], adding items to
ms.assetid: 2e9a28b1-7302-4a93-8037-c5a4183e589a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a6450d99b8df436c64337e52fc14244ecbb0edfc
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/29/2018
ms.locfileid: "43206145"
---
# <a name="adding-items-to-the-header-control"></a>Ajout d'éléments au contrôle Header
Après avoir créé votre contrôle header ([CHeaderCtrl](../mfc/reference/cheaderctrl-class.md)) dans sa fenêtre parente, ajoutez autant « éléments d’en-tête » que vous avez besoin : généralement un par colonne.  
  
### <a name="to-add-a-header-item"></a>Pour ajouter un élément d’en-tête  
  
1.  Préparer un [structure HD_ITEM](/windows/desktop/api/commctrl/ns-commctrl-_hd_itema) structure.  
  
2.  Appelez [CHeaderCtrl::InsertItem](../mfc/reference/cheaderctrl-class.md#insertitem), en passant la structure.  
  
3.  Répétez les étapes 1 et 2 pour les éléments supplémentaires.  
  
 Pour plus d’informations, consultez [Ajout d’un élément à un contrôle d’en-tête](/windows/desktop/Controls/header-controls) dans le SDK Windows.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation de CHeaderCtrl](../mfc/using-cheaderctrl.md)   
 [Contrôles](../mfc/controls-mfc.md)

