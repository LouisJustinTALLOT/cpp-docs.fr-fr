---
title: Méthodes de création d’info-bulles | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CToolTipCtrl class [MFC], creating tool tips
- tool tips [MFC], tool tip controls
- tool tips [MFC], creating
ms.assetid: b015e9f4-ddfb-49a4-a5a6-fa2d45e4d328
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 16b96228bd2f101e30605e555dbbc75b0dff78c3
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46374011"
---
# <a name="methods-of-creating-tool-tips"></a>Méthodes de création d'info-bulles

MFC fournit trois classes pour créer et gérer l’outil de contrôle ToolTip : [CWnd](../mfc/reference/cwnd-class.md), [CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md), [CToolTipCtrl](../mfc/reference/ctooltipctrl-class.md) et [CMFCToolTipCtrl](../mfc/reference/cmfctooltipctrl-class.md). Les fonctions membres dans ces classes encapsulent les API des contrôles communs Windows. Classe `CToolBarCtrl` et classe `CToolTipCtrl` sont dérivés de la classe `CWnd`.

`CWnd` fournit quatre fonctions membres pour créer et gérer des info-bulles : [EnableToolTips](../mfc/reference/cwnd-class.md#enabletooltips), [CancelToolTips](../mfc/reference/cwnd-class.md#canceltooltips), [FilterToolTipMessage](../mfc/reference/cwnd-class.md#filtertooltipmessage), et [OnToolHitTest ](../mfc/reference/cwnd-class.md#ontoolhittest). Consultez ces fonctions membres pour plus d’informations sur l’implémentation des info-bulles.

Si vous créez un à l’aide de la barre d’outils `CToolBarCtrl`, vous pouvez implémenter des info-bulles pour cette barre d’outils directement à l’aide de fonctions membres suivantes : [GetToolTips](../mfc/reference/ctoolbarctrl-class.md#gettooltips) et [SetToolTips](../mfc/reference/ctoolbarctrl-class.md#settooltips). Consultez ces fonctions membres et [gestion des Notifications des info](../mfc/handling-tool-tip-notifications.md) pour plus d’informations sur l’implémentation des info-bulles.

Le `CToolTipCtrl` classe fournit les fonctionnalités de Windows courantes contrôle ToolTip. Un contrôle ToolTip unique peut fournir des informations pour plusieurs outils. Un outil peut être une fenêtre, telle qu’une fenêtre enfant ou de contrôle ou d’une zone rectangulaire définie par l’application au sein de la zone cliente d’une fenêtre. Le [CMFCToolTipCtrl](../mfc/reference/cmfctooltipctrl-class.md) dérive de la classe `CToolTipCtrl` et fournit des fonctionnalités et des styles visuels supplémentaires.

## <a name="see-also"></a>Voir aussi

[Utilisation de CToolTipCtrl](../mfc/using-ctooltipctrl.md)<br/>
[Contrôles](../mfc/controls-mfc.md)

