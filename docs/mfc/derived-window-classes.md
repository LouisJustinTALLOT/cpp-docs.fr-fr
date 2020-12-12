---
description: 'En savoir plus sur : classes de fenêtres dérivées'
title: Classes de fenêtre dérivées
ms.date: 11/04/2016
helpviewer_keywords:
- window class hierarchy
- hierarchies, window classes
- classes [MFC], derived
- CWnd class [MFC], classes derived from
- derived classes [MFC], window classes
- window classes [MFC], derived
ms.assetid: 6f7e437e-fbde-4a06-bfab-72d9dbf05292
ms.openlocfilehash: 9219267b5351f972257d9770f8e8b38039b85788
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97335898"
---
# <a name="derived-window-classes"></a>Classes de fenêtre dérivées

Vous pouvez créer des fenêtres directement à partir de [CWnd](reference/cwnd-class.md)ou dériver de nouvelles classes de fenêtres à partir de `CWnd` . C’est ainsi que vous créez généralement vos propres fenêtres personnalisées. Toutefois, la plupart des fenêtres utilisées dans un programme d’infrastructure sont créées à partir de l’une des `CWnd` classes de fenêtre frame dérivées fournies par MFC.

## <a name="frame-window-classes"></a>Classes de fenêtres Frame

[CFrameWnd](reference/cframewnd-class.md)<br/>
Utilisé pour les fenêtres frame SDI qui encadrent un document unique et sa vue. La fenêtre frame est à la fois la fenêtre frame principale de l’application et la fenêtre frame pour le document actif.

[CMDIFrameWnd](reference/cmdiframewnd-class.md)<br/>
Utilisé comme fenêtre frame principale pour les applications MDI. La fenêtre frame principale est un conteneur pour toutes les fenêtres de document MDI et partage sa barre de menus avec elles. Une fenêtre frame MDI est une fenêtre de niveau supérieur qui apparaît sur le bureau.

[CMDIChildWnd](reference/cmdichildwnd-class.md)<br/>
Utilisé pour les documents individuels ouverts dans une fenêtre frame principale MDI. Chaque document et sa vue sont encadrés par une fenêtre frame enfant MDI contenue dans la fenêtre frame principale MDI. Une fenêtre enfant MDI ressemble à une fenêtre frame classique, mais se trouve à l’intérieur d’une fenêtre frame MDI au lieu de s’asseoir sur le bureau. Toutefois, la fenêtre enfant MDI n’a pas de barre de menus propre et doit partager la barre de menus de la fenêtre frame MDI qui la contient.

Pour plus d’informations, consultez [fenêtres Frame](frame-windows.md).

## <a name="other-window-classes-derived-from-cwnd"></a>Autres classes de fenêtres dérivées de CWnd

Outre les fenêtres Frame, plusieurs autres catégories principales de fenêtres sont dérivées de `CWnd` :

*Views*<br/>
Les vues sont créées à l’aide de la `CWnd` classe dérivée de [CView](reference/cview-class.md) (ou de l’une de ses classes dérivées). Une vue est associée à un document et agit en tant qu’intermédiaire entre le document et l’utilisateur. Une vue est une fenêtre enfant (pas un enfant MDI) qui remplit généralement la zone cliente d’une fenêtre frame SDI ou d’une fenêtre frame enfant MDI (ou de la partie de la zone client non couverte par une barre d’outils et/ou une barre d’État).

*Boîtes de dialogue*<br/>
Les boîtes de dialogue sont créées à l’aide de la `CWnd` classe dérivée de [CDialog](reference/cdialog-class.md).

*Formulaires*<br/>
Les vues de formulaire basées sur des ressources de modèle de boîte de dialogue, telles que des boîtes de dialogue, sont créées à l’aide des classes [CFormView](reference/cformview-class.md), [CRecordView](reference/crecordview-class.md)ou [CDaoRecordView](reference/cdaorecordview-class.md).

*Contrôles*<br/>
Les contrôles tels que les boutons, les zones de liste et les zones de liste modifiable sont créés à l’aide d’autres classes dérivées de `CWnd` . Consultez les [rubriques relatives au contrôle](controls-mfc.md).

*Barres de contrôles*<br/>
Fenêtres enfants qui contiennent des contrôles. Les exemples incluent des barres d’outils et des barres d’État. Consultez [barres de contrôles](control-bars.md).

## <a name="window-class-hierarchy"></a>Hiérarchie des classes de fenêtre

Reportez-vous au [graphique hiérarchique MFC](hierarchy-chart.md) dans la *référence MFC*. Les vues sont expliquées dans l' [architecture document/vue](document-view-architecture.md). Les boîtes de dialogue sont expliquées dans les [boîtes de dialogue](dialog-boxes.md).

## <a name="creating-your-own-special-purpose-window-classes"></a>Création de vos propres classes de fenêtre Special-Purpose

En plus des classes de fenêtres fournies par la bibliothèque de classes, vous pouvez avoir besoin de fenêtres enfants spécialisées. Pour créer une telle fenêtre, créez votre propre classe dérivée de [CWnd](reference/cwnd-class.md)et faites-en une fenêtre enfant d’un frame ou d’une vue. N’oubliez pas que l’infrastructure gère l’étendue de la zone cliente d’une fenêtre frame de document. La majeure partie de la zone cliente est gérée par une vue, mais d’autres fenêtres, telles que les barres de contrôle ou vos propres fenêtres personnalisées, peuvent partager l’espace avec la vue. Vous devrez peut-être interagir avec les mécanismes des classes [CView](reference/cview-class.md) et [CControlBar](reference/ccontrolbar-class.md) pour positionner les fenêtres enfants dans la zone cliente d’une fenêtre frame.

La [création de fenêtres](creating-windows.md) explique comment créer des objets de fenêtre et les fenêtres qu’elles gèrent.

## <a name="see-also"></a>Voir aussi

[Objets de fenêtre](window-objects.md)
