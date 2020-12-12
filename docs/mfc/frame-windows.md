---
description: En savoir plus sur les fenêtres Frame
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
ms.openlocfilehash: ee993b7f8314c28dba38c9ca607366f6fb93da1d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97193498"
---
# <a name="frame-windows"></a>Fenêtres frame

Quand une application s’exécute sous Windows, l’utilisateur interagit avec les documents affichés dans les fenêtres Frame. Une fenêtre frame de document comporte deux composants principaux : le cadre et le contenu qu’il encadre. Une fenêtre frame de document peut être une fenêtre frame SDI ( [single document interface](sdi-and-mdi.md) ) ou une fenêtre enfant MDI ( [multiple document interface](sdi-and-mdi.md) ). Windows gère la majeure partie de l’interaction de l’utilisateur avec la fenêtre frame : déplacement et redimensionnement de la fenêtre, fermeture et minimisation et optimisation. Vous gérez le contenu à l’intérieur du frame.

## <a name="frame-windows-and-views"></a>Fenêtres Frame et vues

L’infrastructure MFC utilise des fenêtres Frame pour contenir des vues. Les deux composants (Frame et contenu) sont représentés et gérés par deux classes différentes dans MFC. Une classe de fenêtre frame gère le frame, et une classe de vue gère le contenu. La fenêtre d’affichage est un enfant de la fenêtre frame. Le dessin et toute autre interaction utilisateur avec le document ont lieu dans la zone cliente de la vue, et non dans la zone cliente de la fenêtre frame. La fenêtre frame fournit un frame visible autour d’une vue, avec une barre de légende et des contrôles de fenêtre standard tels qu’un menu de contrôle, des boutons pour réduire et agrandir la fenêtre et des contrôles pour redimensionner la fenêtre. Le « contenu » se compose de la zone cliente de la fenêtre, qui est entièrement occupée par une fenêtre enfant (la vue). L’illustration suivante montre la relation entre une fenêtre frame et une vue.

![Affichage de la fenêtre Frame](../mfc/media/vc37fx1.gif "Affichage de la fenêtre Frame") <br/>
Fenêtre frame et vue

## <a name="frame-windows-and-splitter-windows"></a>Fenêtres Frame et fenêtres fractionnées

Une autre disposition courante consiste à faire en sorte que la fenêtre frame Frame plusieurs vues, généralement à l’aide d’une [fenêtre fractionnée](multiple-document-types-views-and-frame-windows.md). Dans une fenêtre fractionnée, la zone cliente de la fenêtre frame est occupée par une fenêtre fractionnée, qui à son tour comporte plusieurs fenêtres enfants, appelées volets, qui sont des vues.

### <a name="what-do-you-want-to-know-more-about"></a>Que voulez-vous en savoir plus sur

**Rubriques générales sur les fenêtres Frame**

- [Objets de fenêtre](window-objects.md)

- [Classes de fenêtres Frame](frame-window-classes.md)

- [Classes Frame-Window créées par l’Assistant Application](frame-window-classes-created-by-the-application-wizard.md)

- [Styles des fenêtres Frame](frame-window-styles-cpp.md)

- [Fonctionnement des fenêtres d’image](what-frame-windows-do.md)

**Rubriques sur l’utilisation des fenêtres Frame**

- [Utilisation de fenêtres d’image](using-frame-windows.md)

- [Création de fenêtres d’image de document](creating-document-frame-windows.md)

- [Destruction des fenêtres d’image](destroying-frame-windows.md)

- [Gérer des fenêtres enfants MDI](managing-mdi-child-windows.md)

- [Gestion de l’affichage actuel](managing-the-current-view.md) dans une fenêtre frame qui contient plusieurs vues

- [Gestion des menus, barres de contrôles et accélérateurs (autres objets qui partagent l’espace de la fenêtre frame)](managing-menus-control-bars-and-accelerators.md)

**Rubriques sur les fonctionnalités spéciales des fenêtres frames**

- [Glisser-déplacer des fichiers](dragging-and-dropping-files-in-a-frame-window.md) de l’Explorateur de fichiers ou du gestionnaire de fichiers dans une fenêtre frame

- [Réponse à l’échange dynamique de données (DDE)](responding-to-dynamic-data-exchange-dde.md)

- [États Semimodal : aide contextuelle de Windows (orchestration d’autres actions de fenêtre)](orchestrating-other-window-actions.md)

- [États Semimodal : impression et aperçu avant impression (orchestration d’autres actions de la fenêtre)](orchestrating-other-window-actions.md)

**Rubriques sur d’autres types de fenêtres**

- [Utilisation des vues](using-views.md)

- [Boîtes de dialogue](dialog-boxes.md)

- [Contrôles](controls-mfc.md)

## <a name="see-also"></a>Voir aussi

[Windows](windows.md)
