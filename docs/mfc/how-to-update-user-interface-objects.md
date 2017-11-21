---
title: "Comment : mettre à jour des objets d’Interface utilisateur | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- menus [MFC], updating as context changes
- user interface objects [MFC], updating
- user interface objects [MFC]
- update handlers [MFC]
- enabling UI elements [MFC]
- disabling menus [MFC]
- updating user-interface objects [MFC]
- disabling UI elements [MFC]
- commands [MFC], updating UI
- enabling menus [MFC]
ms.assetid: 82f09773-c978-427b-b321-05a6143b7369
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 79a5b24c1e9d71f422748f4c6fb8cba97786462d
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/24/2017
---
# <a name="how-to-update-user-interface-objects"></a>Comment : mettre à jour des objets d'interface utilisateur
En règle générale, les éléments de menu et boutons de barre d’outils ont plusieurs États. Par exemple, un élément de menu est grisé (grisé) si elle n’est pas disponible dans le contexte actuel. Éléments de menu peuvent également être activée ou désactivée. Un bouton de barre d’outils peut également être désactivé dans le cas contraire, ou il peut être vérifiée.  
  
 Qui met à jour l’état de ces éléments de la modification des conditions du programme logiquement, si un élément de menu génère une commande qui est gérée par, par exemple, un document, il est judicieux pour que le document à mettre à jour l’élément de menu. Le document contient probablement les informations sur laquelle repose la mise à jour.  
  
 Si une commande contient plusieurs objets d’interface utilisateur (par exemple un élément de menu et un bouton de barre d’outils), ils sont routés vers la même fonction de gestionnaire. Ceci encapsule votre code de mise à jour de l’interface utilisateur pour tous les objets d’interface utilisateur équivalente dans un emplacement unique.  
  
 L’infrastructure offre une interface pratique pour la mise à jour automatique des objets d’interface utilisateur. Vous pouvez choisir d’effectuer la mise à jour d’une autre manière, mais l’interface fournie est efficace et facile à utiliser.  
  
 Les rubriques suivantes expliquent l’utilisation des gestionnaires de mise à jour :  
  
-   [Quand les gestionnaires de mise à jour sont appelés](../mfc/when-update-handlers-are-called.md)  
  
-   [La macro ON_UPDATE_COMMAND_UI](../mfc/on-update-command-ui-macro.md)  
  
-   [CCmdUI, classe](../mfc/the-ccmdui-class.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Menus](../mfc/menus-mfc.md)

