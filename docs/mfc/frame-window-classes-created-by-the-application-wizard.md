---
title: Classes de fenêtre frame créées par l'Assistant Application
ms.date: 11/04/2016
f1_keywords:
- CMainFrame
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
ms.openlocfilehash: 46da8fc0cb98406bdf97285d7c6f824afd61c4bb
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62392815"
---
# <a name="frame-window-classes-created-by-the-application-wizard"></a>Classes de fenêtre frame créées par l'Assistant Application

Lorsque vous permettent de créer un nouveau MFC project à partir de la **nouveau projet** boîte de dialogue, en plus des applications, documents et classes d’affichage, l’Assistant Application crée une classe dérivée de fenêtre frame de fenêtre frame principale de votre application. La classe est appelée `CMainFrame` par défaut et les fichiers qui le contiennent sont nommés MAINFRM. H et MAINFRM. CPP.

Si votre application SDI, votre `CMainFrame` classe est dérivée de la classe [CFrameWnd](../mfc/reference/cframewnd-class.md).

Si votre application MDI, `CMainFrame` est dérivé de la classe [CMDIFrameWnd](../mfc/reference/cmdiframewnd-class.md). Dans ce cas `CMainFrame` implémente le frame principal, qui contient les barres de menu, barre d’outils et l’état. L’Assistant Application ne dérive pas d’une nouvelle classe de fenêtre frame de document pour vous. Au lieu de cela, elle utilise l’implémentation par défaut dans [CMDIChildWnd (classe)](../mfc/reference/cmdichildwnd-class.md). L’infrastructure MFC crée une fenêtre enfant pour contenir chaque vue (qui peut être de type `CScrollView`, `CEditView`, `CTreeView`, `CListView`, et ainsi de suite) requis par l’application. Si vous avez besoin personnaliser votre fenêtre frame de document, vous pouvez créer une nouvelle classe de fenêtre frame de document (voir [Ajout d’une classe](../ide/adding-a-class-visual-cpp.md)).

Si vous choisissez de prendre en charge une barre d’outils, la classe a également des variables de membre de type [CToolBar](../mfc/reference/ctoolbar-class.md) et [CStatusBar](../mfc/reference/cstatusbar-class.md) et un `OnCreate` fonction de gestionnaire de messages pour initialiser les deux [ les barres de contrôle](../mfc/control-bars.md).

Ces classes de fenêtre frame fonctionnent comme créé, mais pour améliorer leurs fonctionnalités, vous devez ajouter des variables membres et les fonctions membres. Vous souhaiterez également avoir vos classes de fenêtre Gérer les autres messages Windows. Pour plus d’informations, consultez [modification des Styles d’une fenêtre créée par MFC](../mfc/changing-the-styles-of-a-window-created-by-mfc.md).

## <a name="see-also"></a>Voir aussi

[Classes de fenêtre frame](../mfc/frame-window-classes.md)<br/>
[Fichiers d’en-tête et fichiers sources de contrôle ou de programme MFC](../build/reference/mfc-program-or-control-source-and-header-files.md)

