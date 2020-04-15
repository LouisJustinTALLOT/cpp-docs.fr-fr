---
title: Utilisation d'info-bulles dans un objet CStatusBarCtrl
ms.date: 11/04/2016
helpviewer_keywords:
- tool tips [MFC], using in status bars
- status bars [MFC], tool tips
- CStatusBarCtrl class [MFC], tool tips
ms.assetid: a77597a7-43ef-4b8f-87bc-a8ea1dc63dc3
ms.openlocfilehash: 29d326c708743424686d616bbaf172ccd72481ce
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374692"
---
# <a name="using-tooltips-in-a-cstatusbarctrl-object"></a>Utilisation d'info-bulles dans un objet CStatusBarCtrl

Pour activer les outils pour un `CStatusBarCtrl` contrôle de barre d’état, créez l’objet avec le style SBT_TOOLTIPS.

> [!NOTE]
> Si vous utilisez `CStatusBar` un objet pour implémenter votre barre d’état, utilisez la `CStatusBar::CreateEx` fonction. Il vous permet de spécifier des styles supplémentaires pour l’objet intégré. `CStatusBarCtrl`

Une `CStatusBarCtrl` fois que l’objet a été créé avec succès, utilisez [CStatusBarCtrl::SetTipText](../mfc/reference/cstatusbarctrl-class.md#settiptext) et [CStatusBarCtrl::GetTipText](../mfc/reference/cstatusbarctrl-class.md#gettiptext) pour définir et récupérer le texte de pointe pour un volet spécifique.

Une fois que la pointe de l’outil a été définie, elle n’est affichée que si la pièce a une icône et aucun texte, ou si tout le texte ne peut pas être affiché à l’intérieur de la pièce. Les conseils d’outils ne sont pas pris en charge en mode simple.

## <a name="see-also"></a>Voir aussi

[Utilisation de CStatusBarCtrl](../mfc/using-cstatusbarctrl.md)<br/>
[Contrôles](../mfc/controls-mfc.md)
