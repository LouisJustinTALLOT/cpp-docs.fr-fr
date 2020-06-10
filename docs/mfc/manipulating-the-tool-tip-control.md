---
title: Manipulation du contrôle d'info-bulle
ms.date: 11/04/2016
helpviewer_keywords:
- CToolTipCtrl class [MFC], manipulating tool tip attributes
- tool tips [MFC], attributes
ms.assetid: 3600afe5-712a-4b56-8456-96e85fe879af
ms.openlocfilehash: 61bc35e8b19ba7645736b939acac6cdaa6cb7316
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84622425"
---
# <a name="manipulating-the-tool-tip-control"></a>Manipulation du contrôle d'info-bulle

La classe `CToolTipCtrl` fournit un groupe de fonctions membres qui contrôlent les différents attributs de l' `CToolTipCtrl` objet et la fenêtre d’info-bulle.

Les durées initiales, contextuelles et de réaffichage des fenêtres d’info-bulle peuvent être définies et récupérées avec des appels à [GetDelayTime](reference/ctooltipctrl-class.md#getdelaytime) et [SetDelayTime](reference/ctooltipctrl-class.md#setdelaytime).

Modifiez l’apparence des fenêtres d’info-bulle avec les fonctions suivantes :

- [GetMargin](reference/ctooltipctrl-class.md#getmargin) et [setMargin](reference/ctooltipctrl-class.md#setmargin) récupère et définit la largeur entre la bordure de l’info-bulle et le texte d’info-bulle.

- [GetMaxTipWidth](reference/ctooltipctrl-class.md#getmaxtipwidth) et [SetMaxTipWidth](reference/ctooltipctrl-class.md#setmaxtipwidth) récupère et définit la largeur maximale de la fenêtre d’info-bulle.

- [GetTipBkColor](reference/ctooltipctrl-class.md#gettipbkcolor) et [SetTipBkColor](reference/ctooltipctrl-class.md#settipbkcolor) récupère et définit la couleur d’arrière-plan de la fenêtre d’info-bulle.

- [GetTipTextColor](reference/ctooltipctrl-class.md#gettiptextcolor) et [SetTipTextColor](reference/ctooltipctrl-class.md#settiptextcolor) récupère et définit la couleur de texte de la fenêtre d’info-bulle.

Pour que le contrôle d’info-bulle soit notifié des messages importants, tels que les messages WM_LBUTTONXXX, vous devez relayer les messages vers votre contrôle d’info-bulle. La meilleure méthode pour ce relais consiste à effectuer un appel à [CToolTipCtrl :: RelayEvent](reference/ctooltipctrl-class.md#relayevent)dans la `PreTranslateMessage` fonction de la fenêtre propriétaire. L’exemple suivant illustre une méthode possible (en supposant que le contrôle d’info-bulle est appelé `m_ToolTip` ) :

[!code-cpp[NVC_MFCControlLadenDialog#41](codesnippet/cpp/manipulating-the-tool-tip-control_1.cpp)]

Pour supprimer immédiatement une fenêtre d’info-bulle, appelez la fonction membre [pop](reference/ctooltipctrl-class.md#pop) .

## <a name="see-also"></a>Voir aussi

[Utilisation de CToolTipCtrl](using-ctooltipctrl.md)<br/>
[Commandes](controls-mfc.md)
