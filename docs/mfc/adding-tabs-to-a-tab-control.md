---
description: 'En savoir plus sur : ajout d’onglets à un contrôle Tab'
title: Ajout d'onglets à un contrôle Tab
ms.date: 11/04/2016
helpviewer_keywords:
- tab controls [MFC], adding tabs
- putting tabs on CTabCtrls [MFC]
- CTabCtrl class [MFC], adding tabs
- tabs [MFC], adding to CTabCtrl class [MFC]
ms.assetid: 7f3d9340-e3c7-4c71-9912-be57534ecc78
ms.openlocfilehash: ca25edf349fb11271d4e355241f4724d11bc4ac0
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97185464"
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
[Contrôles](controls-mfc.md)
