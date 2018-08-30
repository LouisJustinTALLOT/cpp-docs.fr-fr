---
title: Sélection d’éléments de contrôle d’arborescence | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- tree controls [MFC], item selection
- controls [MFC], selecting items in
- CTreeCtrl class [MFC], item selection
- item selection in tree controls
ms.assetid: 7bcb3b16-b9c8-4c06-9350-7bc3c1c5009b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: fd6632a44dd4806b8f13683b50cad76b5eebe27a
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/29/2018
ms.locfileid: "43212579"
---
# <a name="tree-control-item-selection"></a>Sélection d’éléments de contrôle d’arborescence
Lorsque la sélection est modifiée à partir d’un élément vers un autre, un contrôle d’arborescence ([CTreeCtrl](../mfc/reference/ctreectrl-class.md)) envoie [TVN_SELCHANGING](/windows/desktop/Controls/tvn-selchanging) et [TVN_SELCHANGED](/windows/desktop/Controls/tvn-selchanged) messages de notification. Les deux notifications incluent une valeur qui spécifie si la modification est le résultat d’un clic de souris ou une combinaison de touches. Les notifications incluent également des informations sur l’élément qui gagne en la sélection et l’élément qui perd la sélection. Vous pouvez utiliser ces informations pour définir les attributs d’élément qui dépendent de l’état de sélection de l’élément. Retour **TRUE** en réponse à `TVN_SELCHANGING` empêche la sélection à partir de la modification ; retour **FALSE** autorise la modification.  
  
 Une application peut modifier la sélection en appelant le [SelectItem](../mfc/reference/ctreectrl-class.md#selectitem) fonction membre.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation de CTreeCtrl](../mfc/using-ctreectrl.md)   
 [Contrôles](../mfc/controls-mfc.md)

