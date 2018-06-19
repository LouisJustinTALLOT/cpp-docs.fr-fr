---
title: Ajout d’éléments au contrôle | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CListCtrl class [MFC], adding items
ms.assetid: 715994bd-340d-4ad2-9882-411654137830
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: eab0c7cb1aebf1675d078aa99941edfd9afdc5a8
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33341363"
---
# <a name="adding-items-to-the-control"></a>Ajout d'éléments au contrôle
Pour ajouter des éléments au contrôle de liste ([CListCtrl](../mfc/reference/clistctrl-class.md)), appelez l’une des différentes versions de la [InsertItem](../mfc/reference/clistctrl-class.md#insertitem) fonction membre, en fonction des informations dont vous disposez. Une version prend une [LV_ITEM](http://msdn.microsoft.com/library/windows/desktop/bb774760) structure que vous avez préparé. Étant donné que le `LV_ITEM` structure contient de nombreux membres, vous avez le plus grand contrôle sur les attributs de l’élément de contrôle de liste.  
  
 Deux membres importants (en ce qui concerne la vue rapport) de la `LV_ITEM` structure sont les `iItem` et `iSubItem` membres. Le `iItem` membre est l’index de base zéro de l’élément de la structure et le `iSubItem` membre est l’index de base un d’un sous-élément, ou zéro si la structure contient des informations sur un élément. Avec ces deux membres, vous pouvez déterminer, par élément, le type et la valeur des informations de sous-élément qui s’affiche lorsque le contrôle de liste est en mode rapport. Pour plus d’informations, consultez [CListCtrl::SetItem](../mfc/reference/clistctrl-class.md#setitem).  
  
 Les membres supplémentaires spécifier de l’élément texte, icône, état et données de l’élément. « Élément de données » est une valeur définie par l’application associée à un élément de liste. Pour plus d’informations sur la `LV_ITEM` de la structure, consultez [CListCtrl::GetItem](../mfc/reference/clistctrl-class.md#getitem).  
  
 Autres versions de `InsertItem` prendre une ou plusieurs valeurs distinctes, correspondant à des membres dans le `LV_ITEM` structure, ce qui vous permet d’initialiser uniquement les membres que vous souhaitez prendre en charge. En règle générale, le contrôle de liste gère le stockage des éléments de liste, mais vous pouvez stocker des informations dans votre application, à l’aide de « éléments de rappel ». Pour plus d’informations, consultez [éléments de rappel et masque de rappel](../mfc/callback-items-and-the-callback-mask.md) dans cette rubrique et [éléments de rappel et masque de rappel](http://msdn.microsoft.com/library/windows/desktop/bb774736) dans le Kit de développement logiciel Windows.  
  
 Pour plus d’informations, consultez [List-View Ajout d’éléments et sous-éléments](http://msdn.microsoft.com/library/windows/desktop/bb774736).  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation de CListCtrl](../mfc/using-clistctrl.md)   
 [Contrôles](../mfc/controls-mfc.md)

