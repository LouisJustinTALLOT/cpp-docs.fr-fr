---
title: Objets d’Interface utilisateur et l’ID de commande | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- keyboard shortcuts, associating with IDs
- MFC, command routing
- toolbar controls [MFC], command ID
- menu items, associating with IDs
- user interface objects [MFC], associating with IDs
- command IDs, user interface objects
- command routing [MFC], MFC
- command handling [MFC], user-interface objects
ms.assetid: 4ea19e9b-ed1e-452e-bd33-7f509107a45b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6b56babf0e42dde521a6bda3a7d9713db519182c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33385597"
---
# <a name="user-interface-objects-and-command-ids"></a>Objets d'interface utilisateur et ID de commande
Éléments de menu, des boutons de barre d’outils et touches accélérateur sont « objets interface utilisateur » capables de générer des commandes. Chacun de ces objets interface utilisateur ait un ID. Vous associez un objet d’interface utilisateur une commande en affectant le même ID à l’objet et de la commande. Comme expliqué dans [Messages](../mfc/messages.md), commandes sont implémentées en tant que messages spéciaux. L’illustration « Commandes dans la structure » ci-dessous montre comment le framework gère les commandes. Lorsqu’un objet d’interface utilisateur génère une commande, tel que `ID_EDIT_CLEAR_ALL`, un des objets dans votre application gère la commande, dans la figure ci-dessous, l’objet de document `OnEditClearAll` fonction est appelée via la table des messages du document.  
  
 ![Commandes dans le Framework](../mfc/media/vc385p1.gif "vc385p1")  
Commandes dans le Framework  
  
 La figure « Commande mise à jour dans la structure » ci-dessous montre comment MFC met à jour les objets d’interface utilisateur tels que les éléments de menu et boutons de barre d’outils. Avant d’un menu déroulant, ou pendant la boucle inactive dans le cas des boutons de barre d’outils, MFC achemine une commande de mise à jour. Dans la figure ci-dessous, l’objet document appelle son gestionnaire de commandes de mise à jour, `OnUpdateEditClearAll`, pour activer ou désactiver l’objet d’interface utilisateur.  
  
 ![Mise à jour dans le cadre de la commande](../mfc/media/vc385p2.png "vc385p2")  
La mise à jour d’une commande dans le Framework  
  
## <a name="see-also"></a>Voir aussi  
 [Messages et commandes dans le Framework](../mfc/messages-and-commands-in-the-framework.md)

