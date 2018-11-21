---
title: Fenêtres frame
ms.date: 11/19/2018
helpviewer_keywords:
- document frame windows [MFC]
- windows [MFC], MDI
- window classes [MFC], frame
- single document interface (SDI) [MFC]
- single document interface (SDI) [MFC], frame windows
- views [MFC], and frame windows
- CFrameWnd class [MFC], frame windows
- frame windows [MFC]
- frame windows [MFC], about frame windows
- MFC, frame windows
- MDI [MFC], frame windows
- splitter windows [MFC], and frame windows
ms.assetid: 40677339-8135-4f5e-aba6-3fced3078077
ms.openlocfilehash: 76c2f303713644c5f78f20d2ea868bd67b9eae71
ms.sourcegitcommit: 9e891eb17b73d98f9086d9d4bfe9ca50415d9a37
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2018
ms.locfileid: "52175373"
---
# <a name="frame-windows"></a>Fenêtres frame

Lorsqu’une application s’exécute sous Windows, l’utilisateur interagit avec les documents affichés dans des fenêtres frame. Une fenêtre frame de document comporte deux composants principaux : le frame et le contenu qui il encadre. Une fenêtre frame de document peut être un [interface monodocument](../mfc/sdi-and-mdi.md) fenêtre frame (SDI) ou un [interface multidocument](../mfc/sdi-and-mdi.md) fenêtre enfant (MDI). Windows gère la majeure partie de l’interaction utilisateur avec la fenêtre frame : déplacement et redimensionnement de la fenêtre fermée et en réduisant et agrandissement. Vous gérez le contenu à l’intérieur du cadre.

## <a name="frame-windows-and-views"></a>Vues et image Windows

L’infrastructure MFC utilise des fenêtres frame qui contient des vues. Les deux composants — frame et contenu — sont représentées et gérées par deux classes différentes de MFC. Une classe de fenêtre frame gère le frame, et une classe de vue gère le contenu. La fenêtre d’affichage est un enfant de la fenêtre frame. Dessin et toute autre interaction utilisateur avec le document ont lieu dans la zone cliente de la vue pas la zone fenêtre frame du client. La fenêtre frame fournit un cadre visible autour d’une vue, avec une barre de légende et les contrôles de fenêtre standard tel qu’un menu de contrôle, boutons réduire et agrandir la fenêtre et les contrôles de redimensionnement de la fenêtre. Le « contenu » se composent de la zone cliente de la fenêtre qui est entièrement occupée par une fenêtre enfant, la vue. La figure suivante montre la relation entre une fenêtre frame et une vue.

![Affichage de la fenêtre de frame](../mfc/media/vc37fx1.gif "Frame d’affichage de la fenêtre") <br/>
Affichage et fenêtre frame

## <a name="frame-windows-and-splitter-windows"></a>Frame Windows et Windows de séparateur

Une autre disposition fréquente concerne la fenêtre frame encadrer plusieurs vues, généralement à l’aide un [fenêtre fractionnée](../mfc/multiple-document-types-views-and-frame-windows.md). Dans une fenêtre fractionnée, la zone cliente de la fenêtre frame est occupée par une fenêtre fractionnée, qui à son tour possède plusieurs fenêtres enfants, appelées volets, qui sont des vues.

### <a name="what-do-you-want-to-know-more-about"></a>Ce que vous souhaitez en savoir plus sur

**Rubriques de la fenêtre de Frame générale**

- [Objets fenêtres](../mfc/window-objects.md)

- [Classes de fenêtre frame](../mfc/frame-window-classes.md)

- [Les classes de fenêtre Frame créées par l’Assistant Application](../mfc/frame-window-classes-created-by-the-application-wizard.md)

- [Styles de fenêtre frame](../mfc/frame-window-styles-cpp.md)

- [Les fenêtres frame](../mfc/what-frame-windows-do.md)

**Rubriques sur l’utilisation de Windows de Frame**

- [Utilisation de fenêtres frame](../mfc/using-frame-windows.md)

- [Création de fenêtres frame de document](../mfc/creating-document-frame-windows.md)

- [Destruction des fenêtres frame](../mfc/destroying-frame-windows.md)

- [La gestion des fenêtres enfants MDI](../mfc/managing-mdi-child-windows.md)

- [Gestion de l’affichage actuel](../mfc/managing-the-current-view.md) dans une fenêtre frame contenant plusieurs vues

- [Gestion des menus, barres de contrôle et accélérateurs (autres objets qui partagent l’espace de la fenêtre frame)](../mfc/managing-menus-control-bars-and-accelerators.md)

**Rubriques sur les fonctionnalités de fenêtre Frame spécial**

- [Faire glisser et déposer des fichiers](../mfc/dragging-and-dropping-files-in-a-frame-window.md) à partir de l’Explorateur de fichiers ou le Gestionnaire de fichiers dans une fenêtre frame

- [Répondre à l’échange dynamique de données (DDE)](../mfc/responding-to-dynamic-data-exchange-dde.md)

- [États semi-modaux : aide Windows contextuelle (orchestration d’autres actions de la fenêtre)](../mfc/orchestrating-other-window-actions.md)

- [États semi-modaux : impression et Aperçu avant impression (orchestration d’autres actions de la fenêtre)](../mfc/orchestrating-other-window-actions.md)

**Rubriques sur les autres types de Windows**

- [Utilisation de vues](../mfc/using-views.md)

- [Boîtes de dialogue](../mfc/dialog-boxes.md)

- [Contrôles](../mfc/controls-mfc.md)

## <a name="see-also"></a>Voir aussi

[Windows](../mfc/windows.md)

