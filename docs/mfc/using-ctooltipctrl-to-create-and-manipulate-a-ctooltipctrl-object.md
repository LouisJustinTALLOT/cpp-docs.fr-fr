---
title: Utilisation de CToolTipCtrl pour créer et manipuler un objet CToolTipCtrl | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- CToolTipCtrl
dev_langs:
- C++
helpviewer_keywords:
- tool tips [MFC], creating
- CToolTipCtrl class [MFC], using
ms.assetid: 0a34583f-f66d-46a1-a239-31b80ea395ad
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 186972164496889b471ebfc11e19017129ad943b
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46378980"
---
# <a name="using-ctooltipctrl-to-create-and-manipulate-a-ctooltipctrl-object"></a>Utilisation de CToolTipCtrl pour créer et manipuler un objet CToolTipCtrl

Voici un exemple de [CToolTipCtrl](../mfc/reference/ctooltipctrl-class.md) utilisation :

### <a name="to-create-and-manipulate-a-ctooltipctrl"></a>Pour créer et manipuler un objet CToolTipCtrl

1. Construire la `CToolTipCtrl` objet.

1. Appelez [créer](../mfc/reference/ctooltipctrl-class.md#create) pour créer le contrôle commun Windows info-bulle et l’attacher à la `CToolTipCtrl` objet.

1. Appelez [AddTool](../mfc/reference/ctooltipctrl-class.md#addtool) pour inscrire un outil avec le contrôle d’info-bulle Info, afin que les informations stockées dans l’info-bulle s’affiche lorsque le curseur se trouve sur l’outil.

1. Appelez [SetToolInfo](../mfc/reference/ctooltipctrl-class.md#settoolinfo) pour définir les informations qui tient à jour une info-bulle pour un outil.

1. Appelez [SetToolRect](../mfc/reference/ctooltipctrl-class.md#settoolrect) pour définir un nouveau rectangle englobant pour un outil.

1. Appelez [HitTest](../mfc/reference/ctooltipctrl-class.md#hittest) pour tester un point pour déterminer si elle se trouve dans le rectangle englobant de l’outil donné et, le cas échéant, récupérer des informations sur l’outil.

1. Appelez [GetToolCount](../mfc/reference/ctooltipctrl-class.md#gettoolcount) pour récupérer un nombre des outils inscrit avec le contrôle info-bulle.

## <a name="see-also"></a>Voir aussi

[Utilisation de CToolTipCtrl](../mfc/using-ctooltipctrl.md)<br/>
[Contrôles](../mfc/controls-mfc.md)

