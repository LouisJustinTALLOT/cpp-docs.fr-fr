---
title: Classes de fenêtre dérivées | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- window class hierarchy
- hierarchies, window classes
- classes [MFC], derived
- CWnd class [MFC], classes derived from
- derived classes [MFC], window classes
- window classes [MFC], derived
ms.assetid: 6f7e437e-fbde-4a06-bfab-72d9dbf05292
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2840a78844f42481389ba868b6ab1bc5713a2c0b
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46448010"
---
# <a name="derived-window-classes"></a>Classes de fenêtre dérivées

Vous pouvez créer des fenêtres directement à partir de [CWnd](../mfc/reference/cwnd-class.md), ou dériver de nouvelles classes de fenêtre à partir de `CWnd`. Voici comment vous créez généralement des fenêtres personnalisées. Toutefois, la plupart des fenêtres utilisées dans un programme de framework sont créés à la place d’un de la `CWnd`-dérivées des classes de fenêtre frame fournies par MFC.

## <a name="frame-window-classes"></a>Classes de fenêtre frame

[CFrameWnd](../mfc/reference/cframewnd-class.md)<br/>
Utilisé pour les fenêtres frame SDI qui encadrent un seul document et sa vue. La fenêtre frame est la fenêtre frame principale de l’application et la fenêtre frame pour le document actif.

[CMDIFrameWnd](../mfc/reference/cmdiframewnd-class.md)<br/>
Utilisé en tant que la fenêtre frame principale pour les applications MDI. La fenêtre frame principale est un conteneur pour toutes les fenêtres de document MDI et partage sa barre de menus avec eux. Une fenêtre frame MDI est une fenêtre de niveau supérieur qui apparaît sur le bureau.

[CMDIChildWnd](../mfc/reference/cmdichildwnd-class.md)<br/>
Utilisé pour les documents individuels ouverts dans une fenêtre frame principale MDI. Chaque document et sa vue sont encadrés par une fenêtre de frame enfant MDI contenue dans la fenêtre frame principale MDI. Une fenêtre enfant MDI ressemble beaucoup à une fenêtre frame typique, mais est contenue dans une fenêtre de frame MDI au lieu d’assis sur le bureau. Toutefois, la fenêtre enfant MDI ne dispose pas d’une barre de menus de son propre et doit faire partie de la barre de menus de la fenêtre frame MDI qui la contient.

Pour plus d’informations, consultez [Frame Windows](../mfc/frame-windows.md).

## <a name="other-window-classes-derived-from-cwnd"></a>Autres Classes de fenêtre dérivées de CWnd

En plus des fenêtres frame, plusieurs autres catégories principales de windows sont dérivés de `CWnd`:

*Vues*<br/>
Les vues sont créées à l’aide de la `CWnd`-classe dérivée [CView](../mfc/reference/cview-class.md) (ou un de ses classes dérivées). Une vue est attachée à un document et fait Office d’intermédiaire entre le document et l’utilisateur. Une vue est une fenêtre enfant (pas un enfant MDI) qui remplit habituellement la zone cliente d’une fenêtre frame SDI ou une fenêtre de frame enfant MDI (ou la partie de la zone cliente non couverte par une barre d’outils et/ou une barre d’état).

*Boîtes de dialogue*<br/>
Boîtes de dialogue sont créés à l’aide de la `CWnd`-classe dérivée [CDialog](../mfc/reference/cdialog-class.md).

*Formulaires*<br/>
Vues de formulaire en fonction des ressources de modèle de boîte de dialogue, telles que des boîtes de dialogue, sont créés à l’aide de classes [CFormView](../mfc/reference/cformview-class.md), [CRecordView](../mfc/reference/crecordview-class.md), ou [CDaoRecordView](../mfc/reference/cdaorecordview-class.md).

*Contrôles*<br/>
Les contrôles tels que des boutons, zones de liste et zones de liste déroulante sont créés à l’aide d’autres classes dérivées de `CWnd`. Consultez [contrôler rubriques](../mfc/controls-mfc.md).

*Barres de contrôles*<br/>
Fenêtres enfants qui contiennent des contrôles. Exemples : barres d’outils et des barres d’état. Consultez [barres de contrôles](../mfc/control-bars.md).

## <a name="window-class-hierarchy"></a>Hiérarchie de classes de fenêtre

Reportez-vous à la [graphique hiérarchique MFC](../mfc/hierarchy-chart.md) dans le *référence MFC*. Les vues sont expliquées dans [Architecture Document/vue](../mfc/document-view-architecture.md). Boîtes de dialogue sont expliquées dans [boîtes de dialogue](../mfc/dialog-boxes.md).

## <a name="creating-your-own-special-purpose-window-classes"></a>Créer vos propres Classes de fenêtre de spécial

En plus des classes de fenêtre fournis par la bibliothèque de classes, vous devrez peut-être les fenêtres enfants de spécial. Pour créer une fenêtre de ce type, créez les vôtres [CWnd](../mfc/reference/cwnd-class.md)-classe dérivée et le rend une fenêtre enfant d’un frame ou la vue. N’oubliez pas que l’infrastructure gère l’étendue de la zone cliente d’une fenêtre frame de document. La plupart de la zone cliente est gérée par une vue, mais les autres fenêtres, telles que contrôle barres ou votre propre windows personnalisées, peuvent partager l’espace avec la vue. Vous devrez peut-être interagir avec les mécanismes des classes [CView](../mfc/reference/cview-class.md) et [CControlBar](../mfc/reference/ccontrolbar-class.md) pour le positionnement des fenêtres enfants dans la zone cliente d’une fenêtre frame.

[Création de Windows](../mfc/creating-windows.md) aborde la création d’objets de fenêtre et les fenêtres qu’ils gèrent.

## <a name="see-also"></a>Voir aussi

[Objets fenêtre](../mfc/window-objects.md)

