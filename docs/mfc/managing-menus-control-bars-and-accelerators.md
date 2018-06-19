---
title: Gestion des Menus, barres de contrôle et accélérateurs | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MDI [MFC], frame windows
- control bars [MFC], updating in frame windows
- menus [MFC], updating as context changes
- user interface objects [MFC], updating
- accelerator tables [MFC]
- sharing menus [MFC]
- updating user-interface objects [MFC]
- frame windows [MFC], updating
- status bars [MFC], updating
ms.assetid: 97ca1997-06df-4373-b023-4f7ecd81047b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1055fd9b1ef75b2090478d85e8251d1800b8b039
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33345740"
---
# <a name="managing-menus-control-bars-and-accelerators"></a>Gestion des menus, barres de contrôle et accélérateurs
La fenêtre frame gère la mise à jour des objets interface-utilisateur, notamment les menus, les boutons de la barre d'outils, la barre d'état et les accélérateurs. Elle gère également le partage de la barre de menus dans les applications MDI.  
  
## <a name="managing-menus"></a>Gestion des menus  
 La fenêtre frame participe à la mise à jour des éléments d’interface utilisateur à l’aide de la `ON_UPDATE_COMMAND_UI` mécanisme décrit dans [comment les objets d’Interface utilisateur de mise à jour](../mfc/how-to-update-user-interface-objects.md). Les boutons des barres d'outils et d'autres barres de contrôle sont mis à jour lors de la boucle inactive. Les éléments composant les menus déroulants de la barre de menus sont mis à jour juste avant le déroulement du menu.  
  
 Pour les applications MDI, la fenêtre frame MDI gère la barre de menus et la légende. Une fenêtre frame MDI possède un menu par défaut utilisé comme barre de menus lorsqu'il n'y a aucune fenêtre enfant MDI active. Lorsqu'il existe des enfants actifs, la barre de menus de la fenêtre frame MDI est prise en charge par le menu de la fenêtre enfant MDI active. Si une application MDI prend en charge plusieurs types de document, tels que les documents composés de graphiques et de feuilles de calcul, chaque type place ses propres menus dans la barre de menus et modifie la légende de la fenêtre frame principale.  
  
 [CMDIFrameWnd](../mfc/reference/cmdiframewnd-class.md) fournit des implémentations par défaut pour les commandes standard dans le menu Fenêtre qui s’affiche pour les applications MDI. En particulier, la commande nouvelle fenêtre (**ID_WINDOW_NEW**) est implémentée pour créer une nouvelle fenêtre frame et la vue sur le document actif. Vous devez remplacer ces implémentations uniquement si vous avez besoin de fonctionnalités de personnalisation avancées.  
  
 Plusieurs fenêtres MDI enfants du même type de document partagent des ressources menu. Si plusieurs fenêtres enfants MDI sont créées par le même modèle de document, elles peuvent toutes utiliser la même ressource menu, épargnant ainsi les ressources système de Windows.  
  
## <a name="managing-the-status-bar"></a>Gestion de la barre d'état  
 La fenêtre frame positionne également la barre d'état dans la zone cliente et gère les indicateurs de la barre d'état. La fenêtre frame efface la zone de message dans la barre d’état des mises à jour en fonction des besoins et affiche les chaînes d’invite lorsque l’utilisateur sélectionne des éléments de menu ou des boutons de barre d’outils, comme décrit dans [affichage des informations de commande dans la barre d’état](../mfc/how-to-display-command-information-in-the-status-bar.md).  
  
## <a name="managing-accelerators"></a>Gestion des accélérateurs  
 Chaque fenêtre frame contient une table d'accélérateurs facultative qui interprète les raccourcis clavier automatiquement. Ce mécanisme simplifie ainsi la définition des touches accélérateur (également appelées touches de raccourci) qui appellent les commandes de menu.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation de fenêtres frame](../mfc/using-frame-windows.md)

