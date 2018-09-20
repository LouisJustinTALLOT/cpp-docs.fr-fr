---
title: CTreeCtrl et CTreeView | Microsoft Docs
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
ms.openlocfilehash: e8acaecbdfb99b8ae0b27023145a0ef6aee1f219
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46399146"
---
# <a name="ctreectrl-vs-ctreeview"></a>CTreeCtrl et CTreeView

MFC fournit deux classes qui encapsulent les contrôles d’arborescence : [CTreeCtrl](../mfc/reference/ctreectrl-class.md) et [CTreeView](../mfc/reference/ctreeview-class.md). Chaque classe est utile dans différentes situations.

Utilisez `CTreeCtrl` lorsque vous avez besoin d’un contrôle de fenêtre enfant simple ; par exemple, dans une boîte de dialogue. Vous pouvez notamment utiliser `CTreeCtrl` s’il y a d’autres contrôles enfants dans la fenêtre, comme dans une boîte de dialogue standard.

Utilisez `CTreeView` lorsque vous souhaitez que le contrôle d’arborescence d’agir comme une fenêtre d’affichage dans l’architecture document/vue ainsi qu’un contrôle d’arborescence. Un `CTreeView` occupe toute la zone cliente d’une fenêtre frame ou la fenêtre de séparateur. Il est redimensionné automatiquement lorsque sa fenêtre parente est redimensionnée, et il peut traiter les messages de commande à partir des menus, barres d’outils et de touches accélérateur. Dans la mesure où un contrôle d’arborescence contient les données nécessaires pour afficher l’arbre, l’objet de document correspondant n’a pas d’être compliqué, vous pouvez même utiliser [CDocument](../mfc/reference/cdocument-class.md) comme type de document dans votre modèle de document.

## <a name="see-also"></a>Voir aussi

[Utilisation de CTreeCtrl](../mfc/using-ctreectrl.md)<br/>
[Contrôles](../mfc/controls-mfc.md)

