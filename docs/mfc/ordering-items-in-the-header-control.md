---
title: Organisation des éléments dans le contrôle Header
ms.date: 11/04/2016
f1_keywords:
- DS_DRAGDROP
helpviewer_keywords:
- sequence [MFC]
- sequence [MFC], header control items
- OrderToIndex method [MFC]
- DS_DRAGDROP notification [MFC]
- GetOrderArray method [MFC]
- SetOrderArray method [MFC]
- header controls [MFC], ordering items
ms.assetid: 5aaef872-75b5-49c5-8fed-6f9a81fca812
ms.openlocfilehash: 5c4fef821efa697d41bf02ef1891efcf0fa21d4b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50583507"
---
# <a name="ordering-items-in-the-header-control"></a>Organisation des éléments dans le contrôle Header

Une fois que vous avez [ajouté des éléments à un contrôle header](../mfc/adding-items-to-the-header-control.md), vous pouvez manipuler ou obtenir des informations sur leur ordre avec les fonctions suivantes :

- [CHeaderCtrl::GetOrderArray](../mfc/reference/cheaderctrl-class.md#getorderarray) et [CHeaderCtrl::SetOrderArray](../mfc/reference/cheaderctrl-class.md#setorderarray)

   Récupère et définit l’ordre de gauche à droite des éléments d’en-tête.

- [CHeaderCtrl::OrderToIndex](../mfc/reference/cheaderctrl-class.md#ordertoindex).

   Récupère la valeur d’index pour un élément d’en-tête spécifique.

Outre les fonctions de membre précédent, le style HDS_DRAGDROP permet à l’utilisateur à glisser -déplacer des éléments d’en-tête dans le contrôle header. Pour plus d’informations, consultez [prise en charge du glisser-déplacer pour les éléments d’en-tête](../mfc/providing-drag-and-drop-support-for-header-items.md).

## <a name="see-also"></a>Voir aussi

[Utilisation de CHeaderCtrl](../mfc/using-cheaderctrl.md)

