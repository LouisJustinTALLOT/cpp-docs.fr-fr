---
title: Windows
ms.date: 11/04/2016
helpviewer_keywords:
- objects [MFC], window
- windows [MFC]
- MFC, windows
- window objects [MFC], MFC Framework
ms.assetid: dd92bf34-842e-40fe-8aea-3028b55314d5
ms.openlocfilehash: 8d8ffccffdf5bb27497e9bc3831f26d33ec8454f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50547301"
---
# <a name="windows"></a>Windows

Cette série d’articles couvre les objets de fenêtre dans l’infrastructure MFC. Toutes les fenêtres MFC dérivent de la classe [CWnd](../mfc/reference/cwnd-class.md), notamment les fenêtres frame, les vues, les boîtes de dialogue et les contrôles.

Le premier groupe d’articles décrit [objets fenêtres](../mfc/window-objects.md) en général. Pour ce groupe pour des informations générales sur les objets de fenêtre C++, comment ils encapsulent une `HWND`, et comment vous en servir lors de la création de vos propres fenêtres, telles que des fenêtres enfants.

Le deuxième groupe d’articles décrit [fenêtres frames](../mfc/frame-windows.md)— windows qui placent un frame autour du contenu, en particulier. Reportez-vous à ce groupe pour plus d’informations sur la façon dont l’infrastructure MFC gère les fenêtres frame et le contenu du frame, y compris les barres de contrôle et de vues.

## <a name="what-do-you-want-to-know-more-about"></a>Ce que vous souhaitez en savoir plus sur

*Rubriques sur les objets de fenêtre en général*

- [Objets fenêtres](../mfc/window-objects.md)

- [Relation entre un C++ gère les objets de fenêtre et HWND](../mfc/relationship-between-a-cpp-window-object-and-an-hwnd.md)

- [Classes de fenêtre dérivées](../mfc/derived-window-classes.md)

- [Création d’objets fenêtres](../mfc/creating-windows.md)

- [Destruction d’objets fenêtres](../mfc/destroying-window-objects.md)

- [Inscrire des classes de fenêtre « »](../mfc/registering-window-classes.md)

- [Utilisation des objets de fenêtre](../mfc/working-with-window-objects.md)

- [Contextes de périphérique](../mfc/device-contexts.md): les objets qui rendent le dessin de Windows indépendant du périphérique

- [Objets graphiques](../mfc/graphic-objects.md): stylets, pinceaux, polices, images bitmap, palettes, régions

*Rubriques de la fenêtre frame*

- [Fenêtres frame](../mfc/frame-windows.md): les objets de fenêtre qui fournissent des frames

- [Vues et fenêtres frame](../mfc/frame-windows.md)

- [Classes de fenêtre frame](../mfc/frame-window-classes.md)

- [Styles de fenêtre frame](../mfc/frame-window-styles-cpp.md)

- [Modification des styles d’une fenêtre créée par MFC](../mfc/changing-the-styles-of-a-window-created-by-mfc.md)

- [Les fenêtres frame](../mfc/what-frame-windows-do.md)

- [Utilisation de fenêtres frame](../mfc/using-frame-windows.md)

- [La gestion des fenêtres enfants (la fenêtre MDICLIENT)](../mfc/managing-mdi-child-windows.md)

- [Gestion des menus, barres de contrôle et accélérateurs](../mfc/managing-menus-control-bars-and-accelerators.md)

- [CFrameWnd](../mfc/reference/cframewnd-class.md)

- [CMDIFrameWnd](../mfc/reference/cmdiframewnd-class.md)

- [CMDIChildWnd](../mfc/reference/cmdichildwnd-class.md)

- [Utilisation de vues](../mfc/using-views.md)

- [Types multidocuments, vues et Windows de Frame (fenêtres fractionnées)](../mfc/multiple-document-types-views-and-frame-windows.md)

- [Messages (mappages et fonctions gestionnaires)](../mfc/messages.md)

*Créer et détruire Windows*

- [Séquence de création d’une fenêtre générale](../mfc/general-window-creation-sequence.md)

- [Détruire des objets fenêtres](../mfc/destroying-window-objects.md)

- [Créer des fenêtres frame de document](../mfc/creating-document-frame-windows.md)

- [Détruire des fenêtres frame](../mfc/destroying-frame-windows.md)

*Créer le séparateur Windows*

- [Créer des fenêtres fractionnées](../mfc/multiple-document-types-views-and-frame-windows.md)

*Gérer Windows de l’enfant et l’affichage actuel*

- [Gérer les fenêtres enfants MDI](../mfc/managing-mdi-child-windows.md)

- [Gérer l’affichage actuel](../mfc/managing-the-current-view.md)

- [Gérer les menus, barres de contrôle et accélérateurs](../mfc/managing-menus-control-bars-and-accelerators.md)

*Utiliser des contextes de périphérique et des Styles de fenêtre*

- [Utiliser des stylets et autres objets graphiques dans un contexte de périphérique](../mfc/graphic-objects.md)

- [Modifier les styles d’une fenêtre créée par MFC](../mfc/changing-the-styles-of-a-window-created-by-mfc.md)

## <a name="see-also"></a>Voir aussi

[Éléments d’Interface utilisateur](../mfc/user-interface-elements-mfc.md)<br/>
[Boîtes de dialogue](../mfc/dialog-boxes.md)<br/>
[Barres d’outils](../mfc/toolbars.md)<br/>
[Barres d’état](../mfc/status-bars.md)<br/>
[Barres de boîte de dialogue](../mfc/dialog-bars.md)

