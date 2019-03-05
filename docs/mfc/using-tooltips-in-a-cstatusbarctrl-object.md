---
title: Utilisation d'info-bulles dans un objet CStatusBarCtrl
ms.date: 11/04/2016
f1_keywords:
- CStatusBarCtrl
helpviewer_keywords:
- tool tips [MFC], using in status bars
- status bars [MFC], tool tips
- CStatusBarCtrl class [MFC], tool tips
ms.assetid: a77597a7-43ef-4b8f-87bc-a8ea1dc63dc3
ms.openlocfilehash: 3f9a1fec7eb951fa76c542e09df751b4c58ddb16
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57265083"
---
# <a name="using-tooltips-in-a-cstatusbarctrl-object"></a>Utilisation d'info-bulles dans un objet CStatusBarCtrl

Pour activer les info-bulles pour un contrôle de barre d’état, créez le `CStatusBarCtrl` objet avec le style SBT_TOOLTIPS.

> [!NOTE]
>  Si vous utilisez un `CStatusBar` objet pour implémenter votre barre d’état, utilisez le `CStatusBar::CreateEx` (fonction). Il permet de spécifier des styles supplémentaires pour l’embedded `CStatusBarCtrl` objet.

Une fois le `CStatusBarCtrl` objet a été créé avec succès, utilisez [CStatusBarCtrl::SetTipText](../mfc/reference/cstatusbarctrl-class.md#settiptext) et [CStatusBarCtrl::GetTipText](../mfc/reference/cstatusbarctrl-class.md#gettiptext) pour définir et extraire le texte d’info-bulle pour un volet spécifique.

Une fois que l’info-bulle a été défini, il est affiché uniquement si la partie a une icône et aucun texte, ou si tout le texte ne peut pas être affichée à l’intérieur de la partie. Info-bulles ne sont pas pris en charge en mode simple.

## <a name="see-also"></a>Voir aussi

[Utilisation de CStatusBarCtrl](../mfc/using-cstatusbarctrl.md)<br/>
[Contrôles](../mfc/controls-mfc.md)
