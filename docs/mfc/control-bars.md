---
title: Barres de contrôles
ms.date: 11/04/2016
helpviewer_keywords:
- command bars [MFC], types of
- toolbars [MFC], control bars
- control bars [MFC]
- MFC, control bars
- control bars [MFC], types of
- CDialogBar class [MFC], control bars
- status bars [MFC], control bars
- CControlBar class [MFC], MFC control bars
- dialog bars [MFC], control bars
- CToolBar class [MFC], control bars
- CStatusBar class [MFC], control bars
ms.assetid: 31831910-3d23-4d70-9e71-03cc02f01ec4
ms.openlocfilehash: a2d3683b744493bb5566456b9e1358c1ddc418d4
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84615977"
---
# <a name="control-bars"></a>Barres de contrôles

"La barre de contrôle" est le nom général pour les barres d'outils, les barres d'état et les barres de boîte de dialogue. Les classes MFC `CToolBar` , `CStatusBar` ,, `CDialogBar` `COleResizeBar` et `CReBar` dérivent de la classe [CControlBar](reference/ccontrolbar-class.md), qui implémente leurs fonctionnalités communes.

Les barres de contrôle sont des fenêtres affichant des lignes de contrôle avec lesquelles les utilisateurs peuvent sélectionner des options, exécuter des commandes ou obtenir des informations du programme. Les types de barres de contrôle comprennent les barres d'outils, les barres de boîte de dialogue et les barres d'état.

- Barres d’outils, dans la classe [CToolBar](reference/ctoolbar-class.md)

- Barres d’État, dans la classe [CStatusBar](reference/cstatusbar-class.md)

- Barres de boîte de dialogue, dans la classe [CDialogBar](reference/cdialogbar-class.md)

- Rebarres, dans la classe [CReBar](reference/crebar-class.md)

> [!IMPORTANT]
> Depuis la version 4,0 de MFC, les barres d’outils, les barres d’État et les info-bulles sont implémentées à l’aide des fonctionnalités système implémentées dans *Comctl32. dll* au lieu de l’implémentation précédente propre à MFC. Dans MFC version 6,0, `CReBar` , qui encapsule également la fonctionnalité Comctl32. dll, a été ajouté.

De brèves présentations des types de barre de contrôle suivent. Pour plus d'informations, consultez les liens ci-dessous.

## <a name="control-bars"></a>Barres de contrôles

Les barres de contrôle améliorent considérablement l'utilisation d'un programme en fournissant des actions rapides et des actions de commande à une étape. La classe `CControlBar` fournit les fonctionnalités communes de toutes les barres d'outils, barres d'état et barres de boîte de dialogue. `CControlBar` fournit les fonctionnalités pour positionner la barre de contrôle dans la fenêtre frame parente. Étant donné qu'une barre de contrôle est généralement la fenêtre enfant d'une fenêtre frame parente, il s'agit d'un "frère" à la vue du client ou du client MDI de la fenêtre frame. Un objet de barre de contrôle utilise des informations sur le rectangle client de sa fenêtre parente pour se positionner. Il modifie le reste du rectangle de la fenêtre du client parent afin que la vue du client ou la fenêtre du client MDI remplisse le reste de la fenêtre du client.

> [!NOTE]
> Si un bouton de la barre de contrôle n’a pas de **commande** ou de gestionnaire de **UPDATE_COMMAND_UI** , le Framework désactive automatiquement le bouton.

## <a name="toolbars"></a>Barres d'outils

Une barre d'outils est une barre de contrôle qui affiche une ligne de boutons bitmap qui exécutent des commandes. Appuyer sur un bouton de la barre d'outils équivaut à choisir un élément de menu ; il appelle le même gestionnaire mappé à un élément de menu si cet élément de menu a le même ID que le bouton de la barre d'outils. Les boutons peuvent être configurés pour apparaître et se comporter comme des boutons de commande, cases d'option ou cases à cocher. Une barre d'outils est généralement alignée au haut d'une fenêtre frame, mais une barre d'outils MFC peut être ancrée de n'importe quel côté de la fenêtre ou flotter dans sa propre mini-fenêtre frame. Une barre d'outils peut également "flotter", et vous pouvez modifier sa taille et la faire glisser avec une souris. Une barre d'outils peut également afficher des info-bulles lorsque l'utilisateur bouge la souris sur les boutons de la barre d'outils. Une info-bulle est une toute petite fenêtre contextuelle qui décrit brièvement l'objectif du bouton.

> [!NOTE]
> À partir de la version 4,0 de MFC, la classe [CToolBar](reference/ctoolbar-class.md) utilise le contrôle commun de barre d’outils Windows. Un `CToolBar` contient un [CToolBarCtrl](reference/ctoolbarctrl-class.md). Néanmoins, les anciennes barres d'outils sont toujours prises en charge. Consultez les [barres d’outils](mfc-toolbar-implementation.md)de l’article.

## <a name="status-bars"></a>Barres d'état

Une barre d'état est une barre de contrôle qui contient les volets de sortie de texte ou "indicateurs". Les volets de sortie sont fréquemment utilisés comme des lignes de message et comme indicateurs d'états. Les exemples de lignes de message incluent les lignes de message d'aide de commande qui expliquent brièvement le menu ou la commande de barre d'outils sélectionné(e) dans le volet situé à l'extrême gauche de la barre d'état par défaut créée par l'Assistant Application MFC. Les exemples d'indicateur d'état sont notamment ARRÊT DÉFIL, VERR. NUM. Les barres d'état sont généralement alignées en bas de la fenêtre frame. Consultez la classe [CStatusBar](reference/cstatusbar-class.md) et la classe [CStatusBarCtrl](reference/cstatusbarctrl-class.md).

## <a name="dialog-bars"></a>Barres de boîte de dialogue

Une barre de boîte de dialogue est une barre de contrôle, basée sur une ressource de modèle de boîte de boîte de dialogue, avec la fonctionnalité d'une boîte de dialogue non modale. Les barres de boîte de dialogue peuvent contenir des contrôles Windows, des contrôles personnalisés ou des contrôles ActiveX. Comme dans une boîte de dialogue, l'utilisateur peut se déplacer dans les contrôles. Les barres de boîte de dialogue peuvent être alignées dans la partie supérieure, inférieure, gauche, ou le côté droit d'une fenêtre frame, et elles peuvent également flotter dans leur propre fenêtre frame. Consultez la classe [CDialogBar](reference/cdialogbar-class.md).

## <a name="rebars"></a>Rebars

Un [Rebar](using-crebarctrl.md) est une barre de contrôle qui fournit des informations relatives à l’ancrage, à la disposition, à l’État et à la persistance pour les contrôles Rebar. Un objet rebar peut contenir plusieurs fenêtres enfants, généralement d'autres contrôles, notamment des zones d'édition, des barres d'outils et des zones de liste. Un objet rebar peut afficher les fenêtres enfants sur une image bitmap spécifiée. Il peut être redimensionné automatiquement ou manuellement en cliquant ou en faisant glisser sa barre de pinces. Consultez la classe [CReBar](reference/crebar-class.md).

## <a name="see-also"></a>Voir aussi

[Éléments de l’interface utilisateur](user-interface-elements-mfc.md)
