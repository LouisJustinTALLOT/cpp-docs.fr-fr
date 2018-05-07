---
title: Ordre des éléments dans le contrôle Header | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- DS_DRAGDROP
dev_langs:
- C++
helpviewer_keywords:
- sequence [MFC]
- sequence [MFC], header control items
- OrderToIndex method [MFC]
- DS_DRAGDROP notification [MFC]
- GetOrderArray method [MFC]
- SetOrderArray method [MFC]
- header controls [MFC], ordering items
ms.assetid: 5aaef872-75b5-49c5-8fed-6f9a81fca812
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: dfa84326286b03f3ed0154138ed7f847440df284
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
---
# <a name="ordering-items-in-the-header-control"></a>Organisation des éléments dans le contrôle Header
Une fois que vous avez [ajouté des éléments à un contrôle header](../mfc/adding-items-to-the-header-control.md), vous pouvez manipuler ou obtenir des informations sur leur ordre avec les fonctions suivantes :  
  
-   [CHeaderCtrl::GetOrderArray](../mfc/reference/cheaderctrl-class.md#getorderarray) et [CHeaderCtrl::SetOrderArray](../mfc/reference/cheaderctrl-class.md#setorderarray)  
  
     Extrait et définit l’ordre de gauche à droite des éléments d’en-tête.  
  
-   [CHeaderCtrl::OrderToIndex](../mfc/reference/cheaderctrl-class.md#ordertoindex).  
  
     Récupère la valeur d’index pour un élément d’en-tête spécifique.  
  
 Outre les fonctions de membre précédent, le `HDS_DRAGDROP` style permet à l’utilisateur de faire glisser et déposer des éléments d’en-tête dans le contrôle header. Pour plus d’informations, consultez [prise en charge du glisser-déplacer pour les éléments d’en-tête](../mfc/providing-drag-and-drop-support-for-header-items.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation de CHeaderCtrl](../mfc/using-cheaderctrl.md)

