---
title: Ajout d'éléments au contrôle Header
ms.date: 11/04/2016
helpviewer_keywords:
- controls [MFC], header
- CHeaderCtrl class [MFC], adding items
- header controls [MFC], adding items to
ms.assetid: 2e9a28b1-7302-4a93-8037-c5a4183e589a
ms.openlocfilehash: 5749a0cae2dfe7e6c9f4c166eca487e36c2d21d2
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84616468"
---
# <a name="adding-items-to-the-header-control"></a>Ajout d'éléments au contrôle Header

Après avoir créé votre contrôle header ([CHeaderCtrl](reference/cheaderctrl-class.md)) dans sa fenêtre parente, ajoutez autant d’éléments d’en-tête que nécessaire : généralement, un par colonne.

### <a name="to-add-a-header-item"></a>Pour ajouter un élément d’en-tête

1. Préparez une structure de [HD_ITEM](/windows/win32/api/commctrl/ns-commctrl-hditemw) .

1. Appelez [CHeaderCtrl :: InsertItem](reference/cheaderctrl-class.md#insertitem), en passant la structure.

1. Répétez les étapes 1 et 2 pour les autres éléments.

Pour plus d’informations, consultez [Ajout d’un élément à un contrôle d’en-tête](/windows/win32/Controls/header-controls) dans la SDK Windows.

## <a name="see-also"></a>Voir aussi

[Utilisation de CHeaderCtrl](using-cheaderctrl.md)<br/>
[Commandes](controls-mfc.md)
