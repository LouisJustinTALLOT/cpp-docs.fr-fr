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
ms.openlocfilehash: c17ba2b6dd79e8e62baa29bba403c136d16a0d95
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/21/2020
ms.locfileid: "80077533"
---
# <a name="frame-window-classes-created-by-the-application-wizard"></a>Classes de fenêtre frame créées par l'Assistant Application

Lorsque vous créez un projet MFC à partir de la boîte de dialogue **nouveau projet** , en plus des classes d’application, de document et de vue, l’Assistant application crée une classe de fenêtre frame dérivée pour la fenêtre frame principale de votre application. La classe est appelée `CMainFrame` par défaut, et les fichiers qui la contiennent sont nommés MAINFRM. H et MAINFRM. Cotisations.

Si votre application est SDI, votre classe `CMainFrame` est dérivée de la classe [CFrameWnd](../mfc/reference/cframewnd-class.md).

Si votre application est MDI, `CMainFrame` est dérivée de la classe [CMDIFrameWnd](../mfc/reference/cmdiframewnd-class.md). Dans ce cas `CMainFrame` implémente le frame principal, qui contient le menu, la barre d’outils et les barres d’État. L’Assistant application ne dérive pas une nouvelle classe de fenêtre frame de document pour vous. Au lieu de cela, elle utilise l’implémentation par défaut dans la [classe CMDIChildWnd](../mfc/reference/cmdichildwnd-class.md). L’infrastructure MFC crée une fenêtre enfant pour contenir chaque vue (qui peut être de type `CScrollView`, `CEditView`, `CTreeView`, `CListView`, etc.) requise par l’application. Si vous avez besoin de personnaliser la fenêtre frame de document, vous pouvez créer une nouvelle classe de fenêtre frame de document (consultez [Ajout d’une classe](../ide/adding-a-class-visual-cpp.md)).

Si vous choisissez de prendre en charge une barre d’outils, la classe a également des variables membres de type [CToolBar](../mfc/reference/ctoolbar-class.md) et [CStatusBar](../mfc/reference/cstatusbar-class.md) et une `OnCreate` fonction de gestionnaire de messages pour initialiser les deux [barres de contrôle](../mfc/control-bars.md).

Ces classes de fenêtres frames fonctionnent comme créées, mais pour améliorer leurs fonctionnalités, vous devez ajouter des variables membres et des fonctions membres. Vous pouvez également faire en sorte que vos classes de fenêtres gèrent d’autres messages Windows. Pour plus d’informations, consultez [modification des styles d’une fenêtre créée par MFC](../mfc/changing-the-styles-of-a-window-created-by-mfc.md).

## <a name="see-also"></a>Voir aussi

[Classes de fenêtre frame](../mfc/frame-window-classes.md)<br/>
[Fichiers d’en-tête et fichiers sources de contrôle ou de programme MFC](../build/reference/mfc-program-or-control-source-and-header-files.md)
