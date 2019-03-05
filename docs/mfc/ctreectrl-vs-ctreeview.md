---
title: CTreeCtrl et CTreeView
ms.date: 11/04/2016
f1_keywords:
- CTreeCtrl
- CTreeView
helpviewer_keywords:
- tree view controls
- CTreeCtrl class [MFC], vs. CTreeView class [MFC]
- CTreeView class [MFC], vs. CTreeCtrl class [MFC]
- tree controls [MFC], and tree view
ms.assetid: bba5af25-103f-4b53-84d3-071bc9bd6494
ms.openlocfilehash: 29349e169e5ad8475001235d9b355da52156d683
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57271630"
---
# <a name="ctreectrl-vs-ctreeview"></a>CTreeCtrl et CTreeView

MFC fournit deux classes qui encapsulent les contrôles d’arborescence : [CTreeCtrl](../mfc/reference/ctreectrl-class.md) et [CTreeView](../mfc/reference/ctreeview-class.md). Chaque classe est utile dans différentes situations.

Utilisez `CTreeCtrl` lorsque vous avez besoin d’un contrôle de fenêtre enfant simple ; par exemple, dans une boîte de dialogue. Vous pouvez notamment utiliser `CTreeCtrl` s’il y a d’autres contrôles enfants dans la fenêtre, comme dans une boîte de dialogue standard.

Utilisez `CTreeView` lorsque vous souhaitez que le contrôle d’arborescence d’agir comme une fenêtre d’affichage dans l’architecture document/vue ainsi qu’un contrôle d’arborescence. Un `CTreeView` occupe toute la zone cliente d’une fenêtre frame ou la fenêtre de séparateur. Il est redimensionné automatiquement lorsque sa fenêtre parente est redimensionnée, et il peut traiter les messages de commande à partir des menus, barres d’outils et de touches accélérateur. Dans la mesure où un contrôle d’arborescence contient les données nécessaires pour afficher l’arbre, l’objet de document correspondant n’a pas d’être compliqué, vous pouvez même utiliser [CDocument](../mfc/reference/cdocument-class.md) comme type de document dans votre modèle de document.

## <a name="see-also"></a>Voir aussi

[Utilisation de CTreeCtrl](../mfc/using-ctreectrl.md)<br/>
[Contrôles](../mfc/controls-mfc.md)
