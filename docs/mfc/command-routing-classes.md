---
title: Classes de routage de commande | Microsoft Docs
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
ms.openlocfilehash: 4b467a85aca4bb1d0405f9bbddee5cb5e4f5b790
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46391534"
---
# <a name="command-routing-classes"></a>Classes de routage des commandes

Lorsque l’utilisateur interagit avec l’application en choisissant les menus ou les boutons de barre de contrôle avec la souris, l’application envoie des messages à partir de l’objet d’interface utilisateur affecté à un objet cible de commande approprié. Classes de cible de commande dérivées de `CCmdTarget` incluent [CWinApp](../mfc/reference/cwinapp-class.md), [CWnd](../mfc/reference/cwnd-class.md), [CDocTemplate](../mfc/reference/cdoctemplate-class.md), [CDocument](../mfc/reference/cdocument-class.md), [CView](../mfc/reference/cview-class.md), et les classes dérivées à partir de celles-ci. Le framework prend en charge le routage automatique de commandes afin que les commandes peuvent être gérés par l’objet le plus approprié actuellement actif dans l’application.

Un objet de classe `CCmdUI` est passé à l’interface utilisateur de commande de mise à jour des cibles de votre commande ([ON_UPDATE_COMMAND_UI](reference/message-map-macros-mfc.md#on_update_command_ui)) gestionnaires pour vous permettre de mettre à jour l’état de l’interface utilisateur pour une commande particulière (par exemple, pour vérification ou remove la vérification des éléments de menu). Vous appelez des fonctions de membre la `CCmdUI` objet à mettre à jour l’état de l’objet d’interface utilisateur. Ce processus est le même si l’objet de l’interface utilisateur associé à une commande particulière est un élément de menu ou un bouton ou les deux.

[CCmdTarget](../mfc/reference/ccmdtarget-class.md)<br/>
Sert de classe de base pour toutes les classes d’objets qui peuvent recevoir et répondre aux messages.

[CCmdUI](../mfc/reference/ccmdui-class.md)<br/>
Fournit une interface de programmation pour la mise à jour des objets d’interface utilisateur tels que les éléments de menu ou des boutons de barre de contrôle. L’objet cible de commande active, désactive, vérifie et/ou efface l’objet d’interface utilisateur avec cet objet.

## <a name="see-also"></a>Voir aussi

[Vue d’ensemble de la classe](../mfc/class-library-overview.md)

