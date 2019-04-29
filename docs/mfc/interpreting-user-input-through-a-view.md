---
title: Interprétation de l'entrée utilisateur via une vue
ms.date: 11/04/2016
helpviewer_keywords:
- interpreting user input through views [MFC]
- views [MFC], user interface and input
- input [MFC], view class [MFC]
- CView class [MFC], interpreting user input
- user input [MFC], interpreting through view class [MFC]
ms.assetid: f0302a70-661f-4781-8fe7-78f082bef2a5
ms.openlocfilehash: 3ef23ad74e1ff53d947453faa5682c5ecc1f4e43
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62310914"
---
# <a name="interpreting-user-input-through-a-view"></a>Interprétation de l'entrée utilisateur via une vue

Autres fonctions membres de la vue gèrent et interprètent toutes les entrées utilisateur. Vous définirez généralement des fonctions membres de gestionnaire de messages dans votre classe d’affichage à traiter :

- Windows [messages](../mfc/messages.md) générées par les actions de souris et clavier.

- [Commandes](../mfc/user-interface-objects-and-command-ids.md) à partir des menus, boutons de barre d’outils et touches accélérateur.

Ces fonctions membres de gestionnaire de messages interprètent les actions suivantes en tant qu’entrée de données, la sélection ou la modification, y compris le déplacement des données vers et depuis le Presse-papiers :

- Mouvements de souris et de clics, fait glisser des double-clics

- Séquences de touches

- Commandes de menu

Les messages Windows votre vue gère varie selon les besoins de votre application.

[Gestion et mappage de message](../mfc/message-handling-and-mapping.md) explique comment affecter des éléments de menu et autres objets d’interface utilisateur aux commandes et comment lier les commandes aux fonctions de gestionnaire. [Gestion et mappage de message](../mfc/message-handling-and-mapping.md) également explique comment MFC achemine les commandes et envoie les messages Windows standard pour les objets qui contiennent les gestionnaires.

Par exemple, votre application peut avoir besoin implémenter le dessin dans la vue directe de la souris. L’exemple Scribble montre comment gérer les messages WM_LBUTTONDOWN, WM_MOUSEMOVE et WM_LBUTTONUP respectivement pour commencer, continuer et terminer le dessin d’un segment de ligne. En revanche, vous devrez peut-être parfois interpréter un clic de souris dans votre vue comme une sélection. De votre vue `OnLButtonDown` fonction gestionnaire déterminait si l’utilisateur a été de dessin ou en sélectionnant. Si vous sélectionnez, le gestionnaire détermine si le clic a été dans les limites d’un objet dans la vue et, le cas échéant, de modifier l’affichage pour afficher l’objet sélectionné.

Votre vue peut également gérer certaines commandes de menu, telles que celles dans le menu Edition pour couper, copier, coller ou supprimer des données sélectionnées à l’aide du Presse-papiers. Ce gestionnaire serait certaines liées au Presse-papiers du membre de l’appeler des fonctions de classe `CWnd` pour transférer un élément de données sélectionné vers ou depuis le Presse-papiers.

## <a name="see-also"></a>Voir aussi

[Utilisation de vues](../mfc/using-views.md)
