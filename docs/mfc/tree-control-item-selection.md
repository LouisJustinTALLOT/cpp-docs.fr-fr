---
title: Sélection d’éléments de contrôle d’arborescence
ms.date: 11/04/2016
helpviewer_keywords:
- tree controls [MFC], item selection
- controls [MFC], selecting items in
- CTreeCtrl class [MFC], item selection
- item selection in tree controls
ms.assetid: 7bcb3b16-b9c8-4c06-9350-7bc3c1c5009b
ms.openlocfilehash: 07c7b673e0f9029f8ece928b0ab17760b3863cc7
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69513340"
---
# <a name="tree-control-item-selection"></a>Sélection d’éléments de contrôle d’arborescence

Lorsque la sélection passe d’un élément à un autre, un contrôle d’arborescence ([CTreeCtrl](../mfc/reference/ctreectrl-class.md)) envoie des messages de notification [TVN_SELCHANGING](/windows/win32/Controls/tvn-selchanging) et [TVN_SELCHANGED](/windows/win32/Controls/tvn-selchanged) . Les deux notifications incluent une valeur qui spécifie si la modification est le résultat d’un clic de souris ou d’une touche. Les notifications incluent également des informations sur l’élément qui obtient la sélection et l’élément qui perd la sélection. Vous pouvez utiliser ces informations pour définir des attributs d’élément qui dépendent de l’état de sélection de l’élément. Le retour de la **valeur true** en réponse à `TVN_SELCHANGING` empêche la sélection de changer; la **valeur false** autorise la modification.

Une application peut modifier la sélection en appelant la fonction membre [SelectItem](../mfc/reference/ctreectrl-class.md#selectitem) .

## <a name="see-also"></a>Voir aussi

[Utilisation de CTreeCtrl](../mfc/using-ctreectrl.md)<br/>
[Contrôles](../mfc/controls-mfc.md)
