---
title: Info-bulles dans des fenêtres non dérivées de CFrameWnd | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- enabling tool tips [MFC]
- TOOLTIPTEXT structure [MFC]
- Help [MFC], tool tips for controls
- TTN_NEEDTEXT message [MFC]
- controls [MFC], tool tips
- handler functions [MFC], tool tips
ms.assetid: cad5ef0f-02e3-4151-ad0d-3d42e6932b0e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 34eb8f0b7394828782a3d0f9ed1ca44fb5731af6
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33382084"
---
# <a name="tool-tips-in-windows-not-derived-from-cframewnd"></a>Info-bulles dans les fenêtres non dérivées de CFrameWnd
Cette série d’articles couvre l’activation d’info-bulles pour les contrôles contenus dans une fenêtre qui n’est pas dérivée [CFrameWnd](../mfc/reference/cframewnd-class.md). L’article [barres d’outils, info-bulles](../mfc/toolbar-tool-tips.md) fournit des informations sur les info-bulles pour les contrôles dans un `CFrameWnd`.  
  
 Les rubriques abordées dans cette famille de l’article sont les suivantes :  
  
-   [Activation des info-bulles](../mfc/enabling-tool-tips.md)  
  
-   [Gestion de la notification TTN_NEEDTEXT pour les info-bulles](../mfc/handling-ttn-needtext-notification-for-tool-tips.md)  
  
-   [La Structure TOOLTIPTEXT](../mfc/tooltiptext-structure.md)  
  
 Info-bulles sont affichées automatiquement pour les boutons et autres contrôles contenus dans une fenêtre parente dérivée de `CFrameWnd`. C’est parce que `CFrameWnd` possède un gestionnaire par défaut pour le [TTN_GETDISPINFO](http://msdn.microsoft.com/library/windows/desktop/bb760269) notification, qui gère les **TTN_NEEDTEXT** notifications à partir de l’outil de conseil contrôles associés à des contrôles.  
  
 Toutefois, ce gestionnaire par défaut est appelé pas lorsque le **TTN_NEEDTEXT** notification est envoyée à partir d’un contrôle d’info-bulle associé à un contrôle dans une fenêtre qui n’est pas un `CFrameWnd`, par exemple un contrôle sur une boîte de dialogue ou une vue de formulaire. Par conséquent, il n’est nécessaire pour fournir une fonction de gestionnaire pour le **TTN_NEEDTEXT** message de notification pour afficher des info-bulles pour les contrôles enfants.  
  
 Les info-bulles par défaut fournies pour les fenêtres en [CWnd::EnableToolTips](../mfc/reference/cwnd-class.md#enabletooltips) n’ont pas de texte qui s’y rapportent. Pour récupérer le texte de l’info-bulle à afficher, le **TTN_NEEDTEXT** notification est envoyée à la fenêtre du parent du contrôle info-bulle juste avant que la fenêtre outil de Conseil s’affiche. S’il n’existe aucun gestionnaire pour ce message affecter une valeur pour le **pszText** membre de la **TOOLTIPTEXT** structure, il n’y a aucun texte affiché pour l’info-bulle.  
  
## <a name="see-also"></a>Voir aussi  
 [Info-bulles](../mfc/tool-tips.md)

