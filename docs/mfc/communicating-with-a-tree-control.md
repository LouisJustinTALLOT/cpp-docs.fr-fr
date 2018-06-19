---
title: Communication avec un contrôle d’arborescence | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- tree controls [MFC], communicating with
- CTreeCtrl class [MFC], calling member functions
- communications, tree controls
- tree controls
ms.assetid: 680ad9ee-b11f-452d-93fa-501ca7d7e069
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: af0b248d5e32b535c23cc17b48efdd551dad7a2c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33341995"
---
# <a name="communicating-with-a-tree-control"></a>Communication avec un contrôle d’arborescence
Vous utilisez différentes méthodes pour appeler des fonctions membres dans un [CTreeCtrl](../mfc/reference/ctreectrl-class.md) objet selon la façon dont l’objet a été créé :  
  
-   Si le contrôle d’arborescence est dans une boîte de dialogue, utilisez une variable membre de type `CTreeCtrl` que vous créez dans la classe de boîte de dialogue.  
  
-   Si le contrôle d’arborescence est une fenêtre enfant, utilisez la `CTreeCtrl` objet (ou pointeur) que vous avez utilisé pour construire l’objet.  
  
-   Si vous utilisez un `CTreeView` de l’objet, utilisez la fonction [CTreeView::GetTreeCtrl](../mfc/reference/ctreeview-class.md#gettreectrl) pour obtenir une référence au contrôle d’arborescence. Vous pouvez initialiser une autre référence avec cette valeur ou assigner l’adresse de la référence à un `CTreeCtrl` pointeur.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation de CTreeCtrl](../mfc/using-ctreectrl.md)   
 [Contrôles](../mfc/controls-mfc.md)

