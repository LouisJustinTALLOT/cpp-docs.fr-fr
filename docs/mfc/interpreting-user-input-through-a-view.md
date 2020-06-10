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
ms.openlocfilehash: 43fb903fa169233ce532e41ecdf02c23ab6037c8
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84621463"
---
# <a name="interpreting-user-input-through-a-view"></a>Interprétation de l'entrée utilisateur via une vue

D’autres fonctions membres du handle de vue et interprètent toutes les entrées d’utilisateur. Vous allez généralement définir les fonctions membres du gestionnaire de messages dans votre classe d’affichage pour traiter les éléments suivants :

- [Messages](messages.md) Windows générés par des actions de la souris et du clavier.

- [Commandes](user-interface-objects-and-command-ids.md) à partir de menus, de boutons de barre d’outils et de touches accélérateur.

Ces fonctions membres du gestionnaire de messages interprètent les actions suivantes comme entrée, sélection ou modification de données, y compris le déplacement des données vers et depuis le presse-papiers :

- Mouvements et clics de la souris, glissement et double-clics

- Séquences

- Commandes de menu

Les messages Windows que votre vue gère dépendent des besoins de votre application.

[Rubriques relatives à la gestion et au mappage des messages](message-handling-and-mapping.md) explique comment assigner des éléments de menu et d’autres objets d’interface utilisateur à des commandes et comment lier les commandes aux fonctions de gestionnaire. Les rubriques sur la [gestion et le mappage des messages](message-handling-and-mapping.md) expliquent également comment les MFC acheminent les commandes et envoient des messages Windows standard aux objets qui contiennent des gestionnaires pour eux.

Par exemple, votre application peut avoir besoin d’implémenter un dessin direct de la souris dans la vue. L’exemple SCRIBBLE montre comment gérer les messages WM_LBUTTONDOWN, WM_MOUSEMOVE et WM_LBUTTONUP respectivement pour commencer, continuer et terminer le dessin d’un segment de ligne. En revanche, vous pouvez parfois avoir besoin d’interpréter un clic de souris dans votre affichage comme une sélection. La fonction de gestionnaire de votre vue `OnLButtonDown` détermine si l’utilisateur a dessiné ou sélectionné. Si vous sélectionnez cette option, le gestionnaire détermine si le clic était dans les limites d’un objet dans la vue et, si tel est le cas, modifie l’affichage pour afficher l’objet tel qu’il est sélectionné.

Votre affichage peut également gérer certaines commandes de menu, telles que celles du menu Edition pour couper, copier, coller ou supprimer des données sélectionnées à l’aide du presse-papiers. Un tel gestionnaire appellera les fonctions membres associées au Presse-papiers de la classe `CWnd` pour transférer un élément de données sélectionné vers ou depuis le presse-papiers.

## <a name="see-also"></a>Voir aussi

[Utilisation des vues](using-views.md)
