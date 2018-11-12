---
title: Sélection d’éléments de contrôle d’arborescence
ms.date: 11/04/2016
helpviewer_keywords:
- tree controls [MFC], item selection
- controls [MFC], selecting items in
- CTreeCtrl class [MFC], item selection
- item selection in tree controls
ms.assetid: 7bcb3b16-b9c8-4c06-9350-7bc3c1c5009b
ms.openlocfilehash: bd3ade31ce1e41481943659ba9a8ef8dd77117fb
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50592713"
---
# <a name="tree-control-item-selection"></a>Sélection d’éléments de contrôle d’arborescence

Lorsque la sélection est modifiée à partir d’un élément vers un autre, un contrôle d’arborescence ([CTreeCtrl](../mfc/reference/ctreectrl-class.md)) envoie [TVN_SELCHANGING](/windows/desktop/Controls/tvn-selchanging) et [TVN_SELCHANGED](/windows/desktop/Controls/tvn-selchanged) messages de notification. Les deux notifications incluent une valeur qui spécifie si la modification est le résultat d’un clic de souris ou une combinaison de touches. Les notifications incluent également des informations sur l’élément qui gagne en la sélection et l’élément qui perd la sélection. Vous pouvez utiliser ces informations pour définir les attributs d’élément qui dépendent de l’état de sélection de l’élément. Retour **TRUE** en réponse à `TVN_SELCHANGING` empêche la sélection à partir de la modification ; retour **FALSE** autorise la modification.

Une application peut modifier la sélection en appelant le [SelectItem](../mfc/reference/ctreectrl-class.md#selectitem) fonction membre.

## <a name="see-also"></a>Voir aussi

[Utilisation de CTreeCtrl](../mfc/using-ctreectrl.md)<br/>
[Contrôles](../mfc/controls-mfc.md)

