---
title: Styles de fenêtre frame (C++) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- window styles [MFC]
- PreCreateWindow method, setting window styles
- windows [MFC], MFC
- frame windows [MFC], styles
- MFC, frame windows
- styles [MFC], windows
ms.assetid: fc5058c1-eec8-48d8-9f76-3fc01cfa53f7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 102b3a4c8372a53aada23ad448ce5dc1cf323a97
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33343756"
---
# <a name="frame-window-styles-c"></a>Styles de fenêtre frame (C++)
Fenêtres frame que vous obtenez avec l’infrastructure conviennent pour la plupart des programmes, mais vous pouvez obtenir plus de souplesse à l’aide de fonctions avancées [PreCreateWindow](../mfc/reference/cwnd-class.md#precreatewindow) et la fonction globale MFC [AfxRegisterWndClass ](../mfc/reference/application-information-and-management.md#afxregisterwndclass). `PreCreateWindow` est une fonction membre de `CWnd`.  
  
 Si vous appliquez le **WS_HSCROLL** et **WS_VSCROLL** styles à la fenêtre frame principale, ils sont appliqués à la place à la **MDICLIENT** fenêtre afin des utilisateurs peuvent faire défiler le **MDICLIENT** zone.  
  
 Si la fenêtre **FWS_ADDTOTITLE** bit de style est défini (ce qui est par défaut), l’affichage indique la fenêtre frame le titre à afficher dans la barre de titre de la fenêtre selon le nom de l’affichage du document.  
  
## <a name="what-do-you-want-to-know-more-about"></a>Que voulez-vous en savoir plus  
  
-   [La gestion des fenêtres enfants MDI (MDICLIENT)](../mfc/managing-mdi-child-windows.md), la fenêtre dans un frame MDI qui contient les fenêtres enfants MDI  
  
-   [Modification des styles d’une fenêtre créée par MFC](../mfc/changing-the-styles-of-a-window-created-by-mfc.md)  
  
-   [Styles de fenêtre](../mfc/reference/styles-used-by-mfc.md#window-styles)  
  
## <a name="see-also"></a>Voir aussi  
 [Fenêtres frame](../mfc/frame-windows.md)

