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
ms.openlocfilehash: d4b4a4876f47452361b13837b0279f5bf98f8658
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62279339"
---
# <a name="managing-mdi-child-windows"></a>Gérer les fenêtres enfants MDI

La fenêtre frame principale MDI (une par application) contient une fenêtre enfant spéciale appelée fenêtre MDICLIENT. Cette dernière gère la zone cliente de la fenêtre frame principale et a elle-même des fenêtres enfants : les fenêtres de document, dérivés `CMDIChildWnd`. Étant donné que les fenêtres de document sont des fenêtres frame eux-mêmes (fenêtres MDI enfants), ils peuvent également avoir leurs propres enfants. Dans tous ces cas, la fenêtre parente gère ses fenêtres enfants et transfère les quelques commandes.

Dans une fenêtre frame MDI, la fenêtre frame gère la fenêtre MDICLIENT, il conjointement avec les barres de contrôles. Cette dernière, à son tour, gère toutes les fenêtres de frame enfant MDI. La figure suivante montre la relation entre une fenêtre frame MDI, sa fenêtre MDICLIENT et ses fenêtres enfants du frame de document.

![Fenêtres enfants dans une fenêtre frame MDI](../mfc/media/vc37gb1.gif "fenêtres enfants dans une fenêtre frame MDI") <br/>
Enfants et Windows de Frame MDI

Une fenêtre frame MDI fonctionne également conjointement avec la fenêtre enfant MDI en cours, le cas échéant. La fenêtre frame MDI délègue les messages de commande à l’enfant MDI avant d’essayer de les gérer lui-même.

## <a name="what-do-you-want-to-know-more-about"></a>Ce que vous souhaitez en savoir plus sur

- [Création de fenêtres frame de document](../mfc/creating-document-frame-windows.md)

- [Styles de fenêtre frame](../mfc/frame-window-styles-cpp.md)

## <a name="see-also"></a>Voir aussi

[Utilisation de fenêtres frame](../mfc/using-frame-windows.md)
