---
title: Implémentation de barre d’état dans MFC | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- COldStatusBar
dev_langs:
- C++
helpviewer_keywords:
- status bars [MFC], implementing in MFC
- CStatusBarCtrl class [MFC], and MFC status bars
- CStatusBar class [MFC], and CStatusBarCtrl class [MFC]
- CStatusBarCtrl class [MFC], and CStatusBar class [MFC]
- status bars [MFC], backward compatibility
- status bars [MFC], old with COldStatusBar class [MFC]
- COldStatusBar class [MFC]
- status bars [MFC], and CStatusBarCtrl class
- CStatusBar class [MFC], and MFC status bars
- status indicators
- status bars [MFC], Windows 95 implementation
ms.assetid: be5cd876-38e3-4d5c-b8cb-16d57a16a142
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 13a85ba03089a9536c8c6512bccd09f1eb34c0a9
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33381086"
---
# <a name="status-bar-implementation-in-mfc"></a>Implémentation de la barre d'état dans MFC
A [CStatusBar](../mfc/reference/cstatusbar-class.md) objet est une barre de contrôle avec une ligne de texte des volets de sortie. Les volets de sortie sont fréquemment utilisés comme des lignes de message et comme indicateurs d'états. Exemples : les lignes de message à l’aide de menu qui expliquent brièvement la commande de menu sélectionné et les indicateurs qui indiquent l’état de l’arrêt défil, VERR. NUM et défil.  
  
 Depuis la version 4.0 de MFC, les barres d’état sont implémentées à l’aide de la classe [CStatusBarCtrl](../mfc/reference/cstatusbarctrl-class.md), qui encapsule une barre de contrôle commun d’état. Pour la compatibilité ascendante, MFC conserve l’implémentation de barre d’état ancienne dans la classe **COldStatusBar**. La documentation pour les versions antérieures de MFC décrit **COldStatusBar** sous `CStatusBar`.  
  
 [CStatusBar::GetStatusBarCtrl](../mfc/reference/cstatusbar-class.md#getstatusbarctrl), une fonction membre new 4.0 de MFC, vous permet de tirer parti de la prise en charge du contrôle commun Windows pour des fonctionnalités supplémentaires et de personnalisation de la barre d’état. `CStatusBar` fonctions membres vous donnent la plupart des fonctionnalités des contrôles communs Windows ; Toutefois, lorsque vous appelez `GetStatusBarCtrl`, vous pouvez donner à vos barres d’état davantage les caractéristiques d’une barre d’état. Lorsque vous appelez `GetStatusBarCtrl`, il retourne une référence à un `CStatusBarCtrl` objet. Vous pouvez utiliser cette référence pour manipuler le contrôle de barre d’état.  
  
 La figure suivante illustre une barre d’état affichant plusieurs indicateurs.  
  
 ![Barre d’état](../mfc/media/vc37dy1.gif "vc37dy1")  
Une barre d’état  
  
 Comme la barre d’outils, l’objet de barre d’état est incorporé dans sa fenêtre frame parente et est généré automatiquement lorsque la fenêtre frame est construite. La barre d’état, comme toutes les barres de contrôle est détruite automatiquement également lorsque le frame parent est détruit.  
  
## <a name="what-do-you-want-to-know-more-about"></a>Que voulez-vous en savoir plus  
  
-   [Mise à jour le texte d’un volet de barre d’état](../mfc/updating-the-text-of-a-status-bar-pane.md)  
  
-   Classes MFC [CStatusBar](../mfc/reference/cstatusbar-class.md) et [CStatusBarCtrl](../mfc/reference/cstatusbarctrl-class.md)  
  
-   [Barres de contrôles](../mfc/control-bars.md)  
  
-   [Barres de boîte de dialogue](../mfc/dialog-bars.md)  
  
-   [Barres d’outils (implémentation de barre d’outils MFC)](../mfc/mfc-toolbar-implementation.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Barres d’état](../mfc/status-bars.md)

