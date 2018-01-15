---
title: "Quand les gestionnaires de mise à jour sont appelés | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- updating user interface objects [MFC]
- command routing [MFC], update commands
- toolbar buttons [MFC], enabling
- disabling toolbar buttons
- menus [MFC], initializing
- update handlers [MFC]
- disabling menu items
- toolbars [MFC], updating
- menus [MFC], updating as context changes
- toolbar controls [MFC], updated during OnIdle method [MFC]
- menu items, enabling
- command routing [MFC], update handlers
- update handlers, calling
ms.assetid: 7359f6b1-4669-477d-bd99-690affed08d9
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: eaf2773a2d9e393c783a39e01c75f8efa62796df
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="when-update-handlers-are-called"></a>Quand les gestionnaires de mise à jour sont-ils appelés ?
Supposons que l’utilisateur clique sur la souris dans le menu fichier, ce qui génère un `WM_INITMENUPOPUP` message. Mécanisme de mise à jour de l’infrastructure met à jour collectivement tous les éléments dans le menu fichier avant du menu déroulant pour que les utilisateurs puissent le voir.  
  
 Pour ce faire, l’infrastructure achemine mettre à jour des commandes pour tous les éléments de menu dans le menu contextuel sur le routage des commandes standard. Cibles de la commande sur le routage ont la possibilité de mettre à jour tous les éléments de menu en faisant correspondre la commande de mise à jour avec une entrée de table des messages appropriée (sous la forme `ON_UPDATE_COMMAND_UI`) et en appelant une fonction de « gestionnaire de mise à jour ». Par conséquent, pour un menu comportant six éléments, six commandes de mise à jour sont envoyées. Si un gestionnaire de mise à jour existe pour l’ID de commande de l’élément de menu, elle est appelée pour effectuer la mise à jour. Si ce n’est pas le cas, le framework vérifie l’existence d’un gestionnaire pour cet ID de commande et Active ou désactive l’élément de menu approprié.  
  
 Si le framework ne trouve pas une `ON_UPDATE_COMMAND_UI` entrée pendant le routage des commandes, elle active automatiquement l’objet d’interface utilisateur s’il existe un `ON_COMMAND` entrée quelque part avec le même ID de commande. Sinon, elle désactive l’objet d’interface utilisateur. Par conséquent, pour vous assurer qu’un objet d’interface utilisateur est activé, fournissez un gestionnaire pour la commande de que l’objet génère ou lui fournir un gestionnaire de mise à jour. Voir la figure dans la rubrique [objets d’Interface utilisateur et l’ID de commande](../mfc/user-interface-objects-and-command-ids.md).  
  
 Il est possible de désactiver la désactivation par défaut des objets d’interface utilisateur. Pour plus d’informations, consultez la [membre m_bAutoMenuEnable](../mfc/reference/cframewnd-class.md#m_bautomenuenable) membre de classe `CFrameWnd` dans les *référence MFC*.  
  
 L’initialisation de menu est activée automatiquement dans le framework, qui se produisent lors de l’application reçoit un `WM_INITMENUPOPUP` message. Lors de la boucle inactive, l’infrastructure recherche le routage des commandes pour les gestionnaires de mise à jour de bouton de la même façon comme il le fait pour les menus.  
  
## <a name="see-also"></a>Voir aussi  
 [Guide pratique pour mettre à jour des objets d’interface utilisateur](../mfc/how-to-update-user-interface-objects.md)

