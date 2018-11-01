---
title: Destruction de la boîte de dialogue
ms.date: 11/04/2016
helpviewer_keywords:
- dialog boxes [MFC], deleting
- destruction, dialog box
- dialog boxes [MFC], destroying
- dialog boxes [MFC], removing
- modeless dialog boxes [MFC], destroying
- MFC dialog boxes [MFC], destroying
- modal dialog boxes [MFC], destroying
ms.assetid: dabceee7-3639-4d85-bf34-73515441b3d0
ms.openlocfilehash: f84e36a2a002610c294653012c40707fddcaba54
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50607465"
---
# <a name="destroying-the-dialog-box"></a>Destruction de la boîte de dialogue

Boîtes de dialogue modales sont normalement créés sur le frame de pile et détruits à la fin de la fonction qui les a créés. Destructeur de l’objet de la boîte de dialogue est appelé lorsque l’objet est hors de portée.

Boîtes de dialogue non modales sont généralement créés et détenus par une fenêtre d’affichage ou le frame parent : fenêtre frame principale de l’application ou une fenêtre frame de document. La valeur par défaut [OnClose](../mfc/reference/cwnd-class.md#onclose) appels du gestionnaire [DestroyWindow](../mfc/reference/cwnd-class.md#destroywindow), qui détruit la fenêtre de la boîte de dialogue. Si la boîte de dialogue est autonome, aucun pointeur ou autres sémantiques d’appartenance particulières, vous devez substituer [PostNcDestroy](../mfc/reference/cwnd-class.md#postncdestroy) pour détruire l’objet de la boîte de dialogue C++. Vous devez également substituer [OnCancel](../mfc/reference/cdialog-class.md#oncancel) et appelez `DestroyWindow` à partir de qu’il contient. Si ce n’est pas le cas, le propriétaire de la boîte de dialogue doit détruire l’objet C++ lorsqu’il n’est plus nécessaire.

## <a name="see-also"></a>Voir aussi

[Cycle de vie d’une boîte de dialogue](../mfc/life-cycle-of-a-dialog-box.md)

