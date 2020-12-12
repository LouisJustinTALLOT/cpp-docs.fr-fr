---
description: En savoir plus sur les méthodes de création d’info-bulles
title: Méthodes de création d'info-bulles
ms.date: 11/04/2016
helpviewer_keywords:
- CToolTipCtrl class [MFC], creating tool tips
- tool tips [MFC], tool tip controls
- tool tips [MFC], creating
ms.assetid: b015e9f4-ddfb-49a4-a5a6-fa2d45e4d328
ms.openlocfilehash: fc710f569e78f9698cdc924a071489c03b2975b1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97203105"
---
# <a name="methods-of-creating-tool-tips"></a>Méthodes de création d'info-bulles

MFC fournit trois classes pour créer et gérer le contrôle d’info-bulle : [CWnd](reference/cwnd-class.md), [CToolBarCtrl](reference/ctoolbarctrl-class.md), [CToolTipCtrl](reference/ctooltipctrl-class.md) et [CMFCToolTipCtrl](reference/cmfctooltipctrl-class.md). Les fonctions membres de l’info-bulle dans ces classes encapsulent l’API de contrôle commun Windows. La classe et la classe `CToolBarCtrl` `CToolTipCtrl` sont dérivées de la classe `CWnd` .

`CWnd` fournit quatre fonctions membres pour créer et gérer des info-bulles : [EnableToolTips](reference/cwnd-class.md#enabletooltips), [CancelToolTips](reference/cwnd-class.md#canceltooltips), [FilterToolTipMessage](reference/cwnd-class.md#filtertooltipmessage)et [OnToolHitTest](reference/cwnd-class.md#ontoolhittest). Pour plus d’informations sur la façon dont ils implémentent les info-bulles, consultez ces fonctions membres individuelles.

Si vous créez une barre d’outils à l’aide de `CToolBarCtrl` , vous pouvez implémenter des info-bulles pour cette barre d’outils directement à l’aide des fonctions membres suivantes : [GetToolTips](reference/ctoolbarctrl-class.md#gettooltips) et [SetToolTips](reference/ctoolbarctrl-class.md#settooltips). Pour plus d’informations sur la façon dont ils implémentent les info-bulles, consultez ces fonctions membres individuelles et [gestion des notifications d’info-bulle](handling-tool-tip-notifications.md) .

La `CToolTipCtrl` classe fournit les fonctionnalités du contrôle commun d’info-bulle Windows. Un seul contrôle d’info-bulle peut fournir des informations pour plusieurs outils. Un outil est soit une fenêtre, telle qu’une fenêtre ou un contrôle enfant, soit une zone rectangulaire définie par l’application dans la zone cliente d’une fenêtre. La classe [CMFCToolTipCtrl](reference/cmfctooltipctrl-class.md) dérive de `CToolTipCtrl` et fournit des fonctionnalités et des styles visuels supplémentaires.

## <a name="see-also"></a>Voir aussi

[Utilisation de CToolTipCtrl](using-ctooltipctrl.md)<br/>
[Contrôles](controls-mfc.md)
