---
description: 'En savoir plus sur : gestion des menus, des barres de contrôles et des accélérateurs'
title: Gestion des menus, barres de contrôle et accélérateurs
ms.date: 11/04/2016
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
ms.openlocfilehash: 21c3791bff00c33db50efbe391863169606fde80
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97244171"
---
# <a name="managing-menus-control-bars-and-accelerators"></a>Gestion des menus, barres de contrôle et accélérateurs

La fenêtre frame gère la mise à jour des objets interface-utilisateur, notamment les menus, les boutons de la barre d'outils, la barre d'état et les accélérateurs. Elle gère également le partage de la barre de menus dans les applications MDI.

## <a name="managing-menus"></a>Gestion des menus

La fenêtre frame participe à la mise à jour des éléments de l’interface utilisateur à l’aide du mécanisme de ON_UPDATE_COMMAND_UI décrit dans [How to UPDATE User-Interface Objects](how-to-update-user-interface-objects.md). Les boutons des barres d'outils et d'autres barres de contrôle sont mis à jour lors de la boucle inactive. Les éléments composant les menus déroulants de la barre de menus sont mis à jour juste avant le déroulement du menu.

Pour les applications MDI, la fenêtre frame MDI gère la barre de menus et la légende. Une fenêtre frame MDI possède un menu par défaut utilisé comme barre de menus lorsqu'il n'y a aucune fenêtre enfant MDI active. Lorsqu'il existe des enfants actifs, la barre de menus de la fenêtre frame MDI est prise en charge par le menu de la fenêtre enfant MDI active. Si une application MDI prend en charge plusieurs types de document, tels que les documents composés de graphiques et de feuilles de calcul, chaque type place ses propres menus dans la barre de menus et modifie la légende de la fenêtre frame principale.

[CMDIFrameWnd](reference/cmdiframewnd-class.md) fournit des implémentations par défaut pour les commandes standard du menu fenêtre qui s’affiche pour les applications MDI. En particulier, la commande Nouvelle fenêtre (ID_WINDOW_NEW) est implémentée pour créer une fenêtre frame et une vue dans le document actif. Vous devez remplacer ces implémentations uniquement si vous avez besoin de fonctionnalités de personnalisation avancées.

Plusieurs fenêtres MDI enfants du même type de document partagent des ressources menu. Si plusieurs fenêtres enfants MDI sont créées par le même modèle de document, elles peuvent toutes utiliser la même ressource menu, épargnant ainsi les ressources système de Windows.

## <a name="managing-the-status-bar"></a>Gestion de la barre d'état

La fenêtre frame positionne également la barre d'état dans la zone cliente et gère les indicateurs de la barre d'état. La fenêtre frame efface et met à jour la zone de message dans la barre d’État si nécessaire et affiche des chaînes d’invite lorsque l’utilisateur sélectionne des éléments de menu ou des boutons de barre d’outils, comme décrit dans [comment afficher des informations de commande dans la barre d’État](how-to-display-command-information-in-the-status-bar.md).

## <a name="managing-accelerators"></a>Gestion des accélérateurs

Chaque fenêtre frame contient une table d'accélérateurs facultative qui interprète les raccourcis clavier automatiquement. Ce mécanisme simplifie ainsi la définition des touches accélérateur (également appelées touches de raccourci) qui appellent les commandes de menu.

## <a name="see-also"></a>Voir aussi

[Utilisation des fenêtres Frame](using-frame-windows.md)
