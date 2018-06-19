---
title: Classes de routage de commande | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.classes.command
dev_langs:
- C++
helpviewer_keywords:
- MFC, command routing
- command routing [MFC], classes
ms.assetid: 4b50e689-2c54-4e6c-90f0-37333e22b2a1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f3e05046ac6754dd585bb1fbf51420ef862af7be
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33341960"
---
# <a name="command-routing-classes"></a>Classes de routage des commandes
Lorsque l’utilisateur interagit avec l’application en choisissant des menus ou boutons de barre de contrôle avec la souris, l’application envoie des messages à partir de l’objet d’interface utilisateur affecté à un objet cible de la commande approprié. Cible de la commande classes dérivées de `CCmdTarget` incluent [CWinApp](../mfc/reference/cwinapp-class.md), [CWnd](../mfc/reference/cwnd-class.md), [CDocTemplate](../mfc/reference/cdoctemplate-class.md), [CDocument](../mfc/reference/cdocument-class.md), [CView](../mfc/reference/cview-class.md), et les classes dérivées à partir de celles-ci. Le framework prend en charge le routage automatique de commandes afin que les commandes peuvent être gérées par l’objet le plus approprié actuellement actif dans l’application.  
  
 Un objet de classe `CCmdUI` est passé à l’interface utilisateur de commande de mise à jour des cibles de votre commande ([ON_UPDATE_COMMAND_UI](reference/message-map-macros-mfc.md#on_update_command_ui)) gestionnaires pour vous permettre de mettre à jour l’état de l’interface utilisateur pour une commande particulière (par exemple, à vérifier ou à supprimer la vérification des éléments de menu). Vous appelez des fonctions de membre la `CCmdUI` objet à mettre à jour l’état de l’objet de l’interface utilisateur. Ce processus est le même si l’objet de l’interface utilisateur associée à une commande particulière est un élément de menu ou un bouton ou les deux.  
  
 [CCmdTarget](../mfc/reference/ccmdtarget-class.md)  
 Sert de classe de base pour toutes les classes d’objets qui peuvent recevoir et répondre aux messages.  
  
 [CCmdUI](../mfc/reference/ccmdui-class.md)  
 Fournit une interface de programmation pour la mise à jour des objets d’interface utilisateur tels que les éléments de menu ou des boutons de barre de contrôle. L’objet cible de commande active, désactive, vérifie et/ou efface l’objet d’interface utilisateur avec cet objet.  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble de la classe](../mfc/class-library-overview.md)

