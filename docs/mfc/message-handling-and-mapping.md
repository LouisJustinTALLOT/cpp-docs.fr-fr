---
title: Gestion et mappage des messages | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC, messages
- message handling [MFC]
- message maps [MFC]
ms.assetid: 62fe2a1b-944c-449d-a0f0-63c11ee0a3cb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 11ac9e794aef374012f2b15faa7e93b907f6a15c
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/29/2018
ms.locfileid: "43194539"
---
# <a name="message-handling-and-mapping"></a>Gestion et mappage des messages
Cette série d’articles décrit comment les messages et commandes sont traités par l’infrastructure MFC et comment les connecter à leurs fonctions gestionnaires.  
  
 Dans les programmes traditionnels pour Windows, les messages Windows sont gérés dans une instruction switch étendue dans une procédure de fenêtre. MFC utilise à la place [tables des messages](../mfc/message-categories.md) pour mapper les messages directs aux fonctions membres de classe distincte. Tables des messages sont plus efficaces que les fonctions virtuelles dans ce but, et ils permettent des messages d’être traités par l’objet C++ plus approprié : application, document, vue et ainsi de suite. Vous pouvez mapper un seul message ou une plage de messages, l’ID de commande, ou ID de contrôle.  
  
 Messages WM_COMMAND, généralement généré par les menus, des boutons de barre d’outils ou des accélérateurs — également utiliser le mécanisme de table des messages. MFC définit une norme [routage](../mfc/command-routing.md) des messages de commande entre l’application, le frame fenêtre, vue et des documents actifs dans votre programme. Vous pouvez remplacer ce routage si vous avez besoin.  
  
 Tables des messages également fournissent un moyen pour mettre à jour des objets d’interface utilisateur (par exemple, les menus et boutons de barre d’outils), l’activation ou de les désactiver en fonction du contexte actuel.  
  
 Pour obtenir des informations générales sur les messages et les files d’attente dans Windows, consultez [Messages et les files d’attente](https://msdn.microsoft.com/library/windows/desktop/ms632590) dans le SDK Windows.  
  
## <a name="what-do-you-want-to-know-more-about"></a>Ce que vous souhaitez en savoir plus sur  
  
-   [Messages et commandes dans le Framework](../mfc/messages-and-commands-in-the-framework.md)  
  
-   [Comment le framework appelle un gestionnaire de messages](../mfc/how-the-framework-calls-a-handler.md)  
  
-   [Comment le Framework effectue des recherches dans les tables des messages](../mfc/how-the-framework-searches-message-maps.md)  
  
-   [Déclaration des fonctions de gestionnaire de messages](../mfc/declaring-message-handler-functions.md)  
  
-   [Mappage des messages à des fonctions](../mfc/reference/mapping-messages-to-functions.md)  
  
-   [Comment afficher des informations sur les commandes dans la barre d’état](../mfc/how-to-display-command-information-in-the-status-bar.md)  
  
-   [Mise à jour dynamique des objets d’interface utilisateur](../mfc/how-to-update-user-interface-objects.md)  
  
-   [Guide pratique pour créer une table des messages pour une classe de modèle](../mfc/how-to-create-a-message-map-for-a-template-class.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Concepts](../mfc/mfc-concepts.md)   
 [Rubriques MFC générales](../mfc/general-mfc-topics.md)   
 [CWnd, classe](../mfc/reference/cwnd-class.md)   
 [CCmdTarget, classe](../mfc/reference/ccmdtarget-class.md)
