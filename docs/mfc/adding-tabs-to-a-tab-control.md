---
title: Ajout d'onglets à un contrôle Tab
ms.date: 11/04/2016
helpviewer_keywords:
- tab controls [MFC], adding tabs
- putting tabs on CTabCtrls [MFC]
- CTabCtrl class [MFC], adding tabs
- tabs [MFC], adding to CTabCtrl class [MFC]
ms.assetid: 7f3d9340-e3c7-4c71-9912-be57534ecc78
ms.openlocfilehash: 8915b3af083ebe318e8527b2f83099bf61e7e3ce
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69509298"
---
# <a name="adding-tabs-to-a-tab-control"></a>Ajout d'onglets à un contrôle Tab

Après avoir créé le contrôle onglet ([CTabCtrl](../mfc/reference/ctabctrl-class.md)), ajoutez autant d’onglets que nécessaire.

### <a name="to-add-a-tab-item"></a>Pour ajouter un élément d’onglet

1. Préparez une structure [TCITEM](/windows/win32/api/commctrl/ns-commctrl-tcitemw) .

1. Appelez [CTabCtrl:: InsertItem](../mfc/reference/ctabctrl-class.md#insertitem), en passant la structure.

1. Répétez les étapes 1 et 2 pour les autres éléments de l’onglet.

Pour plus d’informations, consultez [création d’un contrôle onglet](/windows/win32/Controls/tab-controls) dans la SDK Windows.

## <a name="see-also"></a>Voir aussi

[Utilisation de CTabCtrl](../mfc/using-ctabctrl.md)<br/>
[Contrôles](../mfc/controls-mfc.md)
