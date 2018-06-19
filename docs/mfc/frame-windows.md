---
title: Fenêtres frame | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- document frame windows [MFC]
- windows [MFC], MDI
- window classes [MFC], frame
- single document interface (SDI) [MFC]
- single document interface (SDI) [MFC], frame windows
- views [MFC], and frame windows
- CFrameWnd class [MFC], frame windows
- frame windows [MFC]
- frame windows [MFC], about frame widows
- MFC, frame windows
- MDI [MFC], frame windows
- splitter windows [MFC], and frame windows
ms.assetid: 40677339-8135-4f5e-aba6-3fced3078077
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 515df19bcc11f7a6706985014fc44bc4ff315f36
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33352061"
---
# <a name="frame-windows"></a>Fenêtres frame
Lorsqu’une application s’exécute sous Windows, l’utilisateur interagit avec les documents affichés dans des fenêtres frame. Une fenêtre frame de document présente deux composants majeurs : le frame et le contenu encadré. Une fenêtre frame de document peut être un [interface monodocument](../mfc/sdi-and-mdi.md) fenêtre frame (SDI) ou un [interface multidocument](../mfc/sdi-and-mdi.md) fenêtre enfant (MDI). Windows gère la majeure partie de l’interaction utilisateur avec la fenêtre frame : déplacement et redimensionnement de la fenêtre, fermeture, en réduisant et agrandissement. Vous gérez le contenu à l’intérieur du cadre.  
  
## <a name="frame-windows-and-views"></a>Vues et fenêtres frame  
 L’infrastructure MFC utilise des fenêtres frame pour contenir des vues. Les deux composants — frame et contenu — sont représentés et gérés par deux classes différentes de MFC. Une classe de fenêtre frame gère le frame et une classe d’affichage gère le contenu. La fenêtre d’affichage est un enfant de la fenêtre frame. Dessin et toute autre interaction utilisateur avec le document ont lieu dans la zone cliente de la vue, pas la zone fenêtre frame du client. La fenêtre frame fournit un frame visible autour de la vue, avec une barre de légende et les contrôles de fenêtre standard tels que d’un menu de contrôle, les boutons réduire et agrandir la fenêtre et les contrôles de redimensionnement de la fenêtre. Le « contenu » se comprendre de la zone cliente de la fenêtre, qui est entièrement occupée par une fenêtre enfant, la vue. L’illustration suivante montre la relation entre une fenêtre frame et une vue.  
  
 ![Affichage de la fenêtre de frame](../mfc/media/vc37fx1.gif "vc37fx1")  
Affichage et fenêtre frame  
  
## <a name="frame-windows-and-splitter-windows"></a>Fenêtres frame et fenêtres fractionnées  
 Une autre disposition fréquente est pour la fenêtre frame encadrer plusieurs vues en utilisant généralement un [fenêtre fractionnée](../mfc/multiple-document-types-views-and-frame-windows.md). Dans une fenêtre fractionnée, la zone cliente de la fenêtre frame est occupée par une fenêtre fractionnée, qui à son tour possède plusieurs fenêtres enfants, appelées volets, qui sont des vues.  
  
### <a name="what-do-you-want-to-know-more-about"></a>Que voulez-vous en savoir plus  
 **Rubriques relatives aux fenêtres de Frame général**  
  
-   [Objets fenêtres](../mfc/window-objects.md)  
  
-   [Classes de fenêtre frame](../mfc/frame-window-classes.md)  
  
-   [Les classes de fenêtre Frame créées par l’Assistant Application](../mfc/frame-window-classes-created-by-the-application-wizard.md)  
  
-   [Styles de fenêtre frame](../mfc/frame-window-styles-cpp.md)  
  
-   [Les fenêtres frame](../mfc/what-frame-windows-do.md)  
  
 **Rubriques sur l’utilisation de fenêtres Frame**  
  
-   [Utilisation de fenêtres frame](../mfc/using-frame-windows.md)  
  
-   [Création de fenêtres frame de document](../mfc/creating-document-frame-windows.md)  
  
-   [Détruire des fenêtres frame](../mfc/destroying-frame-windows.md)  
  
-   [Gestion des fenêtres enfants MDI](../mfc/managing-mdi-child-windows.md)  
  
-   [Gestion de l’affichage actuel](../mfc/managing-the-current-view.md) dans une fenêtre frame contenant plusieurs vues  
  
-   [Gestion des menus, barres de contrôles et des raccourcis (autres objets qui partagent l’espace de la fenêtre frame)](../mfc/managing-menus-control-bars-and-accelerators.md)  
  
 **Rubriques sur les fonctions de fenêtre Frame spécial**  
  
-   [Glisser -déplacer des fichiers](../mfc/dragging-and-dropping-files-in-a-frame-window.md) à partir de l’Explorateur de fichiers ou le Gestionnaire de fichiers dans une fenêtre frame  
  
-   [Répondre à l’échange dynamique de données (DDE)](../mfc/responding-to-dynamic-data-exchange-dde.md)  
  
-   [États semi-modaux : aide Windows contextuelle (orchestration d’autres actions Windows)](../mfc/orchestrating-other-window-actions.md)  
  
-   [États semi-modaux : impression et Aperçu avant impression (orchestration d’autres actions Windows)](../mfc/orchestrating-other-window-actions.md)  
  
 **Rubriques sur les autres types de fenêtres**  
  
-   [Utilisation de vues](../mfc/using-views.md)  
  
-   [Boîtes de dialogue](../mfc/dialog-boxes.md)  
  
-   [Contrôles](../mfc/controls-mfc.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Fenêtres](../mfc/windows.md)

