---
title: Gestion des fenêtres enfants MDI | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- MDICLIENT
dev_langs:
- C++
helpviewer_keywords:
- MDI [MFC], child windows
- child windows [MFC], and MDICLIENT window
- MDICLIENT window [MFC]
- windows [MFC], MDI
- frame windows [MFC], MDI child windows
- child windows [MFC]
- MDI [MFC], frame windows
ms.assetid: 1828d96e-a561-48ae-a661-ba9701de6bee
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 58ddef11e56da760bbecaa47f03dfa6c57dfa3ed
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2018
ms.locfileid: "36929479"
---
# <a name="managing-mdi-child-windows"></a>Gérer les fenêtres enfants MDI
La fenêtre frame principale MDI (une par application) contient une fenêtre enfant spéciale appelée fenêtre MDICLIENT. La fenêtre MDICLIENT gère la zone cliente de la fenêtre frame principale et a elle-même des fenêtres enfants : les fenêtres de document dérivées de `CMDIChildWnd`. Étant donné que les fenêtres de document sont des fenêtres frame eux-mêmes (fenêtres MDI enfants), ils peuvent également avoir leurs propres enfants. Dans tous ces cas, la fenêtre parente gère ses fenêtres enfants et transfère des commandes.  
  
 Dans une fenêtre frame MDI, la fenêtre frame gère la fenêtre MDICLIENT, il conjointement avec les barres de contrôles. Cette dernière, à son tour, gère toutes les fenêtres de frame enfant MDI. L’illustration suivante montre la relation entre une fenêtre frame MDI, sa fenêtre MDICLIENT et ses fenêtres enfants du frame de document.  
  
 ![Fenêtres enfants dans une fenêtre frame MDI](../mfc/media/vc37gb1.gif "vc37gb1")  
Enfants et des fenêtres de Frame MDI  
  
 Une fenêtre frame MDI fonctionne aussi en association avec la fenêtre enfant MDI active, si elle existe. La fenêtre frame MDI délègue les messages de commande à l’enfant MDI avant d’essayer de les gérer lui-même.  
  
## <a name="what-do-you-want-to-know-more-about"></a>Que voulez-vous en savoir plus  
  
-   [Création de fenêtres frame de document](../mfc/creating-document-frame-windows.md)  
  
-   [Styles de fenêtre frame](../mfc/frame-window-styles-cpp.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation de fenêtres frame](../mfc/using-frame-windows.md)

