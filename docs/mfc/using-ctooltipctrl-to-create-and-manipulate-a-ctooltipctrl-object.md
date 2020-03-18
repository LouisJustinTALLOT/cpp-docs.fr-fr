---
title: Utilisation de CToolTipCtrl pour créer et manipuler un objet CToolTipCtrl
ms.date: 11/04/2016
helpviewer_keywords:
- tool tips [MFC], creating
- CToolTipCtrl class [MFC], using
ms.assetid: 0a34583f-f66d-46a1-a239-31b80ea395ad
ms.openlocfilehash: 37dc7bc5a411ebab3737b87fd6977b26cff68178
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/17/2020
ms.locfileid: "79442221"
---
# <a name="using-ctooltipctrl-to-create-and-manipulate-a-ctooltipctrl-object"></a>Utilisation de CToolTipCtrl pour créer et manipuler un objet CToolTipCtrl

Voici un exemple d’utilisation de [CToolTipCtrl](../mfc/reference/ctooltipctrl-class.md) :

### <a name="to-create-and-manipulate-a-ctooltipctrl"></a>Pour créer et manipuler un CToolTipCtrl

1. Construisez l’objet `CToolTipCtrl`.

1. Appelez [Create](../mfc/reference/ctooltipctrl-class.md#create) pour créer le contrôle commun d’info-bulle Windows et attachez-le à l’objet `CToolTipCtrl`.

1. Appelez [AddTool](../mfc/reference/ctooltipctrl-class.md#addtool) pour enregistrer un outil avec le contrôle d’info-bulle, afin que les informations stockées dans l’info-bulle s’affichent lorsque le curseur se trouve sur l’outil.

1. Appelez [SetToolInfo](../mfc/reference/ctooltipctrl-class.md#settoolinfo) pour définir les informations conservées par une info-bulle pour un outil.

1. Appelez [SetToolRect](../mfc/reference/ctooltipctrl-class.md#settoolrect) pour définir un nouveau rectangle englobant pour un outil.

1. Appelez [HitTest](../mfc/reference/ctooltipctrl-class.md#hittest) pour tester un point afin de déterminer s’il se trouve dans le rectangle englobant de l’outil donné et, si c’est le cas, récupérer des informations sur l’outil.

1. Appelez [GetToolCount](../mfc/reference/ctooltipctrl-class.md#gettoolcount) pour récupérer le nombre d’outils inscrits avec le contrôle d’info-bulle.

## <a name="see-also"></a>Voir aussi

[Utilisation de CToolTipCtrl](../mfc/using-ctooltipctrl.md)<br/>
[Contrôles](../mfc/controls-mfc.md)
