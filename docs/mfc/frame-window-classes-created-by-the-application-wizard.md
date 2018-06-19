---
title: Classes de fenêtre frame créées par l’Assistant Application | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- CMainFrame
dev_langs:
- C++
helpviewer_keywords:
- application wizards [MFC], frame window classes created by
- window classes [MFC]
- classes [MFC], frame-window
- CMDIFrameWnd class [MFC], frame windows
- window classes [MFC], frame
- CFrameWnd class [MFC], frame windows
- CMDIChildWnd class [MFC], frame windows
- frame window classes [MFC], created by application wizards
- CMainFrame class [MFC]
ms.assetid: 9947df73-4470-49a0-ac61-7b6ee401a74e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d3446de072266fdf7661d2e8d8ca0fc968279646
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33345040"
---
# <a name="frame-window-classes-created-by-the-application-wizard"></a>Classes de fenêtre frame créées par l'Assistant Application
Lorsque vous utilisez la [Assistant Application](../ide/creating-desktop-projects-by-using-application-wizards.md) pour créer une application squelette, outre l’application, document et affichage de classes, l’Assistant Application crée une classe dérivée de fenêtre frame de fenêtre frame principale de votre application. La classe est appelée `CMainFrame` par défaut et les fichiers qui le contiennent sont nommés MAINFRM. H et MAINFRM. CPP.  
  
 Si votre application SDI, votre `CMainFrame` classe est dérivée de la classe [CFrameWnd](../mfc/reference/cframewnd-class.md).  
  
 Si votre application MDI, `CMainFrame` est dérivé de la classe [CMDIFrameWnd](../mfc/reference/cmdiframewnd-class.md). Dans ce cas `CMainFrame` implémente le frame principal, qui contient les barres de menus, barre d’outils et l’état. L’Assistant Application ne dérive pas une nouvelle classe de fenêtre frame de document pour vous. En revanche, il utilise l’implémentation par défaut dans [CMDIChildWnd (classe)](../mfc/reference/cmdichildwnd-class.md). L’infrastructure MFC crée une fenêtre enfant pour contenir chaque vue (qui peut être de type `CScrollView`, `CEditView`, `CTreeView`, `CListView`, et ainsi de suite) requises par l’application. Si vous avez besoin personnaliser votre fenêtre frame de document, vous pouvez créer une nouvelle classe de fenêtre frame de document (consultez [Ajout d’une classe](../ide/adding-a-class-visual-cpp.md)).  
  
 Si vous choisissez de prendre en charge une barre d’outils, la classe a également les variables de membre de type [CToolBar](../mfc/reference/ctoolbar-class.md) et [CStatusBar](../mfc/reference/cstatusbar-class.md) et un `OnCreate` fonction gestionnaire de messages pour initialiser les deux [ barres de contrôles](../mfc/control-bars.md).  
  
 Ces classes de fenêtres frames fonctionnent telles quelles, mais pour renforcer leurs fonctionnalités, vous devez ajouter des variables membres et les fonctions membres. Vous pouvez souhaiter également avoir vos classes de fenêtre à traiter les autres messages Windows. Pour plus d’informations, consultez [modification des Styles d’une fenêtre créée par MFC](../mfc/changing-the-styles-of-a-window-created-by-mfc.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Classes de fenêtre frame](../mfc/frame-window-classes.md)   
 [Fichiers d’en-tête et fichiers sources de contrôle ou de programme MFC](../ide/mfc-program-or-control-source-and-header-files.md)

