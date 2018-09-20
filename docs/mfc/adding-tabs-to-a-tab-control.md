---
title: Ajout d’onglets à un contrôle onglet | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- tab controls [MFC], adding tabs
- putting tabs on CTabCtrls [MFC]
- CTabCtrl class [MFC], adding tabs
- tabs [MFC], adding to CTabCtrl class [MFC]
ms.assetid: 7f3d9340-e3c7-4c71-9912-be57534ecc78
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d5f9a9ab897a91fe886a1ba3ad46fe8fab94d94c
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46416589"
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

