---
title: Gérer les fenêtres enfants MDI
ms.date: 11/19/2018
f1_keywords:
- MDICLIENT
helpviewer_keywords:
- MDI [MFC], child windows
- child windows [MFC], and MDICLIENT window
- MDICLIENT window [MFC]
- windows [MFC], MDI
- frame windows [MFC], MDI child windows
- child windows [MFC]
- MDI [MFC], frame windows
ms.assetid: 1828d96e-a561-48ae-a661-ba9701de6bee
ms.openlocfilehash: 6e8e3d0aa51eeea112597485a9221dcba4feda87
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84618357"
---
# <a name="managing-mdi-child-windows"></a>Gérer les fenêtres enfants MDI

Les fenêtres frames MDI principales (une par application) contiennent une fenêtre enfant spéciale appelée fenêtre MDICLIENT. La fenêtre MDICLIENT gère la zone cliente de la fenêtre frame principale et elle a elle-même des fenêtres enfants : les fenêtres de document, dérivées de `CMDIChildWnd` . Étant donné que les fenêtres de document sont des fenêtres Frame elles-mêmes (fenêtres enfants MDI), elles peuvent également avoir leurs propres enfants. Dans tous ces cas, la fenêtre parente gère ses fenêtres enfants et transmet certaines commandes à celles-ci.

Dans une fenêtre frame MDI, la fenêtre frame gère la fenêtre MDICLIENT, en la repositionnant avec les barres de contrôles. La fenêtre MDICLIENT gère, à son tour, toutes les fenêtres frame MDI enfants. L’illustration suivante montre la relation entre une fenêtre frame MDI, sa fenêtre MDICLIENT et ses fenêtres frame de document enfant.

![Fenêtres enfants dans une fenêtre frame MDI](../mfc/media/vc37gb1.gif "Fenêtres enfants dans une fenêtre frame MDI") <br/>
Fenêtres frame MDI et enfants

Une fenêtre frame MDI fonctionne également conjointement avec la fenêtre enfant MDI active, le cas échéant. La fenêtre frame MDI délègue les messages de commande à l’enfant MDI avant de tenter de les gérer lui-même.

## <a name="what-do-you-want-to-know-more-about"></a>Que voulez-vous en savoir plus sur

- [Création de fenêtres d’image de document](creating-document-frame-windows.md)

- [Styles de fenêtre frame](frame-window-styles-cpp.md)

## <a name="see-also"></a>Voir aussi

[Utilisation des fenêtres Frame](using-frame-windows.md)
