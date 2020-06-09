---
title: Ajout d'onglets à un contrôle Tab
ms.date: 11/04/2016
helpviewer_keywords:
- tab controls [MFC], adding tabs
- putting tabs on CTabCtrls [MFC]
- CTabCtrl class [MFC], adding tabs
- tabs [MFC], adding to CTabCtrl class [MFC]
ms.assetid: 7f3d9340-e3c7-4c71-9912-be57534ecc78
ms.openlocfilehash: 89132e94396b51bee4a111b963c67d029f3dd9df
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84616531"
---
# <a name="adding-tabs-to-a-tab-control"></a>Ajout d'onglets à un contrôle Tab

Après avoir créé le contrôle onglet ([CTabCtrl](reference/ctabctrl-class.md)), ajoutez autant d’onglets que nécessaire.

### <a name="to-add-a-tab-item"></a>Pour ajouter un élément d’onglet

1. Préparez une structure [TCITEM](/windows/win32/api/commctrl/ns-commctrl-tcitemw) .

1. Appelez [CTabCtrl :: InsertItem](reference/ctabctrl-class.md#insertitem), en passant la structure.

1. Répétez les étapes 1 et 2 pour les autres éléments de l’onglet.

Pour plus d’informations, consultez [création d’un contrôle onglet](/windows/win32/Controls/tab-controls) dans la SDK Windows.

## <a name="see-also"></a>Voir aussi

[Utilisation de CTabCtrl](using-ctabctrl.md)<br/>
[Commandes](controls-mfc.md)
