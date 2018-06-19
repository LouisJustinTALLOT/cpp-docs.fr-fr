---
title: CTreeCtrl vs. CTreeView | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- CTreeCtrl
- CTreeView
dev_langs:
- C++
helpviewer_keywords:
- tree view controls
- CTreeCtrl class [MFC], vs. CTreeView class [MFC]
- CTreeView class [MFC], vs. CTreeCtrl class [MFC]
- tree controls [MFC], and tree view
ms.assetid: bba5af25-103f-4b53-84d3-071bc9bd6494
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d71048b6f03f7f1b4400c0a88c178d1b97acdf2f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33342031"
---
# <a name="ctreectrl-vs-ctreeview"></a>CTreeCtrl vs. CTreeView
MFC fournit deux classes qui encapsulent les contrôles d’arborescence : [CTreeCtrl](../mfc/reference/ctreectrl-class.md) et [CTreeView](../mfc/reference/ctreeview-class.md). Chaque classe est utile dans différentes situations.  
  
 Utilisez `CTreeCtrl` lorsque vous avez besoin d’un contrôle de fenêtre enfant simple ; par exemple, dans une boîte de dialogue. Vous pouvez notamment utiliser `CTreeCtrl` s’il y a d’autres contrôles enfants dans la fenêtre, comme dans une boîte de dialogue standard.  
  
 Utilisez `CTreeView` lorsque vous souhaitez que le contrôle se comporte comme une fenêtre d’affichage dans l’architecture document/vue ainsi qu’un contrôle d’arborescence. A `CTreeView` occupe la zone cliente d’une fenêtre frame ou une fenêtre fractionnée. Il est redimensionné automatiquement lorsque sa fenêtre parente est redimensionnée, et il peut traiter des messages de commande à partir des menus, barres d’outils et de touches accélérateur. Dans la mesure où un contrôle d’arborescence contient les données nécessaires à l’affichage de l’arborescence, l’objet de document correspondant pas nécessairement être complexe, vous pouvez même utiliser [CDocument](../mfc/reference/cdocument-class.md) comme type de document dans votre modèle de document.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation de CTreeCtrl](../mfc/using-ctreectrl.md)   
 [Contrôles](../mfc/controls-mfc.md)

