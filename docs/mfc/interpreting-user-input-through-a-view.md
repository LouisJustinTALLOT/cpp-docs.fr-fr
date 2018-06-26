---
title: Interprétation de l’entrée utilisateur via une vue | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- interpreting user input through views [MFC]
- views [MFC], user interface and input
- input [MFC], view class [MFC]
- CView class [MFC], interpreting user input
- user input [MFC], interpreting through view class [MFC]
ms.assetid: f0302a70-661f-4781-8fe7-78f082bef2a5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f62d64ed9479f1d1003536f8c4944b53d04d696f
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2018
ms.locfileid: "36931988"
---
# <a name="interpreting-user-input-through-a-view"></a>Interprétation de l'entrée utilisateur via une vue
Autres fonctions membres de la vue de gérer et interprètent toutes les entrées utilisateur. Vous allez généralement définir des fonctions membres de gestionnaire de messages dans votre classe d’affichage à traiter :  
  
-   Windows [messages](../mfc/messages.md) générées par les actions de la souris et du clavier.  
  
-   [Commandes](../mfc/user-interface-objects-and-command-ids.md) à partir des menus, boutons de barre d’outils et touches accélérateur.  
  
 Ces fonctions membres de gestionnaire de messages interprètent les actions ci-dessous comme données d’entrée, la sélection ou la modification, notamment le déplacement des données vers et depuis le Presse-papiers :  
  
-   Mouvements de souris et les clics, fait glisser des double-clics  
  
-   Séquences de touches  
  
-   Commandes de menu  
  
 Les messages Windows votre vue gère varie selon les besoins de votre application.  
  
 [Gestion et mappage des messages](../mfc/message-handling-and-mapping.md) explique comment assigner des éléments de menu et autres objets d’interface utilisateur pour les commandes et comment lier les commandes aux fonctions de gestionnaire. [Gestion et mappage des messages](../mfc/message-handling-and-mapping.md) également explique comment MFC achemine les commandes et envoie les messages Windows standard pour les objets qui contiennent les gestionnaires.  
  
 Par exemple, votre application peut avoir besoin implémentation directe de la souris dans la vue de dessin. L’exemple Scribble montre comment gérer les messages WM_LBUTTONDOWN, WM_MOUSEMOVE et WM_LBUTTONUP respectivement pour commencer, continuer et terminer le dessin d’un segment de ligne. En revanche, vous devrez peut-être parfois interpréter un clic de souris dans votre vue comme une sélection. De votre vue `OnLButtonDown` fonction gestionnaire détermine si l’utilisateur a été de dessin ou en sélectionnant. Si vous sélectionnez, le gestionnaire détermine si le clic a été dans les limites d’un objet dans la vue et, le cas échéant, modifiez l’affichage pour afficher l’objet sélectionné.  
  
 Votre vue peut également gérer certaines commandes de menu, telles que celles dans le menu Edition pour couper, copier, coller ou supprimer des données sélectionnées à l’aide du Presse-papiers. Un gestionnaire de ce type appelle alors certaines du membre liées au Presse-papiers fonctions de la classe `CWnd` pour transférer un élément de données sélectionné vers ou depuis le Presse-papiers.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation de vues](../mfc/using-views.md)

