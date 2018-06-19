---
title: 'Comment : mettre à jour des objets d’Interface utilisateur | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 422be3d80614c526c7e634d22a0930458e4b4e26
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33346205"
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

