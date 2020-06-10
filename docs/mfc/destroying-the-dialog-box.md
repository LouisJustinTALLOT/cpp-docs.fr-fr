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
ms.openlocfilehash: 9b1244b03dc3f6f418730dd782050448f3bf8934
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84621915"
---
# <a name="destroying-the-dialog-box"></a>Destruction de la boîte de dialogue

Les boîtes de dialogue modales sont normalement créées sur le frame de pile et détruites lorsque la fonction qui les a créées se termine. Le destructeur de l’objet Dialog est appelé lorsque l’objet est hors de portée.

Les boîtes de dialogue non modales sont normalement créées et détenues par une fenêtre frame ou une vue parente : la fenêtre frame principale de l’application ou une fenêtre frame de document. Le gestionnaire [OnClose](reference/cwnd-class.md#onclose) par défaut appelle [DestroyWindow](reference/cwnd-class.md#destroywindow), qui détruit la fenêtre de la boîte de dialogue. Si la boîte de dialogue est autonome, sans aucun pointeurs ni aucune autre sémantique de propriété spéciale, vous devez remplacer [PostNcDestroy](reference/cwnd-class.md#postncdestroy) pour détruire l’objet de boîte de dialogue C++. Vous devez également substituer [OnCancel](reference/cdialog-class.md#oncancel) et appeler `DestroyWindow` à partir de celui-ci. Si ce n’est pas le cas, le propriétaire de la boîte de dialogue doit détruire l’objet C++ lorsqu’il n’est plus nécessaire.

## <a name="see-also"></a>Voir aussi

[Utilisation des boîtes de dialogue dans MFC](life-cycle-of-a-dialog-box.md)
