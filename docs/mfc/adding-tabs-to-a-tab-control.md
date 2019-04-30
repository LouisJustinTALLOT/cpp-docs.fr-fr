---
title: Ajout d'onglets à un contrôle Tab
ms.date: 11/04/2016
helpviewer_keywords:
- tab controls [MFC], adding tabs
- putting tabs on CTabCtrls [MFC]
- CTabCtrl class [MFC], adding tabs
- tabs [MFC], adding to CTabCtrl class [MFC]
ms.assetid: 7f3d9340-e3c7-4c71-9912-be57534ecc78
ms.openlocfilehash: f769de7bcf3e410cca717c17237d1e49ef8562c9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62394765"
---
# <a name="adding-tabs-to-a-tab-control"></a>Ajout d'onglets à un contrôle Tab

Après la création du contrôle tab ([CTabCtrl](../mfc/reference/ctabctrl-class.md)), ajoutez autant de tabulations que vous avez besoin.

### <a name="to-add-a-tab-item"></a>Pour ajouter un élément d’onglet

1. Préparer un [TCITEM](/windows/desktop/api/commctrl/ns-commctrl-tagtcitema) structure.

1. Appelez [CTabCtrl::InsertItem](../mfc/reference/ctabctrl-class.md#insertitem), en passant la structure.

1. Répétez les étapes 1 et 2 pour ajouter d’autres onglets.

Pour plus d’informations, consultez [création d’un contrôle onglet](/windows/desktop/Controls/tab-controls) dans le SDK Windows.

## <a name="see-also"></a>Voir aussi

[Utilisation de CTabCtrl](../mfc/using-ctabctrl.md)<br/>
[Contrôles](../mfc/controls-mfc.md)
