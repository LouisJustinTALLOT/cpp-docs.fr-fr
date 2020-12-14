---
description: 'En savoir plus sur : sélection d’éléments de contrôle d’arborescence'
title: Sélection d’éléments de contrôle d’arborescence
ms.date: 11/04/2016
helpviewer_keywords:
- tree controls [MFC], item selection
- controls [MFC], selecting items in
- CTreeCtrl class [MFC], item selection
- item selection in tree controls
ms.assetid: 7bcb3b16-b9c8-4c06-9350-7bc3c1c5009b
ms.openlocfilehash: 46e1256eea3e8175b996a1b6bdfdd7c1de2739d8
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97264035"
---
# <a name="tree-control-item-selection"></a>Sélection d’éléments de contrôle d’arborescence

Lorsque la sélection passe d’un élément à un autre, un contrôle d’arborescence ([CTreeCtrl](../mfc/reference/ctreectrl-class.md)) envoie des messages de notification [TVN_SELCHANGING](/windows/win32/Controls/tvn-selchanging) et [TVN_SELCHANGED](/windows/win32/Controls/tvn-selchanged) . Les deux notifications incluent une valeur qui spécifie si la modification est le résultat d’un clic de souris ou d’une touche. Les notifications incluent également des informations sur l’élément qui obtient la sélection et l’élément qui perd la sélection. Vous pouvez utiliser ces informations pour définir des attributs d’élément qui dépendent de l’état de sélection de l’élément. Le retour de la **valeur true** en réponse à `TVN_SELCHANGING` empêche la sélection de changer ; la **valeur false** autorise la modification.

Une application peut modifier la sélection en appelant la fonction membre [SelectItem](../mfc/reference/ctreectrl-class.md#selectitem) .

## <a name="see-also"></a>Voir aussi

[Utilisation de CTreeCtrl](../mfc/using-ctreectrl.md)<br/>
[Contrôles](../mfc/controls-mfc.md)
