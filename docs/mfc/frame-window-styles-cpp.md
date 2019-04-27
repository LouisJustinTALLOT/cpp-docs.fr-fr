---
title: Styles de fenêtre frame (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- window styles [MFC]
- PreCreateWindow method, setting window styles
- windows [MFC], MFC
- frame windows [MFC], styles
- MFC, frame windows
- styles [MFC], windows
ms.assetid: fc5058c1-eec8-48d8-9f76-3fc01cfa53f7
ms.openlocfilehash: cade8e7e50779437feb73a94058dc62118c03c10
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62219741"
---
# <a name="frame-window-styles-c"></a>Styles de fenêtre frame (C++)

Les fenêtres frame que vous obtenez avec l’infrastructure sont appropriés pour la plupart des programmes, mais vous pouvez obtenir davantage de flexibilité en utilisant les fonctions avancées [PreCreateWindow](../mfc/reference/cwnd-class.md#precreatewindow) et la fonction globale MFC [AfxRegisterWndClass ](../mfc/reference/application-information-and-management.md#afxregisterwndclass). `PreCreateWindow` est une fonction membre de `CWnd`.

Si vous appliquez le **WS_HSCROLL** et **WS_VSCROLL** styles à la fenêtre frame principale, ils sont appliqués à la place à la **MDICLIENT** fenêtre afin des utilisateurs peuvent faire défiler le **MDICLIENT** zone.

Si la fenêtre **FWS_ADDTOTITLE** bit de style est défini (ce qui est par défaut), la vue indique à la fenêtre frame titre à afficher dans la barre de titre de la fenêtre selon le nom de la vue du document.

## <a name="what-do-you-want-to-know-more-about"></a>Ce que vous souhaitez en savoir plus sur

- [La gestion des fenêtres enfants MDI (MDICLIENT)](../mfc/managing-mdi-child-windows.md), la fenêtre au sein d’un frame MDI qui contient les fenêtres enfants MDI

- [Modification des styles d’une fenêtre créée par MFC](../mfc/changing-the-styles-of-a-window-created-by-mfc.md)

- [Styles de fenêtre](../mfc/reference/styles-used-by-mfc.md#window-styles)

## <a name="see-also"></a>Voir aussi

[Fenêtres frame](../mfc/frame-windows.md)
