---
title: Image des Classes de fenêtre (Architecture) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.classes.frame
dev_langs:
- C++
helpviewer_keywords:
- frame window classes [MFC], document/view architecture
ms.assetid: 5da01fb4-f531-46cc-914f-e422e4f07f5d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b7de72b77be9be90ca876cfef943500a0312d183
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33344176"
---
# <a name="frame-window-classes-architecture"></a>Classes de fenêtre frame (architecture)
Dans l’architecture document/vue, fenêtres frame sont des fenêtres qui contiennent une fenêtre d’affichage. Ils prennent également en charge ayant contrôle barres qui leur sont attachées.  
  
 Dans plusieurs applications d’interface (multidocument MDI) document, la fenêtre principale est dérivée de `CMDIFrameWnd`. Il contient des frames les documents qui sont indirectement `CMDIChildWnd` objets. Le `CMDIChildWnd` objets, à son tour, affichent des documents.  
  
 Dans les applications SDI (interface) de document unique, la fenêtre principale, dérivé de `CFrameWnd`, contient la vue du document actif.  
  
 [CFrameWnd](../mfc/reference/cframewnd-class.md)  
 La classe de base pour la fenêtre frame principale d’une application SDI. Également la classe de base pour toutes les autres classes de fenêtre frame.  
  
 [CMDIFrameWnd](../mfc/reference/cmdiframewnd-class.md)  
 La classe de base pour la fenêtre frame principale d’une application MDI.  
  
 [CMDIChildWnd](../mfc/reference/cmdichildwnd-class.md)  
 La classe de base pour les fenêtres frame de document d’une application MDI.  
  
 [COleIPFrameWnd](../mfc/reference/coleipframewnd-class.md)  
 Fournit la fenêtre frame pour une vue lorsqu’un document serveur est en cours de modification en place.  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble de la classe](../mfc/class-library-overview.md)

