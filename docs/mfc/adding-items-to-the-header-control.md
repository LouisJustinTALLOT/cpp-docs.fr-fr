---
title: Ajout d'éléments au contrôle Header
ms.date: 11/04/2016
helpviewer_keywords:
- controls [MFC], header
- CHeaderCtrl class [MFC], adding items
- header controls [MFC], adding items to
ms.assetid: 2e9a28b1-7302-4a93-8037-c5a4183e589a
ms.openlocfilehash: c751458a3a2e7e049364ef22a161a3dc9f81df13
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50483562"
---
# <a name="adding-items-to-the-header-control"></a>Ajout d'éléments au contrôle Header

Après avoir créé votre contrôle header ([CHeaderCtrl](../mfc/reference/cheaderctrl-class.md)) dans sa fenêtre parente, ajoutez autant « éléments d’en-tête » que vous avez besoin : généralement un par colonne.

### <a name="to-add-a-header-item"></a>Pour ajouter un élément d’en-tête

1. Préparer un [structure HD_ITEM](/windows/desktop/api/commctrl/ns-commctrl-_hd_itema) structure.

1. Appelez [CHeaderCtrl::InsertItem](../mfc/reference/cheaderctrl-class.md#insertitem), en passant la structure.

1. Répétez les étapes 1 et 2 pour les éléments supplémentaires.

Pour plus d’informations, consultez [Ajout d’un élément à un contrôle d’en-tête](/windows/desktop/Controls/header-controls) dans le SDK Windows.

## <a name="see-also"></a>Voir aussi

[Utilisation de CHeaderCtrl](../mfc/using-cheaderctrl.md)<br/>
[Contrôles](../mfc/controls-mfc.md)

