---
title: Classes de routage des commandes
ms.date: 11/04/2016
f1_keywords:
- vc.classes.command
helpviewer_keywords:
- MFC, command routing
- command routing [MFC], classes
ms.assetid: 4b50e689-2c54-4e6c-90f0-37333e22b2a1
ms.openlocfilehash: d7ff275d373cf50ab8ebe52ed454bd25cd473e11
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84624826"
---
# <a name="command-routing-classes"></a>Classes de routage des commandes

Lorsque l’utilisateur interagit avec l’application en choisissant des menus ou des boutons de la barre de commandes avec la souris, l’application envoie des messages à partir de l’objet d’interface utilisateur affecté à un objet cible de commande approprié. Les classes cibles de commande dérivées de `CCmdTarget` incluent [CWinApp](reference/cwinapp-class.md), [CWnd](reference/cwnd-class.md), [CDocTemplate](reference/cdoctemplate-class.md), [CDocument](reference/cdocument-class.md), [CView](reference/cview-class.md)et les classes qui en sont dérivées. Le Framework prend en charge le routage de commande automatique afin que les commandes puissent être gérées par l’objet le plus approprié actuellement actif dans l’application.

Un objet de classe `CCmdUI` est passé à votre commande cible les gestionnaires de l’interface utilisateur de la commande de mise à jour ([ON_UPDATE_COMMAND_UI](reference/message-map-macros-mfc.md#on_update_command_ui)) pour vous permettre de mettre à jour l’état de l’interface utilisateur pour une commande particulière (par exemple, pour vérifier ou supprimer la vérification des éléments de menu). Vous appelez les fonctions membres de l' `CCmdUI` objet pour mettre à jour l’état de l’objet d’interface utilisateur. Ce processus est le même si l’objet d’interface utilisateur associé à une commande particulière est un élément de menu ou un bouton, ou les deux.

[CCmdTarget](reference/ccmdtarget-class.md)<br/>
Sert de classe de base pour toutes les classes d’objets qui peuvent recevoir des messages et y répondre.

[CCmdUI](reference/ccmdui-class.md)<br/>
Fournit une interface de programmation pour mettre à jour des objets d’interface utilisateur, tels que des éléments de menu ou des boutons de barre de contrôle. L’objet cible de commande active, désactive, vérifie et/ou efface l’objet interface utilisateur avec cet objet.

## <a name="see-also"></a>Voir aussi

[Vue d'ensemble des classes](class-library-overview.md)
